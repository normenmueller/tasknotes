# Integration Changelog

## Unreleased

### feat/ui-tweaks

Summary:
- Improves task card affordances and status visibility cues (subtask strip + note widget strip with icon override).
- Subtasks inherit the parent card's visible properties for consistent metadata display.

Changes:
- Add pointer cursor styling for all clickable task card elements (status, priority, indicators, chevron, blocking toggle, context menu, dates).
- Ensure project chevrons are always visible on the right and ordered after other badge icons.
- Mark project task cards with a dedicated class for chevron styling.
- Show a status strip on subtasks only when grouped by status and status is hidden.
- Hide status dots in the note widget and show a status strip instead (icon overrides strip).
- Propagate visible properties from parent task cards to subtasks.

Tests:
- Not run (UI-only change).

### fix-task-prop-based-ident

Summary:
- Prevents property-based task identification from mutating tags; tags change only when explicitly set.

Changes:
- Only add the task tag when tag-based identification is enabled.
- In property-based mode, preserve user/default tags without filtering.
- Only write `frontmatter.tags` during updates when tags are explicitly provided.
- Fixes callumalpass/tasknotes#1391.

Tests:
- Not run (tested manually in Obsidian).

### fix-prio-label-mapping

Summary:
- Ensures Kanban column headers use configured priority labels when grouped by priority, instead of raw values.

Changes:
- Kanban column headers now map priority values to their configured labels when grouped by priority (including swimlanes).

Tests:
- Not run (documentation-only change).

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
