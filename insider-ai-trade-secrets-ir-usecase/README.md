# Insider Threat IR Use Case: AI Supercomputing IP Theft

This repository is a **complete incident-response (IR) use case** inspired by a real-world case of a trusted insider misusing legitimate access to steal confidential AI infrastructure information and attempting to share it with foreign-linked entities.

It includes:
- A full IR use case narrative + **MITRE ATT&CK mappings**
- **Detection & defensive techniques**, data sources, and analytic ideas
- **Playbooks**, **runbooks**, and **templates**
- **Jupyter notebooks** with synthetic log data for hands-on analysis
- A full **tabletop exercise** (TTX) package (facilitator guide + injects)

> ⚠️ This repo uses **synthetic data** and **anonymized personas** for training and tabletop exercises.

## Quick start

### 1) Explore the interactive use case
- `usecase/interactive/START-HERE.md`

### 2) Run the notebooks
```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
jupyter lab
```

Notebooks live in `notebooks/` and use data in `notebooks/data/`.

### 3) Facilitate the tabletop exercise
- `tabletop/tabletop-guide.md`

## Scenario summary

A privileged engineer with legitimate access to sensitive AI supercomputing design artifacts:
- collects **thousands of confidential files** from internal repositories (design docs, code repos, build/orchestration diagrams)
- stages collections to look like normal engineering workflows (selective access patterns, gradual accumulation, off-hours access)
- attempts to exfiltrate via personal cloud and external collaboration channels
- uses travel/VPN/geolocation obfuscation to make activity appear domestic
- pursues external ventures tied to foreign interests

## Repository map

- `usecase/` – Narrative, assumptions, scope, ATT&CK mapping, IR Lead analysis
- `detections/` – Sigma rules + query templates (SPL/KQL/Chronicle/Udm examples)
- `playbooks/` – “what to do” at a high level (roles, decisions, comms)
- `runbooks/` – “how to do it” step-by-step procedures
- `notebooks/` – Hands-on analytics with synthetic audit/DLP/identity data
- `tabletop/` – Facilitator guide, injects, scoring, and participant handouts
- `templates/` – IR ticket, exec brief, chain-of-custody, legal hold templates

## Reference sources

- DOJ press release on the conviction (Jan 2026): see `references/sources.md`
- MITRE ATT&CK technique pages referenced throughout: see `usecase/mitre-mapping.md`

## License
MIT License (see `LICENSE`).
