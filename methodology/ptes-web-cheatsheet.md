<div align="center">

#  Web Pentest Cheatsheet — PTES

**A task-oriented web penetration testing cheatsheet, organised by the seven PTES phases. For every task you get the tools and the websites that help you do it.**

<p>
  <img src="https://img.shields.io/badge/Standard-PTES-c12127?style=flat-square" />
  <img src="https://img.shields.io/badge/Focus-Web%20Application-000000?style=flat-square&logo=owasp&logoColor=white" />
  <img src="https://img.shields.io/badge/Phases-7-d32f2f?style=flat-square" />
  <img src="https://img.shields.io/badge/Style-Cheatsheet-success?style=flat-square" />
  <img src="https://img.shields.io/badge/License-MIT-yellow?style=flat-square" />
</p>

</div>

---

##  Contents

1. [Pre-engagement Interactions](#-phase-1--pre-engagement-interactions)
2. [Intelligence Gathering](#-phase-2--intelligence-gathering)
3. [Threat Modeling](#-phase-3--threat-modeling)
4. [Vulnerability Analysis](#-phase-4--vulnerability-analysis)
5. [Exploitation](#-phase-5--exploitation)
6. [Post-Exploitation](#-phase-6--post-exploitation)
7. [Reporting](#-phase-7--reporting)

---

##  Phase 1 — Pre-engagement Interactions

> Lock down exactly what you are allowed to test before sending a single packet.

### Scope & Rules of Engagement
Define in-scope assets (domains, IPs, APIs), out-of-scope items, testing windows, allowed techniques, data-handling rules, and escalation contacts. Get **written authorisation** before any active testing.

**Websites**

| Site | What it's for |
|---|---|
| [PTES — Pre-engagement](http://www.pentest-standard.org/index.php/Pre-engagement) | Canonical pre-engagement guidance |
| [SANS — Sample RoE](https://www.sans.org/white-papers/33872/) | Rules-of-engagement document templates |
| [OWASP WSTG — Methodology](https://owasp.org/www-project-web-security-testing-guide/) | Web-specific scope checklist |

### Engagement Note-Taking & Evidence Collection
Keep structured notes from day 1 — every command, payload, screenshot, and finding goes in.

**Tools**

[![Notion](https://img.shields.io/badge/Notion-000000?style=flat-square&logo=notion&logoColor=white)](https://www.notion.so/)
[![Obsidian](https://img.shields.io/badge/Obsidian-7C3AED?style=flat-square&logo=obsidian&logoColor=white)](https://obsidian.md/)
[![Trilium](https://img.shields.io/badge/Trilium-2E2E2E?style=flat-square&logo=read-the-docs&logoColor=white)](https://github.com/zadam/trilium)
[![CherryTree](https://img.shields.io/badge/CherryTree-c12127?style=flat-square&logo=read-the-docs&logoColor=white)](https://www.giuspen.net/cherrytree/)

### Contracts & Authorisation
Sign NDAs, contracts, and the authorisation letter electronically.

**Tools**

[![DocuSign](https://img.shields.io/badge/DocuSign-FFCC22?style=flat-square&logo=docusign&logoColor=black)](https://www.docusign.com/)
[![HelloSign](https://img.shields.io/badge/HelloSign-00B3E6?style=flat-square&logo=hellosign&logoColor=white)](https://www.hellosign.com/)

---

##  Phase 2 — Intelligence Gathering

> Map the entire web attack surface — passively first, then actively.

### Subdomain Enumeration
Find every subdomain — the main site is rarely the only attack surface.

**Tools**

[![Amass](https://img.shields.io/badge/Amass-1A5085?style=flat-square&logo=owasp&logoColor=white)](https://github.com/owasp-amass/amass)
[![Subfinder](https://img.shields.io/badge/Subfinder-FF6633?style=flat-square&logo=protonmail&logoColor=white)](https://github.com/projectdiscovery/subfinder)
[![Assetfinder](https://img.shields.io/badge/Assetfinder-2E2E2E?style=flat-square&logo=go&logoColor=white)](https://github.com/tomnomnom/assetfinder)
[![Findomain](https://img.shields.io/badge/Findomain-c12127?style=flat-square&logo=rust&logoColor=white)](https://github.com/Findomain/Findomain)
[![Sublist3r](https://img.shields.io/badge/Sublist3r-3776AB?style=flat-square&logo=python&logoColor=white)](https://github.com/aboul3la/Sublist3r)

**Websites**

| Site | What it's for |
|---|---|
| [crt.sh](https://crt.sh/) | Certificate transparency logs — pulls subdomains from cert SANs |
| [SecurityTrails](https://securitytrails.com/) | DNS history and subdomain database |
| [Chaos](https://chaos.projectdiscovery.io/) | ProjectDiscovery's curated subdomain dataset |
| [VirusTotal](https://www.virustotal.com/) | Passive DNS, related domains |
| [Censys Search](https://search.censys.io/) | Certificate + service search |

### DNS Reconnaissance
Pull every DNS record type — A, AAAA, MX, TXT, CNAME, NS, SOA, PTR — to find related infrastructure.

**Tools**

[![dig](https://img.shields.io/badge/dig-2E2E2E?style=flat-square&logo=gnubash&logoColor=white)](https://linux.die.net/man/1/dig)
[![dnsrecon](https://img.shields.io/badge/dnsrecon-3776AB?style=flat-square&logo=python&logoColor=white)](https://github.com/darkoperator/dnsrecon)
[![dnsenum](https://img.shields.io/badge/dnsenum-557C94?style=flat-square&logo=perl&logoColor=white)](https://github.com/fwaeytens/dnsenum)
[![fierce](https://img.shields.io/badge/fierce-3776AB?style=flat-square&logo=python&logoColor=white)](https://github.com/mschwager/fierce)

**Websites**

| Site | What it's for |
|---|---|
| [DNSdumpster](https://dnsdumpster.com/) | Visual DNS reconnaissance — graph of all records |
| [ViewDNS.info](https://viewdns.info/) | Reverse DNS, IP history, port scan |
| [DNSlytics](https://dnslytics.com/) | Reverse IP, reverse MX, reverse NS lookups |

### Live Host Discovery
Filter your subdomain list down to actually-responding HTTP services.

**Tools**

[![httpx](https://img.shields.io/badge/httpx-c12127?style=flat-square&logo=go&logoColor=white)](https://github.com/projectdiscovery/httpx)
[![httprobe](https://img.shields.io/badge/httprobe-2E2E2E?style=flat-square&logo=go&logoColor=white)](https://github.com/tomnomnom/httprobe)

### Port Scanning
Find every open service on the target IPs — web is usually not the only attack vector.

**Tools**

[![Nmap](https://img.shields.io/badge/Nmap-2E2E2E?style=flat-square&logo=nmap&logoColor=white)](https://nmap.org/)
[![masscan](https://img.shields.io/badge/Masscan-000000?style=flat-square&logo=gnubash&logoColor=white)](https://github.com/robertdavidgraham/masscan)
[![naabu](https://img.shields.io/badge/Naabu-c12127?style=flat-square&logo=go&logoColor=white)](https://github.com/projectdiscovery/naabu)
[![RustScan](https://img.shields.io/badge/RustScan-CE412B?style=flat-square&logo=rust&logoColor=white)](https://github.com/RustScan/RustScan)

**Websites**

| Site | What it's for |
|---|---|
| [Shodan](https://www.shodan.io/) | Pre-indexed scan data — find exposed services without scanning |
| [Censys](https://search.censys.io/) | Certificate-based asset discovery |
| [ZoomEye](https://www.zoomeye.org/) | Alternative cyberspace search engine |
| [FOFA](https://en.fofa.info/) | China-based asset search engine |

### Technology / CMS / WAF Fingerprinting
Identify the stack — server, framework, CMS, libraries, CDN, WAF.

**Tools**

[![WhatWeb](https://img.shields.io/badge/WhatWeb-21759B?style=flat-square&logo=ruby&logoColor=white)](https://github.com/urbanadventurer/WhatWeb)
[![Wappalyzer](https://img.shields.io/badge/Wappalyzer_CLI-4608AD?style=flat-square&logo=googlechrome&logoColor=white)](https://github.com/wappalyzer/wappalyzer)
[![webanalyze](https://img.shields.io/badge/webanalyze-2E2E2E?style=flat-square&logo=go&logoColor=white)](https://github.com/rverton/webanalyze)
[![wafw00f](https://img.shields.io/badge/wafw00f-c12127?style=flat-square&logo=python&logoColor=white)](https://github.com/EnableSecurity/wafw00f)
[![CMSeeK](https://img.shields.io/badge/CMSeeK-3776AB?style=flat-square&logo=python&logoColor=white)](https://github.com/Tuhinshubhra/CMSeeK)

**Websites**

| Site | What it's for |
|---|---|
| [BuiltWith](https://builtwith.com/) | Full technology profile of any website |
| [Wappalyzer.com](https://www.wappalyzer.com/) | Online tech detection |
| [NetCraft](https://sitereport.netcraft.com/) | Hosting + tech site report |

### Web Crawling & JavaScript Analysis
Spider every endpoint, then mine JavaScript files for hidden routes, API endpoints, and secrets.

**Tools**

[![katana](https://img.shields.io/badge/katana-c12127?style=flat-square&logo=go&logoColor=white)](https://github.com/projectdiscovery/katana)
[![gospider](https://img.shields.io/badge/gospider-2E2E2E?style=flat-square&logo=go&logoColor=white)](https://github.com/jaeles-project/gospider)
[![hakrawler](https://img.shields.io/badge/hakrawler-2E2E2E?style=flat-square&logo=go&logoColor=white)](https://github.com/hakluke/hakrawler)
[![LinkFinder](https://img.shields.io/badge/LinkFinder-3776AB?style=flat-square&logo=python&logoColor=white)](https://github.com/GerbenJavado/LinkFinder)
[![SecretFinder](https://img.shields.io/badge/SecretFinder-3776AB?style=flat-square&logo=python&logoColor=white)](https://github.com/m4ll0k/SecretFinder)
[![jsluice](https://img.shields.io/badge/jsluice-2E2E2E?style=flat-square&logo=go&logoColor=white)](https://github.com/BishopFox/jsluice)

### Directory & File Brute-forcing
Enumerate hidden paths, backup files, admin panels, and version-control exposure.

**Tools**

[![ffuf](https://img.shields.io/badge/ffuf-000000?style=flat-square&logo=gnubash&logoColor=white)](https://github.com/ffuf/ffuf)
[![gobuster](https://img.shields.io/badge/gobuster-000000?style=flat-square&logo=go&logoColor=white)](https://github.com/OJ/gobuster)
[![dirsearch](https://img.shields.io/badge/dirsearch-3776AB?style=flat-square&logo=python&logoColor=white)](https://github.com/maurosoria/dirsearch)
[![feroxbuster](https://img.shields.io/badge/feroxbuster-CE412B?style=flat-square&logo=rust&logoColor=white)](https://github.com/epi052/feroxbuster)
[![dirhunt](https://img.shields.io/badge/dirhunt-3776AB?style=flat-square&logo=python&logoColor=white)](https://github.com/Nekmo/dirhunt)

**Websites**

| Site | What it's for |
|---|---|
| [SecLists](https://github.com/danielmiessler/SecLists) | Wordlists for every kind of fuzzing |
| [PortSwigger Wordlists](https://github.com/PortSwigger/wordlists) | Curated wordlists from PortSwigger |
| [assetnote/wordlists](https://wordlists.assetnote.io/) | Massive curated wordlists by Assetnote |

### Historical URL Discovery
Pull every URL the internet has ever seen for the target — Wayback, CommonCrawl, AlienVault.

**Tools**

[![waybackurls](https://img.shields.io/badge/waybackurls-2E2E2E?style=flat-square&logo=go&logoColor=white)](https://github.com/tomnomnom/waybackurls)
[![gau](https://img.shields.io/badge/gau-2E2E2E?style=flat-square&logo=go&logoColor=white)](https://github.com/lc/gau)
[![waymore](https://img.shields.io/badge/waymore-3776AB?style=flat-square&logo=python&logoColor=white)](https://github.com/xnl-h4ck3r/waymore)

**Websites**

| Site | What it's for |
|---|---|
| [Wayback Machine](https://web.archive.org/) | Historical snapshots — often reveal removed endpoints |
| [Common Crawl](https://commoncrawl.org/) | Open repository of web crawl data |
| [AlienVault OTX](https://otx.alienvault.com/) | Passive URL data |

### Hidden Parameter Discovery
Find HTTP parameters that aren't documented but the application still processes.

**Tools**

[![Arjun](https://img.shields.io/badge/Arjun-3776AB?style=flat-square&logo=python&logoColor=white)](https://github.com/s0md3v/Arjun)
[![x8](https://img.shields.io/badge/x8-CE412B?style=flat-square&logo=rust&logoColor=white)](https://github.com/Sh1Yo/x8)
[![ParamSpider](https://img.shields.io/badge/ParamSpider-3776AB?style=flat-square&logo=python&logoColor=white)](https://github.com/devanshbatham/ParamSpider)
[![param-miner](https://img.shields.io/badge/Param_Miner-FF6633?style=flat-square&logo=burpsuite&logoColor=white)](https://github.com/PortSwigger/param-miner)

### GitHub / Source Code Leaks
Companies leak credentials, API keys, internal hostnames, and source code on GitHub all the time.

**Tools**

[![truffleHog](https://img.shields.io/badge/truffleHog-3776AB?style=flat-square&logo=python&logoColor=white)](https://github.com/trufflesecurity/trufflehog)
[![gitleaks](https://img.shields.io/badge/gitleaks-FF6633?style=flat-square&logo=git&logoColor=white)](https://github.com/gitleaks/gitleaks)
[![GitDorker](https://img.shields.io/badge/GitDorker-3776AB?style=flat-square&logo=python&logoColor=white)](https://github.com/obheda12/GitDorker)
[![noseyparker](https://img.shields.io/badge/Nosey_Parker-CE412B?style=flat-square&logo=rust&logoColor=white)](https://github.com/praetorian-inc/noseyparker)

**Websites**

| Site | What it's for |
|---|---|
| [GitHub Search](https://github.com/search) | Manual dorking — `"company.com" filename:.env` |
| [grep.app](https://grep.app/) | Fast regex search across half a million GitHub repos |
| [PublicWWW](https://publicwww.com/) | Source-code search across the entire web |
| [GitDorks Collection](https://github.com/techgaun/github-dorks) | Curated GitHub search dorks |

### OSINT — People & Email Harvesting
Build employee lists, find emails, and check for breached credentials.

**Tools**

[![theHarvester](https://img.shields.io/badge/theHarvester-c12127?style=flat-square&logo=protonvpn&logoColor=white)](https://github.com/laramies/theHarvester)
[![Maltego CE](https://img.shields.io/badge/Maltego_CE-1F1F1F?style=flat-square&logo=maltego&logoColor=white)](https://www.maltego.com/ce/)
[![recon-ng](https://img.shields.io/badge/recon--ng-3776AB?style=flat-square&logo=python&logoColor=white)](https://github.com/lanmaster53/recon-ng)
[![Sherlock](https://img.shields.io/badge/Sherlock-3776AB?style=flat-square&logo=python&logoColor=white)](https://github.com/sherlock-project/sherlock)
[![h8mail](https://img.shields.io/badge/h8mail-3776AB?style=flat-square&logo=python&logoColor=white)](https://github.com/khast3x/h8mail)

**Websites**

| Site | What it's for |
|---|---|
| [LinkedIn](https://www.linkedin.com/) | Employee list, job titles, infer tech stack from postings |
| [Hunter.io](https://hunter.io/) | Email pattern discovery for a domain |
| [Have I Been Pwned](https://haveibeenpwned.com/) | Breach exposure for the target's domain |
| [Dehashed](https://dehashed.com/) | Searchable database of leaked credentials |
| [IntelX](https://intelx.io/) | Search across paste sites and dark-web sources |

### Cloud Asset Discovery
S3 / Azure / GCP buckets often expose backups, dumps, and source code.

**Tools**

[![S3Scanner](https://img.shields.io/badge/S3Scanner-2E2E2E?style=flat-square&logo=go&logoColor=white)](https://github.com/sa7mon/S3Scanner)
[![CloudEnum](https://img.shields.io/badge/CloudEnum-3776AB?style=flat-square&logo=python&logoColor=white)](https://github.com/initstring/cloud_enum)
[![bucket_finder](https://img.shields.io/badge/bucket__finder-557C94?style=flat-square&logo=ruby&logoColor=white)](https://github.com/digininja/bucket_finder)

**Websites**

| Site | What it's for |
|---|---|
| [GrayHatWarfare](https://buckets.grayhatwarfare.com/) | Searchable index of public S3 / Azure / GCP buckets |
| [BuckHacker](https://buckhacker.com/) | Searchable cloud bucket database |

### Subdomain Takeover Detection
Dangling DNS records pointing to deprovisioned cloud resources let an attacker claim them.

**Tools**

[![subjack](https://img.shields.io/badge/subjack-2E2E2E?style=flat-square&logo=go&logoColor=white)](https://github.com/haccer/subjack)
[![nuclei takeover](https://img.shields.io/badge/Nuclei_takeover-c12127?style=flat-square&logo=protonvpn&logoColor=white)](https://github.com/projectdiscovery/nuclei-templates/tree/main/http/takeovers)
[![subzy](https://img.shields.io/badge/subzy-2E2E2E?style=flat-square&logo=go&logoColor=white)](https://github.com/PentestPad/subzy)

**Websites**

| Site | What it's for |
|---|---|
| [can-i-take-over-xyz](https://github.com/EdOverflow/can-i-take-over-xyz) | Catalog of takeover-vulnerable services and fingerprints |

### API & Documentation Discovery
Find Swagger / OpenAPI / Postman collections and undocumented endpoints.

**Tools**

[![kiterunner](https://img.shields.io/badge/kiterunner-2E2E2E?style=flat-square&logo=go&logoColor=white)](https://github.com/assetnote/kiterunner)
[![apkleaks](https://img.shields.io/badge/APKLeaks-3776AB?style=flat-square&logo=python&logoColor=white)](https://github.com/dwisiswant0/apkleaks)

**Websites**

| Site | What it's for |
|---|---|
| [SwaggerHub](https://swagger.io/tools/swaggerhub/) | Public API definitions database |
| [APIs.guru](https://apis.guru/) | Open OpenAPI/Swagger directory |
| [Postman Public Workspaces](https://www.postman.com/explore) | Public API collections |

---

##  Phase 3 — Threat Modeling

> Decide what would actually hurt the organisation before you waste time testing low-impact paths.

### Asset & User Role Identification
List business-critical assets (databases, PII, payment flows, admin panels) and the user roles that interact with them.

**Approach**
- For each asset ask: *"what happens if this leaks / is modified / goes down?"*
- For each role ask: *"what extra power do they have, and what stops them from getting more?"*

### Attack Surface Mapping & Attack Trees
Map every entry point and data flow, then build attack trees — paths from attacker to crown jewels.

**Tools**

[![draw.io](https://img.shields.io/badge/draw.io-F08705?style=flat-square&logo=diagrams.net&logoColor=white)](https://app.diagrams.net/)
[![Excalidraw](https://img.shields.io/badge/Excalidraw-6965DB?style=flat-square&logo=excalidraw&logoColor=white)](https://excalidraw.com/)
[![OWASP Threat Dragon](https://img.shields.io/badge/Threat_Dragon-c12127?style=flat-square&logo=owasp&logoColor=white)](https://owasp.org/www-project-threat-dragon/)
[![Microsoft TMT](https://img.shields.io/badge/Microsoft_TMT-0078D6?style=flat-square&logo=microsoft&logoColor=white)](https://learn.microsoft.com/en-us/azure/security/develop/threat-modeling-tool)

### Path Prioritisation (STRIDE / DREAD)
Score each candidate attack path so you spend test time on the highest impact-likelihood combinations.

**Websites**

| Site | What it's for |
|---|---|
| [OWASP Web Security Testing Guide](https://owasp.org/www-project-web-security-testing-guide/) | Web testing checklist |
| [STRIDE model](https://en.wikipedia.org/wiki/STRIDE_model) | Six threat categories to brainstorm against |
| [HackTricks — Web Methodology](https://book.hacktricks.xyz/network-services-pentesting/pentesting-web) | Real-world attack-path inspiration |
| [Awesome Threat Modeling](https://github.com/hysnsec/awesome-threat-modelling) | Curated resources |

---

##  Phase 4 — Vulnerability Analysis

> Find what *might* let you in. Manual + automated.

### Automated Web Scanning
Run a baseline pass with both an active scanner (Burp / ZAP) and a template-based scanner (Nuclei).

**Tools**

[![Burp Suite](https://img.shields.io/badge/Burp_Suite-FF6633?style=flat-square&logo=burpsuite&logoColor=white)](https://portswigger.net/burp)
[![OWASP ZAP](https://img.shields.io/badge/OWASP_ZAP-000000?style=flat-square&logo=owasp&logoColor=white)](https://www.zaproxy.org/)
[![Nuclei](https://img.shields.io/badge/Nuclei-c12127?style=flat-square&logo=protonvpn&logoColor=white)](https://github.com/projectdiscovery/nuclei)
[![Nikto](https://img.shields.io/badge/Nikto-000000?style=flat-square&logo=kalilinux&logoColor=white)](https://github.com/sullo/nikto)
[![WPScan](https://img.shields.io/badge/WPScan-21759B?style=flat-square&logo=wordpress&logoColor=white)](https://github.com/wpscanteam/wpscan)
[![JoomScan](https://img.shields.io/badge/JoomScan-557C94?style=flat-square&logo=joomla&logoColor=white)](https://github.com/OWASP/joomscan)

### TLS / SSL Configuration Check
Weak ciphers, expired certs, missing HSTS — all standard report findings.

**Tools**

[![testssl.sh](https://img.shields.io/badge/testssl.sh-2E2E2E?style=flat-square&logo=gnubash&logoColor=white)](https://github.com/drwetter/testssl.sh)
[![sslyze](https://img.shields.io/badge/sslyze-3776AB?style=flat-square&logo=python&logoColor=white)](https://github.com/nabla-c0d3/sslyze)
[![sslscan](https://img.shields.io/badge/sslscan-2E2E2E?style=flat-square&logo=gnubash&logoColor=white)](https://github.com/rbsec/sslscan)

**Websites**

| Site | What it's for |
|---|---|
| [SSL Labs](https://www.ssllabs.com/ssltest/) | Authoritative TLS configuration grading |
| [Hardenize](https://www.hardenize.com/) | Holistic security configuration check |

### Security Headers Review
Missing CSP, X-Frame-Options, HSTS, X-Content-Type-Options, Permissions-Policy.

**Tools**

[![shcheck](https://img.shields.io/badge/shcheck-3776AB?style=flat-square&logo=python&logoColor=white)](https://github.com/santoru/shcheck)

**Websites**

| Site | What it's for |
|---|---|
| [securityheaders.com](https://securityheaders.com/) | Online security-header grader |
| [Mozilla Observatory](https://observatory.mozilla.org/) | Holistic web security check |
| [CSP Evaluator](https://csp-evaluator.withgoogle.com/) | Google's CSP validator |

### CVE Lookup for Identified Versions
Map every fingerprinted version to public CVEs.

**Tools**

[![Searchsploit](https://img.shields.io/badge/Searchsploit-2E2E2E?style=flat-square&logo=offensive-security&logoColor=white)](https://www.exploit-db.com/searchsploit)

**Websites**

| Site | What it's for |
|---|---|
| [CVE Mitre](https://cve.mitre.org/) | Authoritative CVE database |
| [NVD](https://nvd.nist.gov/) | NIST vulnerability database with CVSS |
| [Exploit-DB](https://www.exploit-db.com/) | Curated public exploit code |
| [Vulners](https://vulners.com/) | Cross-source vulnerability search |
| [HackerOne — Hacktivity](https://hackerone.com/hacktivity) | Real disclosed bug-bounty reports |

### Dependency / SCA Scanning
Identify vulnerable third-party libraries on the front-end and (where available) the back-end.

**Tools**

[![retire.js](https://img.shields.io/badge/retire.js-F7DF1E?style=flat-square&logo=javascript&logoColor=black)](https://github.com/RetireJS/retire.js)
[![npm audit](https://img.shields.io/badge/npm_audit-CB3837?style=flat-square&logo=npm&logoColor=white)](https://docs.npmjs.com/cli/v9/commands/npm-audit)
[![snyk](https://img.shields.io/badge/Snyk-4C4A73?style=flat-square&logo=snyk&logoColor=white)](https://snyk.io/)
[![OWASP Dependency-Check](https://img.shields.io/badge/Dependency--Check-c12127?style=flat-square&logo=owasp&logoColor=white)](https://owasp.org/www-project-dependency-check/)

---

##  Phase 5 — Exploitation

> Turn vulnerabilities into a foothold. Walk OWASP Top 10 against every input, then go beyond.

### SQL Injection
Error-based, blind, time-based, out-of-band — every database backend.

**Tools**

[![SQLmap](https://img.shields.io/badge/SQLmap-000000?style=flat-square&logo=python&logoColor=white)](https://github.com/sqlmapproject/sqlmap)
[![NoSQLMap](https://img.shields.io/badge/NoSQLMap-3776AB?style=flat-square&logo=python&logoColor=white)](https://github.com/codingo/NoSQLMap)
[![Ghauri](https://img.shields.io/badge/Ghauri-3776AB?style=flat-square&logo=python&logoColor=white)](https://github.com/r0oth3x49/ghauri)

**Websites**

| Site | What it's for |
|---|---|
| [PayloadsAllTheThings — SQLi](https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/SQL%20Injection) | Comprehensive SQLi payload reference |
| [PortSwigger — SQL Injection](https://portswigger.net/web-security/sql-injection) | Free hands-on labs |
| [HackTricks — SQLi](https://book.hacktricks.xyz/pentesting-web/sql-injection) | Methodology + payloads |

### Cross-Site Scripting (XSS)
Reflected, Stored, DOM-based, blind XSS, mutation XSS.

**Tools**

[![XSStrike](https://img.shields.io/badge/XSStrike-c12127?style=flat-square&logo=python&logoColor=white)](https://github.com/s0md3v/XSStrike)
[![XSpear](https://img.shields.io/badge/XSpear-c12127?style=flat-square&logo=ruby&logoColor=white)](https://github.com/hahwul/XSpear)
[![dalfox](https://img.shields.io/badge/dalfox-2E2E2E?style=flat-square&logo=go&logoColor=white)](https://github.com/hahwul/dalfox)
[![BeEF](https://img.shields.io/badge/BeEF-c12127?style=flat-square&logo=ruby&logoColor=white)](https://github.com/beefproject/beef)

**Websites**

| Site | What it's for |
|---|---|
| [PayloadsAllTheThings — XSS](https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/XSS%20Injection) | XSS payload reference (every variant) |
| [PortSwigger XSS Cheat Sheet](https://portswigger.net/web-security/cross-site-scripting/cheat-sheet) | Filter-bypass payload library |
| [HackTricks — XSS](https://book.hacktricks.xyz/pentesting-web/xss-cross-site-scripting) | Methodology + payloads |

### Server-Side Request Forgery (SSRF)
Internal network access, cloud metadata (`169.254.169.254`), localhost service abuse, blind OOB.

**Tools**

[![SSRFmap](https://img.shields.io/badge/SSRFmap-3776AB?style=flat-square&logo=python&logoColor=white)](https://github.com/swisskyrepo/SSRFmap)
[![Gopherus](https://img.shields.io/badge/Gopherus-3776AB?style=flat-square&logo=python&logoColor=white)](https://github.com/tarunkant/Gopherus)
[![Burp Collaborator](https://img.shields.io/badge/Burp_Collaborator-FF6633?style=flat-square&logo=burpsuite&logoColor=white)](https://portswigger.net/burp/documentation/collaborator)
[![interactsh](https://img.shields.io/badge/interactsh-c12127?style=flat-square&logo=go&logoColor=white)](https://github.com/projectdiscovery/interactsh)

**Websites**

| Site | What it's for |
|---|---|
| [PayloadsAllTheThings — SSRF](https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/Server%20Side%20Request%20Forgery) | SSRF payloads + cloud metadata endpoints |
| [PortSwigger — SSRF](https://portswigger.net/web-security/ssrf) | Free hands-on labs |
| [HackTricks — SSRF](https://book.hacktricks.xyz/pentesting-web/ssrf-server-side-request-forgery) | Methodology |

### IDOR / Broken Access Control
Numeric, UUID, hash-based object references; horizontal and vertical privilege escalation.

**Tools**

[![Autorize](https://img.shields.io/badge/Autorize-FF6633?style=flat-square&logo=burpsuite&logoColor=white)](https://github.com/PortSwigger/autorize)
[![AuthMatrix](https://img.shields.io/badge/AuthMatrix-FF6633?style=flat-square&logo=burpsuite&logoColor=white)](https://github.com/SecurityInnovation/AuthMatrix)

**Websites**

| Site | What it's for |
|---|---|
| [PayloadsAllTheThings — IDOR](https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/Insecure%20Direct%20Object%20References) | IDOR test patterns |
| [PortSwigger — Access Control](https://portswigger.net/web-security/access-control) | Broken access control labs |

### File Upload Bypass
Double extensions, content-type spoofing, magic-byte tricks, polyglots, path traversal in filenames.

**Tools**

[![Upload Scanner](https://img.shields.io/badge/Upload_Scanner-FF6633?style=flat-square&logo=burpsuite&logoColor=white)](https://github.com/PortSwigger/upload-scanner)

**Websites**

| Site | What it's for |
|---|---|
| [PayloadsAllTheThings — Upload](https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/Upload%20Insecure%20Files) | File-upload bypass payloads |
| [HackTricks — File Upload](https://book.hacktricks.xyz/pentesting-web/file-upload) | Methodology |

### Authentication Attacks (JWT / OAuth / SAML / 2FA)
Alg confusion, weak HMAC secrets, RS256→HS256, kid injection, OAuth flow bugs, SAML XML signature wrapping, 2FA bypass.

**Tools**

[![jwt_tool](https://img.shields.io/badge/jwt__tool-3776AB?style=flat-square&logo=jsonwebtokens&logoColor=white)](https://github.com/ticarpi/jwt_tool)
[![JWT.io](https://img.shields.io/badge/JWT.io-000000?style=flat-square&logo=jsonwebtokens&logoColor=white)](https://jwt.io/)
[![SAMLRaider](https://img.shields.io/badge/SAML_Raider-FF6633?style=flat-square&logo=burpsuite&logoColor=white)](https://github.com/CompassSecurity/SAMLRaider)
[![hashcat](https://img.shields.io/badge/Hashcat-2E2E2E?style=flat-square&logo=hackthebox&logoColor=white)](https://github.com/hashcat/hashcat)

**Websites**

| Site | What it's for |
|---|---|
| [PayloadsAllTheThings — JWT](https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/JSON%20Web%20Token) | JWT attack reference |
| [PortSwigger — JWT Attacks](https://portswigger.net/web-security/jwt) | Free JWT labs |
| [HackTricks — OAuth](https://book.hacktricks.xyz/pentesting-web/oauth-to-account-takeover) | OAuth-to-takeover playbook |

### Path Traversal / LFI / RFI
`../`, encoded variants, null bytes, log poisoning, PHP wrappers.

**Websites**

| Site | What it's for |
|---|---|
| [PayloadsAllTheThings — File Inclusion](https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/File%20Inclusion) | Traversal + LFI/RFI payloads |
| [HackTricks — File Inclusion](https://book.hacktricks.xyz/pentesting-web/file-inclusion) | Methodology with PHP wrappers |
| [PortSwigger — Path Traversal](https://portswigger.net/web-security/file-path-traversal) | Hands-on labs |

### Server-Side Template Injection (SSTI)
Jinja2, Twig, Freemarker, Velocity, Pebble, Mako.

**Tools**

[![tplmap](https://img.shields.io/badge/tplmap-557C94?style=flat-square&logo=python&logoColor=white)](https://github.com/epinna/tplmap)

**Websites**

| Site | What it's for |
|---|---|
| [PayloadsAllTheThings — SSTI](https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/Server%20Side%20Template%20Injection) | SSTI payloads per engine |
| [HackTricks — SSTI](https://book.hacktricks.xyz/pentesting-web/ssti-server-side-template-injection) | Per-engine methodology |
| [PortSwigger — SSTI](https://portswigger.net/web-security/server-side-template-injection) | Hands-on labs |

### Command Injection
OS command injection, blind injection, time-based, out-of-band.

**Tools**

[![Commix](https://img.shields.io/badge/Commix-c12127?style=flat-square&logo=python&logoColor=white)](https://github.com/commixproject/commix)

**Websites**

| Site | What it's for |
|---|---|
| [PayloadsAllTheThings — Command Injection](https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/Command%20Injection) | OS-command injection payloads |
| [HackTricks — Command Injection](https://book.hacktricks.xyz/pentesting-web/command-injection) | Methodology |

### XXE — XML External Entity
External entity, blind XXE via OOB, XXE-to-SSRF.

**Websites**

| Site | What it's for |
|---|---|
| [PayloadsAllTheThings — XXE](https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/XXE%20Injection) | XXE payloads + OOB techniques |
| [PortSwigger — XXE](https://portswigger.net/web-security/xxe) | Hands-on labs |

### Insecure Deserialization
Java, PHP, Python pickle, .NET, Ruby, Node.js prototype pollution.

**Tools**

[![ysoserial](https://img.shields.io/badge/ysoserial-007396?style=flat-square&logo=java&logoColor=white)](https://github.com/frohoff/ysoserial)
[![ysoserial.net](https://img.shields.io/badge/ysoserial.net-512BD4?style=flat-square&logo=dotnet&logoColor=white)](https://github.com/pwntester/ysoserial.net)
[![PHPGGC](https://img.shields.io/badge/PHPGGC-777BB4?style=flat-square&logo=php&logoColor=white)](https://github.com/ambionics/phpggc)

**Websites**

| Site | What it's for |
|---|---|
| [PayloadsAllTheThings — Deserialization](https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/Insecure%20Deserialization) | Per-language gadget chains |
| [PortSwigger — Deserialization](https://portswigger.net/web-security/deserialization) | Hands-on labs |

### Request Forgery (CSRF) & HTTP Smuggling
Cross-site request forgery (token bypass, SameSite bypass) + HTTP request smuggling (CL.TE, TE.CL, H2C).

**Tools**

[![smuggler.py](https://img.shields.io/badge/smuggler.py-3776AB?style=flat-square&logo=python&logoColor=white)](https://github.com/defparam/smuggler)
[![http-request-smuggler](https://img.shields.io/badge/http--request--smuggler-FF6633?style=flat-square&logo=burpsuite&logoColor=white)](https://github.com/PortSwigger/http-request-smuggler)

**Websites**

| Site | What it's for |
|---|---|
| [PortSwigger — Request Smuggling](https://portswigger.net/web-security/request-smuggling) | Hands-on labs and writeups |
| [HackTricks — HTTP Smuggling](https://book.hacktricks.xyz/pentesting-web/http-request-smuggling) | Variants and walkthroughs |
| [PayloadsAllTheThings — CSRF](https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/CSRF%20Injection) | CSRF payload examples |

### Client-Side Attacks (CORS / postMessage / Prototype Pollution / Clickjacking)

**Websites**

| Site | What it's for |
|---|---|
| [PortSwigger — CORS](https://portswigger.net/web-security/cors) | CORS misconfig labs |
| [PortSwigger — Prototype Pollution](https://portswigger.net/web-security/prototype-pollution) | Client + server-side labs |
| [PortSwigger — Clickjacking](https://portswigger.net/web-security/clickjacking) | Clickjacking labs |
| [HackTricks — postMessage](https://book.hacktricks.xyz/pentesting-web/postmessage-vulnerabilities) | postMessage attacks |

### API Testing — REST & GraphQL & gRPC

**Tools**

[![Postman](https://img.shields.io/badge/Postman-FF6C37?style=flat-square&logo=postman&logoColor=white)](https://www.postman.com/)
[![graphql-cop](https://img.shields.io/badge/graphql--cop-3776AB?style=flat-square&logo=python&logoColor=white)](https://github.com/dolevf/graphql-cop)
[![graphw00f](https://img.shields.io/badge/graphw00f-3776AB?style=flat-square&logo=python&logoColor=white)](https://github.com/dolevf/graphw00f)
[![InQL](https://img.shields.io/badge/InQL-FF6633?style=flat-square&logo=burpsuite&logoColor=white)](https://github.com/doyensec/inql)

**Websites**

| Site | What it's for |
|---|---|
| [HackTricks — GraphQL](https://book.hacktricks.xyz/network-services-pentesting/pentesting-web/graphql) | GraphQL methodology |
| [HackTricks — gRPC-Web](https://book.hacktricks.xyz/network-services-pentesting/pentesting-web/grpc-web-pentest) | gRPC-Web methodology |
| [OWASP API Security Top 10](https://owasp.org/API-Security/) | API-specific risk catalogue |

### Brute-Force / Credential Stuffing

**Tools**

[![Hydra](https://img.shields.io/badge/Hydra-000000?style=flat-square&logo=protonmail&logoColor=white)](https://github.com/vanhauser-thc/thc-hydra)
[![Medusa](https://img.shields.io/badge/Medusa-c12127?style=flat-square&logo=gnubash&logoColor=white)](https://github.com/jmk-foofus/medusa)
[![patator](https://img.shields.io/badge/patator-3776AB?style=flat-square&logo=python&logoColor=white)](https://github.com/lanjelot/patator)
[![ffuf](https://img.shields.io/badge/ffuf-000000?style=flat-square&logo=gnubash&logoColor=white)](https://github.com/ffuf/ffuf)

### Business Logic / Race Conditions
Workflow bypass, price manipulation, coupon reuse, TOCTOU, parallel-request race conditions.

**Tools**

[![Turbo Intruder](https://img.shields.io/badge/Turbo_Intruder-FF6633?style=flat-square&logo=burpsuite&logoColor=white)](https://github.com/PortSwigger/turbo-intruder)

**Websites**

| Site | What it's for |
|---|---|
| [PortSwigger — Business Logic](https://portswigger.net/web-security/logic-flaws) | Free hands-on labs |
| [PortSwigger — Race Conditions](https://portswigger.net/web-security/race-conditions) | Single-packet race-condition labs |

### General-Purpose Reference

**Websites**

| Site | What it's for |
|---|---|
| [PayloadsAllTheThings](https://github.com/swisskyrepo/PayloadsAllTheThings) | Payload reference for every category |
| [HackTricks — Web Pentest](https://book.hacktricks.xyz/network-services-pentesting/pentesting-web) | Methodology + payloads in one place |
| [PortSwigger Web Security Academy](https://portswigger.net/web-security) | Free hands-on labs for every web vulnerability |
| [revshells.com](https://www.revshells.com/) | Reverse-shell payload generator |

---

##  Phase 6 — Post-Exploitation

> Take the foothold to maximum impact — privesc, pivot, persist, exfil.

### Shell Stabilisation
Upgrade a dumb shell to a full interactive PTY before doing anything else.

```bash
# Quick PTY upgrade
python3 -c 'import pty; pty.spawn("/bin/bash")'
# Then Ctrl+Z, on attacker box: stty raw -echo; fg
# Press Enter, then in shell: export TERM=xterm; stty rows 40 columns 200
```

**Tools**

[![socat](https://img.shields.io/badge/socat-2E2E2E?style=flat-square&logo=gnubash&logoColor=white)](http://www.dest-unreach.org/socat/)
[![rlwrap](https://img.shields.io/badge/rlwrap-2E2E2E?style=flat-square&logo=gnubash&logoColor=white)](https://github.com/hanslub42/rlwrap)

### System & Privilege Enumeration
Run automated enumeration first, then drill manually into anything interesting.

**Tools**

[![LinPEAS / WinPEAS](https://img.shields.io/badge/PEASS--ng-2E2E2E?style=flat-square&logo=linux&logoColor=white)](https://github.com/peass-ng/PEASS-ng)
[![lse](https://img.shields.io/badge/lse.sh-2E2E2E?style=flat-square&logo=gnubash&logoColor=white)](https://github.com/diego-treitos/linux-smart-enumeration)
[![pspy](https://img.shields.io/badge/pspy-557C94?style=flat-square&logo=linux&logoColor=white)](https://github.com/DominicBreuker/pspy)
[![PowerUp](https://img.shields.io/badge/PowerUp-5391FE?style=flat-square&logo=powershell&logoColor=white)](https://github.com/PowerShellMafia/PowerSploit/tree/master/Privesc)

**Websites**

| Site | What it's for |
|---|---|
| [HackTricks — Linux Privesc](https://book.hacktricks.xyz/linux-hardening/privilege-escalation) | Exhaustive Linux privesc reference |
| [HackTricks — Windows Privesc](https://book.hacktricks.xyz/windows-hardening/windows-local-privilege-escalation) | Windows privesc reference |
| [GTFOBins](https://gtfobins.github.io/) | Linux living-off-the-land binaries (privesc one-liners) |
| [LOLBAS](https://lolbas-project.github.io/) | Windows living-off-the-land binaries |
| [WADComs](https://wadcoms.github.io/) | Windows AD command reference |

### Credential Hunting
Search filesystem, env vars, browser stores, memory.

**Targets**
- `.env`, `wp-config.php`, `database.yml`, `.aws/credentials`, `.docker/config.json`
- `~/.ssh/`, `~/.git-credentials`, `.bash_history`, `.zsh_history`
- `/etc/shadow`, SAM/NTDS.dit (Windows)

**Tools**

[![LaZagne](https://img.shields.io/badge/LaZagne-3776AB?style=flat-square&logo=python&logoColor=white)](https://github.com/AlessandroZ/LaZagne)
[![Mimikatz](https://img.shields.io/badge/Mimikatz-c12127?style=flat-square&logo=windowsterminal&logoColor=white)](https://github.com/gentilkiwi/mimikatz)

### Container & Cloud Escape
Docker socket exposure, privileged containers, IMDS abuse, K8s service-account token theft.

**Tools**

[![deepce](https://img.shields.io/badge/deepce-2E2E2E?style=flat-square&logo=gnubash&logoColor=white)](https://github.com/stealthcopter/deepce)
[![CDK](https://img.shields.io/badge/CDK-2E2E2E?style=flat-square&logo=go&logoColor=white)](https://github.com/cdk-team/CDK)
[![pacu](https://img.shields.io/badge/Pacu-3776AB?style=flat-square&logo=python&logoColor=white)](https://github.com/RhinoSecurityLabs/pacu)
[![ScoutSuite](https://img.shields.io/badge/ScoutSuite-3776AB?style=flat-square&logo=python&logoColor=white)](https://github.com/nccgroup/ScoutSuite)

**Websites**

| Site | What it's for |
|---|---|
| [HackTricks — Container Escape](https://book.hacktricks.xyz/linux-hardening/privilege-escalation/docker-security/docker-breakout-privilege-escalation) | Docker / K8s escape methodology |
| [Cloud-Metadata Endpoints](https://gist.github.com/jhaddix/78cece26c91c6263653f31ba453e273b) | All cloud IMDS endpoints in one gist |

### Lateral Movement & Pivoting
Tunnel through the foothold to reach internal services.

**Tools**

[![chisel](https://img.shields.io/badge/chisel-2E2E2E?style=flat-square&logo=go&logoColor=white)](https://github.com/jpillora/chisel)
[![ligolo-ng](https://img.shields.io/badge/ligolo--ng-c12127?style=flat-square&logo=go&logoColor=white)](https://github.com/nicocha30/ligolo-ng)
[![sshuttle](https://img.shields.io/badge/sshuttle-3776AB?style=flat-square&logo=python&logoColor=white)](https://github.com/sshuttle/sshuttle)
[![proxychains-ng](https://img.shields.io/badge/proxychains--ng-000000?style=flat-square&logo=gnubash&logoColor=white)](https://github.com/rofl0r/proxychains-ng)

**Websites**

| Site | What it's for |
|---|---|
| [The Hacker Recipes — Movement](https://www.thehacker.recipes/ad/movement) | Lateral movement playbook |
| [ired.team](https://www.ired.team/) | Offensive ops cheatsheet |

### Cleanup & Evidence
Remove every artefact you placed; document what you accessed *without* exfiltrating real data.

**Checklist**
- Remove uploaded shells, test users, scheduled tasks, and registry entries.
- Restore modified configs and databases to original state.
- Verify cleanup with the client point of contact.

---

##  Phase 7 — Reporting

> Make weeks of work actionable for the people who will fix it.

### Executive Summary
One page, no jargon, business risk in plain language. Top three findings ranked by impact.

### Engagement Narrative
Chronological story — how you got from outside to crown jewels. Lets defenders understand the *attack chain*, not just isolated bugs.

### Technical Findings
Each finding gets: title, CVSS score, affected component, reproduction steps with screenshots, business impact, remediation advice, references (CWE / OWASP / vendor docs).

**Tools**

[![SysReptor](https://img.shields.io/badge/SysReptor-c12127?style=flat-square&logo=read-the-docs&logoColor=white)](https://github.com/Syslifters/sysreptor)
[![PwnDoc](https://img.shields.io/badge/PwnDoc-2E2E2E?style=flat-square&logo=read-the-docs&logoColor=white)](https://github.com/pwndoc/pwndoc)
[![Pandoc](https://img.shields.io/badge/Pandoc-557C94?style=flat-square&logo=markdown&logoColor=white)](https://pandoc.org/)
[![ghostwriter](https://img.shields.io/badge/Ghostwriter-3776AB?style=flat-square&logo=python&logoColor=white)](https://github.com/GhostManager/Ghostwriter)

### Scoring & Mapping

**Websites**

| Site | What it's for |
|---|---|
| [FIRST CVSS Calculator](https://www.first.org/cvss/calculator/3.1) | Authoritative CVSS scoring |
| [CWE](https://cwe.mitre.org/) | Common Weakness Enumeration — for finding categorisation |
| [OWASP Top 10](https://owasp.org/www-project-top-ten/) | Standard category mapping |
| [OWASP API Top 10](https://owasp.org/API-Security/) | API-specific category mapping |

### Sample Reports & Templates

**Websites**

| Site | What it's for |
|---|---|
| [TCM Security — Sample Report](https://github.com/hmaverickadams/TCM-Security-Sample-Pentest-Report) | Realistic engagement narrative example |
| [Offensive Security — Sample Report](https://www.offensive-security.com/pwk-online/PWKv1-REPORT.pdf) | Industry-standard report format |
| [public-pentesting-reports](https://github.com/juliocesarfort/public-pentesting-reports) | Curated archive of public pentest reports |
| [PenTest.WS](https://pentest.ws/) | Engagement-management web app with report builder |

---

##  Disclaimer

This cheatsheet is for **authorised** engagements only. Unauthorised testing
of systems you do not own or have written permission to test is illegal in
most jurisdictions.

---

##  References

- [PTES Technical Guidelines](http://www.pentest-standard.org/index.php/Main_Page)
- [OWASP Web Security Testing Guide](https://owasp.org/www-project-web-security-testing-guide/)
- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [PayloadsAllTheThings](https://github.com/swisskyrepo/PayloadsAllTheThings)
- [HackTricks — Web Pentest](https://book.hacktricks.xyz/network-services-pentesting/pentesting-web)
- [The Bug Hunter's Methodology (jhaddix)](https://github.com/jhaddix/tbhm)
- [NIST SP 800-115](https://csrc.nist.gov/publications/detail/sp/800-115/final)

---

[← Back to methodology index](./README.md)  ·  [← Back to repo root](../README.md)
