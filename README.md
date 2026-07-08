# CDR / Open Banking Incident & Error Reference Library

Live site: https://ackmed1337.github.io/cdr-incident-library/

A single-page reference tool for Consumer Data Right (CDR) / Open Banking work:

- **Incident Log** — team root-cause notes for real issues hit in the field (mTLS, IdentityServer4, CDS schema/versioning, etc).
- **Error & Versioning Reference** — the full standard CDR error code catalogue, HTTP header / version negotiation rules, and a live endpoint version schedule (Banking, Common, Admin, Security), all sourced from the [Consumer Data Standards](https://consumerdatastandardsaustralia.github.io/standards/) and re-verified against the live source periodically in-browser.

## How the incident log works

There's no backend — this is a static site on GitHub Pages. Incidents are stored as **GitHub Issues** on this repo instead of free-write storage:

1. Anyone clicking **+ Submit incident** gets a pre-filled GitHub Issue (labelled `incident`) opened in a new tab. Submitting it requires their own GitHub sign-in.
2. It does **not** appear on the site yet — it's pending.
3. A maintainer reviews the issue and adds the `approved` label.
4. Once approved, it shows up in the Incident Log on the site (the page reads issues via the public GitHub API, cached client-side for ~10 minutes).

To review what's pending: [issues labelled `incident` without `approved`](https://github.com/Ackmed1337/cdr-incident-library/issues?q=is%3Aissue+label%3Aincident+-label%3Aapproved).

## Updating the reference data

The error catalogue and version schedule are embedded directly in `index.html`, sourced from `ConsumerDataStandardsAustralia/standards`. The freshness bar at the top of the page re-hashes the live source files (at most every 6 hours) and flags if upstream has changed — it doesn't auto-rewrite the page, so if it flags drift, pull the updated tables manually from the standards repo.
