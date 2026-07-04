# Experiment 004: Shellwalker Home Menu

## Status

Planned

## Testbed

Shellwalker

## Research Area

Predictive friction reduction  
Command-access friction  
Human-approved adaptive interface design

## Hypothesis

If Shellwalker provides a numbered home/menu system, then users can access core features with less command memorization and lower cognitive load without requiring a full GUI rewrite.

## Problem

Shellwalker has gained several useful systems, including tasks, medications, bills, check-ins, adaptive daily briefs, suggestion feedback, and overload detection.

However, as features increase, the user must remember more commands. This creates command memorization friction, especially when the user is tired, overloaded, or returning to the project after time away.

The system needs a simple way to expose core functions without hiding the underlying commands.

## Proposed Change

Add a simple terminal-based home/menu system to Shellwalker.

Possible commands:

- `home`
- `menu`

The menu should display numbered options for common actions.

Initial menu:

1. Daily brief
2. Overload check
3. Focus task
4. Medication menu
5. Task menu
6. Bill menu
7. Check-in menu
8. Suggestion feedback
9. Help
10. Exit menu

## Design Principles

- Reduce command memorization friction.
- Preserve existing command-line behavior.
- Do not remove direct commands.
- Do not automate critical responsibilities away.
- Keep the menu inspectable and predictable.
- Avoid manipulation, urgency tricks, or engagement loops.
- Make the interface easier without making the user passive.

## Privacy Model

This experiment should not add new personal data collection.

The menu should only route the user to existing Shellwalker features.

No raw personal content should be stored for menu usage.

If menu usage tracking is added later, it should store only derived interaction counts by feature category, not raw task, medication, bill, or check-in content.

## Success Criteria

- `home` and/or `menu` opens a numbered terminal menu.
- The menu allows access to core Shellwalker features.
- Existing direct commands still work.
- The menu does not break startup behavior.
- The menu does not silently complete, hide, or remove critical responsibilities.
- Tests pass.
- The implementation remains simple and understandable.

## Failure Criteria

- Menu logic becomes overly complex.
- Existing commands break.
- Critical responsibilities become hidden behind optional menu paths.
- The menu creates pressure, gamification, or engagement loops.
- The feature requires a full GUI rewrite.
- The implementation stores unnecessary personal data.

## Expected Outcome

A lightweight menu layer should make Shellwalker easier to use without changing its underlying command-first structure.

This may become the first step toward a broader adaptive interface system where the system helps the user find the right action without taking control away from them.

## Notes

Shellwalker is the first testbed, not the final product.

This experiment should remain small.
