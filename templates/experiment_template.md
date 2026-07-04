# Experiment Template

## Experiment

Name and number.

## Hypothesis

What do we believe this feature will prove or improve?

## Input

What data does the system use?

Examples:

- Tasks
- Medication logs
- Check-ins
- Bill due dates
- Completion patterns
- User-entered notes
- Time of day
- Startup behavior

## Minimum Data Needed

What is the least amount of data required for this experiment to work?

## Local-Only Data

What data must remain local and should not be shared or centrally stored?

## Derived Signals

Can raw data be converted into safer signals?

Example:

- Instead of exact bill amount, use budget_pressure = low / medium / high.
- Instead of task text, use overdue_task_count.
- Instead of medication name, use medication_logged_today = true / false.

## Consent Level

Choose one:

- Level 0: No personal data
- Level 1: Local non-sensitive data
- Level 2: Local sensitive data
- Level 3: Local automation
- Level 4: Shared aggregate research
- Level 5: Special review required

## Behavior

What should the system do?

Examples:

- Suggest a priority
- Display a warning
- Reduce visible clutter
- Reorder a list
- Ask a check-in question
- Summarize a pattern
- Recommend a smaller action

## Test

How do we know it works?

Examples:

- Unit test
- Manual test
- Simulated user data
- Command output verification

## Risk

What could go wrong?

Examples:

- The system could make wrong assumptions
- The system could become annoying
- The system could increase cognitive load
- The system could hide important information
- The system could over-personalize too early

## Integration Decision

Choose one:

- Accept into Shellwalker
- Revise and retest
- Reject
- Save as research note
- Split into smaller experiment
