# Facilitator guide
### *The Checkout Abandonment Mystery — AI PM Workshop*

**Format:** Hands-on build-along  
**Length:** 90 minutes  
**Audience:** Working PMs — associate through senior  
**Vibe:** Product seminar, not lecture. Quirky professor energy. You're building in public.

---

## The throughline to say out loud at the start

> "Here's the only thing I want you to remember from today: output quality improves when PMs improve the *system* around the model — not just the prompt. We're going to prove that claim five times in the next 90 minutes."

Say this. Write it on the board. Come back to it.

---

## Run of show

| Time | Section | What's happening |
|------|---------|-----------------|
| 0:00–0:10 | Opening + scene-setting | Tell the Terracart story. Make it feel real. |
| 0:10–0:15 | Setup | Orient people to the repo and file structure |
| 0:15–0:35 | Exercise 1 | Notes → PRD (show the bad version first) |
| 0:35–0:50 | Exercise 2 | Transcript → insight memo |
| 0:50–1:00 | Exercise 3 | One source → three audiences |
| 1:00–1:15 | Exercise 4 | Build your context folder |
| 1:15–1:25 | Exercise 5 | PRD reviewer workflow |
| 1:25–1:30 | Close | The meta-lesson + what to do Monday |

---

## Opening (0:00–0:10)

**Don't start with a slide about AI.** Start with the story.

Tell it like a detective story:

> "It's a Monday morning. Maya is doing her weekly ritual — staring at the funnel dashboard over coffee. She's seen these numbers a hundred times. Then she hits the last line of the checkout funnel. 32%. She blinks. She refreshes. Still 32%."

Walk through the discovery narrative (see `discovery-story.md`). Hit these beats:
- The anomaly in the aggregate data
- The step-level breakdown (the 40% drop at payment step)
- The session recordings (the painful mobile keyboard moment)
- The support tickets (78% of "order not received" tickets are actually fine orders)
- The team meeting where everyone is right and nobody agrees

**End the story with the PM's actual problem:**

> "Maya has 4 days to kick off a project to address the gap. She needs a PRD for engineering by Wednesday, an exec summary for Thursday leadership review, and an engineering scope breakdown by Friday. She has messy notes, five interview transcripts, 20 support tickets, and a weak first draft of a PRD that she wrote at 11pm and she knows is bad."

> "We're going to help her. In real time. Using AI."

---

## The setup beat (0:10–0:15)

Orient the room:
- Point them to the GitHub repo
- Show the file structure — takes 2 minutes
- Tell them which files they'll need for each exercise
- Make sure everyone has Claude open and is ready to paste

**Say:** "We're going to do every exercise together. I'll run it on my screen, you run it at your table. We compare outputs in real time."

---

## Exercise 1 — Notes → PRD (0:15–0:35)

**The move:** Do the bad prompt first. Out loud.

> "Let me show you what happens when I ask Claude to just... do it."

Run: `"Write a PRD for fixing Terracart's checkout abandonment problem."`

Wait. Show the output on screen. Ask the room:

> "What did Claude have to make up? What's missing? What's confidently wrong?"

Let people answer. Then:

> "This is what AI PM looks like without a system. Now let's add one."

Run the structured prompt with the meeting notes and the template. Compare side-by-side.

**The moment to land:** The difference is not Claude. It's you. The PM with the template and the constraints got a better output because they built a better system.

**Facilitator tip:** If the structured output is still weak in places, celebrate that. Ask someone to improve it live with a follow-up prompt. The iterative loop is the lesson.

---

## Exercise 2 — Transcript → insight memo (0:35–0:50)

**Set it up with a question:**

> "Has anyone ever been in a research readout where someone said 'users feel confused' and nobody could remember which user said that, or why? Raise your hand."

[Pause for hands]

> "AI is actually great at synthesis — but only if you build in the rules. Watch what happens when we tell it not to invent quotes."

Run the synthesis prompt. When you get the output, spot-check a quote live:

> "Let's find this quote in the actual transcript."

Find it. (If you've prepared, you know Sarah T.'s quote about the keyboard is in Interview 1.)

> "That quote is real. That's not AI hallucination. That's AI retrieval — and it works because we told it not to make things up."

**The meta-lesson:** Sourcing rules change what AI does with your content. Without them, it summarizes. With them, it synthesizes.

---

## Exercise 3 — One source → three audiences (0:50–1:00)

**This one moves fast.** It's the most fun exercise because the contrast is immediate.

