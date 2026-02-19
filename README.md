#  Insider AI Trade Secrets - Incident Response Use Case

> **A complete training package for detecting, investigating, and responding to insider data theft targeting AI systems and trade secrets**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](insider-ai-trade-secrets-ir-usecase/LICENSE)
![Language: Jupyter Notebook](https://img.shields.io/badge/Jupyter-100%25-orange)

---

##  Table of Contents

- [Overview](#-overview)
- [Repository Structure](#-repository-structure)
- [Quick Start](#-quick-start)
- [Use Case Scenario](#-use-case-scenario)
- [Components](#-components)
- [Interactive Labs](#-interactive-labs)
- [Contributing](#-contributing)
- [Security](#-security)
- [License](#-license)

---

##  Overview

This repository provides a **realistic, hands-on training environment** for security teams to practice investigating insider threats targeting AI intellectual property and trade secrets. All data is **100% synthetic** and designed for educational purposes.

### What You'll Learn

 **Detection Engineering** - Build and tune insider threat detections using Sigma rules and SIEM queries  
 **Forensic Analysis** - Investigate repository access anomalies, data exfiltration, and VPN masking  
 **Incident Response** - Follow structured playbooks and runbooks for insider threat scenarios  
 **MITRE ATT&CK Mapping** - Map threats to techniques (T1078, T1213, T1567.002, etc.)  
 **Tabletop Exercises** - Run realistic scenarios with your team  

---

##  Repository Structure

```
insider-ai-trade-secrets-ir-usecase/
│
├──  usecase/                          # Use case documentation & scenario
│   ├── incident-response-usecase.md     # Main scenario description
│   ├── mitre-mapping.md                 # ATT&CK technique mappings
│   ├── ir-lead-analysis.md              # Investigation approach guide
│   ├── scenario.yaml                    # Scenario configuration
│   └── interactive/                     # Guided interactive labs
│       └── START-HERE.md                # Begin your training here!
│
├──  notebooks/                        # Jupyter analysis notebooks
│   ├── 01_access_baselining.ipynb       # Detect abnormal repository access
│   ├── 02_dlp_event_analysis.ipynb      # Analyze DLP incidents & correlations
│   ├── 03_geo_anomaly_vpn.ipynb         # Detect impossible travel & VPN masking
│   ├── 04_data_exfil_correlation.ipynb  # Build staging→exfil timeline
│   └── data/                            # Synthetic telemetry (CSV files)
│       ├── docs_audit.csv               # Document/wiki access logs
│       ├── git_audit.csv                # Code repository audit logs
│       ├── id_auth.csv                  # Identity/SSO/VPN logs
│       ├── proxy.csv                    # Web proxy/egress logs
│       ├── dlp.csv                      # Data Loss Prevention events
│       ├── edr.csv                      # Endpoint Detection & Response
│       └── travel_records.csv           # HR travel data
│
├──  detections/                       # Detection rules & queries
│   ├── sigma/                           # Portable Sigma rules
│   └── queries/                         # SIEM-specific queries
│       ├── splunk_spl.txt               # Splunk SPL examples
│       ├── kql_queries.txt              # Azure Sentinel KQL
│       └── chronicle_udm_pseudocode.txt # Chronicle/UDM examples
│
├──  playbooks/                        # Incident response playbooks
│   ├── insider-data-theft-playbook.md   # Main IR playbook
│   └── communication-playbook.md        # Stakeholder communication guide
│
├──  runbooks/                         # Step-by-step investigation procedures
│   ├── rb-dlp-alert-triage.md           # DLP alert triage runbook
│   ├── rb-anomalous-repo-access.md      # Repository access investigation
│   ├── rb-cloud-storage-exfil.md        # Cloud exfiltration investigation
│   └── rb-evidence-preservation.md      # Evidence collection procedures
│
├──  tabletop/                         # Tabletop exercise materials
│   ├── facilitator-guide.md             # TTX facilitation instructions
│   ├── participant-handouts.md          # Participant materials
│   └── injects/                         # Scenario inject timeline
│       ├── inject-01.md                 # Initial DLP alert
│       ├── inject-02.md                 # VPN anomaly discovered
│       └── inject-03.md                 # Repository audit spike
│
├──  templates/                        # Reusable IR templates
│   ├── scope-ledger.md                  # Track compromised assets
│   ├── executive-brief.md               # Leadership communication template
│   └── containment-change-record.md     # Document containment actions
│
├──  CONTRIBUTING.md                   # Contribution guidelines
├──  SECURITY.md                       # Security policy
└──  LICENSE                           # MIT License

```

---

##  Quick Start

### Prerequisites

- **Python 3.8+** with Jupyter
- **pandas**, **numpy**, **matplotlib** (install via `requirements.txt` if provided)
- Basic understanding of incident response and MITRE ATT&CK

### Getting Started in 3 Steps

1. ** Read the Scenario**
   ```bash
   # Start here to understand the use case
   cat insider-ai-trade-secrets-ir-usecase/usecase/incident-response-usecase.md
   ```

2. ** Run Interactive Labs**
   ```bash
   # Navigate to interactive training
   cat insider-ai-trade-secrets-ir-usecase/usecase/interactive/START-HERE.md
   ```

3. ** Launch Analysis Notebooks**
   ```bash
   cd insider-ai-trade-secrets-ir-usecase/notebooks
   jupyter notebook 01_access_baselining.ipynb
   ```

---

##  Use Case Scenario

### The Insider Threat

**Subject:** `engineer.a` - Senior AI Engineer  
**Alert Trigger:** DLP system flagged unusual uploads to personal cloud storage  
**Timeline:** 30-day investigation window  
**Crown Jewels at Risk:**
- AI model architectures
- Training datasets
- Proprietary orchestration code
- Research documentation

### Investigation Goals

1.  Prove/disprove abnormal collection from sensitive repositories
2.  Identify scope of data accessed (what, when, where)
3.  Determine staging and exfiltration methods
4.  Build timeline with geographic/VPN anomalies
5.  Provide executive brief with remediation actions

### MITRE ATT&CK Techniques Covered

| Technique | ID | Description |
|-----------|----|------------|
| **Valid Accounts** | T1078 | Abuse of legitimate credentials |
| **Data from Information Repositories** | T1213 | Access to SharePoint, wikis, code repos |
| **Code Repositories** | T1213.003 | Git clone/mirror of restricted repos |
| **Exfiltration to Cloud Storage** | T1567.002 | Upload to Dropbox, GDrive, etc. |

 Full mapping: [`usecase/mitre-mapping.md`](insider-ai-trade-secrets-ir-usecase/usecase/mitre-mapping.md)

---

##  Components

### 1️ **Notebooks** (Analysis & Detection)

| Notebook | Purpose | Key Outputs |
|----------|---------|-------------|
| **01_access_baselining.ipynb** | Detect abnormal doc/code access patterns | Z-scores, top anomalous users |
| **02_dlp_event_analysis.ipynb** | Correlate DLP events with proxy logs | Upload timelines, destinations |
| **03_geo_anomaly_vpn.ipynb** | Detect impossible travel & VPN masking | Geographic anomaly flags |
| **04_data_exfil_correlation.ipynb** | Build end-to-end exfil timeline | Staging→exfil event chain |

 **Data Dictionary**: [`notebooks/data/README.md`](insider-ai-trade-secrets-ir-usecase/notebooks/data/README.md)

---

### 2️ **Detections** (Sigma + SIEM Queries)

Pre-built detection rules for:
-  Restricted repository clone/mirror operations
-  Bulk document export from sensitive spaces
-  Uploads to personal cloud storage (Dropbox, GDrive)
-  VPN use from unusual countries
-  Impossible travel patterns

**Formats Available:**
-  Sigma (portable, requires field mapping)
-  Splunk SPL
-  Azure Sentinel KQL
-  Chronicle UDM pseudocode

 **Browse detections**: [`detections/`](insider-ai-trade-secrets-ir-usecase/detections/)

---

### 3️ **Playbooks & Runbooks**

**Playbooks** (strategic, role-based):
- `insider-data-theft-playbook.md` - Full IR lifecycle for insider threats
- `communication-playbook.md` - Stakeholder communication framework

**Runbooks** (tactical, step-by-step):
- `rb-dlp-alert-triage.md` - Triage DLP alerts
- `rb-anomalous-repo-access.md` - Investigate repository anomalies
- `rb-cloud-storage-exfil.md` - Track cloud exfiltration
- `rb-evidence-preservation.md` - Preserve forensic evidence

 **View runbooks**: [`runbooks/`](insider-ai-trade-secrets-ir-usecase/runbooks/)

---

### 4️ **Tabletop Exercise (TTX) Materials**

Run a **2-hour tabletop exercise** with your team:

-  **Facilitator Guide** - How to run the exercise
-  **Participant Handouts** - Roles, data sources, objectives
-  **Timed Injects** - Progressive scenario reveals (T+0, T+10, T+20)

**Deliverables:**
1. Decision log
2. Event timeline
3. Scope ledger
4. Executive brief
5. 5 remediation actions (ATT&CK-mapped)

 **TTX materials**: [`tabletop/`](insider-ai-trade-secrets-ir-usecase/tabletop/)

---

##  Interactive Labs

Self-paced hands-on exercises with solutions:

| Lab | Focus Area | Difficulty |
|-----|------------|------------|
| **Lab 01** | DLP Alert Triage |  Beginner |
| **Lab 02** | Abnormal Repository Collection |  Intermediate |
| **Lab 03** | Geo/VPN Anomaly Detection |  Intermediate |
| **Lab 04** | End-to-End Exfil Timeline |  Advanced |

 **Start here**: [`usecase/interactive/START-HERE.md`](insider-ai-trade-secrets-ir-usecase/usecase/interactive/)

---

##  Synthetic Data Overview

All telemetry is **100% synthetic** and generated for training purposes.

### Data Sources Included

| Source | Records | Fields | Use Case |
|--------|---------|--------|----------|
| **docs_audit.csv** | ~5000 | user, action, space, sensitivity, bytes | Document access patterns |
| **git_audit.csv** | ~3000 | user, action, repo, sensitivity, bytes | Code repository activity |
| **id_auth.csv** | ~2000 | user, src_ip, country, vpn_used | Identity & VPN logs |
| **proxy.csv** | ~4000 | user, dest_domain, category, bytes | Web egress traffic |
| **dlp.csv** | ~500 | user, action, destination, file, policy | DLP events |
| **edr.csv** | ~1500 | user, event_type, process, file_path | Endpoint telemetry |
| **travel_records.csv** | ~50 | user, date, travel_country | HR travel records |

 **Full data dictionary**: [`notebooks/data/README.md`](insider-ai-trade-secrets-ir-usecase/notebooks/data/README.md)

---

##  Learning Outcomes

After completing this use case, you will be able to:

 **Detect** abnormal access patterns using baseline analysis and peer comparison  
 **Investigate** insider threats using structured runbooks and forensic techniques  
 **Correlate** events across multiple data sources (DLP, proxy, EDR, IdP, repo audit)  
 **Build** actionable timelines and scope ledgers for stakeholders  
 **Map** threats to MITRE ATT&CK techniques and develop countermeasures  
 **Communicate** findings to technical and executive audiences  

---

##  Contributing

Contributions are welcome! We're especially interested in:

-  Additional detection rules (Sigma + SIEM queries)
-  Improved notebook analytics and visualizations
-  More tabletop injects and facilitator materials
-  Translations and localization

**Please ensure:**
- All telemetry remains **synthetic**
- No real credentials, keys, or PII are included
- Documentation is clear and beginner-friendly

 **Read the full guide**: [`CONTRIBUTING.md`](insider-ai-trade-secrets-ir-usecase/CONTRIBUTING.md)

---

##  Security

This repository contains **synthetic training data only**. Do not submit:
-  Real incident artifacts
-  Production logs or telemetry
-  Credentials, tokens, or secrets

If you discover a security issue in the **tooling or notebooks**, please open an issue with reproduction steps.

 **Security policy**: [`SECURITY.md`](insider-ai-trade-secrets-ir-usecase/SECURITY.md)

---

##  License

This project is licensed under the **MIT License**.

```
Copyright (c) 2026
```

See [`LICENSE`](insider-ai-trade-secrets-ir-usecase/LICENSE) for full terms.

---

##  Acknowledgments

- **MITRE ATT&CK** for the threat framework
- **Sigma Project** for portable detection rules
- **Security community** for shared knowledge and best practices

---

##  Support & Questions

-  **Discussions**: Open a GitHub Discussion for questions
-  **Bug Reports**: File an issue with `[BUG]` prefix
-  **Feature Requests**: File an issue with `[FEATURE]` prefix

---

<div align="center">

** Ready to start? → [`usecase/interactive/START-HERE.md`](insider-ai-trade-secrets-ir-usecase/usecase/interactive/START-HERE.md)**

---

Made with  for security professionals training to defend against insider threats

 **Star this repo** if you find it useful!

</div>
