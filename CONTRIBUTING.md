# Contributing to Claude Prompt Optimizer

Thank you for your interest in contributing! This project thrives on community input — whether it's new examples, rule improvements, or bug reports.

## How You Can Contribute

### 1. Submit Before/After Examples

The most valuable contribution is real-world optimization examples. If the optimizer transformed a prompt in a particularly impressive (or surprisingly poor) way, we want to see it.

**How to submit:**
- Open a Pull Request adding your example to the relevant file in `examples/`
- Use the existing format: raw prompt → optimized prompt → brief explanation
- Include the domain (coding, creative, business, analysis, etc.)
- Ensure examples demonstrate genuine quality improvement

### 2. Propose New Optimization Rules

If you've identified a pattern that consistently improves prompt quality for Claude Opus 4.6 and isn't covered by the existing 10 rules, propose it.

**Requirements for new rules:**
- Must be grounded in Anthropic's official documentation or reproducible testing
- Must apply to a broad category of prompts (not a single edge case)
- Must include a clear BAD/GOOD before/after example
- Should not conflict with existing rules

**How to propose:**
- Open an Issue using the **Feature Request** template
- Include the rule name, description, rationale, and at least 2 examples

### 3. Report Optimization Problems

If the optimizer produces suboptimal results for a specific prompt, report it so we can improve.

**How to report:**
- Open an Issue using the **Bug Report** template
- Include the raw prompt you submitted
- Include the optimizer's output
- Explain what you expected and what went wrong

### 4. Improve Documentation

Typos, unclear explanations, missing context — all documentation improvements are welcome.

### 5. Translate

The source files were originally written in German. If you'd like to contribute translations to other languages, open an issue to coordinate.

## Pull Request Guidelines

1. **One concern per PR** — don't mix a new example with a rule change
2. **Follow existing formatting** — match the style of the files you're editing
3. **Test your examples** — actually run your before/after examples through Claude Opus 4.6 to verify improvement
4. **Keep descriptions concise** — explain what changed and why in the PR description

## Style Guide

- Use clear, professional English
- Use XML tag names consistently (`<role>`, `<task>`, `<constraints>`, etc.)
- When showing before/after examples, make the improvement obvious and genuine
- Don't invent capabilities the optimizer doesn't have

## Code of Conduct

Be respectful, constructive, and professional. This project exists to help the community — keep interactions focused on improving the optimizer.

## Questions?

Open an Issue with the label `question` — we're happy to help.
