# Lab 02: Abnormal Collection from Repositories

## Prompt

The subject accessed multiple sensitive spaces and repositories over the last 30 days.
Your job is to prove or disprove **abnormal collection**.

## Tasks

- [ ] Identify the top repositories/doc spaces accessed by `engineer.a`
- [ ] Compare access volume to their own baseline and to peer-group baseline
- [ ] Find evidence of bulk export/clone
- [ ] Identify the “crown jewel” objects accessed

**Hint:** Use `notebooks/01_access_baselining.ipynb`.

<details>
<summary>Suggested solution outline</summary>

Look for:
- spikes in **unique objects accessed**
- spikes in **bytes downloaded/exported**
- high **breadth** (many repos/spaces) compared to role baseline
- high-risk actions: `export`, `bulk_download`, `git clone --mirror`, large `git fetch`

Outputs:
- anomaly days (z-score / IQR) for reads + downloads
- list of top sensitive repos and doc spaces with timestamps
- evidence links for the biggest export/clone events
</details>
