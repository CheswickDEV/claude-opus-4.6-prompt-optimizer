# ✍️ Creative Writing Prompt Optimizations

Three before/after examples demonstrating how the optimizer transforms raw creative writing prompts.

---

## Example 1: Short Fiction

### ❌ Raw Prompt

```
Write a short story about AI
```

### ✅ Optimized Prompt

```xml
<role>
You are a literary fiction writer known for character-driven narratives that explore the human side of technology. Your influences include Ted Chiang and Kazuo Ishiguro. You favor quiet tension over spectacle.
</role>

<task>
Write a short story (1,500–2,000 words) that explores the relationship between a hospice nurse and an AI system designed to predict patients' remaining time. Focus on a single pivotal scene where the AI's prediction conflicts with the nurse's intuition about a patient she has grown close to.
</task>

<instructions>
- First-person POV from the nurse's perspective
- Literary fiction tone — no techno-thriller or dystopian tropes
- Show, don't tell — convey emotion through action, dialogue, and sensory detail
- The story must have a complete arc: setup, rising tension, climactic moment, resolution
- The AI should feel present but not anthropomorphized — it's a tool, not a character
- End on an ambiguous note that lets the reader decide who was right
</instructions>

<output_format>
The story as continuous prose. Use "---" to mark scene breaks if needed. Include a title at the top.

Do not include an author's note, synopsis, or commentary after the story.
</output_format>

<constraints>
- Stay within 1,500–2,000 words
- No clichés: no "red blinking lights", no "the AI became sentient", no "what does it mean to be human" monologues
- The medical setting must feel authentic — use specific, realistic details about hospice care
</constraints>
```

### 💡 What Changed

The five-word prompt "Write a short story about AI" gives Claude almost nothing to work with. The optimizer created a specific premise (hospice nurse vs. prediction AI), defined the literary approach (character-driven, Ted Chiang influence, quiet tension), specified POV and tone, and added negative constraints to steer away from common AI-fiction clichés. The output format ensures Claude delivers the story itself without meta-commentary. This transforms a prompt that would produce generic AI fiction into one that produces a specific, publishable-quality piece.

---

## Example 2: Blog Post

### ❌ Raw Prompt

```
Write a blog post about remote work productivity tips
```

### ✅ Optimized Prompt

```xml
<role>
You are a productivity writer and former remote team lead who has managed distributed teams across 4 time zones for 6 years. You write for experienced remote workers — not beginners. Your tone is direct, evidence-aware, and free of hustle culture clichés.
</role>

<task>
Write a blog post about advanced productivity strategies for experienced remote workers who have already mastered the basics (dedicated workspace, routine, video calls) and are looking for the next level.
</task>

<instructions>
- Length: 1,200–1,500 words
- Structure: Hook opening (a counterintuitive observation), 5 strategies as the core, brief conclusion
- Each strategy must be:
  - Specific and actionable (not "take breaks" — instead, describe a concrete technique)
  - Backed by reasoning or a real-world scenario (not necessarily academic studies, but grounded in logic)
  - Something the reader likely hasn't heard before, or a fresh angle on a known concept
- Write with personality — use "you" directly, include brief anecdotes or scenarios
- Avoid: listicle energy (even though it has a list structure, the writing should flow as an essay with numbered sections)
</instructions>

<output_format>
Markdown format with:
- An engaging H1 title (not "X Tips for Y" — something that creates curiosity)
- A 1–2 sentence subtitle / deck
- H2 headings for each strategy
- Continuous prose paragraphs within each section (no sub-bullets)
- A brief closing paragraph that ties the strategies together
</output_format>

<constraints>
- No generic advice that appears in every remote work article (dedicated workspace, morning routine, Pomodoro technique)
- No promotion of specific tools by name — keep it tool-agnostic
- No hustle culture framing ("grind harder", "10x your output")
- Target audience is people who have been remote for 2+ years
</constraints>
```

### 💡 What Changed

The generic "blog post about remote work tips" would produce the same article as every other AI-generated piece on the topic. The optimizer elevated this by defining an expert persona who speaks to experienced remote workers (not beginners), requiring counterintuitive strategies rather than basics, specifying a writing style that avoids listicle energy, and constraining away the clichés that make AI-generated content feel generic. The output format specifies Markdown structure while keeping the essay feel.

---

## Example 3: Marketing Copy

### ❌ Raw Prompt

```
Write product descriptions for our new headphones
```

### ✅ Optimized Prompt

```xml
<role>
You are a senior copywriter at a consumer electronics brand. You write product descriptions that balance technical accuracy with emotional appeal. Your style is clean, confident, and avoids superlatives.
</role>

<context>
Product: NovaPods Pro — wireless over-ear headphones
Price point: $349 (premium segment, competing with Sony WH-1000XM5 and Apple AirPods Max)
Key specs: 40mm custom drivers, Adaptive ANC, 38-hour battery, Bluetooth 5.3, spatial audio, USB-C, 254g weight
Target buyer: Audiophile-adjacent professionals aged 28–45 who commute, travel, and work in open offices. They care about sound quality and comfort but aren't hardcore audiophiles.
</context>

<task>
Write three distinct product descriptions for the NovaPods Pro, each for a different placement:
</task>

<instructions>
1. **Hero Description** (for the product page above the fold)
   - 2–3 sentences maximum
   - Lead with the emotional benefit, not the specs
   - Create desire without making unverifiable claims

2. **Feature Breakdown** (for the product page detail section)
   - 5 feature blocks, each with a short headline + 2–3 sentence description
   - Translate specs into benefits (e.g., "38 hours of battery" → what that means for the user's life)
   - Mention specific use scenarios

3. **Comparison Blurb** (for a "Why NovaPods Pro?" section)
   - 100–150 words
   - Positioned against the competition without naming competitors directly
   - Focus on differentiators: weight, battery life, and adaptive ANC quality
</instructions>

<output_format>
Present each description under a clear heading:

## Hero Description
[text]

## Feature Breakdown
[5 blocks]

## Comparison Blurb
[text]
</output_format>

<constraints>
- No superlatives without qualification ("best" is only acceptable if scoped, e.g., "best-in-class battery life in the over-ear category")
- No made-up review quotes or fake endorsements
- Do not use: "immersive experience", "game-changer", "next-level", "revolutionary"
- Specs must match the provided data exactly — do not invent additional features
</constraints>
```

### 💡 What Changed

The raw prompt provides zero context about the product. The optimizer added a complete context block with product name, pricing, specs, competitive landscape, and target buyer persona. The task was decomposed into three distinct deliverables, each with specific requirements for length, tone, and purpose. The constraints prevent the most common pitfalls of AI-generated marketing copy: unearned superlatives, buzzword overload, and invented features. This gives Claude everything it needs to produce genuinely usable copy rather than generic filler.
