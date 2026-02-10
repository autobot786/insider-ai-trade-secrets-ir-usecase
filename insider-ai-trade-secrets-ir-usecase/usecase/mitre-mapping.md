# MITRE ATT&CK Mapping: Insider Misuse for IP Theft

This mapping treats the insider as an “adversary” performing **collection → staging → exfiltration**, while leveraging **Valid Accounts**.

> Tip: In insider scenarios, the **hard part is not “how they got in”** but **how they used trust**.

## Attack chain (high level)

1. **Access with valid credentials** to sensitive repos
2. **Collect** from information repositories and code repos
3. **Stage** data locally (export/clone/archive) or in remote workspaces
4. **Exfiltrate** to personal cloud / external sharing channels
5. **Evade**: blend in, throttle, geo-mask, delete artifacts

## Technique mapping table

| ATT&CK Tactic | Technique ID | Technique | How it appears in this scenario | Detection ideas (signals) | Defensive controls (prevention/limit) |
|---|---:|---|---|---|---|
| Initial Access / Persistence | T1078 | Valid Accounts | Insider uses legitimate SSO/VPN access to reach crown-jewel systems | anomalous logins, new device tokens, unusual MFA patterns, impossible travel | least-privilege, strong auth, continuous access review, device trust/ZTNA |
| Collection | T1213 | Data from Information Repositories | Mining internal docs/wikis/Drive for design artifacts | spikes in reads/downloads of sensitive spaces; new export jobs | tiered access; information barriers; separate “crown jewel” workspaces |
| Collection | T1213.003 | Code Repositories | cloning/reading AI infra source code and build scripts | unusual clone depth/volume; rare repo access; large fetches | restrict repo export; enforce signed commits; repo permissions review |
| Collection | T1119 | Automated Collection | scripted bulk downloads from repos | repeated API calls; high request rate; uniform user-agent | API rate-limits; anomaly detection; require just-in-time access |
| Collection | T1005 | Data from Local System | local copies created on endpoints for staging | mass file creation; “sensitive” labels written to disk | EDR + DLP endpoint controls; prevent storing to unmanaged paths |
| Collection | T1039 | Data from Network Shared Drive | bulk reads from shared engineering drives | SMB/NFS reads; large file open counts | separate network segments; restrict shares; classification labels |
| Collection / Staging | T1560 | Archive Collected Data | zip/tar/7z archives for transfer | archive tool execution; large archive outputs | block unapproved archivers; detect sensitive-content archives |
| Staging | T1074.001 | Local Data Staging | keeping exports in local temp/work dirs | new large directories; repetitive naming patterns | workstation hardening; encrypted disks; monitor staging directories |
| Staging | T1074.002 | Remote Data Staging | staging in remote VMs / cloud workspace | data moved to non-standard cloud buckets/projects | org policy constraints; restrict cross-project writes; CASB |
| Defense Evasion | T1090 | Proxy | VPN/proxy usage to mask geo and origin | sudden proxy/VPN usage; ASN anomalies; new egress paths | enforce corp VPN; block consumer VPN; geo/IP allowlists (careful) |
| Defense Evasion | T1036 | Masquerading | naming exports to look like normal builds; work-hour “blending” | benign-looking file names but unusual content sensitivity | content-based DLP; label-based monitoring; peer-group baselines |
| Defense Evasion | T1070.004 | File Deletion | removing local staged artifacts or clearing history | deletion spikes; recent file wipe patterns | EDR anti-tamper; immutable logs; endpoint forensic readiness |
| Exfiltration | T1567.002 | Exfiltration to Cloud Storage | uploading to personal cloud (Drive/Dropbox/etc.) | CASB alerts; OAuth token creation; unusual upload volume | block personal cloud; conditional access; DLP inline inspection |
| Exfiltration | T1020 | Automated Exfiltration | scripted periodic uploads to reduce spikes | recurring small uploads; beacon-like intervals | anomaly models on periodicity; upload throttling |
| Exfiltration | T1030 | Data Transfer Size Limits | chunking uploads to avoid thresholds | many small uploads just under policy limit | “near-threshold” analytics; enforce cumulative thresholds |
| Exfiltration | T1041 | Exfiltration Over C2 Channel | (optional) exfil over web APIs/proxy | long-lived sessions; unusual non-browser uploads | TLS inspection where lawful; egress allowlisting |

## Notes for defenders

- **Insider activity looks “legitimate”**: focus on *behavioral anomalies* and *policy boundary crossings* (external share, personal accounts, unusual breadth).
- Correlate across layers: **repo access + endpoint staging + egress + DLP** is far stronger than any single control.
