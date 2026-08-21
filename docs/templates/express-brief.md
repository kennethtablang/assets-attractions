# Express Campaign — [NAME]

> One file. Brief + copy + QA. Fill top to bottom. Should take under 30 minutes of actual writing.
> Lane rules: [`express-campaign-sop.md`](../express-campaign-sop.md)

| | |
|---|---|
| **Campaign ID** | DTM-2026-MM-CODE |
| **Code** (UTM root) | `code` |
| **Date** | |
| **Send** | ____ @ 17:00–19:00 GST |
| **Lane** | Express / Flash |

---

## 1. Offer  ⛔ GATE

**Offer (customer-facing, verbatim):**
>

**Valid:** ____ → ____   **Promo code:** ________

| Product | Net cost | Campaign price | Margin % | In approved band? | Evergreen list? | Blackout this window? |
|---|---|---|---|---|---|---|
| | | | | ☐ | ☐ | ☐ No |
| | | | | ☐ | ☐ | ☐ No |
| | | | | ☐ | ☐ | ☐ No |

- [ ] Every margin inside the pre-approved band → **if not, stop. Full lane.**
- [ ] Every product on the evergreen confirmed list → **if not, stop. Full lane.**
- [ ] Booking system shows the campaign price
- [ ] Promo code created and active

**Goal:** ______ bookings / ______ AED revenue

---

## 2. Audience

**Segment:** ________________  **Size:** ________

- [ ] Suppressed: bought this product in last 30 days
- [ ] Suppressed: received a campaign in last 5 days
- [ ] Suppressed: unengaged 180d+
- [ ] *(Flash only)* Sending to engaged-90d segment only

---

## 3. Copy

**Subject A:**
**Subject B** *(or "reusing swipe-file winner: ____")*:
**Preview text** (40–90 chars, must not repeat the subject):

**Headline:**
**Subheadline:**

**Body:**
>

**CTA button text:** ________ *(same verb everywhere)*

**Product cards**

| # | Name | One-line benefit | Price | Link |
|---|---|---|---|---|
| 1 | | | | |
| 2 | | | | |
| 3 | | | | |

**Urgency line:** "Offer ends ____"

---

## 4. Assets & Links

| Asset | Source | Committed | Under weight |
|---|---|---|---|
| Hero 1200×800 (≤150 KB) | Canva / `attractions/` | ☐ | ☐ |
| Header 1200×400 (≤40 KB) | reused | ☐ | ☐ |
| Cards 580×580 (≤80 KB each) | `attractions/` | ☐ | ☐ |

**Git tag:** `campaign/{yyyy}-{code}`
**CDN base:** `https://cdn.jsdelivr.net/gh/kennethtablang/assets-attractions@{tag}/...`

**Landing page:** ________________ *(must already exist)*
**UTM:** `utm_source=mailchimp&utm_medium=email&utm_campaign={code}_{yyyy}&utm_content=hero_cta`
- [ ] UTM registered in the registry tab

---

## 5. QA  ⛔ GATE — nothing below is skippable

### The five non-negotiables
- [ ] **Margin** checked against the approved band
- [ ] **Availability** confirmed, no blackouts this window
- [ ] **Every price and date** matches §1 exactly — read twice
- [ ] **Every link clicked**, not spot-checked
- [ ] **Real end-to-end test booking completed, promo code applied**

### Content
- [ ] Attraction names spelled correctly (check the supplier's own site)
- [ ] Discount maths correct
- [ ] `AED 199` format used consistently
- [ ] No placeholder text left (`XXX`, `[insert]`, `TBC`, `{{`)
- [ ] Read aloud once, end to end

### Build
- [ ] Sender name `Dubai Ticket Magic`, monitored reply-to
- [ ] Preview text set
- [ ] Correct segment, count recorded: ________
- [ ] All links carry the UTM; `utm_content` differs per position
- [ ] Clicked a link → **confirmed in GA4 Realtime**
- [ ] Alt text on every image
- [ ] Images load from the **pinned tag**, not `@main`
- [ ] Total HTML under 100 KB
- [ ] Unsubscribe link present and visible

### Render
- [ ] Test sent to 4 real inboxes (2 minimum for flash), one mobile-only
- [ ] Checked on a real phone
- [ ] Merge tag fallback set (no "Hi ,")

### Pre-send
- [ ] Timezone Asia/Dubai
- [ ] Not Friday afternoon, not a public holiday
- [ ] No other campaign to this segment within 5 days

**Reviewed by:** ____________  **Time:** ________

---

## 6. Post-send

| When | Check | Value | OK |
|---|---|---|---|
| T+30m | Delivery ≥98% | | ☐ |
| T+30m | Bounce <2% | | ☐ |
| T+30m | GA4 Realtime, correct UTM | | ☐ |
| T+2h | CTR | | ☐ |
| T+2h | Complaints <0.05% | | ☐ |
| T+24h | Conversions | | ☐ |

**Stop everything if:** bounce >5% · complaints >0.1% · zero clicks at 2h with normal opens

---

## 7. Close (within 3 days)

- [ ] Register row updated with results
- [ ] Winning subject line → swipe file
- [ ] New assets → `attractions/` library

**Three lines of lessons:**
1.
2.
3.
