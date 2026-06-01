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

The standalone tool now requires a verified Coordinare account session before users can create boards, add/edit/delete documents, create tasks, import manifests, load example data, or export packages. A verified CTMS session remains accepted as a transition fallback. It supports a permanent General board for site-specific documents, study-specific boards, document creation/editing, task follow-up, JSON/CSV manifest import, CSV/JSON exports, and ZIP exports with originals when local attachments or `fileUrl` values are available.

## Auth Model

The current standalone Documents Manager has no backend document store of its own. Coordinare authentication is verified by calling `https://coordinare.co/api/sso/session` with browser credentials; CTMS authentication is also verified through `https://ctms.coordinare.co/api/document-manager/session` as a transition fallback. Unauthenticated browsers receive a failed session check and all mutating document controls remain disabled. The `?sso=connected` / `?ctms=connected` URL flags and localStorage session markers are display-only client-side markers and must never be treated as access control. Any future backend sync must re-authenticate against Coordinare or CTMS server-side and must not trust URL flags or localStorage markers.

Authenticated usage events are sent to `https://ctms.coordinare.co/api/document-manager/events` and summarized for the DSCS admin at `/admin/documents`. These events contain product usage counts and event metadata only; they do not upload document files or turn browser-local document records into the regulated source of truth.

Thanks.
