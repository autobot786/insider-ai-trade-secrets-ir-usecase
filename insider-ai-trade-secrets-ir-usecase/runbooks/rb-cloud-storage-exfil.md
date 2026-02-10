# Runbook: Cloud Storage / External Sharing Exfil Investigation

## Goal
Confirm whether data left the boundary and via which channel(s).

## Steps

1) **CASB/DLP review**
- list all incidents for the subject (30–90 days)
- extract destination accounts, share links, recipients
- confirm allow/deny outcomes

2) **OAuth and app grants**
- list newly granted third-party apps and OAuth tokens
- identify cloud sync clients (Drive/Dropbox/OneDrive) tokens on endpoints
- revoke suspicious tokens (coordinate with IR Lead)

3) **Proxy / egress logs**
- identify uploads: POST/PUT large transfers
- detect near-threshold chunking patterns
- correlate with repo export times

4) **Endpoint corroboration**
- browser history for upload portals (policy-dependent)
- file hashes and timestamps of staged archives
- cloud sync client logs (if present)

## Outputs
- Confirmed/attempted exfil destinations
- Time-aligned correlation: staging → upload
- Evidence bundle for Legal/HR
