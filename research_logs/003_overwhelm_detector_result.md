# Research Log 003: Overwhelm Detector

## Experiment

Experiment 003: Overwhelm Detector

## Date

2026-07-04

## Goal

Add a small local overload signal detector that uses safe derived signals to suggest a lower-friction next step.

The goal is not to diagnose the user or claim certainty about emotional state.

The goal is to detect possible overload signals and offer a smaller path forward.

## Hypothesis

If Shellwalker detects possible overload signals from safe local data, then it can suggest a smaller, less overwhelming next step without claiming certainty about the user’s emotional state.

## What Was Built

Shellwalker now includes an `overwhelm` command.

The command performs an overload check using derived-only scoring.

The detector uses safe local signals such as:

* Open task count
* Overdue task count
* Medication logged today flag
* Bill due-soon flag
* Recent check-in trend signals

The output uses cautious language and frames the result as a limited estimate.

Critical responsibilities remain unchanged and visible.

## Files Changed

In the Shellwalker repository:

* `main.py`
* `tests/test_shellwalker.py`

## Tests Added

Nine tests were added covering:

* No overload signal with minimal data
* Mild overload signal with several open tasks
* Strong overload signal with many overdue tasks and missing medication
* Bill due soon contributing to score
* Check-in trend contributing cautiously
* Output using cautious language
* Output not claiming the user is overwhelmed with certainty
* Critical responsibilities not being hidden
* Existing Shellwalker commands still working

## Tests Run

```text id="amjc3p"
52 passed
python3 -m py_compile main.py passed
```

## Shellwalker Commit

```text id="fiorgw"
f8eaff3 Add overload signal detector
```

## What Worked

The overload detector was implemented successfully.

The command uses derived-only scoring rather than raw personal content.

The output uses cautious language.

The feature does not diagnose the user.

The feature does not hide medication, bill, or overdue-task responsibilities.

All tests passed.

Compile check passed.

This experiment establishes the first friction-state detector in Shellwalker.

## What Failed

No test failures were reported.

No compile errors were reported.

## Risks and Limitations

The thresholds are fixed heuristics.

Check-in scoring uses the latest three entries.

Overdue bills count toward due-soon.

Medication timing is not considered.

The detector is a limited estimate and may be wrong.

The feature may need tuning after real use.

## Privacy Notes

This experiment uses local derived signals only.

The detector does not need:

* Personal identity
* Location
* Raw private notes
* Bank information
* Medication names
* Bill names
* Exact bill amounts
* Raw emotional journal content

The detector uses counts, flags, and trend signals instead of sensitive raw data.

## Human Notes

This experiment should be accepted as a v0.1 detector.

Experiment 001 gave Shellwalker adaptive prioritization.

Experiment 002 gave Shellwalker feedback.

Experiment 003 gives Shellwalker a basic friction-state detector.

Together, these form a stronger adaptive loop:

```text id="m9em5c"
detect possible friction state
rank what matters
show a suggestion
record feedback
adjust future behavior
```

This is an important step toward predictive friction reduction.

## Decision

Accept as v0.1 detector.

## Next Step

Use Shellwalker normally and observe whether the `overwhelm` command feels useful, too sensitive, too quiet, or too judgmental.

Potential next experiments:

* Experiment 004: One-Thing Mode
* Experiment 005: Suggestion Explanation
* Experiment 006: Suggestion History Pruning
* Experiment 007: Adaptive Feature Visibility
