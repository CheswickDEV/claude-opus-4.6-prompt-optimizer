---
name: Bug Report
about: Report a case where the optimizer produced suboptimal results
title: "[BUG] "
labels: bug
assignees: ''
---

## Describe the Problem

A clear description of what went wrong with the optimization.

## Raw Prompt (Input)

```
Paste the exact prompt you submitted to the optimizer here.
```

## Optimizer Output

```
Paste the optimizer's full response here (analysis + optimized prompt + notes).
```

## Expected Behavior

What did you expect the optimized prompt to look like? What's wrong with the output?

## Actual Behavior

What specifically is suboptimal about the optimization? For example:
- Missing context that should have been inferred
- Incorrect complexity routing (over-optimized / under-optimized)
- Wrong role assignment
- XML structure issues
- Contradictory instructions in the output
- Rule that should have fired but didn't (or vice versa)

## Environment

- **Interface**: Claude.ai Project / API / Workbench / Other
- **Model**: Claude Opus 4.6 (confirm or specify)
- **Language**: English / German / Other

## Additional Context

Add any other context, screenshots, or notes here.
