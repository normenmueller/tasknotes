# feat-note-widget-status-strip

## Note widget status strip (icon-aware)

The task card note widget now renders status as a subtle right-edge strip for both project cards and subtasks, reducing visual noise while keeping status visible. If a status icon is configured, the icon is shown instead of the strip.

Examples (illustrative):

- Note widget without status icons: project + subtasks show a thin status strip; no status dots.
- Note widget with status icons: the icon appears and the strip is suppressed.

## Changelog

### Task Cards & Note Widgets

- Filter `status` from note widget visible properties so dots are not shown by default.
- Add a note-widget card mode that renders a status strip for project cards and subtasks.
- Preserve status icons in the note widget (icon overrides strip).
