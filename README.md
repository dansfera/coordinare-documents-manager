# Coordinare Documents Manager

Standalone read-only document inventory and export tool for Coordinare.

Hosted URL: https://documentmanager.coordinare.co/

## What It Does

- Imports a JSON or CSV manifest from any source.
- Stores the imported manifest locally in the browser.
- Filters by study, site, source, search text, and selection.
- Exports selected metadata as CSV or JSON.
- Packages selected original files into a ZIP when `fileUrl` values are browser-fetchable.
- Includes `manifest.csv`, `manifest.json`, `orphan_report.json`, and `export_metadata.json` inside ZIP exports.

## Why It Is Separate

This is intentionally independent from the Coordinare CTMS app and from Polsia production internals. Polsia only needs to link to the hosted tool anywhere the app currently mentions or links to Documents or Document Manager.

## Manifest Fields

The importer accepts flexible field names and normalizes them into:

- `id`
- `source`
- `title`
- `study`
- `site`
- `board`
- `type`
- `size`
- `owner`
- `uploaded`
- `status`
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
