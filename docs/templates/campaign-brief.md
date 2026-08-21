# Campaign Brief — [CAMPAIGN NAME]

> Copy this file to `campaigns/{yyyy}/{mm}-{campaign-slug}/brief.md` and fill it in.
> The brief is not complete until §4 names **one** KPI with **one** number.

| | |
|---|---|
| **Campaign ID** | DTM-2026-MM-CODE |
| **Campaign code** | `code` (matches UTM root) |
| **Track** | B2C / B2B / Both |
| **Type** | seasonal / promo / product-launch / always-on / b2b |
| **Owner** | |
| **Priority score** | /58 |
| **Status** | IDEA |
| **Created** | YYYY-MM-DD |

---

## 1. Research Summary
*(Stage 1 — cap at 90 minutes)*

**Demand trend (Google Trends, UAE, 12m):** rising / flat / falling —
**Top organic queries (Search Console):**
1.
2.
3.

**Competitor pricing** *(record the date — prices go stale)*

| Competitor | Product | Price (AED) | Inclusions | Cancellation | Checked |
|---|---|---|---|---|---|
| | | | | | |
| | | | | | |
| | | | | | |

**Competitor ads currently running (Meta Ad Library):**
- Hook:
- Hook:

**Five audience insights:**
1.
2.
3.
4.
5.

**Three positioning angles considered:**
1.
2.
3.

**Insight that changed the offer:**

---

## 2. Offer & Margin
*(Stage 2 — GATE: requires commercial sign-off)*

**Offer mechanic:** discount % / bundle / kids-go-free / BOGO / added-value / urgency-only
**Offer statement (customer-facing, verbatim):**
>

**Valid:** YYYY-MM-DD → YYYY-MM-DD
**Promo code:**
**Terms & conditions:**

| Product | Net Cost | RRP | Campaign Price | Unit Margin AED | Margin % | Forecast Units | Forecast Revenue | Forecast GP |
|---|---|---|---|---|---|---|---|---|
| | | | | | | | | |
| | | | | | | | | |
| **TOTAL** | | | | | | | | |

**Margin floor:** ____%
**Stress test at 50% of forecast volume — still profitable?** Yes / No
**VAT (5%) treatment confirmed:** ☐
**Commercial sign-off:** ______________  Date: __________

---

## 3. Inventory & Supplier Confirmation
*(Stage 3 — GATE: no unconfirmed product may be promoted)*

| Product | Supplier | Contact | Confirmed? | Price valid to | Blackout dates | Image rights | Date |
|---|---|---|---|---|---|---|---|
| | | | ☐ | | | ☐ | |
| | | | ☐ | | | ☐ | |

☐ Booking system reflects campaign price
☐ Promo code tested with a real end-to-end booking
☐ Blackout dates reflected in landing page T&Cs

---

## 4. Objective & KPI
*(Stage 4 — GATE: one KPI, one number)*

**Primary KPI:**
**Target:**
**Deadline:**

> Write it as one sentence:
> "___ [metric] of ___ [number], at ___ [quality bar], from ___ [source], by ___ [date]."

**Secondary metrics (tracked, not optimised for):**
-
-

---

## 5. Audience
*(Stage 5)*

**Track:** B2C / B2B

### B2C segments

| Segment | Mailchimp segment name | Size | Rationale |
|---|---|---|---|
| | | | |
| | | | |

**Suppressions applied:**
- ☐ Purchasers of the same product in the last 30 days
- ☐ Anyone who received a campaign in the last 5 days
- ☐ Unengaged 180d+
- ☐ Hard bounces
- ☐ Other:

**Total addressable for this send:** ________

### B2B ICP *(if applicable)*

| Filter | Value |
|---|---|
| Person location | |
| Industry | |
| Employee count | |
| Job titles (exact) | |
| Seniority | |
| Email status | Verified only |
| Exclusions | |
| Apollo saved list name | `ICP-{segment}-{emirate}-{yyyymm}` |
| Target contact count | |
| Cold outreach tool + sending domain | |

---

## 6. Message & Content Strategy
*(Stage 8)*

**Core message (one sentence):**
> For [audience], [offer] is the [category] that [benefit], because [proof]. Book by [deadline].

**Three proof points, ranked:**
1.
2.
3.

**Emotional angle:** escape / family time / value / novelty / status / urgency

**Primary CTA (identical verb everywhere):**

**Channel content map:**

| Channel | Content required | Owner | Due |
|---|---|---|---|
| Email | Subject A/B, preview, hero copy, 3–6 cards, CTA | | |
| Landing page | Headline, benefits, product blocks, FAQ, T&Cs | | |
| Instagram feed | 3 captions | | |
| Instagram story | 2 frames | | |
| WhatsApp | 2 variants | | |
| Website banner | Headline + CTA | | |

---

## 7. Assets Required
*(Stage 10 — see Appendix B of the MCOS for specs)*

| Asset | Dimensions | Max weight | Filename | Status |
|---|---|---|---|---|
| Email header | 1200×400 | 40 KB | `{code}-{yyyy}-email-header-1200x400.png` | ☐ |
| Email hero | 1200×800 | 150 KB | `{code}-{yyyy}-email-hero-{desc}-1200x800.jpg` | ☐ |
| Product cards ×__ | 580×580 | 80 KB | `{code}-{yyyy}-email-card-{product}-580x580.jpg` | ☐ |
| Web banner | 1920×600 | 200 KB | `{code}-{yyyy}-web-banner-1920x600.jpg` | ☐ |
| IG feed | 1080×1350 | 300 KB | `{code}-{yyyy}-ig-feed-1080x1350.jpg` | ☐ |
| IG story | 1080×1920 | 300 KB | `{code}-{yyyy}-ig-story-1080x1920.jpg` | ☐ |
| OG image | 1200×630 | 150 KB | `{code}-{yyyy}-og-1200x630.jpg` | ☐ |

**Asset repo path:** `campaigns/{yyyy}/{mm}-{slug}/`
**Git tag at asset freeze:** `campaign/{yyyy}-{code}`
**CDN base URL:** `https://cdn.jsdelivr.net/gh/kennethtablang/assets-attractions@{tag}/campaigns/...`

---

## 8. Tracking

| Parameter | Value |
|---|---|
| `utm_campaign` | `{code}_{yyyy}` |
| Landing page URL | |
| GA4 conversion event | |
| Registered in UTM Registry | ☐ |

**Planned `utm_content` values:**
- `hero_cta`
- `card_{product}`
- `footer_cta`
- `resend_hero_cta`
- `story_swipeup`

---

## 9. Schedule

| Stage | Date | Owner | Done |
|---|---|---|---|
| Research | | | ☐ |
| Offer approved | | | ☐ |
| Suppliers confirmed | | | ☐ |
| Copy complete | | | ☐ |
| Design complete | | | ☐ |
| Landing page live | | | ☐ |
| Email built | | | ☐ |
| QA signed | | | ☐ |
| **SEND** | **____ 17:00–19:00 GST** | | ☐ |
| Resend to non-openers | +48–72h | | ☐ |
| Campaign end | | | ☐ |
| Analytics pulled | +3–7d | | ☐ |
| Post-mortem | +7d | | ☐ |

**Send-date sanity check:** ☐ Not a Friday ☐ Not a UAE public holiday ☐ No other campaign to this segment within 5 days ☐ Mailchimp timezone = Asia/Dubai

---

## 10. Budget

| Line | Planned AED | Actual AED |
|---|---|---|
| Paid social | | |
| Paid search | | |
| Design/production | | |
| Tools | | |
| **Total** | | |

---

## 11. Risks

| Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|
| | | | |
