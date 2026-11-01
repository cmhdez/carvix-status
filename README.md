> **Design and created with ❤ by Carlos M. Hernandez**

# Carvix status

## [Live status](https://status.carvix.com): <!--live status--> **🟩 All systems operational**

The Carvix status page ([status.carvix.com](https://status.carvix.com)) and an uptime checker that runs outside AWS, on GitHub Actions, using [Upptime](https://upptime.js.org).

## What is monitored

Only public, customer-facing endpoints, every 5 minutes. Never the staff console or anything behind a sign-in. The list lives in [`.upptimerc.yml`](./.upptimerc.yml).

- **Carvix website**: https://carvix.com
- At launch (listed in the config, commented out until they serve): the API health check (`https://api.carvix.com/health`) and the Help Center (`https://carvix.com/help`).

## How paging works

1. When a check fails, Upptime opens an issue titled `🛑 <site> is down` (or `⚠️ <site> has degraded performance`) with the labels `status` and the site's slug.
2. [`pagerduty.yml`](./.github/workflows/pagerduty.yml) sees the new issue and triggers an incident on the PagerDuty service **Carvix uptime (external)**: critical when down, warning when degraded. The dedup key is `upptime-<issue number>`.
3. When the site recovers, Upptime closes the issue and the workflow resolves the incident. Closing or deleting the issue by hand resolves it too; reopening it pages again.

`skipDeleteIssues: true` keeps short outages as closed issues, so the incident history is complete. The routing key is the repository secret `PAGERDUTY_ROUTING_KEY`.

## Adding a site

Add an entry under `sites:` in `.upptimerc.yml` with a `name`, a short `slug` and the `url`, then push to `master`. Setup CI rebuilds the page, and the new site pages PagerDuty with no other change. Only add a URL once it serves, or it pages straight away.

## Status

<!--start: status pages-->
<!--end: status pages-->

> **Design and created with ❤ by Carlos M. Hernandez**
