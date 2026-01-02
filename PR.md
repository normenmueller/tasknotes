# feat/ui-tweaks

## Task Card Interaction Cues

This change set improves task card affordances by making all clickable icons show a pointer cursor, and by keeping the project chevron visible on the right after other badge icons.

Examples (illustrative):

- Status and priority dots now show a pointer cursor to indicate they are clickable.
- Project chevron stays visible on project cards and appears after other badge icons.

## Changelog

- Add pointer cursor styling for all clickable task card elements (status, priority, indicators, chevron, blocking toggle, context menu, dates).
- Ensure project chevrons are always visible on the right and ordered after other badge icons.
- Mark project task cards with a dedicated class for chevron styling.

## Tests

- Not run (UI-only change).
