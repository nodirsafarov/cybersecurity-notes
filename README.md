<div align="center">

#  Cybersecurity Notes — for Newcomers

**Hand-picked offensive security notes written for people just entering the field.**

<p>
  <img src="https://img.shields.io/badge/For-Newcomers-c12127?style=flat-square" />
  <img src="https://img.shields.io/badge/Focus-Offensive%20Security-000000?style=flat-square" />
  <img src="https://img.shields.io/badge/OWASP-Top%2010-000000?style=flat-square&logo=owasp&logoColor=white" />
  <img src="https://img.shields.io/badge/Active%20Directory-Red%20Team-d32f2f?style=flat-square" />
  <img src="https://img.shields.io/badge/Status-Living%20Document-success?style=flat-square" />
  <img src="https://img.shields.io/badge/License-CC%20BY--SA%204.0-yellow?style=flat-square" />
</p>

</div>

---

##  Who this is for

If you are **just entering cybersecurity** and you keep getting buried under giant
references like HackTricks, PayloadsAllTheThings, or PortSwigger — this repo is for you.

Each note here is:

-  **Distilled** — only the stuff you actually need for your first 10 boxes / labs
-  **Practical** — every command shown was run in a real lab, not copy-pasted from a wiki
-  **Newcomer-friendly** — minimal jargon, plenty of "why" not just "how"
-  **Mapped to free platforms** — HTB Academy, TryHackMe, PortSwigger Web Academy, free CTFs

I write these as **I learn them**. If a topic is here, I have actually tested it.
If something is missing, I haven't gotten there yet — [open an issue](https://github.com/nodirsafarov/cybersecurity-notes/issues)
and tell me what you'd like to see next.

---

##  How to use this repo

If you are brand new to offensive security, follow this order — it matches the path
that worked for me:

1. **Methodology** → [`methodology/`](./methodology/) — learn the frameworks before the tools
2. **Cheatsheets** → [`cheatsheets/`](./cheatsheets/) — print these out, you'll need them
3. **Web Security** → [`web-security/`](./web-security/) — start with OWASP Top 10
4. **Active Directory** → [`active-directory/`](./active-directory/) — once web feels comfortable
5. **Tools** → [`tools/`](./tools/) — deepen knowledge of the toolkit you already use
6. **Writeups** → [`writeups/`](./writeups/) — see the methodology applied to real boxes

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

##  Want to contribute?

This repo is **for newcomers, by a newcomer** — so contributions are extra welcome:

-  **Found a typo or unclear sentence?** → open a PR
-  **Have a clearer way to explain a concept?** → open a PR
-  **Stuck on a topic?** → open an issue, I'll write a note for it
-  **Want to add your own writeup?** → open a PR with the file in `writeups/`

No PR is too small. Even fixing a single command improves the resource for the next learner.

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
