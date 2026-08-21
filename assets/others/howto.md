# How To Run Marketing Campaigns — Start Here

**Plain-language guide to the campaign system.**
Read this first. Everything else is detail hanging off it.

---

## The core idea

Think of a restaurant kitchen. Most of the work happens **before anyone orders** — the prep, the stocked fridge, the recipe cards, the standard plates. Once that's done, cooking a dish is fast and comes out the same every time.

Right now, every campaign is cooked from scratch: buy the ingredients, invent the recipe, hunt for a plate. That's why campaigns feel slow and why each one starts from zero.

> **Build the kitchen once. Then cooking is fast.**

Everything in this system is either **building the kitchen** (done once) or **cooking** (done every campaign).

---

## Part 1 — Every campaign answers 6 questions

Ignore the long stage lists for now. A campaign is really six questions, answered in order. You can't skip ahead.

| # | Question | What it actually means | If you skip it |
|---|---|---|---|
| **1** | **Should we do this?** | Score the idea before starting | You spend two weeks on a weak campaign |
| **2** | **Will it make money?** | The offer and the margin | You sell out at a loss |
| **3** | **Can we deliver it?** | Supplier confirmed, tickets available, no blackout dates | You refund customers and annoy suppliers |
| **4** | **Who do we tell, what do we say?** | Pick the audience. Write the copy. Make the images. | You send the wrong offer to the wrong people |
| **5** | **Does it actually work?** | Every link, every price, a real test booking | You waste the entire send on a dead button |
| **6** | **Did it work?** | Pull the numbers. Write down what you learned. | You run campaigns for years without getting better |

**Questions 2 and 3 cost real money if skipped.**
**Question 5 wastes the whole send.**
**Question 6 is the one everyone skips** — and it's the only one that makes the *next* campaign better.

That's the whole pipeline. Everything else is detail.

---

## Part 2 — What you prepare (once)

Four groups. Do them in this order, because each depends on the one before.

### Group 1 — Foundation *(~1 day)*

**Without this you can send emails but you cannot measure anything.**

- [ ] **1.** Create a private `marketing-ops` repo, move `docs/` into it
      *Why: margins and supplier prices must not sit in a public repo*
- [ ] **2.** Restructure and compress this asset repo
      *Why: images are currently 700–850 KB and need to be under 150 KB*
- [ ] **3.** Decide: pay for Mailchimp, or move to MailerLite free
      *Why: the current free tier caps at 500 contacts and blocks A/B testing*
- [ ] **4.** Verify SPF, DKIM and DMARC on the sending domain
      *Why: without these, Gmail and Yahoo send you straight to spam*
- [ ] **5.** Install GA4 + Microsoft Clarity, wire up the booking conversion
      *Why: this is what makes Question 6 possible. Without it you will never know if an email produced a sale.*
- [ ] **6.** Set up the campaign register in Google Sheets
      *Why: one row per campaign. It is the system's memory.*

### Group 2 — Reusable materials *(~1.5 days)*

This is the stocked fridge and the recipe cards.

- [ ] **7.** Canva Brand Kit + 4 templates (email header, email hero, Instagram feed, Instagram story)
      *Turns design from 3 hours into 30 minutes*
- [ ] **8.** **Attraction image library** — every product you sell, pre-cropped to hero and card sizes, compressed
      *The single biggest time-saver. Never hunt for an image again.*
- [ ] **9.** Build the 12 standard audience segments + the suppression segment
      *Stops you emailing the whole list, which is what destroys deliverability*
- [ ] **10.** Set your real brand colour in the email template
      *A placeholder red is in there now*

### Group 3 — Commercial groundwork *(~half a day, needs commercial sign-off)*

**This is what makes same-day campaigns possible.**

- [ ] **11.** **Margin bands** — how deep you may discount per category without asking anyone
- [ ] **12.** **Evergreen product list** — attractions with standing prices and known blackout dates

These two **pre-answer Questions 2 and 3**, the two slowest gates. On a rush day you check a list instead of waiting for someone to reply to an email. That is the entire trick behind the one-day lane.

### Group 4 — Already built ✅

Templates, checklists, prompt pack, email HTML, SOPs. Nothing to prepare.

---

## Part 3 — Two ways to run a campaign

