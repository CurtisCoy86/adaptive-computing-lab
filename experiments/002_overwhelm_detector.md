# Experiment 002: Overwhelm Detector

## Hypothesis

Shellwalker can identify possible overwhelm by detecting combinations of overdue tasks, missed medication logs, negative check-in trends, and bills due soon.

## Input

- Number of overdue tasks
- Missed medication logs
- Check-in score trends
- Bills due soon
- Incomplete recurring items

## Behavior

Shellwalker flags a possible overload state and suggests reducing the visible workload.

Example:

```text
Possible overload detected.

You have several unfinished items. Consider using One-Thing Mode instead of reviewing the full list.
```

## Test

Use simulated data sets representing normal, busy, and overloaded states.

## Risk

- The system may feel judgmental.
- The system may infer too much.
- The system may be wrong because it has limited data.

## Integration Decision

Start as a passive message only. Do not let it automatically change task lists yet.
