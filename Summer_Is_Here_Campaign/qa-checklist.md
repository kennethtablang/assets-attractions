# Campaign QA Checklist — [CAMPAIGN NAME]

**Campaign ID:** ____________  **Send date:** ____________
**Built by:** ____________  **Reviewed by:** ____________ *(must be a second person)*

> No campaign moves from `QA` to `SCHEDULED` until every box in sections A–E is ticked.
> Sections F–H are completed at and after launch.

---

## A. Content accuracy — the errors you cannot undo

- [ ] Every **price** in the email matches the offer sheet exactly
- [ ] Every **date** matches the offer sheet exactly (start, end, blackouts)
- [ ] Every **attraction name** spelled correctly (check against the supplier's own website)
- [ ] Discount percentage / savings amount is arithmetically correct
- [ ] Promo code is correct and case-matches the booking system
- [ ] Terms & conditions present and linked
- [ ] Offer deadline stated in the email body, not just the subject
- [ ] Currency formatted consistently (`AED 199`, not `199 AED` / `199AED` mixed)
- [ ] Copyright year in the footer is current
- [ ] No placeholder text remains (`Lorem`, `XXX`, `[insert]`, `TBC`)
- [ ] Copy read aloud once, end to end

## B. Email build

- [ ] Campaign named per convention: `{yyyy}-{mm}-{CODE}-email-{variant}`
- [ ] Sender name is the standard one (`Dubai Ticket Magic`)
- [ ] From address is a **monitored** inbox, not no-reply
- [ ] Reply-to set correctly
- [ ] Subject line ≤45 characters; both A/B variants entered
- [ ] Preview text set (40–90 chars) and does **not** repeat the subject
- [ ] Correct segment selected; **contact count recorded: ________**
- [ ] Suppression segment applied
- [ ] Content width 600px
- [ ] Total HTML **under 100 KB** (Gmail clips above ~102 KB and hides the footer)
- [ ] Every image has alt text that carries meaning
- [ ] Every image loads from the **pinned jsDelivr tag** (not `@main`, not `raw.githubusercontent.com`)
- [ ] CTA is a bulletproof button (HTML/CSS), not an image
- [ ] CTA tap target ≥44px tall
- [ ] Body text ≥14px (≥16px mobile)
- [ ] Unsubscribe link present, visible, and not shrunk or hidden
- [ ] Physical business address in the footer
- [ ] Google Analytics link tracking enabled in Mailchimp campaign settings
- [ ] Mailchimp account timezone = **Asia/Dubai**

## C. Links & tracking

- [ ] **Every single link clicked and verified** — not spot-checked
- [ ] All links carry `utm_source`, `utm_medium`, `utm_campaign`
- [ ] `utm_content` differs per link position (`hero_cta`, `card_x`, `footer_cta`)
- [ ] `utm_campaign` matches the register exactly (lowercase, underscores)
- [ ] UTM combination registered in the UTM Registry tab
- [ ] Clicked a live link and **confirmed it appears in GA4 Realtime** with the right campaign
- [ ] Landing page URL is production, not staging
- [ ] No shortened links in the email body

## D. Rendering

- [ ] Test sent to **at least 4 real inboxes**: Gmail, Outlook, Apple Mail, one mobile-only
- [ ] Renders correctly on a **real phone**, not just a simulator
- [ ] **Dark mode** checked — logo and text still legible
- [ ] **Images-off** checked — the offer is still understandable from text and alt text
- [ ] Merge tags tested with a real contact; **fallback text set** (no "Hi ,")
- [ ] No horizontal scroll on mobile
- [ ] Spam score checked (mail-tester.com) — score ≥8/10

## E. Landing page

- [ ] Headline matches the email's promise (no message mismatch)
- [ ] Offer and price stated above the fold
- [ ] Products listed with prices matching the offer sheet
- [ ] Benefits stated, not just features
- [ ] Social proof present (rating / review count / quote)
- [ ] Primary CTA above the fold **and** repeated below
- [ ] Mobile responsive — tested on a real device
- [ ] **PageSpeed Insights run; LCP < 2.5s**
- [ ] Images compressed and served in WebP where possible
- [ ] Page title and meta description written
- [ ] OG image and OG tags set (test how it looks pasted into WhatsApp)
- [ ] Canonical URL set
- [ ] GA4 firing
- [ ] Microsoft Clarity firing
- [ ] Conversion event fires on the confirmation page — **verified in GA4 Realtime**
- [ ] Confirmation page is a distinct URL
- [ ] All forms submit successfully and the submission is received
- [ ] No broken links (run the link checker)
- [ ] T&Cs and blackout dates published
- [ ] **Real end-to-end test booking completed, including the promo code**

## F. Pre-send final

- [ ] Segment count re-confirmed immediately before scheduling: ________
- [ ] Send date/time correct in **Asia/Dubai**
- [ ] Not a Friday; not a UAE public holiday
- [ ] No other campaign hitting this segment within 5 days
- [ ] Social posts scheduled
- [ ] Website banner live
- [ ] Booking system live with the campaign price
- [ ] Supplier availability re-confirmed if more than 7 days since Stage 3

**Reviewer sign-off:** ______________  **Date/time:** ____________

## G. Post-launch monitoring

| When | Check | Value | OK? |
|---|---|---|---|
| T+30min | Delivery rate (≥98%) | | ☐ |
| T+30min | Bounce rate (<2%) | | ☐ |
| T+30min | GA4 Realtime showing traffic on the correct UTM | | ☐ |
| T+2h | CTR trajectory | | ☐ |
| T+2h | Spam complaints (<0.05%) | | ☐ |
| T+2h | Landing page errors in Clarity | | ☐ |
| T+24h | Full metric set recorded | | ☐ |
| T+24h | First conversions recorded | | ☐ |
| T+24h | Watched 3 Clarity recordings of non-converters | | ☐ |
| T+48–72h | Resend-to-non-openers decision made | | ☐ |

**Stop-everything triggers:** bounce >5% · spam complaints >0.1% · delivery <95% · zero clicks after 2h with normal opens (broken link) · GA4 showing traffic with no UTM (broken tracking)

## H. Campaign close

- [ ] Campaign end date reached; offer expired on the landing page and in the booking system
- [ ] Website banner removed or swapped
- [ ] Analytics pulled and **reconciled against actual booking system revenue**
- [ ] Register row updated with all results
- [ ] Post-mortem written within 7 days
- [ ] Assets archived and git-tagged: `campaign/{yyyy}-{code}`
- [ ] Winning subject line and creative added to the swipe file
- [ ] Lessons converted into scored backlog items
- [ ] Status set to `COMPLETED`
