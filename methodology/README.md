# Methodology

The frameworks I use to structure pentest engagements and lab work — keeps me from
chasing tangents and missing whole categories of vulnerabilities.

## Index

- [OWASP Web Security Testing Guide v4.2](./owasp-wstg.md) *(WIP)*
- [PTES — Penetration Testing Execution Standard](./ptes.md) *(WIP)*
- [Cyber Kill Chain](./cyber-kill-chain.md) *(WIP)*
- [MITRE ATT&CK Mapping](./mitre-attack.md) *(WIP)*
- [Pentest Report Structure](./report-structure.md) *(WIP)*

---

## How frameworks fit together

| Phase | OWASP WSTG | PTES | Kill Chain | MITRE ATT&CK |
|---|---|---|---|---|
| Pre-engagement | — | Pre-engagement Interactions | — | — |
| Intel gathering | Information Gathering | Intelligence Gathering | Reconnaissance | TA0043 Reconnaissance |
| Threat modeling | Configuration Mgmt | Threat Modeling | Weaponization | TA0042 Resource Development |
| Vuln discovery | Identity, Auth, Authz, … | Vulnerability Analysis | Delivery / Exploitation | TA0001 / TA0002 |
| Exploitation | (per category) | Exploitation | Installation | TA0003 Persistence |
| Post-exploitation | — | Post-Exploitation | Command & Control | TA0011 C2 / TA0008 Lateral |
| Reporting | — | Reporting | Actions on Objectives | (output) |

---

## My personal engagement flow

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

## What HR / hiring managers want to see

For Junior Pentester roles, I focus on demonstrating I can:

- ✅ Follow a **systematic methodology** (not "spray and pray")
- ✅ Document findings with **PoC, impact, remediation** sections
- ✅ Map attacks to **MITRE ATT&CK** — defensive teams expect this
- ✅ Communicate technical findings to **non-technical stakeholders**
- ✅ Use **OWASP Top 10 / WSTG** as a checklist for web targets
- ✅ Distinguish **PTES phases** clearly in reports

These are the soft-skill signals interviewers actually grade — technical depth is
table-stakes, methodology discipline is what separates juniors from "noise".

---

## References

- [OWASP WSTG v4.2](https://owasp.org/www-project-web-security-testing-guide/v42/)
- [PTES Technical Guidelines](http://www.pentest-standard.org/index.php/Main_Page)
- [Lockheed Martin Cyber Kill Chain](https://www.lockheedmartin.com/en-us/capabilities/cyber/cyber-kill-chain.html)
- [MITRE ATT&CK Enterprise Matrix](https://attack.mitre.org/matrices/enterprise/)
- [NIST SP 800-115 — Technical Guide to Information Security Testing](https://csrc.nist.gov/publications/detail/sp/800-115/final)
