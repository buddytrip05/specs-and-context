# The discovery story
### How Terracart found the $2.1M/month hole

---

## The company

**Terracart** is a mid-market e-commerce platform for specialty outdoor goods — camping gear, hiking apparel, gardening tools. Founded in 2019. About 280 employees. Growing fast but burning cash. The board just asked the CEO a pointed question about unit economics.

The product team is a team of six: two senior PMs, two associate PMs, a head of design, and a growth analyst. Everyone is stretched thin. Everyone has opinions.

---

## Week 1: The anomaly in the dashboard

On a Tuesday morning in Q2, Maya Okonkwo — senior PM, owns the checkout experience — is doing her weekly ritual of staring at the funnel dashboard over coffee.

She's seen these numbers a hundred times. Visitors to product page. Product page to cart. Cart to checkout. Checkout to purchase.

That last number stops her.

> **Cart → checkout:** 84%  
> **Checkout → purchase:** 32%

She blinks. She refreshes. Still 32%.

The cart-to-checkout rate is healthy — people *want* to buy. But then something happens between the checkout page and the confirmation page that kills 68% of transactions.

She Slacks the growth analyst: *"Hey, pull the checkout funnel for me broken down by step. Something's wrong."*

---

## Week 1: The funnel data arrives

The analyst sends back a spreadsheet. Here's what it shows:

| Checkout step | Users entering | Users completing | Drop rate |
|---------------|---------------|-----------------|-----------|
| Shipping info | 18,400 | 16,750 | 9% |
| Shipping method | 16,750 | 15,200 | 9% |
| Payment info | 15,200 | 9,100 | **40%** |
| Order review | 9,100 | 8,650 | 5% |
| Confirmation | 8,650 | 5,888 | **32%** |

The bleeding is happening in two places: the payment info step (40% drop) and between order review and confirmation (32% drop). But nobody had been looking at step-level data — only the overall funnel number. The anomaly had been hiding in the aggregate for at least three months.

Annualized, the revenue gap between their actual conversion rate (32%) and a reasonable benchmark for their category (52%) is approximately **$2.1M**.

---

## Week 2: The session recordings

Maya pulls a sample of 50 session recordings from users who dropped at the payment step. What she sees:

- Users who reach the payment page on **mobile** abandon at 58% — almost double the desktop rate of 31%
- A repeating pattern: user fills in card number, hits tab to move to expiration date field... and the keyboard *shifts* on mobile. The expiration field is now behind the keyboard. Some users scroll. Most don't.
- Three users in the sample attempted to submit with the CVV field blank, got an error, and left immediately without correcting it
- Several users opened a new tab, presumably to check if they had a promo code, and never came back

The UX is leaking users like a colander, but the bleeding isn't random — it's concentrated, reproducible, and fixable.

---

## Week 2: Support tickets tell a different story

Meanwhile, the head of customer support forwards Maya a Slack message:

*"We're getting a lot of 'my order didn't go through' tickets. But when I look them up in the system, the orders DID go through — they just didn't get a confirmation email. People are double-ordering. This is a mess."*

Maya pulls the support ticket data. In the last 60 days:

- **214 tickets** tagged "order not received / no confirmation"
- Of those, **167 were orders that actually processed** — the confirmation email failed silently
- **47 were genuine order failures** — mostly due to card decline with a confusing error message ("Transaction could not be completed. Please try again." — no reason given)
- The double-order problem has caused 23 refund requests totaling $4,100 in refunded revenue this quarter

The checkout abandonment problem has a twin: a silent confirmation failure that's eroding trust and customer support capacity at the same time.

---

## Week 3: The team meeting

Maya calls a cross-functional meeting. In the room: herself, the head of engineering (Priya), a product designer (Cam), the growth analyst (Darius), and the head of support (Lena).

What follows is 47 minutes of productive chaos. Everyone has a theory:

- **Priya (Engineering):** "The payment processor we switched to six months ago has stricter validation. The error messages it returns are opaque — we just pass them through as-is."
- **Cam (Design):** "The form is broken on mobile. I've been saying this for two quarters. The expiration field jumps behind the keyboard. I even filed a ticket."
- **Darius (Analytics):** "The drop rate correlates with device type AND with cart value. Carts over $150 abandon at higher rates. People are hesitating on big purchases."
- **Lena (Support):** "The confirmation email is the real fire. We're handling 30+ tickets a week from people who are confused about whether they even have an order."
- **Maya (PM):** *[writing everything down, trying not to visibly panic about the $2.1M number]*

The meeting ends without consensus on root cause or priority. Everyone is right about something. Nobody can agree on what to fix first.

---

## Week 3: The customer interviews

Maya does five quick customer interviews with people who abandoned checkout in the last 30 days (recruited via a support follow-up email). Key quotes:

> "I filled in my card and then I couldn't see where to put the expiration date. I thought maybe the site had crashed so I just gave up." — Shopper, mobile, $87 cart

> "I got an error that said 'transaction could not be completed' but I could see the money had been taken out of my bank account. I freaked out." — Shopper, desktop, $214 cart

> "I wasn't sure if I had a promo code somewhere so I opened a new tab to check my email. When I came back the cart was still there but I'd lost the payment fields. I just... didn't try again." — Shopper, mobile, $63 cart

> "The shipping cost wasn't shown until the very end. I was kind of expecting $8 and it was $14. I just put the item on my wishlist and left." — Shopper, desktop, $45 cart

> "Everything seemed to work but I never got an email. I called customer service, they said my order was fine. But it took like three days for me to feel okay about it." — Shopper, desktop, $310 cart

---

## The problem, properly stated

After three weeks of data, recordings, tickets, and interviews, here's what Terracart actually knows:

**There are three distinct failure modes in the checkout experience:**

1. **Mobile form UX failure** — The payment form is broken on mobile, causing 58% abandonment at the payment step for mobile users (vs. 31% on desktop). Root cause: keyboard occlusion on the expiration field, no scroll-lock compensation.

2. **Error messaging failure** — Payment errors are returned verbatim from the processor with no human-readable explanation, causing confusion and permanent abandonment. Some users believe they've been charged when they haven't (and some actually have been charged in edge cases).

3. **Confirmation email failure** — 78% of "order not received" tickets are orders that processed successfully but didn't trigger a confirmation email. This is a silent trust killer that inflates support volume and causes double-orders.

**The big, messy insight:** These feel like three separate bugs. They're not. They're three symptoms of the same root cause — the checkout experience was never stress-tested as a system. It was built feature by feature, tested on desktop Chrome, and shipped. The seams are showing.

---

## What the team has to decide

The product team now has to answer five questions:

1. What do we fix first — the mobile UX, the error messages, or the confirmation email?
2. What's the right framing for the PRD — one document covering all three, or three separate workstreams?
3. How do we prioritize given engineering capacity is already at 80% for the quarter?
4. What does success look like, and how do we measure it?
5. How do we tell the story to the exec team without making it sound like the product has been broken for three months? (Because it has.)

*This is where you come in.*

---

## Why this problem is a perfect workshop case

- It has **messy inputs** (meeting notes where everyone disagrees)
- It has **customer evidence** (interview quotes, support tickets)
- It has **quantified impact** ($2.1M) but also **ambiguity** (three root causes, unclear priority)
- It needs **multiple artifacts** (PRD, exec brief, engineering handoff, Slack update)
- It has **real PM tension** (what do you fix first when everything is on fire?)

Every exercise in this workshop uses Terracart's checkout problem as its source of truth. By the end, you'll have built a complete PM artifact stack — from raw discovery to stakeholder communication — using AI as your co-pilot.
