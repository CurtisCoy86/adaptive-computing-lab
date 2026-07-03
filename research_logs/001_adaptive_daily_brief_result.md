# Research Log 001: Adaptive Daily Brief

## Experiment

Experiment 001: Adaptive Daily Brief

## Date

2026-07-03

## Goal

Test whether Shellwalker's startup daily brief can reduce cognitive load by prioritizing the most important user state instead of listing everything equally.

## Hypothesis

A daily brief that changes based on user state will reduce cognitive load more than a static startup summary.

## What Was Built

Shellwalker's daily brief was updated to follow a priority order:

1. Medication not logged today
2. Bills due today or soon
3. Overdue tasks
4. Check-in trend concern, if available
5. Normal open tasks

The brief now limits visible tasks to three so the startup output does not become overwhelming.

The full task list remains available through the normal task list command.

## Files Changed

In the Shellwalker repository:

* `main.py`
* `tests/test_shellwalker.py`

## Tests Added

Tests were added for:

* Medication missing today
* Bill due soon
* Multiple overdue tasks
* No urgent items
* Empty or minimal data
* Priority ordering
* Task-list preservation
* Cautious check-in language

## Tests Run

```text
35 passed
python3 -m py_compile main.py passed
```

## Shellwalker Commit

```text
8cecd89 Add adaptive daily brief
```

## What Worked

The adaptive daily brief now follows the required priority order.

The brief reduces task visibility to the most important few items.

Existing task-list behavior was preserved.

The system uses cautious language around check-in trends.

All tests passed.

## What Failed

No test failures were reported.

No compile errors were reported.

## Risks and Limitations

The check-in thresholds are initial heuristics and may need adjustment after real use.

Unusually large medication or bill lists are not currently capped.

The brief may still need tuning based on whether it feels helpful during actual daily startup use.

## Human Notes

This experiment should be accepted as an initial baseline, not as a final adaptive system.

The feature successfully moves Shellwalker from a static assistant toward adaptive cognitive-load reduction.

The next phase should observe whether the brief actually feels clearer during use.

## Decision

Accept as initial experimental baseline.

## Next Step

Use Shellwalker normally and evaluate whether the new daily brief feels helpful, too aggressive, too quiet, or too cluttered.

Potential next experiment:

Experiment 002: Overwhelm Detector
