# Lab 04: Containment Decision & Evidence Plan (IR Lead)

## Prompt

You have strong indicators of malicious intent, but you want to preserve evidence and prevent further loss.

## Tasks

- [ ] Choose containment strategy (quiet vs hard) with rationale
- [ ] Write an evidence capture checklist (identity, repos, endpoint, network, DLP)
- [ ] Define the **scope ledger** structure (fields and storage location)
- [ ] Define comms: who is notified, in what order, and what you *don’t* say yet

<details>
<summary>Suggested plan</summary>

**Quiet containment** first (if no confirmed egress):
- revoke external sharing; block personal cloud
- reduce repo permissions; step-up auth for exports/clones
- increase logging and alerting for subject + crown-jewel repos
- coordinate HR/legal for device acquisition plan

**Evidence checklist:**
- immutable exports of relevant log ranges
- endpoint triage image and volatile capture (policy-dependent)
- OAuth tokens/app grants and revocation logs
- DLP incident packet + file fingerprints

**Scope ledger fields:**
`timestamp, user, device, source_system, object_id, object_type, action, bytes, destination, evidence_ref, confidence`

**Comms:** IR+SOC+Legal+HR+Exec sponsor; avoid tipping off subject.
</details>
