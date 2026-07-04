# Research Log 006: Shellwalker Guided Submenus

## Experiment

Experiment 006: Shellwalker Guided Submenus

## Testbed

Shellwalker

## Implementation Commit

6130c2a Add guided home submenus

## Date

2026-07-04

## Summary

Shellwalker was updated with guided submenus for core life-assistant systems.

The previous home menu reduced some command memorization friction, but several options only displayed command help. This experiment replaced those placeholder help routes with real guided submenu flows for medications, tasks, bills, check-ins, and suggestion feedback.

The goal was to make Shellwalker easier to use without replacing direct commands or turning the project into a full GUI.

## What Changed

- Home option 4 now opens a guided Medication submenu.
- Home option 5 now opens a guided Task submenu.
- Home option 6 now opens a guided Bill submenu.
- Home option 7 now opens a guided Check-in submenu.
- Home option 8 now opens a guided Suggestion Feedback submenu.
- Add actions prompt for required fields.
- State-changing actions display current records before asking for an explicit name, number, or ID.
- Back returns safely to the home menu.
- Existing direct commands continue to work.
- Existing save format remains unchanged.

## Test Results

- Automated tests: 73 passed.
- Compile check: passed.
- Full terminal submenu regression: passed.
- Working tree clean after implementation.

## Manual Test

The following home menu paths were manually tested:

- `home`
- `4` Medication menu
- `5` Task menu
- `6` Bill menu
- `7` Check-in menu
- `8` Suggestion feedback menu
- `10` Exit home

All tested submenu routes opened correctly and returned safely.

## What Worked

The guided submenus reduced command memorization friction while preserving the command-line structure.

The implementation kept direct commands intact, avoided new personal data storage, and required explicit user input for state-changing actions.

This helped Shellwalker feel more usable without making the system more controlling.

## What Did Not Change

Shellwalker is still a terminal application.

This experiment did not add predictive behavior, adaptive menu ordering, or a graphical interface.

Historical cleanup for completed tasks and paid bills remains a separate future design issue.

## Privacy / Agency Review

No new raw personal data collection was added.

Submenus collect the same user input that existing commands already require.

State-changing actions still require explicit user selection.

The system does not silently complete, remove, pay, dismiss, or hide critical responsibilities.

## Research Notes

This experiment supports the idea that adaptive computing does not need to start with complex prediction.

Reducing interface friction can be an adaptive design step by itself.

Guided menus help the user reach existing functions with less memory burden, especially when tired, overloaded, or returning after time away.

This creates a better foundation for future focus recommendations.

## Follow-Up Questions

- Should submenus eventually remember the last-used area?
- Should the home menu show a recommended next area without forcing it?
- Should Focus Mode route into these submenus?
- Should paid bills and completed tasks have separate history menus?
- Should menu flows support cancellation from every prompt?

## Conclusion

Experiment 006 was successful.

Shellwalker now provides guided access to core life-assistant features while preserving direct command access and user agency.

This is a strong foundation for a future Focus Mode experiment.
