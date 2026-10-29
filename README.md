# FNR status (GitHub Pages)

**EXPERIMENTAL / not FNR-000.** Public live snapshot of Formal Neural Reasoner experimental training progress.

- Site: https://tsrnc2.github.io/fnr-status/
- Data: [`status.json`](./status.json) (sanitized; no secrets)
- UI: [`index.html`](./index.html) polls `status.json` every 60s

## How it updates

1. **After hub folds** — `multi-cloud-train` keep-spawner best-effort calls `scripts/publish_fnr_status_pages.sh`.
2. **Continue / manual** — same publish script from the training box.
3. **GitHub Actions** — on push here, Pages redeploys; weekday schedule keeps the deployment warm. Rebuild-from-REGISTRY runs in private `multi-cloud-train` via `refresh-fnr-status.yml` when `FNR_STATUS_DEPLOY_TOKEN` is set.

Not a T7 ALLOW. Checker owns proof. Snapshot ≠ sole live health source for ops decisions.
