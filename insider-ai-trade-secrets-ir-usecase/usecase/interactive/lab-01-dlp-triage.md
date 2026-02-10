# Lab 01: DLP Alert Triage (Analyst)

## Prompt

A **DLP incident** fires:

- Policy: `Restricted-AI-IP`
- Action: `Upload blocked (personal cloud)`
- User: `engineer.a@orchid.example`
- Destination: `drive.personal.example`
- File: `orchestrator_design_export.zip`
- Size: `1.4 GB`
- Device: `corp-laptop-14`

## Your tasks (answer in your IR notes)

- [ ] What *immediate* context do you pull (logs / sources)?
- [ ] What makes this more likely insider misuse vs a false positive?
- [ ] What 3 follow-up questions decide severity?
- [ ] Do you escalate to IR? Why?

<details>
<summary>Suggested analyst approach</summary>

**Pull context (minimum):**
- identity: last 7d logins, device posture, MFA outcomes
- endpoint: process tree that created `*.zip`, source paths, recent file reads
- repo audits: what objects were read/exported leading up to the zip
- DLP details: classifier hits, fingerprints, prior incidents for this user
- network/proxy: upload attempts (bytes, destination, protocol)

**Insider indicators:**
- large archive + restricted classifier + personal destination
- repeated attempts / alternate destinations
- off-hours staging + unusual breadth of repo access
- new OAuth token or new sync client

**3 severity questions:**
1) Did any data *successfully* leave the boundary (shares/links/other cloud)?  
2) What **sensitivity** and **scope** of content is in the archive (fingerprints/labels)?  
3) Is the account/device context consistent (geo anomalies, new device, odd VPN/proxy)?

**Escalate:** Yes. This is a crown-jewel data egress attempt with strong signals.
</details>
