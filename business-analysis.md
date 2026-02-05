# 📊 Business & Analysis Prompt Optimizations

Three before/after examples demonstrating how the optimizer transforms raw business and analysis prompts.

---

## Example 1: Migration Strategy

### ❌ Raw Prompt

```
Create a migration plan from Exchange to Microsoft 365
```

### ✅ Optimized Prompt

```xml
<role>
You are a senior IT infrastructure consultant with extensive experience in Microsoft 365 migrations for mid-sized European companies. You understand the technical, organizational, and regulatory dimensions of cloud transitions.
</role>

<context>
We are a mid-sized company with 200 employees across 3 locations in Germany. We currently run Exchange Server 2016 on-premise. Budget for the migration is approximately €50,000. The IT team consists of 4 people. We have a works council — change management processes are required. All planning must account for GDPR/data privacy requirements.
</context>

<task>
Create a comprehensive migration strategy document for transitioning from our on-premise Exchange Server 2016 to Microsoft 365.
</task>

<instructions>
The document should cover:

1. **Phase Plan** — Break the migration into clear phases (assessment, pilot, staged rollout, decommission). For each phase, specify duration, key activities, responsible parties, and dependencies.

2. **Risk Assessment** — Identify the top 10 risks (technical, organizational, regulatory) with likelihood, impact, and mitigation strategies. Pay special attention to data loss, downtime, and GDPR compliance.

3. **Cost Breakdown** — Estimate costs for licensing (M365 plans for 200 users), migration tooling, external consulting (if needed), training, and contingency. Compare against the €50,000 budget and flag if it's insufficient.

4. **Technical Migration Approach** — Recommend a migration method (cutover, staged, hybrid) with rationale. Address mailbox migration, public folders, shared mailboxes, distribution lists, and DNS/MX record changes.

5. **Change Management** — Outline a communication and training plan for employees. Address works council involvement requirements. Include a timeline for user notifications.

6. **Checklist** — A pre-migration checklist, a go-live checklist, and a post-migration verification checklist.
</instructions>

<output_format>
Structure as a professional document with:
- Executive summary (5–7 sentences at the top)
- Numbered sections matching the 6 areas above
- Tables for the phase plan, risk matrix, and cost breakdown
- The checklists as actionable checkbox lists
- Total length: 2,000–3,000 words
</output_format>

<constraints>
- All recommendations must be specific to Exchange 2016 → Microsoft 365 (not generic cloud migration advice)
- Cost estimates must use realistic 2024/2025 pricing for the German/EU market
- GDPR requirements are non-negotiable — flag any step that has data privacy implications
- If the €50,000 budget is likely insufficient, state this clearly with a revised estimate
- Do not recommend third-party tools without explaining why native Microsoft tools are insufficient
</constraints>
```

### 💡 What Changed

The one-line prompt gave no context about the company, existing infrastructure, budget, or regulatory environment. The optimizer added a detailed context block that enables Claude to make specific (rather than generic) recommendations. The task was decomposed into 6 clear deliverables, each with explicit requirements. The constraints ensure the output is grounded in reality — realistic pricing, GDPR compliance, and honest budget assessment. This is a complex prompt (🔴) that gets the near-full 10-component treatment.

---

## Example 2: Quarterly Sales Analysis

### ❌ Raw Prompt

```
Analyze our Q3 sales numbers
```

### ✅ Optimized Prompt

```xml
<role>
You are a senior business analyst with expertise in SaaS revenue modeling, cohort analysis, and sales team performance evaluation. You communicate findings clearly to C-level stakeholders.
</role>

<context>
Company profile: B2B SaaS, Series B, ARR $12M. Q3 showed 8% QoQ revenue growth (down from 15% in Q2). Sales team expanded from 12 to 18 reps during Q3. Primary market: mid-market enterprise (100–1,000 employees). Average deal size: $24K ACV. Sales cycle: 45–60 days. Churn rate in Q3: 4.2% (up from 3.1% in Q2).
</context>

<task>
Analyze the Q3 sales performance based on the data provided and deliver an executive-ready assessment with actionable recommendations.
</task>

<instructions>
Your analysis should cover:

1. **Growth Deceleration Diagnosis** — What are the most likely root causes for the drop from 15% to 8% QoQ growth? Consider: ramp time for new reps, market conditions, deal size changes, pipeline quality, and the increased churn.

2. **Sales Team Expansion ROI** — Evaluate whether the expansion from 12 to 18 reps is paying off. Calculate implied per-rep productivity for old vs. new reps. Estimate ramp time and when the new reps should reach full productivity.

3. **Churn Impact** — Quantify the revenue impact of the churn increase (3.1% → 4.2%). Discuss whether this is a leading indicator of a deeper retention problem.

4. **Three Actionable Recommendations for Q4** — Each recommendation must include: what to do, expected impact (quantified where possible), and implementation timeline.
</instructions>

<output_format>
Structure as:

## Executive Summary
3–4 sentences: the headline finding and the single most important recommendation.

## Detailed Analysis
Separate sections for each of the 4 areas above. Use prose paragraphs with supporting calculations inline. Include a summary table of key metrics where helpful.

## Recommendations
Numbered list with sub-sections: Action, Expected Impact, Timeline.

Total length: 800–1,200 words.
</output_format>

<constraints>
- Base all analysis on the provided data — clearly flag where you are making assumptions
- Quantify impact wherever possible (dollar amounts, percentages, timelines)
- Do not sugarcoat findings — if the numbers suggest a problem, state it directly
- Keep the tone professional and fact-based, suitable for a board meeting context
</constraints>
```

