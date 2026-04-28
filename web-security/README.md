# Web Security

Notes on web application vulnerabilities, organised by OWASP Top 10 and personal experience from PortSwigger Web Security Academy, HackTheBox web challenges, and TryHackMe.

## Index

### Injection
- [SQL Injection](./sql-injection.md) *(WIP)*
- [Command Injection](./command-injection.md) *(WIP)*
- [Server-Side Template Injection (SSTI)](./ssti.md) *(WIP)*

### Cross-Site Scripting
- [XSS — Reflected, Stored, DOM-based](./xss.md) *(WIP)*

### Server-Side Request Forgery
- [SSRF Bypasses](./ssrf.md) *(WIP)*

### Access Control
- [IDOR — Insecure Direct Object References](./idor.md) *(WIP)*
- [Broken Access Control patterns](./broken-access.md) *(WIP)*

### Authentication
- [JWT Attacks](./jwt.md) *(WIP)*
- [Session Fixation & Hijacking](./session-attacks.md) *(WIP)*
- [Password Reset Vulnerabilities](./password-reset.md) *(WIP)*

### File Operations
- [File Upload Bypasses](./file-upload.md) *(WIP)*
- [LFI / RFI](./lfi-rfi.md) *(WIP)*
- [Path Traversal](./path-traversal.md) *(WIP)*

### Other
- [XXE — XML External Entity](./xxe.md) *(WIP)*
- [Deserialization Attacks](./deserialization.md) *(WIP)*
- [Race Conditions](./race-conditions.md) *(WIP)*

---

## My testing methodology

For every web target I follow this loop until coverage feels complete:

1. **Recon** — full port scan, subdomain enumeration, technology fingerprinting (Wappalyzer / `whatweb`)
2. **Mapping** — Burp Suite passive crawl, manual browsing of every functional area
3. **Content discovery** — `ffuf` / `gobuster dir` with appropriate wordlists for the stack
4. **Authentication probing** — guessable creds, default accounts, password spray, account enumeration
5. **Authenticated walk-through** — IDOR, BAC, business logic, hidden parameters (`Arjun`, `paramspider`)
6. **Per-input fuzzing** — every parameter through Burp Intruder for SQLi, XSS, command injection, SSRF
7. **Out-of-band** — Burp Collaborator for blind injections and SSRF-to-internal
8. **Reporting** — every finding documented with PoC, impact, remediation

---

## Burp Suite extensions I rely on

| Extension | Use case |
|---|---|
| **Active Scan++** | Adds checks Burp Pro misses |
| **JWT Editor** | JWT decoding, signing, alg confusion |
| **Logger++** | Persistent request log across sessions |
| **Hackvertor** | Tag-based encoding/encryption helper |
| **Param Miner** | Hidden parameter discovery |
| **Turbo Intruder** | Fast race-condition testing |
| **Authorize** | Quick BAC/IDOR detection |
| **Autorize** | Same idea, different workflow |

---

## Wordlists I keep handy

```
/usr/share/seclists/Discovery/Web-Content/raft-large-words.txt        # generic content discovery
/usr/share/seclists/Discovery/Web-Content/api/api-endpoints.txt        # API enumeration
/usr/share/seclists/Discovery/Web-Content/burp-parameter-names.txt     # hidden params
/usr/share/seclists/Fuzzing/SQLi/Generic-SQLi.txt                      # SQLi fuzz
/usr/share/seclists/Fuzzing/XSS/XSS-Jhaddix.txt                        # XSS fuzz
/usr/share/seclists/Passwords/xato-net-10-million-passwords-1000.txt   # spraying
```

---

## References

- [OWASP Web Security Testing Guide v4.2](https://owasp.org/www-project-web-security-testing-guide/v42/)
- [PortSwigger Web Security Academy](https://portswigger.net/web-security)
- [HackTricks — Pentesting Web](https://book.hacktricks.xyz/pentesting-web/web-vulnerabilities-methodology)
- [PayloadsAllTheThings](https://github.com/swisskyrepo/PayloadsAllTheThings)
