# Integration Changelog

## Unreleased

### feat-note-widget-status-strip

Summary:
- Note widget cards render status as a subtle right-edge strip; status icons remain visible when configured.

Changes:
- Filter `status` from note widget visible properties to avoid showing dots by default.
- Add a note-widget card mode that renders a status strip for project cards and subtasks.
- Preserve status icons in the note widget (icons override the strip).

Tests:
- Not run (pending Obsidian verification).

### feat-subtask-status-strip

Summary:
- Subtasks show a subtle status-colored stripe (instead of a full dot) only when grouped by status.

Changes:
- Mark task cards as status-hidden only when status is grouped (hideStatusIndicator).
- Subtasks inherit parent visible properties (including custom fields).
- Subtasks inherit that state and replace the status dot with a thin right-edge stripe.
- Add styling for the subtask status stripe.
- Subtask rendering now receives the parent view’s status visibility settings.

Tests:
- Not run (tested manually in Obsidian).

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

### feat/ui-tweaks

Summary:
- Improves task card affordances with pointer cursors on clickable icons and a consistently visible project chevron.

Changes:
- Add pointer cursor styling for all clickable task card elements (status, priority, indicators, chevron, blocking toggle, context menu, dates).
- Ensure project chevrons are always visible on the right and ordered after other badge icons.
- Mark project task cards with a dedicated class for chevron styling.

Tests:
- Not run (UI-only change).

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