### Full lane — about 2 weeks

For big seasonal campaigns: National Day, Christmas, Ramadan, Summer. Too much revenue at stake to rush. Walk all six questions properly.

### Express lane — one day (~5 hours)

For reactive campaigns: a supplier releases inventory, the weather turns, a competitor moves, a gap appears in the calendar.

Questions 2 and 3 are already answered by your margin bands and evergreen list, so you go straight to 4, 5, 6.

```
09:00  Offer + margin check + availability check     20 min
09:20  Confirm no blackouts, create promo code       15 min
09:35  Copy — use the prompt pack                    45 min
10:20  Creative — Canva template swap + compress     60 min
11:20  Build email from the HTML template            45 min
12:05  BREAK — step away, fresh eyes catch errors    40 min
12:45  QA — links, prices, test booking              45 min
13:30  Second person reviews                         15 min
13:45  Schedule                                      15 min
17:00  SEND
```

### Flash — 90 minutes

Genuine urgency only. Text-led email, one image from the library, no Canva, existing landing page, sent to your engaged-90-day segment only. Maximum one per fortnight.

**Rule of thumb:** if more than about a third of your campaigns are express, the problem is your planning, not the express lane.

---

## Part 4 — Which file do I open?

You will not re-read the big documents. Day to day, you touch these:

| I want to… | Open |
|---|---|
| Run a big seasonal campaign | `docs/templates/campaign-brief.md` |
| Run a one-day campaign | `docs/templates/express-brief.md` |
| Write copy fast | `docs/prompts/express-copy-prompts.md` |
| Build the email | `email/templates/email.html` |
| Check before sending | `docs/templates/campaign-qa-checklist.md` |
| Write up results | `docs/templates/campaign-post-mortem.md` |
| Track everything | `docs/campaign-register.csv` |
| Look up a detail I've forgotten | `docs/marketing-campaign-os.md` |
| Remember the express rules | `docs/express-campaign-sop.md` |

**How a campaign starts:** copy a brief template into a new campaign folder, add a row to the register, fill the brief top to bottom.
**How a campaign ends:** results in the register, post-mortem written, assets tagged, lessons noted.

---

## Part 5 — Five things that are never skipped

Whichever lane you're in, however rushed:

1. **Margin checked** — a campaign that sells out below cost is worse than no campaign
2. **Availability confirmed** — never promote something you cannot deliver
3. **Every price and date verified** — the most damaging error there is, and it cannot be undone
4. **Every link clicked** — not spot-checked. A dead CTA wastes the entire send.
5. **A real test booking, including the promo code** — the only proof money can actually arrive

If you're too rushed for these five, you're too rushed to send.

---

## Part 6 — Things that are easy to get wrong

| Mistake | What happens |
|---|---|
| Emailing the whole list every time | Unsubscribes and spam complaints climb, then your emails stop reaching inboxes at all |
| Judging campaigns on open rate | Open rate is inflated by privacy features. Use **clicks** and **bookings**. |
| Uploading cold B2B contacts to Mailchimp | Account suspension and permanent damage to your sending domain |
| Images over the weight limit | Gmail cuts the email off, which hides the footer and breaks the unsubscribe link |
| Spaces in filenames | Links break in some email clients |
| Skipping the post-mortem when a campaign went well | You never learn what to repeat |
| Two campaigns to the same people within 5 days | Fastest way to get unsubscribed |

---

## Part 7 — How you know you're finished preparing

- [ ] I can see in GA4 whether an email produced a booking
- [ ] My images are under the weight limits and load from a pinned CDN link
- [ ] My audience segments are saved, so I never send to the whole list again
- [ ] I know my discount limits without asking anyone
- [ ] I know which products I can promote today without emailing a supplier
- [ ] I have an image ready for every product I sell
- [ ] **I have run one campaign all the way through and written the post-mortem**

That last one matters most.

> A system that has been run once is a system.
> A system that has only been written down is a folder of documents.

---

## Summary

1. Six questions per campaign. Answer them in order.
2. Prepare the kitchen once — about 3 working days of setup.
3. Big campaigns take two weeks. Reactive ones take a day. Both use the same six questions.
4. Five things are never skipped, no matter how urgent.
5. Write down what you learned, or you'll learn nothing.
