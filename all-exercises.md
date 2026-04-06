# Workshop exercises
### *Build-along guide — The Checkout Abandonment Mystery*

---

> **The rule for every exercise:**  
> Every exercise ends with something concrete — a doc, a reusable prompt, or a before/after that makes the value obvious. If you finish early, try improving the output. If you're stuck, ask Claude why your output is weak and what's missing.

---

## Exercise 1 — Messy notes → PRD draft
**Time:** 15–20 minutes  
**What you build:** A structured first-draft PRD using Claude and the PRD template  
**Files you need:** `meeting-notes-raw.md`, `prd-template.md`

---

### The setup

Maya has 3 days to turn her chaotic meeting notes into a PRD that Priya (Eng) and Cam (Design) can actually use. Her notes are honest, messy, and full of useful signal — but they're not a PRD.

Your job: use Claude to get from notes to structured first draft. Then improve it.

---

### Step 1 — Do it the wrong way first (5 min)

Open Claude. Paste this prompt exactly:

> "Write a PRD for fixing Terracart's checkout abandonment problem."

Look at what you get. Notice what's missing. Notice what Claude had to invent. This is the baseline.

**Discussion question:** What did Claude have to guess? Where is it confidently wrong?

---

### Step 2 — Add structure and context (10 min)

Now use this prompt instead. Copy the contents of `meeting-notes-raw.md` and `prd-template.md` and paste them in:

```
You are helping a product manager named Maya draft a PRD for Terracart's checkout improvement initiative.

Use ONLY the information in the meeting notes below. Do not invent data, names, or requirements that are not in the notes. Where information is missing or unclear, mark it explicitly as [UNKNOWN — needs resolution] rather than filling it in.

Use the PRD template provided as your output structure.

Context notes:
[PASTE meeting-notes-raw.md HERE]

PRD template:
[PASTE prd-template.md HERE]

Important constraints:
- This PRD covers three workstreams: mobile form UX, error messaging, and confirmation email
- Engineering has 1–2 sprints of capacity
- Success metrics need to be discussed with the analytics team but should be directionally defined
- The tone should be clear and direct, written for an engineering and design audience, not executives
```

---

### Step 3 — Improve the output (5 min)

When Claude gives you a draft, pick the weakest section and follow up:

> "The requirements section for the mobile form workstream is too vague. Rewrite it with specific, testable acceptance criteria based on the session recording findings in the notes. Format as a numbered checklist."

**Key lesson:** The first output is a draft, not a deliverable. Your job as PM is to know what good looks like — and direct Claude toward it.

---

### Reflection questions
- What did Claude do well that surprised you?
- What did it get wrong or make up?
- What would have been different if you hadn't given it the template?
- How would you improve the prompt for next time?

---

---

## Exercise 2 — Interview transcript → evidence-backed insight memo
**Time:** 15 minutes  
**What you build:** A structured insight memo with themes, evidence, and recommended actions  
**Files you need:** `customer-interview-transcript.md`, `support-tickets-sample.md`

---

### The setup

Maya has five interview transcripts and 20 support tickets. She needs to synthesize them into something she can share with the team — and defend. Not vibes, not summaries. Evidence-backed themes.

---

### The prompt

```
You are a product manager synthesizing qualitative research for the Terracart checkout initiative.

Your job is to extract structured insights from the customer interview transcripts and support ticket sample below.

Output format:
1. Top 3 themes (one clear headline per theme, 1–2 sentence description)
2. Evidence table — for each theme, provide 2–3 direct quotes or ticket excerpts as supporting evidence, with the source labeled (Interview 1, Ticket #TRR-XXXX, etc.)
3. Severity/frequency assessment — for each theme, rate: How many customers does this affect? How severe is the experience failure? (Use H/M/L)
4. Recommended product actions — for each theme, one specific, actionable recommendation

Rules:
- Do not invent or paraphrase quotes. Use exact language from the sources.
- Do not include themes unless you have at least 2 pieces of evidence to support them.
- Be direct. This is an internal document for a cross-functional team, not a marketing summary.

Interview transcripts:
[PASTE customer-interview-transcript.md HERE]

Support ticket sample:
[PASTE support-tickets-sample.md HERE]
```

