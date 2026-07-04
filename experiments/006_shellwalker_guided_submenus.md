# Experiment 006: Shellwalker Guided Submenus

## Status

Planned

## Testbed

Shellwalker

## Research Area

Command-access friction  
Guided interaction design  
Predictive friction reduction  
User agency

## Hypothesis

If Shellwalker provides guided submenus for common life-assistant areas, then users can manage tasks, medications, bills, and check-ins with less command memorization while preserving direct command access.

## Problem

Shellwalker now has a home menu, but several options still only show command help.

This reduces some command memorization friction, but the user still has to remember exact syntax for common actions after choosing an area.

For example, choosing the task area should eventually allow the user to list, add, complete, or remove tasks through guided prompts instead of requiring command memorization.

## Proposed Change

Add simple guided submenus for core life-assistant systems:

- Task menu
- Medication menu
- Bill menu
- Check-in menu
- Suggestion feedback menu, if simple

The existing home menu should route into these submenus.

Direct commands must continue to work.

## Possible Task Menu

1. List tasks
2. Add task
3. Complete task
4. Remove task
5. Back

## Possible Medication Menu

1. List medications
2. Add medication
3. Log medication
4. Remove medication
5. Back

## Possible Bill Menu

1. List bills
2. Add bill
3. Mark bill paid
4. Remove bill
5. Back

## Possible Check-in Menu

1. Add check-in
2. Show check-in trend
3. Back

## Possible Suggestion Menu

1. List suggestions
2. Accept suggestion
3. Dismiss suggestion
4. Show suggestion stats
5. Back

## Design Principles

- Reduce command memorization friction.
- Preserve direct command access.
- Keep all actions human-approved.
- Do not silently complete, remove, pay, dismiss, or hide responsibilities.
- Avoid adding raw personal data storage.
- Keep menus simple and predictable.
- Prefer clear prompts over automation.
- Do not turn Shellwalker into a full GUI.

## Privacy Model

This experiment should not add new personal data collection.

Submenus should only route to existing behavior or collect the same user input that existing commands already collect.

No raw usage tracking should be added.

Suggestion feedback should remain privacy-safe by suggestion type.

## Success Criteria

- Home menu routes to real guided submenus instead of command-help placeholders.
- Users can perform common task, medication, bill, and check-in actions through numbered menus.
- Existing direct commands still work.
- Critical responsibilities remain visible.
- Destructive actions still require clear user intent.
- Existing tests pass.
- New or updated tests cover submenu routing.
- Implementation remains simple.

## Failure Criteria

- Menu logic becomes overly complex.
- Direct commands break.
- Submenus silently complete or hide responsibilities.
- The system stores unnecessary personal data.
- User agency is reduced.
- Shellwalker becomes harder to maintain.

## Expected Outcome

Guided submenus should make Shellwalker feel less clunky and easier to use without requiring a full graphical interface.

This experiment should move Shellwalker from a command-only testbed toward a more accessible adaptive assistant interface.

## Notes

This experiment should remain small.

Do not add predictive behavior yet.

The goal is guided access, not automation.
