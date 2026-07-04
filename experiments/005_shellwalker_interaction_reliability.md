# Experiment 005: Shellwalker Interaction Reliability Pass

## Status

Planned

## Testbed

Shellwalker

## Research Area

User agency  
Interaction reliability  
Predictive friction reduction  
Trust-preserving adaptive systems

## Hypothesis

If Shellwalker makes command behavior clearer, protects user data from accidental loss, and keeps suggestion feedback predictable, then the system will reduce cognitive load more effectively without creating confusion or mistrust.

## Problem

Shellwalker’s automated audit found that the core systems work and tests pass, but several interaction behaviors feel clunky or surprising.

The system technically functions, but some commands create cognitive friction:

- Suggestion IDs become stale after refreshing the daily brief.
- The `new` command can erase life-assistant data without confirmation.
- Feedback scoring messages are unclear.
- Home menu labels overpromise submenu behavior.
- Multi-word names behave inconsistently.
- Some invalid inputs are accepted.

These issues matter because adaptive systems must be predictable, inspectable, and safe to correct.

A system that surprises the user increases cognitive load, even if it passes automated tests.

## Audit Summary

Automated audit results:

- No repository files were changed.
- Working tree remained clean.
- Automated tests: 57 passed.
- Compile check passed.
- All 28 public commands were exercised using isolated temporary saves.
- Save/reload persistence worked.
- Roll failure, partial success, and success branches worked.

Confirmed issues:

1. Suggestion IDs become stale unexpectedly.
2. `new` can erase all life-assistant data without confirmation.
3. Accepted-feedback output is confusing.
4. Home submenu labels overpromise.
5. Multi-word names behave inconsistently.
6. Input validation gaps exist.
7. Feedback history grows on every brief refresh.
8. Historical data management is limited.

## Proposed Change

Perform a focused reliability pass on Shellwalker’s command and menu behavior.

Primary fixes:

1. Keep suggestion IDs actionable until explicit feedback, or clearly report when a suggestion is no longer active.
2. Prevent `new` from erasing life-assistant data without explicit confirmation.
3. Improve accepted/dismissed feedback wording.
4. Rename home menu labels or make menu actions match their labels.
5. Improve validation for invalid medication times and negative bill amounts.

Secondary fixes, if simple:

1. Clarify or support multi-word names.
2. Prevent duplicate feedback history from growing on every brief refresh.
3. Improve cleanup paths for paid bills and completed tasks.

## Design Principles

- Predictability is part of reducing cognitive load.
- Passing tests is not enough if the user experience feels unreliable.
- Critical personal data should not be erased accidentally.
- Feedback loops must remain understandable.
- The system should explain state changes clearly.
- The system should preserve agency and avoid hidden behavior.
- Fix confusing behavior before adding larger adaptive features.

## Privacy Model

This experiment should not add new raw personal data collection.

Suggestion feedback should continue storing feedback by suggestion type, not raw suggestion content.

Any new tracking or state management should remain minimal and local.

No surveillance-style usage logging should be added.

## Success Criteria

- Refreshing the daily brief does not unexpectedly make visible suggestions unactionable.
- If a suggestion is no longer actionable, the system clearly explains why.
- `new` does not erase life-assistant data without explicit confirmation.
- Feedback messages distinguish immediate feedback change from cumulative score.
- Home menu labels accurately describe what each option does.
- Option 8 gives direct access to active suggestion feedback, preferably `suggest list`.
- Invalid medication times are rejected.
- Negative bill amounts are rejected.
- Existing commands continue to work.
- Existing tests pass.
- New or updated tests cover the fixed behaviors.

## Failure Criteria

- Suggestion state becomes more confusing.
- Fixes require a large rewrite.
- `new` still silently erases life-assistant data.
- Critical responsibilities become easier to hide or dismiss accidentally.
- More raw personal data is stored.
- Existing commands break.

## Expected Outcome

Shellwalker should feel more predictable and less clunky.

This experiment should improve trust in the system by making command behavior clearer, safer, and easier to reason about.

## Notes

This is a reliability and agency pass, not a feature expansion.

The priority is not adding more adaptive behavior.

The priority is making the existing adaptive behavior trustworthy.