Run all three prompts in sequence. Show them next to each other:
- The exec brief: punchy, dollar-forward, no jargon
- The eng handoff: specific, blocker-aware, action-oriented
- The Slack update: human, no bullet points, no "hey team!"

Ask the room:

> "Same information. Three different documents. Which one took the most effort from you? Which took the most effort from Claude?"

**The answer:** The effort from you was mostly in naming the audience's priorities explicitly. That's PM work. Claude did the format and tone transformation. That's AI work.

---

## Exercise 4 — Context folder (1:00–1:15)

**Shift the energy here.** This is the "take it home" exercise.

Say:

> "Every exercise today worked because you gave Claude context. But you had to paste everything in manually each time. What if you built a context system once and it made every conversation better automatically?"

Show them the folder structure. Build the CONTEXT.md live — but use YOUR product instead of Terracart. This is the moment where it gets personal.

> "Open a new Claude tab. Describe your product, your team, your current initiative. Let's build your CONTEXT.md right now."

Give them 8 minutes to build it. Then run the test:

> "Paste your CONTEXT.md into a new Claude conversation. Ask it to write a Slack message about a fictional initiative at your company. See what you get."

**The moment:** Watch someone's face when Claude uses the right internal terminology, the right tone, the right stakeholder framing — because it's in the context file.

---

## Exercise 5 — PRD reviewer (1:15–1:25)

**Frame it right:**

> "The most dangerous moment in PM work is when you've written a PRD and you think it's done. The review process is where your assumptions get stress-tested. AI can simulate that stress test before you put the doc in front of real people."

Run the three-persona critique on the weak PRD. Read a few outputs aloud. Pick the most painful one and ask:

> "Is this critique fair? Have you been in a meeting where an engineer gave you this exact feedback — just more politely?"

Then build the reusable checklist together:

> "Let's make this permanent. Ask Claude to turn this review pattern into a checklist you can run on any PRD."

---

## Close (1:25–1:30)

Come back to the throughline:

> "Output quality improves when PMs improve the system around the model — not just the prompt."

Name the five things they built:
1. A structured PRD from messy notes
2. An evidence-backed insight memo with real sourcing
3. Three audience-specific communications from one document
4. A context folder that makes every future conversation better
5. A reusable PRD review workflow

> "You didn't do any of this by writing better prompts. You did it by building better systems. That's the AI PM superpower. Not prompting. Systems."

**The one thing to do Monday:**
> "Pick one thing from today and use it on a real artifact this week. Not a demo. A thing you actually have to ship. That's where it gets real."

---

## Backup plans

**If the group is ahead of schedule:**
- Run the pre-mortem bonus prompt on the Terracart initiative
- Have the group compare outputs across tables — what did different people's prompts produce?
- Go deeper on Exercise 4 — build a decision log entry from the meeting notes

**If the group is behind schedule:**
- Combine Exercises 3 and 5 (skip the Slack update, go straight to the reviewer)
- Do Exercise 4 as homework with clear instructions

**If someone's Claude is broken:**
- Have them pair with a neighbor
- Share your screen for the big exercises

---

## The quirky professor toolkit

A few beats that work well for a PM audience:

**"The 11pm PRD test"** — Ask if anyone has written a document they were ashamed of the next morning. Then show the weak PRD. "This is Maya's 11pm draft. Let's fix it without judgment."

**"The hallucination trap"** — Before Exercise 2, ask what everyone knows about AI hallucination. Then show them how sourcing rules prevent it. "The model isn't magic. It does what you tell it. The question is whether you told it the right thing."

**"The prompt is the last thing"** — Remind the room that the prompt is only as good as the context you've built around it. A perfect prompt on a blank context gives you a generic output. A mediocre prompt with rich context gives you a useful one. "The prompt is not your product. The system is your product."

**"Ship it or it's a hobby"** — At the close, push people to commit to a real-world use case before they leave the room. AI tools that only get used in workshops are a genre. Don't be a genre.

---

## Repo structure reminder

```
ai-pm-workshop/
├── README.md
├── 00-facilitator/
│   └── facilitator-guide.md          ← You are here
├── 01-discovery-narrative/
│   └── discovery-story.md
├── 02-raw-inputs/
│   ├── meeting-notes-raw.md
│   ├── customer-interview-transcript.md
│   ├── support-tickets-sample.md
│   ├── weak-prd-draft.md
│   └── prd-template.md
├── 03-exercises/
│   └── all-exercises.md
├── 04-prompts/
│   └── prompt-library.md
└── 05-outputs-reference/
    └── (outputs added after workshop)
```

---

*Facilitator guide version 1.0*  
*Built for ProductTank Dallas. Fork freely.*
