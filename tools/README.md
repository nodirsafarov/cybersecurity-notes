# Tools

Personal notes on the tools I use day-to-day for offensive security work.
Each note covers my own workflow — not a manual replacement, just the
configuration tweaks and shortcuts I have actually validated.

## Index

- [Burp Suite — Configuration & Workflow](./burp-suite.md) *(WIP)*
- [Nmap — Scan recipes I rely on](./nmap.md) *(WIP)*
- [BloodHound — Custom Cypher queries](./bloodhound.md) *(WIP)*
- [Impacket — Cheatsheet](./impacket.md) *(WIP)*
- [Metasploit — Common modules and quirks](./metasploit.md) *(WIP)*
- [SQLmap — Tricky flags I keep forgetting](./sqlmap.md) *(WIP)*
- [Hashcat — Mode reference and rule files](./hashcat.md) *(WIP)*
- [ffuf — Wordlists and filter recipes](./ffuf.md) *(WIP)*

---

## My toolkit, by category

### Web
- **Burp Suite Community** — primary intercepting proxy
- **OWASP ZAP** — fallback / open-source comparison
- **SQLmap** — automated SQLi exploitation
- **ffuf / gobuster / dirsearch** — content discovery
- **Nikto** — quick low-hanging-fruit scanner
- **WPScan** — WordPress-specific
- **Wfuzz** — parameter / wordlist fuzzing

### Network & AD
- **Nmap** — universal port scanner
- **BloodHound** + **SharpHound** — AD attack path analysis
- **CrackMapExec** — SMB / WinRM Swiss army knife
- **Impacket** suite — Python implementations of Windows protocols
- **Evil-WinRM** — interactive WinRM shell
- **Responder** — LLMNR / NBT-NS poisoning
- **Wireshark** — packet analysis

### Exploitation
- **Metasploit Framework** — exploits + post-exploitation
- **Searchsploit** — local Exploit-DB lookup
- **Hydra** / **Medusa** — service brute-force

### Password attacks
- **John the Ripper** — versatile cracker
- **Hashcat** — GPU-accelerated cracking
- **kerbrute** — Kerberos username enumeration
- **CeWL** — wordlist generator from web pages

### Privilege escalation
- **LinPEAS** / **WinPEAS** — automated privesc enumeration
- **linux-smart-enumeration (lse.sh)** — alternative for Linux
- **PowerUp.ps1** — Windows privesc checks

---

## Setup notes

### Burp Suite — JVM tuning for big projects
```bash
java -Xmx4g -jar burpsuite_community.jar
```

### Add a Burp custom keybinding for "Send to Repeater + switch tab"
`User options → Hotkeys → Send to Repeater (jump to)` → bind to `Ctrl+R`.

### Always-on alias collection
```bash
# ~/.zshrc snippet
alias nmap-quick='nmap -T4 -F'
alias nmap-full='sudo nmap -sC -sV -p- --min-rate=2000'
alias serve='python3 -m http.server 8000'
alias listen='nc -lvnp 4444'
alias rlisten='rlwrap -cAr nc -lvnp 4444'
alias urlencode='python3 -c "import urllib.parse,sys;print(urllib.parse.quote(sys.argv[1]))"'
alias urldecode='python3 -c "import urllib.parse,sys;print(urllib.parse.unquote(sys.argv[1]))"'
alias b64enc='base64 -w0'
alias b64dec='base64 -d'
```
