# Inject 04 (T+35): Endpoint Staging Evidence

**Delivered to:** Endpoint/Forensics  
**Channel:** EDR alert + telemetry

**Content:**
EDR shows:
- `7z` execution creating `accelerator_arch_docs.7z`
- output size > 1 GB
- staging folder: `/Users/engineer.a/tmp/`

**Expected actions:**
- Preserve endpoint evidence
- Check for additional archives, deletion attempts, sync clients
- Correlate staging timestamps with DLP/proxy uploads
