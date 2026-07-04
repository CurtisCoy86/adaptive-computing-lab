# Privacy Model v0.1

## Core Principle

Adaptive Computing Lab is built around data minimalism, local-first design, and user-owned adaptation.

The system should collect the least sensitive, least identifying, most local form of data needed to provide help.

Personalization does not require surveillance.

## Guiding Rule

Keep raw personal data local. Share only consented, anonymized friction patterns.

The lab does not need to know who the user is to study where friction occurs.

## Data Minimalism

Adaptive Computing Lab practices data minimalism.

If a derived signal is enough, do not store the raw data.

If a local reference is enough, do not copy the data.

If a temporary calculation is enough, do not persist it.

If the user has not approved the signal, do not use it.

Data collection is not a default. It is a justified design choice.

## Local-First Personal Data

Sensitive personal data should remain on the user’s device by default.

Examples of local-only data include:

* Name
* Address
* Phone number
* Email address
* Bank account information
* Exact bank balance
* Account numbers
* Passwords
* Government IDs
* Medical records
* Medication names
* Biometric data
* Facial recognition data
* Raw camera data
* Raw microphone data
* Exact location history
* Private messages
* Full email contents
* Children or family identifying details
* Legal documents

If it can identify, expose, embarrass, financially harm, medically expose, or endanger the user, it stays local by default.

## Derived Signals

The system should prefer derived signals over raw personal data.

Example:

Instead of storing:

* Rent is $650
* Rent is due on the 5th
* User has a specific bank balance
* User lives at a specific address

The system may locally derive:

* Housing bill due soon
* Budget pressure is high
* Payday is within a certain window

For research, this may become only:

* Budget friction event occurred

## Store Meaning, Not Identity

The system should store the meaning of a friction event, not the identifying details behind it.

Bad central data:

```text
Curtis has $214.18 in his bank account and rent due at a specific address.
```

Better local derived signal:

```text
housing_bill_due_soon = true
budget_pressure = high
```

Best aggregate research signal:

```text
financial_admin_friction_event = true
income_timing_pressure = high
```

## Local Reference, Global Pattern

Adaptive Computing Lab uses a local-reference, global-pattern model.

The local system may reference personal reality with permission.

The broader research system should only study anonymized, consented, non-identifying friction patterns.

The local system knows the person.

The research layer studies the pattern.

## Collective Research

Collective friction research must be opt-in.

Any shared research data should be:

* Anonymized
* Aggregated
* Consent-based
* Minimally detailed
* Non-identifying
* Deletable when possible
* Free from raw personal text
* Free from exact location
* Free from exact timestamps unless necessary

The system may study friction, but it must not turn human struggle into an extractive product.

## Experiment Data Requirement

Every experiment should include a data section answering:

1. What is the minimum data needed?
2. Can raw data stay local?
3. Can a derived signal be used instead?
4. Does the system need to persist this data?
5. Can the user inspect it?
6. Can the user delete it?
7. What consent level is required?
8. What should never be collected for this experiment?

## Consent Levels

### Level 0: No Personal Data

The experiment uses no personal data.

### Level 1: Local Non-Sensitive Data

The experiment uses local app data such as task counts, command usage, or settings.

### Level 2: Local Sensitive Data

The experiment references sensitive data locally, such as medication, finances, email, or health signals.

### Level 3: Local Automation

The experiment changes behavior or triggers actions on the user’s device.

### Level 4: Shared Aggregate Research

The experiment contributes anonymized friction patterns to broader research.

### Level 5: Not Allowed Without Special Review

The experiment would involve raw biometric data, raw camera/microphone data, exact location history, private messages, financial account details, medical records, or other high-risk data.

## Hard Boundaries

Adaptive Computing Lab should not:

* Sell personal data
* Store central identity profiles
* Require facial recognition
* Require exact location
* Upload raw emails by default
* Upload bank data by default
* Upload health data by default
* Hide what is being tracked
* Make major changes without user approval
* Turn helpful personalization into surveillance

## Design Law

Adaptive Computing Lab should never centralize personal life data when a local reference or derived signal is enough.

## Closing Statement

The system can be deeply personal without being centrally invasive.

The goal is to prove that helpful adaptation can be built from minimal, local, user-approved signals.
