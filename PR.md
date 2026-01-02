# feat/ui-tweaks

## Task Card Interaction Cues

Task card affordances are improved by making all clickable icons show a pointer cursor, and by keeping the project chevron visible on the right after other badge icons.

Examples (illustrative):

- Status and priority dots now show a pointer cursor to indicate they are clickable.
- Project chevron stays visible on project cards and appears after other badge icons.

## Subtask Status Strip When Grouped by Status

When a view is grouped by status, the status property is hidden but subtasks still need a status cue (they can differ from their parent). In that case, subtasks render a thin status-colored stripe on the right edge instead of the full dot. If status is simply hidden via properties (without grouping), no status indicator is shown at all.

## Note Widget Status Strip (icon-aware)

In the task card note widget, status is displayed as a subtle right-edge strip for both project cards and subtasks. If a status icon is configured, the icon is shown instead of the strip.

## Subtasks Inherit Visible Properties

Subtasks now inherit the parent card's visible properties (including custom fields), so their metadata line matches the parent configuration.

## Changelog

- Add pointer cursor styling for all clickable task card elements (status, priority, indicators, chevron, blocking toggle, context menu, dates).
- Ensure project chevrons are always visible on the right and ordered after other badge icons.
- Mark project task cards with a dedicated class for chevron styling.
- Show a status strip on subtasks only when grouped by status and status is hidden.
- Hide status dots in the note widget and show a status strip instead (icon overrides strip).
- Propagate visible properties from parent task cards to subtasks.

## Tests

- Not run (UI-only change).
