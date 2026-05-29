# Coordinare Documents Manager

Standalone document board, task, and export tool for Coordinare.

Hosted URL: https://documentmanager.coordinare.co/

## What It Does

- Uses the Coordinare CTMS login flow through a CTMS auth bridge.
- Creates a permanent General board for site-specific, non-study-specific documents.
- Creates study-specific boards with study/site metadata.
- Adds, edits, opens, and deletes documents with expiration dates, owners, notes, local attachments, or file URLs.
- Tracks board-specific tasks for missing documents, expirations, and migration cleanup.
- Imports a JSON or CSV manifest from any source and stores it locally in the browser.
- Exports selected metadata as CSV or JSON.
- Packages selected originals into a ZIP when local attachments or browser-fetchable `fileUrl` values are available.
- Includes `manifest.csv`, `manifest.json`, `boards.json`, `task_board_export.csv/json`, `orphan_report.json`, and `export_metadata.json` inside ZIP exports.

## Why It Is Separate

This is intentionally independent from Polsia production internals. It connects to the Coordinare CTMS auth flow for login, then stores document boards locally in the browser until a CTMS backend sync is added. Polsia only needs to link to the hosted tool anywhere the app currently mentions or links to Documents or Document Manager.

## Manifest Fields

The importer accepts flexible field names and normalizes them into:

- `id`
- `source`
- `title`
- `study` or `study_id`
- `site` or `site_name`
- `board` or `board_name`
- `type`
- `size`
- `owner`
- `expiration` or `expiration_date`
- `uploaded` or `created_at`
- `fileUrl`

Common aliases are supported, including `file_url`, `download_url`, `signedUrl`, `study_id`, `site_name`, `uploaded_at`, and `created_at`.

## Local Preview

```bash
python3 -m http.server 4173 --bind 127.0.0.1
```

Then open:

```text
http://127.0.0.1:4173/
```

## Polsia Handoff

Please link every Coordinare Documents / Document Manager entry point to `https://documentmanager.coordinare.co/`, including:

- Homepage Documents button
- Dashboard Documents button or card
- Navigation/sidebar links
- Any Document Manager links
- Any Task Board attachment/document links that are intended to open the document inventory

Do not modify production data, delete the old page, change upload behavior, or migrate files. This request is only to route document-related links to the standalone tool.
