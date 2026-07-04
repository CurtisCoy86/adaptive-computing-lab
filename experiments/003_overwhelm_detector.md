# Experiment 003: Overwhelm Detector

## Hypothesis

If Shellwalker detects possible overload signals from safe local data, then it can suggest a smaller, less overwhelming next step without claiming certainty about the user’s emotional state.

## Purpose

Experiment 001 gave Shellwalker adaptive priority through the daily brief.

Experiment 002 gave Shellwalker a suggestion feedback loop.

Experiment 003 begins the first friction-state detection system.

The goal is not to diagnose the user.

The goal is to detect possible overload signals and offer a lower-friction path.

## Input

Shellwalker may use safe local signals such as:

* Open task count
* Overdue task count
* Medication logged today flag
* Bill due-soon flag
* Recent check-in trend bucket
* Suggestion feedback score for low-friction modes

## Minimum Data Needed

This experiment only needs:

* `open_task_count`
* `overdue_task_count`
* `missed_medication_flag`
* `bill_due_soon_flag`
* `checkin_trend_bucket`
* `low_friction_suggestion_score`, if available

The experiment does not need:

* Task text
* Medication names
* Bill names
* Exact bill amounts
* Location
* Identity
* Private check-in notes
* Raw emotional journal content

## Local-Only Data

The following must remain local:

* Actual task descriptions
* Medication details
* Bill details
* Check-in notes
* Any private notes or personal entries

## Derived Signals

Raw personal data should be converted into safer local signals.

Examples:

* Instead of task descriptions, use `overdue_task_count`
* Instead of medication name, use `missed_medication_flag`
* Instead of bill name or amount, use `bill_due_soon_flag`
* Instead of check-in notes, use `checkin_trend_bucket`

Possible check-in trend buckets:

* `stable`
* `low_mood`
* `low_focus`
* `high_lockup`
* `mixed_concern`
* `unknown`

## Consent Level

Level 1: Local non-sensitive data

If future versions use medication details, financial details, email, health sensors, or biometric information, consent level must be reviewed again.

## Behavior

Shellwalker should detect possible overload using a simple local heuristic.

The output should use cautious language.

Acceptable wording:

```text id="wjj54u"
Possible overload signal detected.
You have several open loops today. Consider using a smaller view or focusing on one next action.
```

Avoid wording like:

```text id="qift10"
You are overwhelmed.
You are failing.
You are mentally overloaded.
```

The system should suggest a lower-friction option, such as:

* Use `focus`
* Use One-Thing Mode if available later
* Review only the top priority
* Run `today` for a brief summary
* Complete medication first if medication is missing

## Overload Score v0.1

A simple score is enough for v0.1.

Possible scoring:

* Open tasks >= 5: `+2`
* Open tasks >= 8: additional `+2`
* Overdue tasks >= 2: `+2`
* Overdue tasks >= 5: additional `+2`
* Medication not logged today: `+2`
* Bill due soon: `+1`
* Low mood trend: `+1`
* Low focus trend: `+1`
* High lockup trend: `+1`

Possible levels:

* `0-2`: no overload signal
* `3-5`: mild overload signal
* `6+`: strong overload signal

These thresholds are experimental and should be reviewed after use.

## Critical Responsibility Rule

The detector must not hide critical responsibilities.

Examples:

* Medication
* Bills
* Health-related reminders
* Safety-related reminders
* Legal or financial deadlines

If overload is detected, Shellwalker may suggest a smaller view, but it should not remove critical items from visibility.

## Suggested Commands

Possible command:

```bash id="uov7kp"
overwhelm
```

Possible output:

```text id="y59v3f"
Overload Check
--------------
Signal: mild

Possible overload signal detected.
You have several open loops today.

Suggested next step:
Use `focus` to pick one task, or run `today` for the daily brief.
```

The command name may change if the current Shellwalker style suggests a better fit.

## Integration With Daily Brief

If the overload signal is mild or strong, the daily brief may include a cautious note.

Example:

```text id="jmn4l6"
Possible overload signal:
Several open loops are active today. A smaller next step may help.
```

This should not dominate the brief.

## Test

Add tests for:

1. No overload signal with minimal data.
2. Mild overload signal with several open tasks.
3. Strong overload signal with many overdue tasks and missing medication.
4. Bill due soon contributing to the score.
5. Check-in trend contributing cautiously.
6. Output uses cautious language.
7. Output does not claim the user is overwhelmed with certainty.
8. Critical responsibilities are not hidden.
9. Existing Shellwalker commands still work.

## Risk

* The detector may feel judgmental if wording is careless.
* Thresholds may be too sensitive or not sensitive enough.
* The system may overreact to temporary clutter.
* The system may increase cognitive load if it adds too much text.
* The detector may imply emotional certainty from limited data.
* Users may need a way to disable or quiet the detector later.

## Safety Notes

The detector should say “possible overload signal,” not “you are overwhelmed.”

The detector should suggest smaller next steps, not make life decisions.

The detector should use derived signals, not raw personal content.

The detector should remain local-only.

## Integration Decision

Accept only if:

* The heuristic is simple and understandable.
* The language is cautious.
* Tests pass.
* Critical items remain visible.
* The feature feels like support, not judgment.
* The implementation does not overcomplicate Shellwalker.

## Next Step

If accepted, future experiments can improve:

* One-Thing Mode
* Adaptive Feature Visibility
* Suggestion Explanation
* Suggestion History Pruning
* Adaptive language tone
* Routine detection
