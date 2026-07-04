# Experiment 002: Suggestion Feedback Loop

## Hypothesis

If Shellwalker records whether suggestions are accepted, dismissed, or ignored, then future suggestions can become more useful and less annoying over time.

This creates the first basic learning loop for Adaptive Computing Lab.

## Purpose

Experiment 001 made the daily brief adaptive by priority.

Experiment 002 adds feedback.

The goal is to let Shellwalker begin learning which suggestions actually help the user and which ones create unnecessary drag.

## Input

* Suggestions shown to the user
* User response to suggestions
* Time of suggestion
* Suggestion type
* Current Shellwalker context
* Existing task, medication, bill, and check-in state

## Minimum Data Needed

The experiment only needs:

* Suggestion ID or type
* Timestamp or date bucket
* Whether the suggestion was shown
* Whether the user accepted it
* Whether the user dismissed it
* Whether the user ignored it
* A simple usefulness score

The experiment does not need personal identity, exact location, private notes, raw task text, medication names, bill names, or financial amounts.

## Local-Only Data

The following should remain local:

* Actual task text
* Medication details
* Bill details
* Check-in notes
* Any personal notes or private entries

## Derived Signals

Raw personal data should be converted into safer signals.

Examples:

* Instead of task text, use `suggestion_type = one_thing_mode`
* Instead of bill name, use `suggestion_type = bill_due_soon`
* Instead of medication name, use `suggestion_type = medication_log`
* Instead of exact emotional note, use `suggestion_type = check_in_prompt`

## Consent Level

Level 1: Local non-sensitive data

If future versions connect suggestion feedback to medication, finance, email, or health signals, consent level should be reviewed again.

## Behavior

Shellwalker should record basic suggestion feedback.

Possible feedback states:

* `shown`
* `accepted`
* `dismissed`
* `ignored`

Shellwalker should allow the user to respond to a suggestion.

Example commands may include:

```bash
suggestions
suggest accept <id>
suggest dismiss <id>
suggest stats
```

The exact command names may change based on the current Shellwalker style.

## Expected Behavior

When Shellwalker shows a suggestion, it records that the suggestion was shown.

If the user accepts the suggestion, Shellwalker increases that suggestion type’s usefulness score.

If the user dismisses the suggestion, Shellwalker decreases that suggestion type’s usefulness score.

If a suggestion is repeatedly dismissed, Shellwalker should reduce how often that suggestion appears.

If a suggestion is repeatedly accepted, Shellwalker may rank it higher in future daily briefs.

## Scoring v0.1

Simple scoring is enough.

Example:

* Accepted: `+2`
* Dismissed: `-2`
* Ignored: `-1`
* Shown: `0`

A suggestion type with a negative score should become less visible.

A suggestion type with a positive score may become more visible.

## Critical Responsibility Rule

Critical responsibilities should not silently disappear.

Examples:

* Medication
* Bills
* Health-related reminders
* Safety-related reminders
* Legal or financial deadlines

If a critical suggestion is repeatedly dismissed, Shellwalker may make the wording quieter or less repetitive, but it should not hide the responsibility completely.

## Test

Add tests for:

1. A suggestion being recorded as shown.
2. A suggestion being accepted and increasing score.
3. A suggestion being dismissed and decreasing score.
4. Suggestion stats displaying correctly.
5. Repeated dismissals reducing future visibility for low-risk suggestions.
6. Critical suggestions not being fully hidden after dismissal.
7. Existing Shellwalker commands still working.

## Risk

* The system may hide useful suggestions too quickly.
* The system may overfit to a small number of interactions.
* The user may dismiss something once due to timing, not because it is useless.
* Important responsibilities could become too quiet if the rules are careless.
* The feedback system could add complexity to a simple terminal app.

## Safety Notes

The first version should be local-only.

No feedback data should be shared outside the local Shellwalker data store.

The system should explain adaptation in simple language.

Example:

```text
This suggestion appears less often because it was dismissed several times.
```

## Integration Decision

Accept only if:

* Feedback is easy to record.
* Existing commands are preserved.
* Tests pass.
* Critical suggestions are protected.
* The system remains understandable.

## Next Step

If accepted, future experiments can use suggestion feedback to improve:

* Adaptive Daily Brief
* One-Thing Mode
* Overwhelm Detector
* Language style adaptation
* Routine detection