### 💡 What Changed

"Analyze our Q3 sales numbers" is impossible to act on without data. The optimizer added a realistic context block with specific metrics (ARR, growth rates, team size, churn, deal size) that enable Claude to perform actual analysis rather than produce generic frameworks. The task was decomposed into 4 specific analysis areas. The constraints enforce intellectual honesty (flag assumptions, don't sugarcoat) and quantification. The output format ensures the result is board-ready, not an academic essay.

---

## Example 3: Competitive Landscape Brief

### ❌ Raw Prompt

```
Compare the top project management tools
```

### ✅ Optimized Prompt

```xml
<role>
You are a technology analyst writing for a VP of Engineering who needs to select a project management tool for a 50-person software development team. You prioritize practical evaluation over marketing claims.
</role>

<context>
Our team: 50 engineers across 6 squads, working in 2-week sprints. Current tools: Jira (pain point: too complex, low adoption), Slack (primary communication), GitHub (code). Budget: up to $25/user/month. Key requirements: sprint planning, backlog management, roadmap visualization, GitHub integration, and lightweight enough that engineers actually use it daily.
</context>

<task>
Create a structured competitive comparison of the 5 most relevant project management tools for our use case. Evaluate each against our specific requirements and deliver a clear recommendation.
</task>

<instructions>
1. **Select the 5 most relevant tools** based on our context. Briefly justify why these 5 were chosen over others (e.g., why not Basecamp, why not Monday.com).

2. **Comparison Matrix** — Evaluate each tool across these dimensions:
   - Sprint planning & backlog management capability
   - GitHub integration depth (not just "it integrates" — specify what data flows and how)
   - Learning curve / ease of adoption
   - Pricing for 50 users
   - Roadmap / high-level planning features
   - Customizability vs. opinionation

3. **Strengths & Weaknesses** — For each tool, 2–3 sentences on its primary strength and its biggest weakness for our specific use case.

4. **Recommendation** — Your top pick with reasoning, and a runner-up if the top pick doesn't work out. Address the migration path from Jira.
</instructions>

<output_format>
Structure as:

## Tool Selection Rationale
Brief paragraph on methodology.

## Comparison Matrix
A Markdown table with tools as rows and evaluation dimensions as columns. Use a rating scale: ⭐⭐⭐ (excellent), ⭐⭐ (adequate), ⭐ (weak).

## Individual Assessments
One subsection per tool: strength, weakness, pricing detail.

## Recommendation
Top pick + runner-up with reasoning. Migration considerations from Jira.

Total length: 1,000–1,500 words.
</output_format>

<constraints>
- Evaluate based on current 2024/2025 capabilities — not historical reputation
- Pricing must be specific and accurate for the 50-user tier
- Do not rely on marketing copy — assess practical capability. If a feature exists but is poorly implemented, say so.
- If you are uncertain about a specific feature or pricing detail, state this explicitly rather than guessing
- The recommendation must be defensible to a VP — "it feels better" is not sufficient reasoning
</constraints>
```

### 💡 What Changed

The generic "compare project management tools" would produce a surface-level overview useful to no one in particular. The optimizer added a specific decision context (team size, current tools, pain points, budget, requirements) that transforms this from a generic comparison into a decision-support document. The task specifies exactly what "compare" means: a structured matrix, individual assessments, and a defensible recommendation. The constraints enforce intellectual honesty — flag uncertainty rather than guessing, evaluate actual capability rather than marketing, and provide reasoning that would survive scrutiny from a VP.
