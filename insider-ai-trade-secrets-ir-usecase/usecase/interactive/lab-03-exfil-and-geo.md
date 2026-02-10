# Lab 03: Exfiltration Path + Geo Masking

## Prompt

Identity telemetry suggests activity was made to “look domestic”, while upload attempts target personal cloud.

## Tasks

- [ ] Identify suspicious VPN/proxy patterns (new ASN, new exit nodes, time-of-day spikes)
- [ ] Correlate geo/IP with repo access and DLP events
- [ ] Determine the likely exfil channel(s)
- [ ] Decide: quiet containment or hard containment?

**Hint:** Use `notebooks/03_geo_anomaly_vpn.ipynb` and `notebooks/02_dlp_event_analysis.ipynb`.

<details>
<summary>Suggested solution outline</summary>

Indicators:
- rapid geo changes (impossible travel)
- VPN sessions from residential IPs not previously used
- OAuth token creation for personal cloud apps
- repeated near-threshold uploads (“chunking”)

Decision rule (example):
- If **confirmed successful transfer** → hard containment.
- If only **blocked attempts** but high intent → quiet containment + legal/HR engagement.
</details>
