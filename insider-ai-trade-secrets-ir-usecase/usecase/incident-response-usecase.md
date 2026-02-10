# Incident Response Use Case: Insider Theft of AI Supercomputing IP

## Executive narrative

A trusted engineer (“Engineer A”) with legitimate access to highly sensitive AI infrastructure materials abuses that access to **collect and attempt to exfiltrate** confidential information related to:
- custom accelerator architecture (TPU/GPU-class components)
- cluster/orchestration platforms for large-scale training
- high-performance networking components (SmartNICs / RDMA fabrics)

The insider is suspected of preparing to share the information with **foreign-linked entities** while masking indicators (travel/geolocation obfuscation, staged access patterns, gradual collection).

This use case trains defenders to detect and respond to **misuse of valid credentials** and **abnormal internal data movement**.

## Business impact

- Loss of trade secrets and competitive advantage
- National security / regulatory exposure (depending on jurisdiction)
- Legal action and reputational damage
- Potential downstream compromise if code/configs expose exploitable weaknesses

## Scope

**In-scope systems** (examples; adapt to your environment):
- Identity & access: SSO/IdP, MFA logs, VPN/ZTNA logs, privileged access logs
- Collaboration & knowledge repos: Confluence/Wiki, Drive/Docs, ticketing systems
- Source control: GitHub Enterprise / GitLab, CI/CD audit logs
- Artifact/object storage: S3/GCS/Azure Blob; build artifact registries
- Endpoints: EDR telemetry, device control (USB), local file events
- Network: proxy logs, DNS logs, egress monitoring, CASB
- DLP: content inspection + policy violations (uploads/shares)

**Out-of-scope**: malware analysis, exploit-driven initial access (this is a trusted-insider scenario).

## Detection goals (what “good” looks like)

Detect and confirm:
1. **Anomalous collection** from sensitive repositories (volume, breadth, unusual resource sets)
2. **Staging** (bulk export, archiving, local copies, use of personal workspaces)
3. **Exfiltration attempts** (cloud storage uploads, external sharing, unusual egress)
4. **Defense evasion** in a “legitimate user” context (VPN/geo masking, time-shifting, blending)
5. **Policy violations** (dual employment, undisclosed conflicts, external collaboration)

## Incident objectives

- Stop further exfiltration while preserving evidence
- Determine scope: what was accessed, copied, and transferred
- Attribute: account owner vs misuse; insider intent indicators
- Support HR/Legal for employee action and potential law enforcement referral
- Identify control gaps and implement durable improvements

## Key questions for responders

- Which repositories and document classes were accessed? When? How much?
- Were there bulk exports/clones/snapshots outside normal workflows?
- Did data leave trusted boundaries (external shares, personal cloud, devices)?
- What user/device/IP context does the activity have? (geo/time/VPN)
- Were there attempts to delete logs, reduce auditability, or evade DLP?
- What other accounts were involved (service accounts, secondary identities)?

## Required telemetry (minimum viable)

- Identity auth logs (SSO, VPN/ZTNA, MFA challenges)
- Repository audit logs (read/download/export/clone events + object IDs)
- DLP/CASB events (uploads/shares; policy hits)
- Proxy/egress logs (destination categories; cloud storage)
- EDR process/file telemetry (archiving tools; mass file access; cloud sync clients)

## Escalation and decision points

- **HR/Legal engagement**: early and structured, to manage employee actions and evidence
- **Containment**: how to restrict access without tipping off the insider too soon
- **Legal hold**: preserve mailbox/chat/account data (enterprise eDiscovery if available)
- **Law enforcement referral**: criteria and chain-of-custody requirements

## Deliverables in this repo

- MITRE mapping: `usecase/mitre-mapping.md`
- IR lead analysis: `usecase/ir-lead-analysis.md`
- Playbooks: `playbooks/`
- Runbooks: `runbooks/`
- Detections: `detections/`
- Notebooks + synthetic logs: `notebooks/`
- Tabletop exercise package: `tabletop/`
