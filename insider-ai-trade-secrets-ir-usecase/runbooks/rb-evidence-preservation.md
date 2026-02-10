# Runbook: Evidence Preservation & Chain of Custody

## Goal
Preserve evidence suitable for HR/legal action and potential law enforcement referral.

## Steps

1) **Legal hold trigger**
- Engage Legal to determine whether to issue a legal hold.
- Identify systems in scope: email, chat, docs, repos, endpoints, cloud accounts.

2) **Log preservation**
- Export relevant time ranges from:
  - identity auth logs
  - repo audit logs
  - DLP/CASB
  - proxy/egress logs
  - EDR telemetry
- Store in immutable storage with access controls.

3) **Endpoint acquisition**
- Follow HR/legal procedure for device retrieval.
- Capture:
  - full disk image (if permitted)
  - memory/volatile data (if permitted)
  - key artifacts: browser history, sync client logs, archive files

4) **Document chain-of-custody**
- Use `templates/chain-of-custody-form.md`
- Record who handled what, when, and where it was stored.

## Outputs
- Evidence inventory
- Chain-of-custody documentation
- Immutable evidence storage location
