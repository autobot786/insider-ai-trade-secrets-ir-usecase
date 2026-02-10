# Tabletop Exercise (TTX): Insider Theft of AI Supercomputing IP

## Duration
90–120 minutes

## Audience
SOC, IR, IAM, DLP/CASB, Endpoint/Forensics, Legal, HR, Engineering leadership, (optional) Comms/PR.

## Exercise objectives
Participants will:
1. Detect and triage insider data theft signals (DLP + repo anomalies)
2. Practice **containment decisions** (quiet vs hard)
3. Build an **evidence plan** and scope ledger
4. Coordinate HR/legal process and communications
5. Produce an executive update and remediation actions

## Scenario overview (fictional)
A privileged engineer with access to crown-jewel AI infrastructure materials shows:
- escalating breadth of access to sensitive docs and code
- bulk exports/clones and local staging
- attempted uploads to personal cloud storage
- geolocation obfuscation consistent with foreign travel masking

## Roles (suggested)
- Incident Commander / IR Lead
- SOC Analyst Lead
- IAM Lead
- DLP/CASB Lead
- Endpoint Forensics Lead
- Legal Counsel
- HR Partner
- Engineering Manager
- Executive Sponsor (CISO)

## Rules of engagement
- Assume you can request logs/telemetry listed in `usecase/incident-response-usecase.md`
- Use “facts + confidence” language
- If uncertain, decide based on risk and record assumptions

## Materials
- Injects: `tabletop/injects/`
- Participant handout: `tabletop/participant-handouts.md`
- Scoring: `tabletop/scoring.md`
- Reference: `usecase/mitre-mapping.md`, playbooks/runbooks

## Run of show

1) **Kickoff (5 min)** – facilitator reads scenario and goals  
2) **Inject 1–2 (20 min)** – DLP alert triage and escalation  
3) **Inject 3–5 (30 min)** – repo anomalies, staging evidence, identity anomalies  
4) **Inject 6–7 (20 min)** – containment decision, HR/legal involvement  
5) **Inject 8 (15 min)** – executive brief & comms  
6) **Debrief (10–15 min)** – lessons learned and action items

## Facilitation tips
- Encourage parallel workstreams (IAM vs forensics vs comms)
- Ask participants to create: **timeline**, **scope ledger**, **decision log**
- Keep the focus on boundary crossings and evidence quality
