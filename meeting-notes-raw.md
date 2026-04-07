# [RAW INPUT — DO NOT EDIT]
# Terracart cross-functional checkout meeting
# Notes taken by: Maya Okonkwo (PM)
# Date: Tuesday 
# Attendees: Maya (PM), Priya (Eng lead), Cam (Design), Darius (Analytics), Lena (Support)

---

ok so I'm just going to type as fast as I can and clean this up later

Started at 2pm, ended around 2:47

**context I gave at the top:**
- 68% of people who hit the payment page don't complete the purchase
- on mobile it's 58% drop at payment step alone
- we're losing roughly 2.1M annually compared to category benchmark
- pulled 3 weeks of data, session recordings, and 214 support tickets

---

**Priya:**
the payment processor switch in Q4 last year — nobody stress tested the error messages. they just come through as raw API responses. "transaction could not be completed please try again" — that's their string, we just show it verbatim. there's no human readable layer. she mentioned there's a CVV validation issue too where the error is technically correct (card declined) but looks like a network error to the user. also said eng is at like 80% capacity this quarter, they can pull in 1-2 sprints max. 

also brought up: there's a race condition on mobile where if you submit too fast the payment token doesn't generate before the form submits. it's intermittent. she's seen it in logs but can't consistently reproduce. maybe 2% of failures.

**Cam:**
[was clearly frustrated before the meeting started, I think this has been filed as a ticket already]
keyboard occlusion on expiration field — on iOS specifically (and some Android) the keyboard pops up when you focus the payment form, which pushes the expiration field behind the keyboard. users have to know to scroll. most don't. he showed us a screen recording. it was painful to watch. 

also: the form has no inline validation. you only find out about errors after you hit "place order." which for mobile users means you scrolled back up, filled in something wrong, and now the error is at the top of the form but you're looking at the bottom.

he also mentioned the promo code field — if a user leaves the payment page to go find a promo code, the session doesn't preserve state. they come back to a blank form. he had designs for a persistent cart sidebar but that never got prioritized.

Cam made a pointed comment: "this is 18 months of deferred UX debt, not a bug." nobody responded directly to that.

**Darius:**
pulled some segments I hadn't seen:
- cart value over $150: 44% abandonment rate at payment (vs 28% for sub-$150 carts)
- new visitors vs returning: new visitors abandon at 52%, returning customers at 31%
- mobile users from organic search abandon at 61%, mobile users from email campaigns abandon at 43% (email = more purchase intent going in?)
- he thinks the high-cart-value abandonment is "anxiety" not UX — people hesitate on big purchases, especially with a brand they don't know well

trust signals: we have a security badge on the form but Darius ran an eye-tracking heatmap (from a while ago, different context) that shows most users never look at the bottom of the payment form where the badge is. 

Darius was pretty confident the confirmation email problem is a separate issue that's inflating the support ticket numbers. Lena disagreed.

**Lena:**
support is getting crushed. 30+ tickets per week on "order not received" — 78% of those are orders that actually went through fine, the confirmation email just silently failed. her team is having to manually look up orders in the system and reassure people. 

she's also seeing double-orders: people who didn't get a confirmation email, assumed the order failed, placed it again. she had a spreadsheet, we didn't have time to look at it but she said there have been at least 23 duplicate refund requests this quarter.

there was a tense moment where Lena said "if this were customer service software, this would be a sev-1" and Priya said "we're triaging across the whole product, not just checkout." it didn't escalate but the energy shifted.

Lena's ask: whatever we build, the confirmation email fix needs to be in the first release. she can't keep absorbing this support volume.

---

**things we didn't agree on:**
- is this one PRD or three separate workstreams? (Maya: leaning toward one coherent experience doc. Priya: wants it scoped to what eng can actually build this quarter)
- priority order: everyone had different instincts
  - Priya: fix the race condition + error messages first (infrastructure)
  - Cam: fix the mobile form UX first (highest impact on conversion)
  - Darius: A/B test trust signals first (low lift, could have big impact)
  - Lena: fix confirmation email first (team is drowning)
  - Maya: no consensus, taking it to document

- success metrics: nobody defined these. Darius said "we should set a conversion rate target" but we ran out of time

---

**open questions from the meeting:**
1. do we have the data to separate "mobile UX failures" from "payment processor failures"? Priya thinks yes, needs a day to pull it
2. what is the actual SLA on the confirmation email fix? is this a config issue or a rebuild?
3. has legal looked at the "charged but no confirmation" edge cases? potential chargeback exposure
4. can we get user testing on the mobile checkout flow before we commit to a fix direction?
5. what's the competitive benchmark for checkout conversion in outdoor/specialty e-commerce?

---

**my takeaways (unfiltered):**
- we have three distinct problems masquerading as one
- the mobile UX thing is probably the highest conversion impact but requires design + eng alignment
- the confirmation email thing is the most urgent from a trust/support perspective
- error messaging is the easiest fix but nobody's excited about it
- Cam is right that this is deferred UX debt — the question is how we frame that to leadership without it sounding like an indictment of past decisions
- need to write this up as a PRD before Thursday, which means I have 36 hours
- also need an exec summary for the Friday leadership review
- also Priya wants an engineering scope breakdown by Monday

*send help*
