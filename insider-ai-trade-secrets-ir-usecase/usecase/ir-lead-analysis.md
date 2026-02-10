# IR Lead Analysis: Insider Misuse & Trade Secret Theft Attempt

## What we know (from initial alert context)

- The subject account belongs to a privileged engineer with access to AI infrastructure repositories.
- Over the past ~30 days, activity shows increasing breadth/volume of access to “crown jewel” assets.
- DLP/CASB alerts indicate attempted external transfer (personal cloud storage / external sharing).
- Identity telemetry shows inconsistent geolocation and atypical VPN/proxy use.

**Working assumption:** This is **deliberate misuse** until proven otherwise.

## Primary hypotheses (ranked)

1. **Malicious insider** intentionally collecting and exfiltrating confidential IP.
2. **Account takeover** of a privileged engineer (less likely if device posture consistent, but must be ruled out).
3. **Benign but risky behavior** (e.g., offsite backup, poor judgment) escalating into a policy violation.

## IR priorities

1. **Preserve evidence** (immutability matters): logs, endpoint artifacts, mailbox/chat, repo audit trails.
2. **Stop further loss** without tipping off the insider prematurely.
3. **Scope**: identify what was accessed, copied, staged, and transferred.
4. **Decide**: HR action, legal hold, executive notifications, law-enforcement readiness.
5. **Remediate**: fix the control gaps that enabled the behavior.

## First 60 minutes: decisions & actions

### Decisions
- Do we **quiet-contain** (reduce permissions, increase monitoring) or **hard-contain** (disable account)?
- Is this likely to require **legal hold** today?
- Which executives/HR/Legal need to be in the room immediately?

### Actions (parallel)
- **Elevate logging**: increase retention/verbosity on repos, cloud storage, proxy, DLP for the subject.
- **Snapshot identities**: current group memberships, repo permissions, OAuth tokens, API keys.
- **Endpoint preservation**: identify active devices; isolate for forensic capture if policy allows.
- **Data egress blocks**: temporarily block personal cloud domains for the subject or enforce step-up auth.

## Evidence plan (what we must capture)

- Identity: SSO logins, MFA challenges, VPN/ZTNA sessions, device posture signals
- Repositories: read/download/export/clone events, object IDs, bytes, search queries
- Endpoints: file creation, archive commands, cloud sync clients, browser downloads
- Network: proxy logs for uploads, destination categories, DNS + SNI where available
- DLP/CASB: incident IDs, content fingerprints, recipients, sharing links
- Collaboration: chat/email relating to external ventures, recruiting, or document sharing

## Containment strategy

### Quiet containment (preferred early if risk allows)
- Reduce access to crown-jewel repos to “need-to-know”
- Enforce step-up authentication for high-risk actions (exports, clones, external shares)
- Disable ability to create external shares; restrict OAuth to approved apps
- Apply DLP hard-block rules for sensitive classifiers
- Increase monitoring and alert thresholds tuned to the subject account

### Hard containment (if exfil is confirmed or imminent)
- Suspend account / revoke sessions and OAuth tokens
- Isolate endpoints from network
- Freeze access keys and service accounts tied to the subject
- Preserve and collect devices under HR/legal procedure

## How we determine scope

We treat scope as a **set of objects**:
- docs/pages viewed/exported
- repos cloned/fetched + commit ranges
- artifacts downloaded (builds, images)
- files staged locally (paths, hashes, sizes)
- transfer destinations (accounts, share links, IPs)

Deliverable: a **scope ledger** (time, object, action, bytes, destination, evidence link).

## Risk assessment

- **Likelihood:** High (behavior indicates intentional concealment + boundary crossing).
- **Impact:** Critical (crown-jewel IP; competitive + legal/national-security implications).
- **Time sensitivity:** High (once data leaves the boundary, retrieval is uncertain).

## Post-incident improvements (what we expect to recommend)

1. **Privilege + access review**: least privilege, time-bound access, separation for crown-jewel repos
2. **Behavioral analytics**: peer-group baselines on repo access, exports, clones, and shares
3. **Egress governance**: personal cloud blocking or conditional access; cumulative transfer thresholds
4. **DLP modernization**: fingerprinting for key doc classes; hard-block exfil for “restricted” data
5. **Developer workflow controls**: restrict repo export; monitor high-risk git operations
6. **Insider risk program**: clear escalation, HR partnership, ethics reporting culture
7. **Forensic readiness**: immutable logging, longer retention, standardized evidence capture
