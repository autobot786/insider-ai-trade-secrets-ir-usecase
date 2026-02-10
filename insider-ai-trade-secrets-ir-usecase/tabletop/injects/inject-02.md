# Inject 02 (T+10): Repeated Attempts

**Delivered to:** SOC / DLP Lead  
**Channel:** Follow-up alert

**Content:**
Within 45 minutes of the first alert, additional DLP incidents appear:
- different destination: `dropbox.example`
- archive name changes: `accelerator_arch_docs.7z`
- one attempt is **allowed** due to policy exception for “engineering tools testing”

**Expected actions:**
- Confirm which transfer succeeded (bytes, destination account)
- Escalate severity
- Recommend containment changes (disable exception, block personal cloud)
