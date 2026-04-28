# Methodology

The frameworks I use to structure pentest engagements and lab work — keeps me from
chasing tangents and missing whole categories of vulnerabilities.

##  Featured

###  [PTES Web Pentest Cheatsheet](./ptes-web-cheatsheet.md)
A task-oriented web penetration testing cheatsheet structured around the seven PTES phases.
For every task you get the **tools** and the **websites** that help you do it — clickable.

**Coverage:** 52 tasks across 7 phases — ~140 tools, ~95 websites.

---

##  Index

- [**PTES Web Pentest Cheatsheet**](./ptes-web-cheatsheet.md) ✅
- [OWASP Web Security Testing Guide v4.2](./owasp-wstg.md) *(WIP)*
- [Cyber Kill Chain](./cyber-kill-chain.md) *(WIP)*
- [Pentest Report Structure](./report-structure.md) *(WIP)*

---

##  My personal engagement flow

```
1. Scope confirmation       (read SOW / RoE, confirm IP ranges)
2. Recon                    (passive, then active)
3. Mapping                  (build attack surface inventory)
4. Vulnerability discovery  (manual + automated)
5. Exploitation             (chain to highest impact)
6. Post-exploitation        (lateral, privesc, data access)
7. Cleanup                  (revert changes, document IoCs)
8. Reporting                (executive + technical sections)
9. Retest                   (validate remediation)
```

Most of my time goes into **2-4 (recon → discovery)**. Exploitation is usually the
fastest phase if recon was thorough.

---

##  References

- [PTES Technical Guidelines](http://www.pentest-standard.org/index.php/Main_Page)
- [OWASP WSTG v4.2](https://owasp.org/www-project-web-security-testing-guide/v42/)
- [NIST SP 800-115 — Technical Guide to Information Security Testing](https://csrc.nist.gov/publications/detail/sp/800-115/final)
