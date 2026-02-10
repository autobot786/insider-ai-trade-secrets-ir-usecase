# Runbook: Credential & Session Containment (Insider Scenario)

## Principles
- Contain with minimum disruption while preventing further data access.
- Preserve evidence (don’t destroy logs).

## Quiet containment actions
- Remove subject from crown-jewel groups/roles
- Enforce step-up auth for exports/clones/shares
- Restrict external sharing and personal cloud destinations
- Increase monitoring thresholds and alerting

## Hard containment actions
- Disable account and revoke active sessions
- Revoke OAuth tokens / app passwords
- Rotate API keys and secrets the subject could access
- Suspend or restrict service accounts used by the subject (if any)
- Isolate endpoints from network (forensics-ready)

## Outputs
- Change record with timestamps and approver
- List of revoked tokens/sessions and impacted systems
