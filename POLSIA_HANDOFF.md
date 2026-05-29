# Polsia Request: Link To Coordinare Documents Manager

Hi Polsia,

We are moving the Coordinare document board, task, and export workflow to a separate standalone tool named **Coordinare Documents Manager**.

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

The standalone tool now uses the Coordinare CTMS auth flow for login. It supports a permanent General board for site-specific documents, study-specific boards, document creation/editing, task follow-up, JSON/CSV manifest import, CSV/JSON exports, and ZIP exports with originals when local attachments or `fileUrl` values are available.

## Auth Model

The current standalone Documents Manager has no backend session of its own. The `?ctms=connected` URL flag and `coordinare.documents.ctmsSession` localStorage value are display-only client-side markers and must never be treated as access control. Any future backend sync must re-authenticate against CTMS server-side and must not trust either the URL flag or localStorage marker.

Thanks.