---

### The follow-up

When you have the output, follow up with:

> "Now write a 2-sentence executive summary that could go at the top of this memo — summarizing the most important finding and its business impact."

**Key lesson:** AI is excellent at synthesis from source material. It is bad at making things up when given clear sourcing rules. The rules in the prompt ("do not invent quotes") are what make this trustworthy, not magic.

---

### Reflection questions
- Did Claude honor the sourcing rules? Check a few quotes — are they real?
- Is there a theme you would have surfaced that Claude missed?
- How is this different from just asking "summarize these interviews"?

---

---

## Exercise 3 — One source → three audiences
**Time:** 10–12 minutes  
**What you build:** An exec brief, an engineering handoff note, and a Slack update — all from one source document

---

### The setup

Maya has her insight memo from Exercise 2. Now she has to say the same thing three different ways:

- **Friday leadership review** — VP and CEO, 5 minutes of attention, they care about money and timeline
- **Engineering kick-off** — Priya's team, they need scope, ambiguity, and open questions
- **Team Slack** — The broader product team, casual update, no jargon, keep it moving

---

### Part A — Exec brief

```
You are a product manager preparing a 5-bullet executive summary for a Friday leadership review at Terracart.

The audience: VP of Product and CEO. They care about: revenue impact, timeline, and risk. They do not want to read a PRD. They have 3 minutes.

Source: [PASTE your insight memo from Exercise 2 OR paste the discovery narrative from 01-discovery-narrative/discovery-story.md]

Format: 5 bullets maximum. Start with the business impact. End with the ask (what you need from them). Bullets should be complete sentences but punchy — no longer than 20 words each. No jargon.
```

---

### Part B — Engineering handoff note

```
Now rewrite the same information as an engineering kick-off note for the lead engineer, Priya.

Priya's priorities: scope clarity, open questions she needs answered before work can start, and known technical risks.

Format:
- 2-sentence context (what and why)
- Workstream breakdown (3 workstreams, 2–3 bullets each on what needs to be built)
- Open questions that need engineering input before scoping
- Known technical risks or dependencies
- What you need from Priya by Monday

Tone: direct, collegial, assumes technical competence. No marketing language.
```

---

### Part C — Slack update

```
Now write a Slack message to the broader product team channel announcing this initiative.

Audience: Designers, PMs, analysts — smart people who are busy and will spend 30 seconds on this.

Requirements:
- 3–5 sentences max
- No bullet points (this is Slack, not a memo)
- Should communicate: what problem we're solving, why it matters, and what's next
- Tone: confident and clear, not formal. Like a human wrote it.
- Do NOT start with "Hey team!" or "Exciting news!"
```

---

### Reflection questions
- How did the same facts land differently in each format?
- Which version was hardest for Claude to get right? Why?
- What would you have changed about each output?
- Notice how the quality of your Exercise 2 output affected Exercise 3 — this is the "source of truth" effect.

---

---

## Exercise 4 — Build your context folder
**Time:** 15 minutes  
**What you build:** A reusable context system you can take back to your actual job

---

### The concept

The exercises you've done today worked because you gave Claude context — templates, transcripts, constraints. But you had to paste all of that in manually every time.

What if it was already organized and ready to go?

A context folder is a lightweight system that lives alongside your product work and makes every AI interaction faster, more consistent, and less dependent on a perfect prompt. It's not a magic trick. It's just good filing.

---

### Step 1 — Build the folder structure (5 min)

Create this structure (on your computer, in Notion, wherever you keep work):

```
/[product-name]-context/
├── CONTEXT.md          ← The master brief (who we are, what we're building, who our users are)
├── /research/
│   ├── interview-transcripts/
│   ├── support-data/
│   └── competitive-notes/
├── /specs/
│   ├── active-prd/
│   └── approved-prd/
├── /decisions/
│   └── decision-log.md  ← Why did we make key choices?
└── /stakeholders/
    └── audience-guide.md ← How to talk to each stakeholder
```

---

### Step 2 — Write your CONTEXT.md (10 min)

This is the most important file. Use this prompt to build it:

