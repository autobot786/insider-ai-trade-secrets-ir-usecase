# Playbook: Insider Threat – Suspected Data Theft / Trade Secret Exfiltration

## Purpose
Provide a repeatable response process for suspected insider theft of sensitive data, especially “crown jewel” IP.

## Trigger conditions
Any of the following (especially in combination):
- DLP/CASB indicates attempted or successful transfer to personal cloud, external sharing, or removable media
- Unusual bulk access/export/clone of sensitive repositories
- Identity anomalies (new device, impossible travel, atypical VPN/proxy patterns)
- HR/manager report of concerning behavior, conflict-of-interest signals, or policy violations

## Roles & responsibilities
- **SOC Analyst**: initial triage, evidence preservation of alerts/logs, escalation packet
- **IR Lead**: containment decision, investigation plan, executive communication
- **IAM Owner**: access review, session/token revocation, policy enforcement
- **DLP/CASB Owner**: confirm transfer outcomes, tune blocks, provide incident artifacts
- **Endpoint Forensics**: device acquisition, timeline reconstruction, artifact collection
- **Legal Counsel**: legal hold, employee action guidance, law enforcement readiness
- **HR**: employee process, interviews, device retrieval coordination
- **Comms/PR** (as needed): external messaging strategy

## Core flow

### 1) Triage & validate
- Confirm alert fidelity (classifier, fingerprint, rule)
- Verify account and device context
- Start a **case log** and preserve initial evidence

### 2) Scope quickly
- Identify affected repositories/objects
- Determine if data left boundary (external share links, successful uploads)
- Identify other identities/apps involved (OAuth, API keys, service accounts)

### 3) Contain
Choose based on risk:
- **Quiet**: reduce access + increase monitoring + block egress
- **Hard**: disable account + isolate device + revoke tokens

### 4) Investigate
- Build a timeline: identity → repo access → staging → egress
- Produce the **scope ledger**
- Determine intent indicators (pattern, concealment, external collaboration)

### 5) Recover & improve
- Revoke / rotate access secrets
- Implement durable controls and policy changes
- Document lessons learned and update detections

## Decision guidance: Quiet vs hard containment

Hard containment is recommended if:
- successful external transfer is confirmed, or
- active exfil is in progress, or
- there is a credible risk of immediate large loss

Quiet containment is recommended if:
- exfil attempts are blocked but intent indicators are strong and
- you need additional evidence before HR action

## Outputs
- Situation report (SITREP) within 4 hours of IR engagement
- Executive brief within 24 hours
- Post-incident report + remediation plan within 10 business days
