> [!IMPORTANT]
> ### 🚀 A newer version is here: [Claude Opus 4.8 Prompt Optimizer »](https://github.com/CheswickDEV/claude-opus-4.8-prompt-optimizer)
> This 4.6 optimizer has been superseded. The 4.8 edition is calibrated for Opus 4.8 (effort defaults to `high` everywhere, per-turn adaptive thinking). This version stays here for reference.
# 🧠 Claude Prompt Optimizer

### Turn any raw prompt into a production-ready, Anthropic best-practice prompt — in seconds.

[![GitHub Stars](https://img.shields.io/github/stars/CheswickDEV/claude-opus-4.6-prompt-optimizer?style=social)](https://github.com/CheswickDEV/claude-opus-4.6-prompt-optimizer)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Claude Model](https://img.shields.io/badge/Claude-Opus_4.6-blueviolet)](https://www.anthropic.com)
[![Last Commit](https://img.shields.io/github/last-commit/CheswickDEV/claude-opus-4.6-prompt-optimizer)](https://github.com/CheswickDEV/claude-opus-4.6-prompt-optimizer/commits/main)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)

---

**Claude Prompt Optimizer** is a meta-prompting system that transforms vague, unstructured prompts into professionally optimized prompts following [Anthropic's official best practices](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering). Paste any raw prompt — from a one-liner to a detailed brief — and get back a structured, XML-tagged, model-specific prompt engineered for Claude Opus 4.6's full capabilities.

> **This is not a prompt collection.** It's a systematic optimization engine with 10 codified rules, a 10-component prompt architecture, and complexity-based routing — all derived from Anthropic's documentation and real-world testing.

---

## 📋 Table of Contents

- [Before & After](#-before--after)
- [Features](#-features)
- [How It Works](#-how-it-works)
- [Quick Start](#-quick-start)
- [The 10 Optimization Rules](#-the-10-optimization-rules)
- [Prompt Framework (10 Components)](#-prompt-framework-10-components)
- [Examples](#-examples)
- [Why Claude Opus 4.6 Specific?](#-why-claude-opus-46-specific)
- [Repository Structure](#-repository-structure)
- [Contributing](#-contributing)
- [License](#-license)
- [Star This Repo](#-star-this-repo)

---

## ⚡ Before & After

<table>
<tr>
<th width="50%">❌ Raw Prompt</th>
<th width="50%">✅ Optimized Prompt</th>
</tr>
<tr>
<td>

```
Write me a Python script that analyzes
CSV files and finds anomalies
```

</td>
<td>

```xml
<role>
You are a senior data engineer specializing
in anomaly detection and statistical analysis
with Python.
</role>

<context>
I have CSV datasets from production IoT
sensors. Files range from 10K–5M rows with
columns: timestamp, sensor_id, value, status.
Some contain missing values and irregular
time intervals.
</context>

<task>
Write a Python script that:
1. Loads one or more CSV files
2. Detects statistical anomalies using
   z-score and IQR methods
3. Handles missing data gracefully
4. Outputs a summary report with flagged rows
</task>

<constraints>
- Use only pandas, numpy, scipy (no ML libs)
- Handle files up to 5M rows efficiently
- Include type hints and docstrings
- Add CLI argument parsing for file paths
</constraints>

<output_format>
Provide the complete script in a single Python
code block, followed by a usage example and
sample output showing detected anomalies.
</output_format>
```

</td>
</tr>
</table>

The optimizer analyzed the vague input, inferred the likely use case, added a domain-expert role, defined constraints for production quality, and structured everything with XML tags that Claude Opus 4.6 parses with precision.

---

## ✨ Features

- **10 Codified Optimization Rules** — systematic, reproducible prompt improvements based on Anthropic's documentation
- **10-Component Prompt Framework** — modular architecture covering role, context, task, constraints, examples, and more
- **Complexity-Based Routing** — automatically scales optimization depth (minimal → moderate → full) based on prompt complexity
- **Claude Opus 4.6 Specific** — tuned for 200K context window, adaptive thinking, literal instruction following, and no-prefill architecture
- **XML Tag Structuring** — transforms flat text into semantically tagged sections that Claude parses reliably
- **Ambiguity Resolution** — detects missing information and either infers it or prompts you for clarification
- **Domain Detection** — identifies the prompt's domain (coding, creative writing, analysis, etc.) and applies domain-specific patterns
- **Quality Guardrails** — built-in checks prevent common failure modes like over-optimization, hallucination triggers, and context overflow
- **Language Preservation** — responds in the user's language; optimized prompts stay in the original language unless you request otherwise
- **Iterative Refinement** — give feedback and the optimizer revises targeted sections without re-doing the full analysis

---

## 🔄 How It Works

```
┌─────────────────┐     ┌──────────────────────────┐     ┌─────────────────────┐
│   Your Raw      │     │   Prompt Optimizer        │     │  Optimized Prompt   │
│   Prompt        │────▶│                           │────▶│  Ready for Claude   │
│   (any format)  │     │  Analyze → Route →        │     │  Opus 4.6           │
│                 │     │  Structure → Optimize →   │     │                     │
│                 │     │  Quality Check            │     │                     │
└─────────────────┘     └──────────────────────────┘     └─────────────────────┘
```

**The 5-step workflow under the hood:**

1. **Prompt Analysis** — the optimizer detects intent, complexity level, domain, expected output type, and missing elements
2. **Complexity Routing** — simple prompts get 3–4 components; moderate ones get 5–7; complex prompts get the full 10-component framework
3. **Rule Application** — the relevant subset of 10 optimization rules fires (not all rules apply to every prompt)
4. **Quality Check** — a built-in checklist ensures the task is unambiguous, XML tags are valid, examples match the desired behavior, and no contradictory instructions exist
5. **Structured Output** — you receive the analysis, the optimized prompt in a copy-ready code block, and concise notes explaining what changed and why

---

## 🚀 Quick Start

Choose the method that fits your workflow:

### Option A: Claude Project (Recommended)

1. Open [claude.ai](https://claude.ai) and create a new **Project**
2. Paste the contents of [`CLAUDE.md`](CLAUDE.md) into the **Project Instructions** field
3. Upload [`GUIDE.md`](GUIDE.md) as a **knowledge file** in the project
4. Start a conversation — paste any raw prompt and the optimizer handles the rest

### Option B: Direct Paste

1. Copy the full contents of [`CLAUDE.md`](CLAUDE.md)
2. Paste it as the **system prompt** in any Claude interface (API Console, Workbench, etc.)
3. Send your raw prompt as the user message

### Option C: API Integration

```python
import anthropic

client = anthropic.Anthropic()

# Load the optimizer system prompt
with open("CLAUDE.md", "r") as f:
    system_prompt = f.read()

message = client.messages.create(
    model="claude-opus-4-6-20250929",
    max_tokens=8096,
    system=system_prompt,
    messages=[
        {"role": "user", "content": "Your raw prompt here"}
    ]
)

print(message.content[0].text)
```

### Meta Commands

Once running, you can type these commands in the conversation:

| Command | What It Does |
|---------|-------------|
| `help` | Explains how the optimizer works |
| `rules` | Shows a compact summary of all 10 optimization rules |
| `example` | Displays a full before/after optimization demo |
| `framework` | Shows the 10-component framework overview |
| `tips` | Gives 5 practical tips for writing better input prompts |

---

## 📏 The 10 Optimization Rules

| # | Rule | What It Does |
|---|------|-------------|
| 1 | **Be Explicit & Detailed** | Replaces vague instructions with specific, detailed ones. Claude 4.x follows instructions literally — precision pays off. |
| 2 | **Provide Context & Motivation** | Explains *why* an instruction matters, not just *what* to do. Claude performs better when it understands the purpose. |
| 3 | **Use XML Tags for Structure** | Wraps prompt sections in semantic XML tags (`<role>`, `<task>`, `<constraints>`, etc.) that Claude is trained to parse reliably. |
| 4 | **Inject Few-Shot Examples** | Adds 3–5 diverse input/output examples when the task involves classification, formatting, or ambiguous patterns. |
| 5 | **Activate Chain-of-Thought** | Adds explicit step-by-step reasoning triggers for complex tasks. Works with Opus 4.6's adaptive thinking to boost quality. |
| 6 | **Assign an Expert Role** | Gives Claude a specific persona with domain expertise, experience level, and communication style. |
| 7 | **Define Output Format Explicitly** | Prescribes the exact structure, length, and format of the response. Uses positive phrasing ("write prose paragraphs" not "don't use lists"). |
| 8 | **Optimize for Long Context** | Places long documents at the start of the prompt, tags them with indexed XML, and instructs Claude to extract before answering. |
| 9 | **Steer Tool Use & Agentic Behavior** | Clearly specifies whether Claude should *act* or *advise*, and encourages parallel tool calls for independent actions. |
| 10 | **Prevent Over-Engineering** | Adds explicit anti-overengineering clauses to keep Claude focused on what was actually requested. |

> **Not every rule fires for every prompt.** A simple factual question won't get 10 XML tags — it'll get a clean, focused refinement. The optimizer scales proportionally.

---

## 🏗️ Prompt Framework (10 Components)

The optimizer draws from 10 structural components when building the optimized prompt. Think of these as building blocks — the optimizer selects the right subset based on complexity routing.

```
┌─────────────────────────────────────────────────────┐
│                  OPTIMIZED PROMPT                    │
├─────────────────────────────────────────────────────┤
│  1. ROLE / PERSONA                                  │
│     Who should Claude be?                           │
├─────────────────────────────────────────────────────┤
│  2. TASK CONTEXT                                    │
│     Why is this task being performed?               │
├─────────────────────────────────────────────────────┤
│  3. TONE CONTEXT                                    │
│     What communication style?                       │
├─────────────────────────────────────────────────────┤
│  4. BACKGROUND DATA / DOCUMENTS                     │
│     Relevant information (XML-tagged)               │
├─────────────────────────────────────────────────────┤
│  5. DETAILED TASK DESCRIPTION                       │
│     What exactly needs to be done?                  │
├─────────────────────────────────────────────────────┤
│  6. RULES & CONSTRAINTS                             │
│     What is / isn't allowed?                        │
├─────────────────────────────────────────────────────┤
│  7. EXAMPLES (Few-Shot)                             │
│     Input/output pairs in <examples> tags           │
├─────────────────────────────────────────────────────┤
│  8. OUTPUT FORMAT                                   │
│     Structure, length, format of the response       │
├─────────────────────────────────────────────────────┤
│  9. THINKING INSTRUCTIONS                           │
│     Chain-of-Thought / Thinking Guidance            │
├─────────────────────────────────────────────────────┤
│ 10. INPUT / VARIABLE                                │
│     {{USER_INPUT}} placeholder                      │
└─────────────────────────────────────────────────────┘
```

<details>
<summary><strong>Component Details (click to expand)</strong></summary>

| # | Component | XML Tag | When Used |
|---|-----------|---------|-----------|
| 1 | Role / Persona | `<role>` | Almost always — anchors expertise and tone |
| 2 | Task Context | `<context>` | When the task needs background or motivation |
| 3 | Tone Context | _(within `<role>` or `<instructions>`)_ | When communication style matters |
| 4 | Background Data | `<documents>`, `<input>` | When user provides data, code, or documents |
| 5 | Task Description | `<task>` | Always — the core instruction |
| 6 | Rules & Constraints | `<constraints>`, `<instructions>` | When boundaries, limits, or prohibitions apply |
| 7 | Examples | `<examples><example>` | For classification, formatting, or ambiguous patterns |
| 8 | Output Format | `<output_format>` | When format isn't self-evident |
| 9 | Thinking Instructions | `<thinking>` guidance | For complex reasoning, math, multi-step logic |
| 10 | Input / Variable | `{{VARIABLE_NAME}}` | When the prompt is a reusable template |

</details>

---

## 📚 Examples

Full before/after examples for different domains are in the [`examples/`](examples/) directory:

- **[Coding Prompts](examples/coding-prompts.md)** — script generation, API design, code review
- **[Creative Writing](examples/creative-writing.md)** — fiction, blog posts, copywriting
- **[Business & Analysis](examples/business-analysis.md)** — strategy, executive summaries, data analysis

### Quick Example: Blog Article

<table>
<tr>
<th>❌ Raw</th>
<th>✅ Optimized</th>
</tr>
<tr>
<td>

```
Write a blog post about AI in healthcare
```

</td>
<td>

```xml
<role>
You are an experienced technology journalist
specializing in digital health and medical AI
applications. You write for an audience of
healthcare managers, physicians, and health-tech
investors.
</role>

<task>
Write a well-researched blog article about the
current state and future of AI in healthcare.
</task>

<instructions>
- The article should be 1,500–2,000 words
- Structure it with a compelling intro, 4–5
  content sections, and a forward-looking
  conclusion
- Include concrete real-world examples from
  diagnostics, drug development, patient care,
  and administration
- Address challenges honestly: data privacy
  (especially GDPR), liability, bias in
  training data
- Back claims with specific, verifiable facts
  and studies where possible
- Write in a professional but accessible tone
  — no marketing speak, no exaggerated promises
</instructions>

<output_format>
Continuous prose with subheadings (##). No
bullet point lists in the body text. Format
for direct CMS insertion.

Structure:
1. Title (attention-grabbing, not clickbait)
2. Introduction (hook + relevance)
3. Body (4–5 sections with subheadings)
4. Conclusion with outlook
</output_format>

<constraints>
- Do not present unsubstantiated claims or
  speculation as facts
- No marketing language or buzzword overload
- If uncertain about a fact, flag it
  transparently
</constraints>
```

</td>
</tr>
</table>

> This is the actual example from the optimizer's meta-prompt — a real transformation it produces.

---

## 🎯 Why Claude Opus 4.6 Specific?

This optimizer isn't model-agnostic. It's specifically tuned for Claude Opus 4.6's architecture and behaviors:

| Feature | How the Optimizer Uses It |
|---------|--------------------------|
| **200K Context Window** | Generates comprehensive prompts with full examples and context without worrying about token limits. Uses long-context optimization (Rule 8) to place documents correctly. |
| **Adaptive Thinking** | Strategically triggers extended thinking for complex reasoning tasks. Avoids the word "think" when extended thinking may be disabled (uses "analyze", "evaluate" instead). |
| **XML Tag Parsing** | Claude Opus 4.6 parses XML tags as semantic structure — the optimizer exploits this with consistent, well-nested tags. |
| **Literal Instruction Following** | Claude 4.x follows instructions more literally than predecessors. Examples are adopted exactly. The optimizer writes precise, unambiguous instructions. |
| **No Prefill Support** | Opus 4.6 returns a 400 error on assistant prefills. The optimizer never generates prefill patterns — it uses explicit format instructions instead. |
| **Over-Engineering Tendency** | Opus models tend to add unrequested features. Rule 10 adds explicit anti-overengineering clauses when appropriate. |
| **Positive Phrasing** | Claude 4.x responds better to "do X" than "don't do Y". The optimizer formulates all instructions positively. |
| **Action vs. Advice Distinction** | Claude 4.x distinguishes sharply between "suggest changes" and "implement changes". The optimizer makes this explicit. |

---

## 📂 Repository Structure

```
claude-prompt-optimizer/
├── README.md                          # You are here
├── CLAUDE.md                          # Core meta-prompt (the optimizer engine)
├── GUIDE.md                           # User guide: how to write input prompts
├── PROJECT_INSTRUCTIONS.md            # System behavior & configuration docs
├── CONTRIBUTING.md                    # How to contribute
├── LICENSE                            # MIT License
├── .github/
│   └── ISSUE_TEMPLATE/
│       ├── bug_report.md              # Report optimization problems
│       └── feature_request.md         # Suggest new rules or features
└── examples/
    ├── README.md                      # Example category overview
    ├── coding-prompts.md              # Before/after: coding tasks
    ├── creative-writing.md            # Before/after: creative tasks
    └── business-analysis.md           # Before/after: business tasks
```

---

## 🤝 Contributing

We welcome contributions! Whether it's a new optimization example, a rule refinement, or a bug report — see **[CONTRIBUTING.md](CONTRIBUTING.md)** for guidelines.

Key ways to contribute:
- Submit before/after optimization examples from your real-world usage
- Propose new optimization rules (with evidence from Anthropic's documentation)
- Report cases where the optimizer produces suboptimal results
- Improve or translate documentation

---

## 📄 License

This project is licensed under the **MIT License** — see [LICENSE](LICENSE) for details.

You're free to use this optimizer personally, commercially, in your own projects, or as part of a larger system.

---

## ⭐ Star This Repo

If this optimizer saves you time or improves your Claude results, please consider starring the repo — it helps others discover it and motivates continued development.

[![Star History Chart](https://api.star-history.com/svg?repos=CheswickDEV/claude-opus-4.6-prompt-optimizer&type=Date)](https://star-history.com/#CheswickDEV/claude-opus-4.6-prompt-optimizer&Date)

**[⭐ Star this repo](https://github.com/CheswickDEV/claude-opus-4.6-prompt-optimizer)** | **[🐛 Report an issue](https://github.com/CheswickDEV/claude-opus-4.6-prompt-optimizer/issues)** | **[💡 Request a feature](https://github.com/CheswickDEV/claude-opus-4.6-prompt-optimizer/issues/new?template=feature_request.md)**

---
<p align="center">
  <a href="https://cheswick.dev">
    <img src="https://img.shields.io/badge/CHESWICK.DEV-00d4ff?logo=firefox&logoColor=0a0a0f&labelColor=a855f7" alt="cheswick.dev" />
  </a>
</p>

<p align="center">
  Made with 🖤 by <a href="https://cheswick.dev">cheswick.dev </a> · Not affiliated with Anthropic
</p>
