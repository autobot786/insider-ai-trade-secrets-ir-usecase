# Runbook: Investigate Abnormal Repository Access (Docs + Code)

## Goal
Prove/disprove abnormal collection from sensitive repositories and identify scope.

## Steps

1) **Define baseline window**
- subject baseline: prior 60–90 days
- peer baseline: same team/role cohort

2) **Pull repository audit logs**
- docs/wiki: view, export, download, search
- code: clone, fetch, archive download, API token usage

3) **Compute anomalies**
- counts of unique objects accessed per day
- bytes downloaded per day
- breadth: number of repos/spaces touched per day

4) **Identify high-risk actions**
- bulk export jobs
- `git clone --mirror`, `git bundle`, unusually large `git fetch`
- archive downloads of repos
- access to “restricted” labels/spaces

5) **Build scope ledger**
Record objects, times, and evidence references.

## Outputs
- Top 10 sensitive repositories/spaces accessed
- List of crown-jewel objects accessed
- Timeline of bulk export/clone events
- Preliminary scope ledger
