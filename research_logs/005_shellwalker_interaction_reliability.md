# Research Log 005: Shellwalker Interaction Reliability Pass

## Experiment

Experiment 005: Shellwalker Interaction Reliability Pass

## Testbed

Shellwalker

## Implementation Commit

Pending

## Date

2026-07-04

## Summary

Shellwalker received a focused interaction reliability pass after an audit found that the core systems worked, but some user-facing behaviors were confusing, surprising, or unsafe.

This experiment focused on suggestion lifecycle clarity, reset protection, feedback wording, menu accuracy, and input validation.

## Audit Basis

Before implementation:

- Automated tests: 57 passed.
- Compile check passed.
- All 28 public commands were exercised.
- Save/reload persistence worked.
- Core systems worked without crashes.

However, the audit confirmed several interaction issues:

- Suggestion IDs became stale after daily brief refreshes.
- `new` could erase life-assistant data without confirmation.
- Feedback output confused immediate feedback with cumulative score.
- Home menu labels overpromised submenu behavior.
- Multi-word names behaved inconsistently.
- Invalid medication times and negative bill amounts were accepted.

## What Changed

Pending.

## Test Results

Pending.

## What Worked

Pending.

## What Did Not Work

Pending.

## Privacy / Agency Review

The experiment did not add new raw personal data collection.

The changes were intended to improve user agency by making system behavior clearer and reducing accidental destructive actions.

Suggestion feedback remained privacy-safe by tracking feedback by suggestion type rather than raw personal content.

## Research Notes

This experiment reinforced that adaptive computing needs interaction reliability before deeper adaptation.

A system can technically pass tests while still increasing cognitive load if its behavior feels surprising.

Predictability, clear state, and safe correction are foundational parts of user-owned adaptive systems.

## Follow-Up Questions

- Should Shellwalker separate RPG identity reset from life-assistant data reset?
- Should suggestions have stable IDs across days?
- Should there be an explicit suggestion archive?
- Should completed tasks and paid bills have separate history views?
- Should command parsing support quoted names globally?
- Should the home menu evolve into real submenus?

## Conclusion

Pending.
