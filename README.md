<div align="center">

#  Cybersecurity Notes

**My personal knowledge base for offensive security — Web Pentesting & Red Team.**

<p>
  <img src="https://img.shields.io/badge/Focus-Offensive%20Security-c12127?style=flat-square" />
  <img src="https://img.shields.io/badge/OWASP-Top%2010-000000?style=flat-square&logo=owasp&logoColor=white" />
  <img src="https://img.shields.io/badge/Active%20Directory-Red%20Team-d32f2f?style=flat-square" />
  <img src="https://img.shields.io/badge/Status-Living%20Document-success?style=flat-square" />
  <img src="https://img.shields.io/badge/License-CC%20BY--SA%204.0-yellow?style=flat-square" />
</p>

</div>

---

##  About

A second-brain for everything I learn during HackTheBox machines, TryHackMe rooms,
PortSwigger Web Security Academy labs, and CTFs — focused on **Web Application
Penetration Testing** and **Active Directory / Red Team** tradecraft.

Each note here is:

-  **Practical** — every command shown was run in a real lab, not copy-pasted from a wiki
-  **Concise** — kept to the essentials I actually reach for during engagements
-  **Tested** — only what I have validated in my own environment makes it in

This is my own working reference — if it's here, I have actually used it.

---

##  Repository Map

| Folder | What's inside |
|---|---|
| [`web-security/`](./web-security/) | OWASP Top 10 walkthroughs — SQLi, XSS, SSRF, IDOR, SSTI, auth flaws |
| [`active-directory/`](./active-directory/) | AD attacks — Kerberoasting, AS-REP, ACL abuse, DCSync, lateral movement |
| [`tools/`](./tools/) | Tool-specific notes — Burp Suite, Nmap, BloodHound, Impacket, Metasploit |
| [`methodology/`](./methodology/) | OWASP Testing Guide, PTES, Cyber Kill Chain, MITRE ATT&CK mapping |
| [`writeups/`](./writeups/) | HTB / TryHackMe / CTF writeups (after machines retire) |
| [`cheatsheets/`](./cheatsheets/) | Quick-reference one-pagers for engagements |
| [`resources/`](./resources/) | Curated links — blogs, courses, books, CVE references |

---

##  Featured Notes

###  Web Security
- [SQL Injection — Manual Exploitation Cheatsheet](./web-security/sql-injection.md)
- [XSS — Reflected, Stored, DOM-based](./web-security/xss.md)
- [SSRF — Bypasses & Internal Service Discovery](./web-security/ssrf.md)
- [IDOR — Finding & Exploiting Access Control Flaws](./web-security/idor.md)
- [File Upload Bypass Techniques](./web-security/file-upload.md)

###  Active Directory
- [AD Enumeration Workflow](./active-directory/enumeration.md)
- [Kerberoasting & AS-REP Roasting](./active-directory/kerberoasting.md)
- [BloodHound — Attack Path Analysis](./active-directory/bloodhound.md)
- [Lateral Movement & Pivoting](./active-directory/lateral-movement.md)

###  Cheatsheets
- [Reverse Shells One-Liner Reference](./cheatsheets/reverse-shells.md)
- [Linux Privilege Escalation](./cheatsheets/linpriv.md)
- [Windows Privilege Escalation](./cheatsheets/winpriv.md)

> ⚠️ Some files above are **work in progress** — I add a new note after every machine
> I solve. Watch the repo to follow along.

---

##  Methodology I follow

### For web targets
1.  **Recon** — `nmap -sC -sV -p- target` · `ffuf` · subdomain enumeration · technology fingerprinting
2.  **Mapping** — Burp Suite passive crawl · `gobuster dir` · spider authenticated areas
3.  **OWASP Top 10 sweep** — manual checks against each category
4.  **Authenticated testing** — IDOR, BAC, business-logic flaws
5.  **Documentation** — capture every step in Markdown for the report

### For Active Directory targets
1.  **External recon** — `nmap` · service enumeration on 53/88/389/445/636
2.  **Initial foothold** — null session enumeration · password spraying · phishing simulation
3.  **Domain enumeration** — BloodHound + SharpHound · `ldapsearch` · `rpcclient`
4.  **Privilege escalation** — Kerberoasting · AS-REP Roasting · ACL abuse · DACL chains
5.  **Lateral movement** — Pass-the-Hash · Pass-the-Ticket · psexec/wmiexec
6.  **Domain dominance** — DCSync · Golden/Silver Tickets · NTDS.dit dump
7.  **Cleanup & report** — log artifacts, write the engagement narrative

---

##  Currently Learning

- [ ] Mastering Active Directory attack chains end-to-end (PEH / CRTP path)
- [ ] PortSwigger Web Security Academy — Advanced topics
- [ ] OSCP-style enumeration discipline
- [ ] Custom Python tooling for recon automation
- [ ] Pentest report writing (engagement narrative + technical findings)

---

##  Contributions

If you spot something wrong, outdated, or unclear:

-  **Found a typo or unclear sentence?** → open a PR
-  **Have a sharper way to explain a concept?** → open a PR
-  **Want to add your own writeup?** → open a PR with the file in `writeups/`

PRs of any size welcome.

---

##  Stats

This repo grows with every machine I solve. Below is a rough running count of notes added
per category — updated as I publish.

```
web-security/      ████████████░░░░░░░░  pending notes
active-directory/  ██████████░░░░░░░░░░  pending notes
tools/             ████████░░░░░░░░░░░░  pending notes
writeups/          ██████░░░░░░░░░░░░░░  pending notes
cheatsheets/       ████░░░░░░░░░░░░░░░░  pending notes
```

---

##  Resources I rely on

- **HackTricks** — https://book.hacktricks.xyz/
- **PayloadsAllTheThings** — https://github.com/swisskyrepo/PayloadsAllTheThings
- **PortSwigger Web Security Academy** — https://portswigger.net/web-security
- **The Hacker Recipes** — https://www.thehacker.recipes/
- **Pentestmonkey** — http://pentestmonkey.net/
- **GTFOBins / LOLBAS** — for living-off-the-land binaries

---

##  License

Notes are released under [Creative Commons BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) —
free to share and adapt with attribution.

Code snippets are MIT.

---

<div align="center">

Maintained by **[@nodirsafarov](https://github.com/nodirsafarov)** —
Junior Penetration Tester from Tashkent, Uzbekistan.

[ ![](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://linkedin.com/in/nodir-safarov-a717703a1)
[ ![](https://img.shields.io/badge/Telegram-26A5E4?style=flat-square&logo=telegram&logoColor=white)](https://t.me/nodir_1000000000)
[ ![](https://img.shields.io/badge/Email-EA4335?style=flat-square&logo=gmail&logoColor=white)](mailto:nodirsafarov32@gmail.com)

</div>
