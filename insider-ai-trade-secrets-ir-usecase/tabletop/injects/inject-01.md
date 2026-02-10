# Inject 01 (T+0): DLP Alert – Restricted AI IP Upload Attempt

**Delivered to:** SOC / IR Lead  
**Channel:** Ticket / SIEM alert

**Content:**
A DLP incident triggers:

- Policy: `Restricted-AI-IP`
- Action: `Upload blocked (personal cloud)`
- User: `engineer.a@orchid.example`
- Destination: `drive.personal.example`
- File: `orchestrator_design_export.zip`
- Size: `1.4 GB`
- Device: `corp-laptop-14`

**Expected actions:**
- Triage fidelity (policy, classifier, scope)
- Pull identity + repo + endpoint context
- Decide if escalation to IR is warranted
