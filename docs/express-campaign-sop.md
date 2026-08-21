# Express Campaign SOP — Same-Day Email Production

**Purpose:** Produce and send a complete marketing email in one working day (~5 hours), or in 90 minutes for a flash offer.
**Relationship to the full pipeline:** This is a second lane, not a replacement. Both lanes share the same register, naming conventions, and tracking standards. See [`marketing-campaign-os.md`](marketing-campaign-os.md).

---

## 1. The rule that makes this work

> **Express speed comes from the asset library, not from cutting corners.**

You cannot run an express campaign from a cold start. The day is fast because the email template, the segments, the attraction imagery, the Canva templates, and the prompt pack already exist. Build those once (§2). After that, a campaign is a **swap**: new offer, new products, new copy into an existing skeleton.

Your first express campaign will take a full day. Your fifth will take three hours.

---

## 2. Prerequisites — build once, then never again

Nothing below is optional. Missing any one of them turns a one-day campaign back into a three-day campaign.

| # | Prerequisite | Where | Build time |
|---|---|---|---|
| 1 | **Reusable email HTML template** with swappable blocks | `email/templates/email.html` | Done ✅ |
| 2 | **Express brief** (brief + QA in one file) | `docs/templates/express-brief.md` | Done ✅ |
| 3 | **Copy prompt pack** — paste-ready, no prompt writing on the day | `docs/prompts/express-copy-prompts.md` | Done ✅ |
| 4 | **Evergreen attraction image library** — every product you sell, pre-cropped to email card + hero sizes, compressed, committed | `attractions/` in the public repo | 3–4h once |
| 5 | **Canva templates** — email header, email hero, IG feed, IG story, locked to Brand Kit | Canva | 3h once |
| 6 | **Saved Mailchimp segments** — the 12 standard segments + suppression segment | Mailchimp | 2h once |
| 7 | **Pre-approved margin bands** — the discount depth you're allowed to offer per product category without fresh sign-off | `docs/margin-bands.md` (private) | 1h once, with commercial |
| 8 | **Pre-confirmed evergreen products** — the attractions with standing price agreements and known blackout dates | `docs/evergreen-products.md` (private) | 2h once |
| 9 | **Swipe file** of winning subject lines | `swipe-file/` | Grows over time |

**Items 7 and 8 are what actually buy you the day.** They front-load the two slowest gates in the full pipeline — margin approval and supplier confirmation — so that on the day you are *checking against a list* instead of *waiting on an email reply*.

---

## 3. When you are allowed to use the express lane

| Situation | Lane |
|---|---|
| Offer sits inside a **pre-approved margin band** | ✅ Express |
| All products are on the **evergreen pre-confirmed list** | ✅ Express |
| Reusing an existing offer mechanic (weekend deal, under-AED-100, flash) | ✅ Express |
| Supplier flash inventory, competitor response, weather-driven push | ✅ Express |
| Filling an unexpected gap in the calendar | ✅ Express |
| **New product** not previously confirmed | ❌ Full lane — needs Stage 3 |
| **Discount deeper than the approved band** | ❌ Full lane — needs Stage 2 sign-off |
| **New audience segment** never tested | ❌ Full lane |
| Major seasonal campaign (National Day, Christmas, Ramadan) | ❌ Full lane — too much revenue at stake |
| New landing page required | ❌ Full lane — or reuse an existing page |
| Budget above AED 5,000 | ❌ Full lane |

**Governance rule:** if more than half your campaigns in a quarter are express, your margin bands are too loose or your calendar planning has broken down. Express is for the reactive 30%.

---

## 4. The five non-negotiables

Everything else in the full pipeline can be compressed. These five cannot, because each one costs real money or real reputation and none can be undone after send.

1. **Margin checked** — against the pre-approved band. Ten seconds, not a meeting. A campaign that sells out below cost is worse than no campaign.
2. **Product availability confirmed** — evergreen list, plus a 5-minute check that nothing is blacked out this weekend.
3. **Every price and date verified against the offer** — the single most damaging error class. Read them twice.
4. **Every link clicked** — not spot-checked. A dead CTA wastes the entire send.
5. **A real end-to-end test booking, including the promo code** — the only proof the money can actually arrive.

If you are too rushed for these five, you are too rushed to send.

---

## 5. The one-day timeline (~5 working hours)