```
I am a product manager working on [your product or a product you know well]. Help me write a CONTEXT.md file that I can paste into any AI conversation to give instant, useful context.

The file should include:
1. Product overview (2–3 sentences: what it is, who it's for, what problem it solves)
2. Current focus / active initiative (what the team is working on right now)
3. Key users (2–3 user segments with a one-line description of each)
4. Team structure (PM, design, eng leads — names and roles)
5. How we write (tone, vocabulary, and style preferences for product docs)
6. Known constraints (e.g., "engineering is at 80% capacity," "we can't change the payment processor this quarter")
7. Things to avoid saying (jargon we've agreed not to use, terms that mean different things internally vs. externally)

Use this information about my product:
[DESCRIBE YOUR PRODUCT — or use Terracart as a stand-in]
```

---

### Step 3 — Test the difference (if time allows)

Ask Claude the same question twice — once without CONTEXT.md, once with it pasted in. Compare the outputs.

**Prompt to test:**
> "Draft a short Slack message announcing that we're pausing feature X for one sprint to address a reliability issue."

**Key lesson:** The context folder doesn't make Claude smarter. It makes every conversation start from a better place. It's not about prompt engineering — it's about information architecture.

---

### Take this home

The context folder you built today works for your real job. File your next interview transcript in `/research/`. Log your next key decision in `/decisions/decision-log.md`. Paste your `CONTEXT.md` into your next Claude conversation and watch the output quality difference.

---

---

## Exercise 5 — PRD reviewer workflow
**Time:** 10–12 minutes  
**What you build:** A reusable review prompt that critiques PRDs from different stakeholder lenses

---

### The setup

Maya's PRD draft (see `weak-prd-draft.md`) is... not great. She knows it. But she's too close to it to see all the gaps. She needs cross-functional review — and she needs it before the Thursday deadline, not after.

Claude can simulate cross-functional review. It's not the same as real feedback. But it catches the obvious gaps before you put the doc in front of real people.

---

### Part A — The basic critique

```
Review this PRD as a senior engineering lead preparing to scope the work.

Your job: identify every ambiguity, missing constraint, or unclear requirement that would block you from writing a technical spec. Be specific. Quote the relevant section. Rate each issue as a blocker (cannot start work) or a clarifying question (can start but need resolution before completion).

PRD to review:
[PASTE weak-prd-draft.md HERE]
```

---

### Part B — The persona critique

Now run three more reviews in one prompt:

```
Review the same PRD from three different perspectives. For each perspective, identify the top 2–3 problems with the document from their point of view.

Perspective 1 — VP of Product
What this person cares about: business impact, timeline, risk, and whether the team is solving the right problem.

Perspective 2 — Customer support lead
What this person cares about: whether the fix will reduce inbound support volume, whether there's a customer communication plan, and whether edge cases have been thought through.

Perspective 3 — A skeptical engineer
What this person cares about: specificity of requirements, absence of technical assumptions, and whether the success metrics are actually measurable.

PRD:
[PASTE weak-prd-draft.md HERE]
```

---

### Part C — Build the reusable prompt

Now do the meta-exercise: turn this into a reusable workflow you can run on any PRD.

```
Based on the review you just did, write me a reusable PRD review checklist that I can use on any product document. 

Format it as a checklist with three sections:
1. Completeness check (is everything that should be there, there?)
2. Clarity check (are the requirements specific and testable?)
3. Stakeholder alignment check (has this been written in a way that each key audience can act on it?)

Each section should have 5–7 specific checklist items. Make them actionable, not vague.
```

Save this checklist. It's yours now.

---

### Reflection questions
- Did the persona reviews surface anything the basic critique missed?
- What did the "skeptical engineer" perspective find that you hadn't noticed?
- How would you use this workflow in your real job? What would you change?

---

---

## The meta-lesson

Every exercise followed the same pattern:

**Messy input → structured context → draft artifact → review loop → audience-specific output**

That pattern is not a Claude trick. It's how good PM writing works. Claude just makes it faster — when you give it the right system to work within.

The PMs who get the most out of AI are not the ones with the cleverest prompts. They're the ones who have invested in their context, their templates, and their standards. The model does the drafting. The PM does the thinking.

---

*Workshop materials version 1.0 — fork and remix freely*
