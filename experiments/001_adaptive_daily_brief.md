# Experiment 001: Adaptive Daily Brief

## Hypothesis

A daily brief that changes based on user state will reduce cognitive load more than a static startup summary.

## Input

- Medication status
- Tasks
- Bills
- Check-in history
- Current date
- Overdue items

## Behavior

Shellwalker generates a startup daily brief that prioritizes the most important items instead of listing everything equally.

Expected behavior:

- If medication is not logged, show medication first.
- If bills are due soon, show bills second.
- If many tasks are overdue, show only the top one to three.
- If check-ins are trending low, suggest a small grounding action.
- Use cautious, supportive language.
- Do not hide full information permanently.

## Possible Output

Example:

```text
Daily Brief

Priority 1: Medication has not been logged today.
Priority 2: One bill is due soon.
Priority 3: You have several open tasks. Start with one.

Suggested next action:
Run: meds log
```

## Test

Create sample data for different user states and confirm the brief changes appropriately.

Test cases:

1. Medication missing, no urgent bills, normal tasks.
2. Medication logged, bill due soon, no overdue tasks.
3. Many overdue tasks, low check-in trend.
4. No urgent items.
5. Empty data.

## Risk

- The system may choose the wrong priority.
- The system may hide too much information.
- The system may increase cognitive load if the brief becomes too long.
- The system may sound too certain about emotional state.

## Integration Decision

Accept only if the brief feels clearer than the current startup output.
