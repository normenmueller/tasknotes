# Integration Changelog

## Unreleased

### fix-angle-brackets

Summary:
- Improves angle‑bracket link handling, project title display, and dependency link normalization for consistent internal link resolution.

Changes:
- Supports `<...>` autolinks and angle-bracket markdown links with URL decoding and `.md` handling.
- Normalizes internal link resolution across overlays, filters, group headers, and renderers.
- Prefers frontmatter `title` for project link display when appropriate.
- Normalizes dependency entries and expands resolution candidates for more reliable linking.

Tests:
- Added unit coverage for angle‑bracket link parsing and project display name resolution in `linkUtils`.

### fix-prio-label-mapping

Summary:
- Ensures Kanban column headers use configured priority labels when grouped by priority, instead of raw values.

Changes:
- Kanban column headers now map priority values to their configured labels when grouped by priority (including swimlanes).

Tests:
- Not run (documentation-only change).
