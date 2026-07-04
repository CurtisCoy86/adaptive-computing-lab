# Predictive Friction Reduction

## Core Idea

Modern predictive systems are often used to capture attention, increase engagement, sell ads, or influence behavior.

Adaptive Computing Lab redirects this pattern.

The goal is not to predict what a person will click.

The goal is to predict where a person may experience friction, overload, delay, confusion, or unnecessary effort.

## Moral Inversion

Ad-tech prediction often asks:

```text
What is this person likely to click, watch, buy, or engage with?
```

Adaptive Computing Lab asks:

```text
What is this person trying to do, what is getting in their way, and what small adaptation could help?
```

## Support Value

Instead of ranking content by expected engagement, Adaptive Computing Lab ranks possible helpful actions by expected support value.

Possible support factors:

* Urgency
* Importance
* Cognitive-load reduction
* Past usefulness
* User preference
* Annoyance risk
* Agency risk
* Safety importance

## Basic Loop

```text
observe → score → rank → suggest → user approves → adapt → learn
```

## Simple Example

If a user repeatedly ignores full task lists, the system may reduce task visibility and suggest One-Thing Mode.

If the user accepts One-Thing Mode repeatedly, the system may ask whether it should become the default during high-load days.

If the user dismisses a suggestion multiple times, the system should stop showing it for a while.

## Important Boundary

The system should not remove all friction.

It should remove unnecessary friction and preserve meaningful friction.

Meaningful friction includes:

* Confirmation before major changes
* Review before spending money
* Learning effort
* Safety checks
* Awareness of important responsibilities

## Design Principle

Adaptive systems should demote what is unused, elevate what is useful, and ask before changing what is important.

## Critical Responsibility Rule

Critical responsibilities can be demoted in wording, but not silently removed.

Examples:

* Medication
* Bills
* Health-related reminders
* Safety-related reminders
* Legal or financial deadlines

## Research Direction

This note establishes predictive friction reduction as a core research pillar of Adaptive Computing Lab.

The long-term goal is to test whether predictive personalization can reduce cognitive load without becoming manipulative, invasive, or agency-reducing.
