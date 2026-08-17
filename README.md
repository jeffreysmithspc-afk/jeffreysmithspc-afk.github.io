# Impact Water Inc — Volunteer Release Signing Page

This repository serves the public signing page for Impact Water Inc's
volunteer Release of Liability, at:

**https://jeffreysmithspc-afk.github.io/**

Printed QR codes point at that address. **Do not delete or rename this
repository** — doing so kills every printed QR code.

## How it works

- `index.html` is the entire signing page: release text, form, and a
  finger-drawn signature pad. Fully self-contained (no build step, no
  dependencies).
- On submit, the page POSTs JSON to a Google Apps Script backend owned by
  mark@impactwater.org, which generates the signed PDF, files it in Google
  Drive, logs it, and emails copies to Impact Water and the volunteer.
- No volunteer data ever touches this repository or GitHub.

## Updating the legal text

The release text lives in **two** places that must stay in sync:

1. `Code.gs` (`WAIVER_CLAUSES`) in the Apps Script project — drives the PDF.
2. `index.html` here — drives what volunteers read on screen.

Both carry a version tag (currently `8.15.2026`). The backend **rejects
submissions from a page whose version doesn't match its own**, so a stale
page fails safely instead of collecting signatures on outdated terms. When
changing the text: update both, bump the version in both, redeploy the Apps
Script (Manage deployments → New version), and commit here.
