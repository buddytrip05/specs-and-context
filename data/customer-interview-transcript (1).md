# [RAW INPUT — DO NOT EDIT]
# Terracart — customer interview transcripts
# Conducted by: Maya Okonkwo (PM)
# Method: 20-minute Zoom calls, recruited from support follow-up email
# Screener: Abandoned checkout in last 30 days OR submitted "order not received" ticket
# Sample size: 5 interviews
# Transcribed by: Otter.ai (lightly cleaned)

---

## Interview 1 — "Sarah T." | Mobile, $87 cart | Abandoned at payment

**Maya:** Can you walk me through what happened when you were checking out?

**Sarah:** Yeah, so I was on my phone, I was like waiting for my kid's soccer practice to end. I found the rain jacket I wanted, put it in my cart, and started checking out. I got through the address stuff okay. Then I got to the payment part and I typed in my card number and hit the next field — like the expiration date — and the keyboard popped up and I just... couldn't see the field anymore. I thought maybe the page had crashed or something. I tried tapping around but I couldn't figure out where to put the date.

**Maya:** What did you do next?

**Sarah:** I just gave up. I figured I'd do it on my laptop later. And then I forgot. And then I just bought it on Amazon because I needed it for a camping trip the next weekend.

**Maya:** Would you have bought from Terracart if the checkout had worked?

**Sarah:** Oh, yeah. I liked the jacket. I wasn't price-shopping or anything. I just literally couldn't figure out how to complete the form.

---

## Interview 2 — "Marcus D." | Desktop, $214 cart | Abandoned at order review

**Maya:** Tell me about your checkout experience.

**Marcus:** So this is a little embarrassing but I kind of panicked. I was buying a tent — it was a big purchase for me, like $214 — and I went through the whole checkout, put in my card info, clicked the button. And I got an error that said... I wrote it down actually because it freaked me out... it said "Transaction could not be completed. Please try again." But I checked my bank account and the money was already out. Like I had a pending charge.

**Maya:** Oh no. What happened after that?

**Marcus:** I called my bank. They said it looked like a normal pending charge. So I called Terracart's support number. They eventually figured out that there was like a temporary authorization that got declined but the bank saw it before the decline registered. Or something. I don't totally understand it. But I never placed the order because I was scared to get double-charged. I ended up ordering from another site. I never got a refund on the pending charge either — it just fell off after a few days. But I didn't know it was going to do that.

**Maya:** How did that experience make you feel about Terracart?

**Marcus:** [pause] I mean, it made me not trust the checkout. Which is kind of the whole website. I haven't been back.

---

## Interview 3 — "Priya R." (different from our Priya!) | Mobile, $63 cart | Abandoned mid-payment

**Maya:** Walk me through what happened.

**Priya R.:** Okay so I had a promo code. Or I thought I did. I got an email from Terracart a while back and I thought there was a code in it. So I was at the payment page, and I went to go look for the code in my email. I opened Gmail, found the email, no code — it was just a sale announcement. When I came back to Terracart, the payment form was blank. Like I had to re-enter everything. My card number, the expiration, all of it.

**Maya:** And you didn't redo it?

**Priya R.:** I mean... I was standing in line at the grocery store by this point. I just didn't have time. And it felt like a bad sign, you know? Like if the website can't remember what I just typed, what's it going to do with my order?

**Maya:** That's really helpful framing. Is there anything that would have made you come back and complete the purchase?

**Priya R.:** If the form had just... still been filled in when I came back? Like every other website does that. Even if it just saved the card type and last four digits or something so I didn't have to do it again.

---

## Interview 4 — "Jordan K." | Desktop, $45 cart | Abandoned at shipping step

**Maya:** You actually dropped off before the payment step — at shipping. Can you tell me more?

**Jordan:** Yeah so I didn't realize how expensive the shipping was going to be until basically the last step. I had a $45 cart and the shipping was $14. I guess I expected like $8 or free shipping or something. It just felt like a lot on top of what I was already spending for what it was.

**Maya:** Did you look for a free shipping threshold or promo?

**Jordan:** I looked around for like two seconds but I couldn't find anything obvious. I added the item to my wishlist and figured I'd wait for a sale or if I had more stuff to buy.

**Maya:** Have you come back since?

**Jordan:** No. But I might. I don't know.

**Maya:** If we'd shown you the shipping cost earlier — like on the product page or in the cart — would that have changed your behavior?

**Jordan:** Maybe? I would have at least known what I was getting into. It's the surprise at the end that feels bad. I don't mind paying for shipping if I know about it upfront.

---

## Interview 5 — "Christine L." | Desktop, $310 cart | Order completed, but no confirmation email

**Maya:** So your order actually went through — this is a little different from the other conversations.

**Christine:** Right, so I bought a really nice sleeping bag — it was like $310, a big splurge. I went all the way through checkout, it said "processing" and then I got a blank screen. No "your order is confirmed" page, nothing. I waited. Then I got no email.

**Maya:** What was your reaction?

**Christine:** I was convinced I'd been scammed. I know, I know — it's a real website. But I'd never ordered from Terracart before and $310 is a lot of money for me. I called my credit card company, I filed a report... I feel a little silly about it now. Eventually I called Terracart's support line, they found my order, it was fine, it shipped two days later.

**Maya:** How long did that whole saga take?

**Christine:** Like three days of me being stressed about it. The customer service person was really nice, to be fair. But I had already told two of my friends not to shop there. [laughs] Sorry.

**Maya:** No, that's genuinely helpful. Did you get the sleeping bag?

**Christine:** Yeah, I love it. I might order again if I needed something. But I'd be nervous about the checkout. Which is a weird feeling when the product is great.

---

## Raw notes from interviews — Maya's unfiltered observations

**Pattern 1: Mobile keyboard UX is a literal blocker.** Sarah's story is not an edge case. She wanted to buy. She had her card out. The form broke on her and she went to Amazon. This is a pure UX failure with zero ambiguity.

**Pattern 2: Error messages create catastrophic trust collapse.** Marcus's story is the worst case scenario — a charging error with an opaque message that made a $214 customer feel like he'd been defrauded. He's gone. He will not return. One bad error message = one lost customer and potential word-of-mouth damage.

**Pattern 3: Session state loss is a deal-breaker on mobile.** Priya R.'s behavior (leave to find promo code, come back to blank form) is completely predictable and completely preventable. Every other e-commerce checkout preserves form state. Ours doesn't.

**Pattern 4: Shipping cost surprise is a separate but real problem.** Jordan's issue is upstream — the shipping cost reveal at the end of checkout is a well-documented UX anti-pattern. This is outside the scope of the current sprint but worth logging.

**Pattern 5: The confirmation failure is a trust catastrophe, not a minor email bug.** Christine told two friends not to shop at Terracart. Because of a silent email failure. She still loves the product. She's afraid of our checkout. That is a very specific and very fixable kind of damage.

**Across all 5 interviews:** Nobody blamed the product. Everyone wanted to buy. The checkout experience is actively destroying transactions that would have happened.

This is not a demand problem. It is a plumbing problem.
