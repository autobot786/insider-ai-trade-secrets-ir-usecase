# Runbook: DLP Alert Triage for Insider Data Theft

## Inputs
- DLP incident ID
- User identity (email/UPN), device ID
- Destination (domain/app), action (blocked/allowed)

## Steps

### 1) Validate alert fidelity
- Confirm classifier/fingerprint hit and confidence
- Confirm policy: “restricted/crown jewel” vs generic sensitive
- Check if this is a repeat offender (prior incidents, warnings)

### 2) Determine outcome
- Was the transfer **blocked** or **allowed**?
- If allowed, identify:
  - exact destination account (recipient, share link, bucket)
  - bytes transferred
  - time window and number of files

### 3) Pull immediate context (last 7–30 days)
- Identity:
  - logins, MFA patterns, new device registrations
  - VPN/ZTNA sessions and geo anomalies
- Repo audits:
  - sensitive objects accessed, exports, clones
- Endpoint/EDR:
  - process that created file (zip/tar), source paths, recent file reads
- Proxy/egress:
  - uploads to cloud storage, webmail, developer paste sites

### 4) Risk score (example)
- +3: restricted classifier/fingerprint
- +3: personal cloud destination
- +2: archive > 500MB
- +2: off-hours staging
- +2: repeated attempts / multiple destinations
- +2: geo anomalies / new device token
- **≥7 → escalate to IR Lead immediately**

### 5) Escalate packet
Provide:
- incident summary + timestamps
- user/device context
- evidence links/log exports
- recommended next action (quiet vs hard containment)

## Outputs
- IR ticket created
- Evidence preserved (DLP packet + key log exports)
- Escalation decision recorded
