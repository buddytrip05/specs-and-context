# Prompt library
### *Workshop copy-paste prompts — The Checkout Abandonment Mystery*

All prompts in this file are designed to work with the Terracart case study. Adapt the bracketed sections for your real product.

---

## Prompt patterns (the theory)

Before the specific prompts — here's the mental model behind all of them:

| Pattern | What it does |
|---------|-------------|
| **Template anchoring** | Give Claude your actual output template so it fills in your structure, not its own |
| **Source grounding** | Tell Claude to use only the source material provided — no invention |
| **Unknown flagging** | Instruct Claude to mark gaps explicitly rather than fill them with plausible-sounding fiction |
| **Audience scoping** | Name the audience, their concerns, and the format explicitly |
| **Persona critique** | Ask Claude to evaluate from a specific stakeholder's point of view |
| **Constraint definition** | Tell Claude what it cannot do (scope, length, style) — not just what it should do |

---

## Exercise 1 prompts — Notes → PRD

### The bad prompt (intentional baseline)
```
Write a PRD for fixing Terracart's checkout abandonment problem.
```
*Use this first. See what Claude invents. Then run the good version.*

---

### The structured prompt
```
You are helping a product manager named Maya draft a PRD for Terracart's checkout improvement initiative.

Use ONLY the information in the meeting notes below. Do not invent data, names, or requirements that are not in the notes. Where information is missing or unclear, mark it explicitly as [UNKNOWN — needs resolution] rather than filling it in.

Use the PRD template provided as your output structure.

Context notes:
[PASTE meeting-notes-raw.md]

PRD template:
[PASTE prd-template.md]

Important constraints:
- This PRD covers three workstreams: mobile form UX, error messaging, and confirmation email
- Engineering has 1–2 sprints of capacity
- Success metrics need to be discussed with the analytics team but should be directionally defined
- Tone: clear and direct, written for an engineering and design audience, not executives
```

---

### The sharpening follow-up
```
The requirements section for [workstream] is too vague. Rewrite it with specific, testable acceptance criteria based only on the evidence in the meeting notes. Format as a numbered checklist. Each item should be a complete, binary statement that a QA engineer could test.
```

---

## Exercise 2 prompts — Transcript → insight memo

### The structured synthesis prompt
```
You are a product manager synthesizing qualitative research for the Terracart checkout initiative.

Your job is to extract structured insights from the customer interview transcripts and support ticket sample below.

Output format:
1. Top 3 themes (one clear headline per theme, 1–2 sentence description)
2. Evidence table — for each theme, provide 2–3 direct quotes or ticket excerpts as supporting evidence, with the source labeled (Interview 1, Ticket #TRR-XXXX, etc.)
3. Severity/frequency assessment — rate each theme: How many customers does this affect? How severe is the experience failure? (Use H/M/L)
4. Recommended product actions — for each theme, one specific, actionable recommendation

Rules:
- Do not invent or paraphrase quotes. Use exact language from the sources.
- Do not include themes unless you have at least 2 pieces of evidence.
- Be direct. This is an internal document for a cross-functional team, not a marketing summary.

Interview transcripts:
[PASTE customer-interview-transcript.md]

Support ticket sample:
[PASTE support-tickets-sample.md]
```

---

### The exec summary add-on
```
Now write a 2-sentence executive summary for the top of this memo. It should state the most important finding and its quantified business impact. Write it for a VP who has 30 seconds.
```

---

## Exercise 3 prompts — One source → three audiences

### Exec brief
```
You are a product manager preparing a 5-bullet executive summary for a Friday leadership review at Terracart.

The audience: VP of Product and CEO. They care about: revenue impact, timeline, and risk. They do not want to read a PRD. They have 3 minutes.

Source:
[PASTE your insight memo OR the discovery narrative]

Format: 5 bullets maximum. Start with the business impact. End with the ask (what you need from them). Bullets should be complete sentences, no longer than 20 words each. No jargon.
```

---

