# Known Issues

This file tracks known issues, limitations, risks, and future maintenance items discovered during Adaptive Computing Lab experiments.

The goal is not to fix everything immediately.

The goal is to avoid forgetting important observations while keeping each experiment small.

## Status Labels

* `open` — not addressed yet
* `watch` — observe during normal use
* `planned` — likely future experiment
* `fixed` — addressed
* `accepted risk` — known limitation accepted for now

---

## Shellwalker Known Issues

### 001: Suggestion history grows without pruning

Status: `open`

Source:

* Experiment 002: Suggestion Feedback Loop
* Shellwalker commit: `649212a Add suggestion feedback loop`

Description:

Suggestion feedback history currently grows without a pruning, archiving, or compaction rule.

Risk:

Over time, the save file may become cluttered with old suggestion records.

Possible future fix:

Create a suggestion history pruning or compaction experiment.

Possible approaches:

* Keep only recent raw suggestion records
* Aggregate older records by suggestion type
* Preserve scores while pruning old events
* Allow user to clear suggestion history

---

### 002: Suggestion visibility threshold is fixed

Status: `watch`

Source:

* Experiment 002: Suggestion Feedback Loop

Description:

Suggestion visibility reduction currently uses a fixed score threshold.

Risk:

A fixed threshold may be too aggressive for some suggestion types and too weak for others.

Possible future fix:

Allow thresholds to vary by suggestion type or user preference.

---

### 003: Feedback operates by suggestion type, not individual context

Status: `watch`

Source:

* Experiment 002: Suggestion Feedback Loop

Description:

Feedback currently applies to a suggestion type, such as `open_task`, rather than a more specific context.

Risk:

Dismissing one kind of open-task suggestion could reduce visibility for all open-task suggestions.

Possible future fix:

Add privacy-safe suggestion context.

Example:

* `open_task_many_tasks`
* `open_task_low_priority`
* `checkin_trend_low_focus`
* `bill_due_soon`

Do not store raw personal content.

---

### 004: Accepting a suggestion does not complete the underlying action

Status: `accepted risk`

Source:

* Experiment 002: Suggestion Feedback Loop

Description:

When a user accepts a suggestion, Shellwalker records positive feedback but does not automatically complete the related action.

Risk:

The word “accept” may imply that the action itself was completed.

Current mitigation:

Shellwalker prints:

```text id="bxizn5"
Feedback only; use the normal command to complete the action.
```

Possible future fix:

Add clearer wording or future action-linked suggestions.

---

### 005: Repeated daily brief views may create duplicate suggestion records

Status: `watch`

Source:

* Experiment 002: Suggestion Feedback Loop

Description:

The daily brief records suggestions when it is generated. Running the brief multiple times may create multiple suggestion records.

Risk:

Repeated viewing may distort suggestion feedback history.

Possible future fix:

Deduplicate suggestions by type and date, or record only one suggestion per type per day.

---

### 006: Critical suggestions are protected but may need tone adjustment

Status: `watch`

Source:

* Experiment 002: Suggestion Feedback Loop

Description:

Medication, bill, and overdue-task suggestions remain visible regardless of feedback score.

Risk:

This protects important responsibilities, but repeated reminders could still become annoying.

Possible future fix:

Allow critical suggestions to become quieter without disappearing.

Example:

* Shorter wording
* Lower visual emphasis
* Less repetition
* “Still important, shown quietly” mode

---

## Future Experiment Candidates

### Suggestion History Pruning

Possible experiment number:

`Experiment 003` or later

Goal:

Prevent suggestion history from growing endlessly while preserving useful feedback scores.

---

### Overwhelm Detector

Possible experiment number:

`Experiment 003`

Goal:

Detect possible overload using safe local signals such as overdue task count, missed medication flag, bill due-soon flag, and check-in trend bucket.

---

### Suggestion Explanation

Goal:

Allow the user to inspect why a suggestion appears more or less often.

Possible command:

```bash id="9xcg4b"
suggest explain <type>
```

Example output:

```text id="v7w4qb"
Open-task suggestions appear less often because they were dismissed several times.
Medication reminders remain visible because they are marked as critical.
```

---

## Daily Review Practice

Before starting new work, review this file and ask:

1. Is anything urgent?
2. Is anything becoming annoying during real use?
3. Should any known issue become the next experiment?
4. Are we stacking new features on top of an unresolved foundation problem?


---


### 007: Overload detector thresholds are fixed heuristics

Status: `watch`

Source:
- Experiment 003: Overwhelm Detector
- Shellwalker commit: `f8eaff3 Add overload signal detector`

Description:
The overload detector uses fixed thresholds for open tasks, overdue tasks, medication state, bills due soon, and check-in trends.

Risk:
The detector may be too sensitive or not sensitive enough for real use.

Possible future fix:
Tune thresholds after manual use notes or allow user-adjustable sensitivity.


---


### 008: Medication timing is not considered by overload detector

Status: `watch`

Source:
- Experiment 003: Overwhelm Detector

Description:
The detector treats medication not logged today as a signal without considering whether the scheduled medication time has arrived.

Risk:
The detector may add overload score too early in the day.

Possible future fix:
Compare medication scheduled time to current time before counting it as missing.


---


## Shellwalker interaction reliability limitations

The Shellwalker audit found several user interaction issues that may require future refinement:

- Suggestion lifecycle and ID stability can become confusing if suggestions are regenerated too often.
- Multi-word names are not yet handled consistently across all commands.
- Historical cleanup for completed tasks and paid bills remains limited.
- Feedback history may need pruning or summarization if it grows too large.

These issues affect usability and cognitive load more than core functionality.


---



## Shellwalker historical cleanup limitations

After Experiment 005, paid-bill and completed-task historical cleanup remains limited.

Paid bills and completed tasks may require separate history views or new numbering/removal semantics. This was not changed during the interaction reliability pass because it would require a broader design decision.

Future work should explore history management without making critical responsibilities easier to hide accidentally.


---



