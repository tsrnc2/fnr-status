# FNR status (GitHub Pages)

**EXPERIMENTAL / not FNR-000.** Public live snapshot of Formal Neural Reasoner experimental training progress.

- Site: https://tsrnc2.github.io/fnr-status/
- Data: [`status.json`](./status.json) (sanitized; no secrets; schema_version ≥ 2)
- UI: [`index.html`](./index.html) polls `status.json` every 60s

## How it updates

1. **After hub folds** — `multi-cloud-train` keep-spawner best-effort calls `scripts/publish_fnr_status_pages.sh`.
2. **Continue / manual** — same publish script from the training box.
3. **GitHub Actions** — on push here, Pages redeploys; weekday schedule keeps the deployment warm. Rebuild-from-REGISTRY runs in private `multi-cloud-train` via `refresh-fnr-status.yml` when `FNR_STATUS_DEPLOY_TOKEN` is set.

## Reading the dashboard (t95u)

- **UI auto-refresh** reloads the **published** `status.json` only — it is **not** live EC2/Linode telemetry.
- **`aws_burst.current`** is the only current AWS letter. History / latest DONE are completed letters and must not be read as the live burst.
- **Observation ages** show when each metric/status was observed relative to snapshot build time.
- **Validation accuracy** is shown prominently (`validation_accuracy.val_acc_pct`); metrics are producer-reported.
- Trend may be MIXED; EXPERIMENTAL progress ≠ FNR-000 admission.

Not a T7 ALLOW. Checker owns proof. Snapshot ≠ sole live health source for ops decisions.
