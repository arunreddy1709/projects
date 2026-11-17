# Projects

A portfolio of automation and Microsoft 365 / Entra ID administration projects. Each project lives in its own repository with full documentation, setup steps and screenshots. All published data is fictional demo data.

## Featured

### [Entra ID Sign-In Audit & Licence Review](https://github.com/arunreddy1709/entra-signin-audit)

![Dashboard overview](https://raw.githubusercontent.com/arunreddy1709/entra-signin-audit/main/docs/screenshots/01-dashboard-overview.png)

A daily, self-recovering Microsoft Graph sign-in collector with a desktop licence-review dashboard. It replaced a fragile monthly 31-day export.

- **Problem:** Entra ID P2 keeps only 30 days of sign-in logs, and month-long Graph pulls failed with HTTP 410 (an expired `nextLink`) and timeouts.
- **Solution:** a checkpointed daily collection in 6-hour slices that splits and retries a failing slice on its own. Data is staged, deduplicated and only then committed. It produces per-user last-sign-in history and Remove / Review licence verdicts from the M365 admin center export.
- **Result:** the first production run collected about 49,000 sign-ins in 105 minutes with no failed slices. Licence-removal candidates now refresh automatically every weekday.
- **Stack:** Windows PowerShell 5.1, Microsoft Graph (v1.0 + beta), Task Scheduler, a local `HttpListener` API, vanilla HTML/JS/SVG charts, and OpenXML (`.xlsx` written without Excel).

| Skill area | Shown in this project |
|---|---|
| Identity & M365 | Entra ID sign-in logs, interactive vs non-interactive sign-ins, licence hygiene |
| Automation | Scheduled collection, catch-up after missed days, stop/pause controls, toast notifications |
| Reliability | Half-open time windows, slice splitting on 410/timeout, retries with back-off, atomic file swaps, single-instance lock |
| Security | DPAPI-encrypted secret, localhost-only API with per-launch token, no secrets in the repo |
| Reporting | Interactive dashboard, monthly Excel reports, a read-only HTML view for managers |

## Repository index

| Repository | Description | Tech |
|---|---|---|
| [entra-signin-audit](https://github.com/arunreddy1709/entra-signin-audit) | Entra ID sign-in collector and licence-review dashboard | PowerShell, Microsoft Graph |

*More projects will be added here as they are published.*