### Engineering handoff note
```
Rewrite the same information as an engineering kick-off note for lead engineer Priya.

Priya's priorities: scope clarity, open questions she needs answered before work can start, and known technical risks.

Format:
- 2-sentence context (what and why)
- Workstream breakdown (3 workstreams, 2–3 bullets each)
- Open questions that need engineering input before scoping
- Known technical risks or dependencies
- What you need from Priya by Monday

Tone: direct, collegial, assumes technical competence. No marketing language.

Source:
[PASTE your insight memo OR the discovery narrative]
```

---

### Slack update
```
Write a Slack message to the broader product team channel announcing this initiative.

Audience: Designers, PMs, analysts — smart people who are busy and will skim this in 30 seconds.

Requirements:
- 3–5 sentences max
- No bullet points
- Communicate: what problem we're solving, why it matters, and what's next
- Tone: confident and clear, not formal
- Do NOT start with "Hey team!" or "Exciting news!"

Source:
[PASTE your insight memo OR the discovery narrative]
```

---

## Exercise 5 prompts — PRD reviewer

### Engineering lens
```
Review this PRD as a senior engineering lead preparing to scope the work.

Identify every ambiguity, missing constraint, or unclear requirement that would block you from writing a technical spec. Be specific — quote the relevant section. Rate each issue as a BLOCKER (cannot start work) or CLARIFYING QUESTION (can start but need resolution before completion).

PRD:
[PASTE weak-prd-draft.md]
```

---

### Three-persona critique
```
Review this PRD from three different perspectives. For each, identify the top 2–3 problems with the document from their point of view.

Perspective 1 — VP of Product
Cares about: business impact, timeline, risk, whether we're solving the right problem.

Perspective 2 — Customer support lead
Cares about: whether the fix will reduce support volume, whether there's a customer communication plan, whether edge cases are addressed.

Perspective 3 — Skeptical engineer
Cares about: specificity of requirements, absence of technical assumptions, whether success metrics are measurable.

PRD:
[PASTE weak-prd-draft.md]
```

---

### Reusable review checklist builder
```
Based on the PRD critique you just completed, write a reusable PRD review checklist for any product document.

Three sections:
1. Completeness check — is everything that should be there, there?
2. Clarity check — are requirements specific and testable?
3. Stakeholder alignment check — can each key audience act on this?

Each section: 5–7 specific checklist items. Actionable, not vague.
```

---

## Bonus prompts — Take these home

### The context-boost test
Run this prompt twice — once without your CONTEXT.md, once with it pasted in. Compare the outputs.

```
Draft a short Slack message (3 sentences max) announcing that we're pausing [feature name] for one sprint to address a reliability issue. Tone should be honest but not alarming.
```

---

### The decision log entry
Use this to document any product decision so future-you and future-Claude can understand the reasoning.

```
Help me write a decision log entry for the following product decision:

Decision made: [what you decided]
Options considered: [what else you looked at]
Key factors: [what drove the decision]
Who was involved: [stakeholders in the decision]
Reversibility: [easy / hard / irreversible]
Date: [date]

Format it as a brief, structured log entry that someone joining the team in 6 months could read and understand.
```

---

### The pre-mortem
Run this on any feature before you ship it.

```
We are about to ship the following feature: [describe the feature].

Run a pre-mortem. Assume it's 3 months from now and the feature failed badly. 

Generate:
1. The three most likely failure modes (be specific — not generic)
2. For each, what early warning sign would have told us it was going wrong?
3. For each, what could we have done differently before shipping?

Be direct and honest. The purpose of this exercise is to surface uncomfortable scenarios before they happen.
```

---

### The stakeholder-ready summary
When you have a long document and need a quick version for someone specific.

```
Summarize the following document for [role/name]. 

They care most about: [2–3 things].
They have: [X minutes] of attention.
Format: [bullets / prose / table].
Do NOT include: [anything they won't care about].

Document:
[PASTE document]
```

---

*Prompt library version 1.0 — all prompts are starting points, not scripts. Modify everything.*
