# The discovery story
### How Terracart found the $2.1M/month hole

---

## The company

**Terracart** is a mid-market e-commerce platform for specialty outdoor goods - think like the Target version of REI — camping gear, hiking apparel, gardening tools. Founded in 2019. About 280 employees. Growing but burning cash. The board just asked the CEO a pointed question about unit economics.

The product team is a team of six: one CPO, one senior PM, two associate PMs, a senior designer, and a user research analyst. Everyone is stretched thin. Everyone has opinions.

---

## Monday morning: The anomaly in the dashboard

Maya's Monday morning ritual is fifteen minutes with coffee and the growth dashboard. She's done it every week for two years. The dashboard shows the same six numbers it always shows: sessions, product page views, cart adds, checkout starts, purchases, revenue. 

All trending in the right direction. Green arrows, mostly.

The checkout-to-purchase rate sits at 32%. It has sat at 32% — give or take a point — for as long as Maya can remember. She has never flagged it. Neither has anyone else. It is, as far as anyone on the team is concerned, just what the number is.

What changes on this particular Monday is not the data. It's Maya's frame of reference.

Last week, she was at an industry meetup. Talking to a PM at a comparable B2C brand — similar price points, similar customer profile. Not a direct competitor, just a peer. The conversation drifted to metrics, the way those conversations do, and the other PM mentioned their checkout conversion rate almost in passing: "We just cracked 54%, which felt like a big deal after being stuck in the high 40s for two years."

Maya smiled and moved on. But the number stuck.

She pulls up the dashboard on Monday and stares at 32% with new eyes. Not "this is our number." For the first time: "Is our number okay?"

She doesn't know the answer. And the dashboard can't tell her — it has no benchmark, no industry comparison, no red line. It just shows the number.

She opens a new tab and spends twenty minutes reading a competitive market analysis report she make in Perplexity about e-commerce checkout conversion benchmarks.  

The range she finds: 45–58%. Her number is 32%.

Now she wants to understand where the 32% is coming from. But here's the thing — the dashboard doesn't break down the checkout funnel by step. It shows checkout starts and purchases. The middle is a black box. She has always assumed the drop-off was distributed, a little friction everywhere. She has never actually looked.

She Slacks her user research analyst: "Hey, can you please pull the checkout funnel for me broken down by step. Like each individual step — shipping, payment, review."

Darius responds twenty minutes later: "Yeah I can get that. It's not in the standard dashboard — I have to pull it manually from the tables themselves and build a new dash. Give me an hour."

This is the moment. The step-level data has existed in the analytics platform the entire time. Darius has access to it. It has just never been configured into a standard report, never been asked for, never been looked at. For too long the checkout experience has been bleeding users at the payment step and nobody has seen it because nobody has looked at the right level of the data.

The data wasn't missing. The context was missing. A benchmark from a casual conversation at a meetup is what finally provided it.

---

## Monday Lunchtime 1: The funnel data arrives

The analyst sends back a spreadsheet. Here's what it shows:

| Checkout step | Users entering | Users completing | Drop rate |
|---------------|---------------|-----------------|-----------|
| Shipping info | 18,400 | 16,750 | 9% |
| Shipping method | 16,750 | 15,200 | 9% |
| Payment info | 15,200 | 9,100 | **40%** |
| Order review | 9,100 | 8,650 | 5% |
| Confirmation | 8,650 | 5,888 | **32%** |

The bleeding is happening in two places: the payment info step (40% drop) and between order review and confirmation (32% drop). But nobody had been looking at granular data — only the overall funnel number. The anomaly had been hiding in the aggregate for a long time.

Annualized, the revenue gap between their actual conversion rate (32%) and a reasonable benchmark for their category (52%) is approximately **$2.1M**.

---

## Monday Afternoon: The session recordings

Maya pulls a sample of 50 session recordings from PostHog where users dropped at the payment step. What she sees:

- Users who reach the payment page on **mobile** abandon at 58% — almost double the desktop rate of 31%
- A repeating pattern: user fills in card number, hits tab to move to expiration date field... and the keyboard *shifts* on mobile. The expiration field is now behind the keyboard. Some users scroll. Most don't.
- Three users in the sample attempted to submit with the CVV field blank, got an error, and left immediately without correcting it
- Several users opened a new tab, presumably to check if they had a promo code, and never came back

The UX is leaking users like a colander, but the bleeding isn't random — it's concentrated, reproducible, and fixable.

---

