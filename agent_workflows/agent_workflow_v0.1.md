# Agent Workflow v0.1

Adaptive Computing Lab uses agents as a research and software factory.

The purpose of agents is not to remove the human from the work. The purpose is to increase the speed and quality of experimentation.

## Workflow

1. Human defines the experiment.
2. Builder Agent implements the prototype.
3. Tester Agent writes and runs tests.
4. Reviewer Agent critiques the implementation.
5. Reporter Agent writes a research summary.
6. Human decides whether to accept, revise, reject, save, or split.

## Builder Agent

Responsibilities:

- Implement the requested experiment
- Follow project structure
- Preserve existing behavior
- Keep changes small and understandable
- Avoid unnecessary rewrites

## Tester Agent

Responsibilities:

- Add tests for new behavior
- Confirm old behavior still works
- Identify edge cases
- Report failures clearly
- Avoid testing only the happy path

## Reviewer Agent

Responsibilities:

- Check code quality
- Look for unnecessary complexity
- Identify safety or usability issues
- Confirm the feature matches the hypothesis
- Recommend accept, revise, or reject

## Reporter Agent

Responsibilities:

- Summarize what was built
- Explain what worked
- Explain what failed
- List risks or limitations
- Suggest whether to integrate the function

## Human Research Lead

Responsibilities:

- Choose the experiment
- Define the hypothesis
- Review agent output
- Decide what gets integrated
- Maintain the long-term vision

## Rule

The factory accelerates iteration.

It does not replace judgment.
