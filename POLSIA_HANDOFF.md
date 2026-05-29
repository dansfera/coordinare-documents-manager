# Polsia Request: Link To Coordinare Documents Manager

Hi Polsia,

We are moving the Coordinare document inventory/export workflow to a separate standalone tool named **Coordinare Documents Manager**.

Please update every Coordinare place that mentions or links to Documents, Document Manager, or the document inventory so it points to:

https://documentmanager.coordinare.co/

This includes:

- Homepage Documents button
- Dashboard Documents button/card
- Navigation/sidebar Documents links
- Document Manager links
- Task Board attachment/document links that are intended to open the document inventory

Please keep this as a routing-only change:

- No production data changes
- No deletes
- No upload behavior changes
- No migration
- No modification to R2/Neon data

The standalone tool accepts a JSON/CSV manifest, stores it locally in the browser, exports selected metadata as CSV/JSON, and packages originals into a ZIP when `fileUrl` values are fetchable.

Thanks.
