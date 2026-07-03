# Experiment 003: One-Thing Mode

## Hypothesis

When the user is overloaded, showing one recommended next action may be more useful than showing a full task list.

## Input

- Tasks
- Due dates
- Medication status
- Bills
- User priority markers

## Behavior

Shellwalker offers a command that displays only one recommended next action.

Example command:

```bash
one
```

Example output:

```text
Next best action:
Take medication.

After that, run `one` again.
```

## Priority Order v0.1

1. Medication not logged today
2. Bill due today or overdue
3. Overdue task
4. Task marked important
5. Soonest due task
6. Gentle check-in prompt
7. No action needed

## Test

Confirm the command selects from medication, urgent bills, overdue tasks, and normal tasks in the correct order.

## Risk

- The system may choose the wrong action.
- The system may oversimplify important responsibilities.
- The user may need to inspect the full list.

## Integration Decision

Integrate only as optional mode. Never replace the full task list.
