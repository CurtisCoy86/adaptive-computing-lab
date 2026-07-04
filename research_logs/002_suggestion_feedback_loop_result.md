# Research Log 002: Suggestion Feedback Loop

## Experiment

Experiment 002: Suggestion Feedback Loop

## Date

2026-07-04

## Goal

Add a small local feedback system so Shellwalker can record whether suggestions are accepted, dismissed, or ignored.

This experiment creates the first basic learning loop for adaptive behavior.

## Hypothesis

If Shellwalker records whether suggestions are accepted, dismissed, or ignored, then future suggestions can become more useful and less annoying over time.

## What Was Built

Shellwalker now includes suggestion feedback commands:

```text
suggest list
suggest accept <id>
suggest dismiss <id>
suggest stats
```

The system can record suggestion feedback states:

```text
shown
accepted
dismissed
ignored
```

The feedback loop uses simple scoring:

```text
accepted: positive feedback
dismissed: negative feedback
ignored: negative/low-engagement feedback
shown: neutral record
```

Critical medication, bill, and overdue-task suggestions remain visible regardless of score.

## Files Changed

In the Shellwalker repository:

* `main.py`
* `tests/test_shellwalker.py`

## Tests Added

Eight feedback-loop tests were added covering:

* Suggestion recorded as shown
* Suggestion accepted and score increased
* Suggestion dismissed and score decreased
* Suggestion stats display
* Repeated dismissals reducing visibility for low-risk suggestions
* Critical suggestions not being fully hidden
* Automatic ignored state
* Privacy-safe records

## Tests Run

```text
43 passed
python3 -m py_compile main.py passed
```

## Shellwalker Commit

```text
649212a Add suggestion feedback loop
```

## What Worked

The feedback loop was implemented successfully.

Suggestion commands were added without breaking existing Shellwalker behavior.

All tests passed.

Compile check passed.

The privacy-safe record requirement was included.

Critical suggestions remain protected even when dismissed.

This successfully creates the first v0.1 learning mechanism inside Shellwalker.

## What Failed

No test failures were reported.

No compile errors were reported.

## Risks and Limitations

Feedback currently operates by suggestion type, not individual content.

Suggestion history currently grows without pruning.

The visibility threshold is fixed.

Accepting a suggestion does not complete the underlying action.

The scoring system is simple and may need tuning after real use.

## Privacy Notes

This experiment uses local suggestion feedback only.

The feedback system does not need personal identity, location, raw private notes, bank information, medication names, bill details, or other sensitive personal content.

The system records suggestion type and feedback state, not the personal content behind the suggestion.

## Human Notes

This experiment should be accepted as a v0.1 learning loop.

Experiment 001 gave Shellwalker adaptive priority.

Experiment 002 gives Shellwalker feedback.

Together, they create the first real adaptive cycle:

```text
rank what matters
show a suggestion
record user response
adjust future behavior
```

This is a foundational step toward predictive friction reduction.

## Decision

Accept as v0.1 learning loop.

## Next Step

Use Shellwalker normally and observe whether suggestion feedback feels useful, annoying, too hidden, or too manual.

Potential next experiments:

* Experiment 003: Overwhelm Detector
* Experiment 004: Adaptive Feature Visibility
* Experiment 005: Suggestion History Pruning
* Experiment 006: One-Thing Mode
