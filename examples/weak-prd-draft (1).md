# [RAW INPUT — DO NOT EDIT]
# Terracart — Checkout improvement PRD (DRAFT v0.1)
# Author: Maya Okonkwo
# Status: ROUGH DRAFT — needs work — written at 11pm please be kind
# Last updated: Week 3, Day 4

---

## Overview

We have a checkout problem. Users are dropping off and it's costing us money. This PRD covers the improvements we want to make to the checkout experience to increase conversion.

---

## Background

Analytics shows high abandonment at the payment step. Support is getting a lot of tickets about orders not being confirmed. There are also some mobile issues that have been raised.

---

## Goals

- Improve checkout conversion rate
- Reduce support tickets
- Better mobile experience
- Fix the email thing

---

## Non-goals

- Redesigning the cart page
- Changing the product listing pages
- Major payment processor changes (maybe)

---

## User stories

- As a user, I want to be able to complete checkout on my phone
- As a user, I want to know if my order went through
- As a user, I want clear error messages
- As a user, I want the form to be easy to use

---

## Requirements

### Mobile form improvements
We should fix the mobile form. The expiration field issue should be addressed. Inline validation would also be good. Form state should be preserved if the user navigates away.

### Error message improvements
Error messages should be more helpful. Instead of technical messages from the payment processor, we should show messages that tell users what to do. Probably needs eng input on what's possible.

### Confirmation email
The confirmation email is failing sometimes. This should be fixed. Probably a reliability issue. Need to understand root cause.

### Trust signals
Maybe add better trust signals to the payment page? Darius mentioned this might help with high-value cart abandonment.

---

## Success metrics

Conversion rate should go up. Support tickets should go down. We should probably define specific numbers but need to align with Darius on what's realistic.

---

## Open questions

1. Can we do all of this in one sprint?
2. What does eng think?
3. Is the confirmation email a quick fix or a big project?
4. Should we A/B test?

---

## Timeline

Ideally done soon. Leadership wants to see improvement this quarter. Engineering said they have 1-2 sprints. So probably 4-6 weeks?

---

## Risks

- Engineering capacity is limited
- We might not know if things work until we ship
- The payment processor stuff might be complicated

---

## Appendix

Meeting notes, interview transcripts, and support ticket data available separately.

---

*Note to self: this needs way more detail before Thursday. the requirements section especially. and i need actual metrics. and cam needs design specs. and priya needs scope. i have 36 hours. help.*
