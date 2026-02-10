# Inject 05 (T+45): Identity Anomaly / Geo Masking

**Delivered to:** IAM / IR  
**Channel:** Identity analytics alert

**Content:**
Identity platform flags:
- login from `SG` source IP with VPN exit showing `UK`
- new device token created for `corp-laptop-14`
- MFA prompts occurring at unusual hours

**Expected actions:**
- Determine whether this is account takeover or insider intent
- Apply step-up auth / session restrictions
- Decide containment posture