## Monday evening: Support tickets tell a different story

After going to the gym to clear her head Maya pulls the support ticket data. 

In the last 60 days:

- **214 tickets** tagged "order not received / no confirmation"
- Of those, **167 were orders that actually processed** — the confirmation email failed silently
- **47 were genuine order failures** — mostly due to card decline with a confusing error message ("Transaction could not be completed. Please try again." — no reason given)
- The double-order problem has caused 97 refund requests totaling $15,124 in refunded revenue this quarter

The checkout abandonment problem has another layer: a silent confirmation failure that's eroding trust and draining customer support capacity at the same time.

---

## Tuesday morning: The team meeting

Maya calls a cross-functional meeting. In the room: herself, the head of engineering (Priya), a product designer (Cam), the user analyst (Darius), and the head of support (Lena).

What follows is 47 minutes of productive chaos. Everyone has a theory:

- **Priya (Engineering):** "The payment processor we switched to six months ago has stricter validation. The error messages it returns are opaque — we don't transform them at all, just pass them through to the front-end as-is."
- **Cam (Design):** "The form is broken on mobile. I've been saying this for 4 months. The expiration field jumps behind the keyboard. I even filed a ticket."
- **Darius (Analytics):** "The drop rate correlates with device type AND with cart value. Carts over $150 abandon at higher rates. People are hesitating on big purchases."
- **Lena (Support):** "The confirmation email is the real fire. We're handling 40+ tickets a week from people who are confused about whether they even have an order."
- **Maya (PM):** *[writing everything down, trying not to visibly panic about the lost revenue and the multiple problems identified]*

The meeting ends without consensus on root cause or priority. Everyone is right about something. Nobody can agree on what to fix first.

---

## Wednesday: The customer interviews

Maya does five quick customer interviews with people who abandoned checkout in the last 30 days (recruited via a support follow-up email). Key quotes:

> "I filled in my card and then I couldn't see where to put the expiration date. I thought maybe the site had crashed so I just gave up." — Shopper, mobile, $87 cart

> "I got an error that said 'transaction could not be completed' but I could see the money had been taken out of my bank account. I freaked out." — Shopper, desktop, $214 cart

> "I wasn't sure if I had a promo code somewhere so I opened a new tab to check my email. When I came back the cart was still there but I'd lost the payment fields. I just... didn't try again." — Shopper, mobile, $63 cart

> "The shipping cost wasn't shown until the very end. I was kind of expecting $8 and it was $14. I just put the item on my wishlist and left." — Shopper, desktop, $45 cart

> "Everything seemed to work but I never got an email. I called customer service, they said my order was fine. But it took like three days for me to feel okay about it." — Shopper, desktop, $310 cart

---

## The problem, properly stated

After three days of digging in data, back and forth in meetings, reviewing recordings, analyzing tickets, and conducting interviews, here's what Maya and Terracart actually knows:

**There are three distinct failure modes in the checkout experience:**

1. **Mobile form UX failure** — The payment form is broken on mobile, causing 58% abandonment at the payment step for mobile users (vs. 31% on desktop). Root cause: keyboard occlusion on the expiration field, no scroll-lock compensation.

2. **Error messaging failure** — Payment errors are returned verbatim from the processor with no human-readable explanation, causing confusion and permanent cart abandonment. Some users believe they've been charged when they haven't (and some actually have been charged in edge cases).

3. **Confirmation email failure** — 78% of "order not received" tickets are orders that processed successfully but didn't trigger a confirmation email. This is a silent trust killer that inflates support volume and causes double-orders (and cancellations/refunds).

**The big, messy insight:** These feel like three separate conditions. But they're not. They're three symptoms of the same root cause — the checkout experience was never stress-tested end to end as a system. It was built in silos feature by feature, tested only on Chrome desktop, and shipped. The seams are showing.

---

## What the team has to decide

The product team now has to answer five questions:

1. What do we fix first — the mobile UX, the error messages, or the confirmation email?
2. What's the right framing for the PRD — one document covering all three, or three separate workstreams?
3. How do we prioritize given engineering capacity is already at 80% for the quarter?
4. What does success look like, and how do we measure it?
5. How do we tell the story to the exec team without making it sound like the product has been broken for six months or more? (Because it has.)

*This is where you come in.*

---

Every exercise in this workshop uses Terracart's checkout problem as its source of truth. By the end, you'll have built a complete PM artifact stack — from raw discovery to stakeholder communication — using AI as your co-pilot.