| Time | Block | Do this | Output |
|---|---|---|---|
| **09:00–09:20** | **Frame** | Open `express-brief.md`. Fill §1 Offer and §2 Audience. Check the margin band. Check the evergreen list. | Offer locked |
| **09:20–09:35** | **Verify** | Confirm no blackout dates this window. Confirm booking system price. Create the promo code. | Green light |
| **09:35–10:20** | **Copy** | Open the prompt pack. Run Prompt 1 (subject lines) → Prompt 2 (email body) → Prompt 3 (Claude refine). Paste into §3 of the brief. | Copy done |
| **10:20–11:20** | **Creative** | Canva template → swap headline, price, images from the `attractions/` library → export → Squoosh → rename → commit → tag → CDN URLs | Assets live |
| **11:20–12:05** | **Build** | Copy `email/templates/email.html`, delete unused blocks, fill the tokens, paste into Mailchimp as a code template. Set subject, preview, sender, segment, UTMs. | Email built |
| **12:05–12:45** | **Break** | Actually step away. Fresh eyes catch price errors; tired eyes do not. | — |
| **12:45–13:30** | **QA** | Work §5 of the brief. Test to 4 real inboxes. Click every link. Test booking with the promo code. | Checklist green |
| **13:30–13:45** | **Review** | Second person reads §5. If genuinely alone, read the email aloud start to finish. | Signed off |
| **13:45–14:00** | **Schedule** | Confirm segment count. Confirm Asia/Dubai. Schedule for 17:00–19:00. Log the register row. | Scheduled |
| **17:00–19:00** | **SEND** | — | Live |
| **+30 min** | **Health check** | Delivery, bounce, GA4 Realtime on the right UTM | Confirmed |
| **+2 hours** | **Second check** | CTR trajectory, spam complaints, Clarity for landing page errors | Confirmed |

**Send timing reminder:** Thursday or Friday morning for B2C weekend planning. During Ramadan shift to 20:00–22:00 GST. Never Friday afternoon.

---

## 6. The 90-minute flash variant

For genuine urgency — a supplier releases distressed inventory Thursday morning for the weekend.

**What changes:** no new creative at all.

| Time | Do this |
|---|---|
| **0:00–0:10** | Offer + margin band check + availability check |
| **0:10–0:30** | Copy — subject line, one paragraph, one CTA. Prompt 4 in the pack ("flash email"). |
| **0:30–0:40** | Pull an existing hero from `attractions/`. **Do not open Canva.** Text-led email. |
| **0:40–1:00** | Build in Mailchimp from the flash block set (header → text offer → CTA → footer) |
| **1:00–1:20** | QA — the five non-negotiables only. Two inboxes minimum, one mobile. |
| **1:20–1:30** | Schedule and send |

**Flash constraints:**
- Text-led, one image maximum, one CTA, no product grid
- Existing landing page only — never build a page in flash mode
- Send to your **engaged 90-day segment only**, not the full list. A rushed email to your whole list risks complaints that outlast the offer.
- Cap at one flash per fortnight. Frequency is what kills lists.

---

## 7. What express deliberately drops

Be conscious about these — they're the trade you're making, not oversights.

| Dropped | Consequence | Mitigation |
|---|---|---|
| Formal research (Stage 1) | No competitor price context | Only run express on offers you already know are competitive |
| A/B testing | No subject-line learning from this send | Use a proven winner from the swipe file |
| New landing page | Traffic goes to an existing page | Keep 3 evergreen pages permanently live: weekend deals, under AED 100, family |
| Dark mode + images-off checks | Small rendering risk | The HTML template already handles both — this is why the template exists |
| Second-person review *(if solo)* | Higher error risk | Read aloud. Non-optional if you're alone. |
| Post-mortem depth | Less learning | Still log results in the register. A 3-line note beats nothing. |

**Never dropped:** the five non-negotiables in §4, UTM tracking, the register row, and the unsubscribe link.

---

## 8. After the send

Express campaigns still close properly, just faster. Within 3 days:

- [ ] Register row updated: sent, delivered, CTR, CTOR, conversions, revenue
- [ ] Three lines in `lessons_learned` — what worked, what didn't, whether to repeat
- [ ] Winning subject line added to the swipe file
- [ ] Any new asset moved into `attractions/` so the next express campaign is faster

That last one is the compounding mechanism. Every express campaign should leave the library richer than it found it.
