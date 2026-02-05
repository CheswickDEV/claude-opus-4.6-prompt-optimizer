# Guide: How to Write Your Prompt for the Optimizer

## The Most Important Thing First

You **don't need a fixed format**. The optimizer is built to work with raw text. But the more context you provide, the more precise the result will be.

---

## Minimal Version (Always Works)

Just write what you want:

```
Write me a Python script that merges CSV files
```

The optimizer automatically detects intent, domain, and complexity, and fills in everything that's missing.

---

## Better Version: The 4-Sentence Method

If you want better results, answer these questions in 2–4 sentences:

### 1. WHAT should Claude do?
→ The actual task

### 2. FOR WHOM / WHY?
→ Target audience or use case

### 3. HOW should the result look?
→ Format, length, style, language

### 4. WHAT SHOULD BE AVOIDED? (optional)
→ Things you explicitly don't want

**Example:**

```
Write a blog article about AI in recruiting.
Target audience is HR managers at mid-sized companies.
The article should be roughly 1,500 words, practical with concrete tool recommendations.
No marketing speak, no exaggerated promises.
```

---

## Pro Version: Context Block

For complex tasks, you can provide additional context in a structured way. You don't need to use XML tags — the optimizer adds those automatically. Just write naturally:

```
Task: Create a migration strategy from our on-premise Exchange Server to Microsoft 365.

Context: We are a mid-sized company with 200 employees, 
3 locations in Germany, and currently use Exchange 2016. 
Budget is approximately €50,000. IT team consists of 4 people.

Result should be: A structured document with a phase plan, 
risk assessment, cost breakdown, and checklist.

Important: Data privacy/GDPR must be considered. 
We have a works council — change management is relevant.
```

---

## Special Cases

### Coding Prompts
Specify the programming language, use case, and desired quality characteristics:

```
Python function that merges PDFs. 
Should handle large files (500+ pages), 
include error handling, and be usable as a CLI tool.
```

### Creative Prompts
Describe tone, mood, target audience, and length:

```
Write a short story in a sci-fi noir style. 
Protagonist is an AI forensics investigator in Neo-Berlin 2087. 
Approximately 3,000 words, dark tone, plot twist at the end.
```

### Analysis Prompts
Describe the data source, the question, and the desired result:

```
Analyze the attached quarterly figures and identify 
the 3 biggest cost drivers. Result as an executive summary 
for the C-suite, max. 1 page.
```

### System Prompt Optimization
If you want to optimize a system prompt for your own project, say so explicitly:

```
Optimize the following system prompt for my customer support project:
[your system prompt here]
The project should classify support tickets and generate response suggestions.
```

---

## What You DON'T Need to Do

- ❌ Don't write XML tags — the optimizer adds them
- ❌ Don't define roles — the optimizer selects the right one
- ❌ Don't know prompt engineering techniques — that's exactly what this tool is for
- ❌ Don't write perfectly polished text — bullet points and rough notes work fine

---

## What Happens After Optimization?

1. You receive the optimized prompt in a code block → copy it with one click
2. Paste it into a new Claude conversation (or into your project / API call)
3. If something doesn't fit → tell the optimizer, and it revises targeted sections

**Tip:** You can also say "make the prompt shorter", "add examples", or "change the role to X" — the optimizer responds to iterative feedback.
