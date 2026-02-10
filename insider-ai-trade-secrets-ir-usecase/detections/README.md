# Detections

This folder provides **starter detections** for insider data theft scenarios.

Contents:
- `sigma/` – portable Sigma rules (field mapping needed)
- `queries/` – example SIEM queries (Splunk SPL, KQL, Chronicle-style pseudocode)

> These detections are intentionally conservative and should be tuned to your environment (baseline, peer groups, sensitivity labels).

## ATT&CK mapping
Rules include `tags:` such as:
- `attack.t1078`
- `attack.t1213`
- `attack.t1213.003`
- `attack.t1567.002`
