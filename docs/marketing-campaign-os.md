# Dubai Ticket Magic — Marketing Campaign Operating System (MCOS)

**Version:** 1.0
**Owner:** Kenneth Tablang
**Last updated:** 2026-08-07
**Scope:** B2C attraction/experience ticket sales + B2B group and trade sales, UAE market.

---

## 1. Executive Summary

### What this system is

A two-track campaign pipeline (B2C and B2B) built almost entirely on tools you already pay nothing for, with a fixed 10-working-day sprint, one campaign register, one naming convention, and five things automated. Everything else stays manual on purpose.

### The five decisions that define the system

**1. Split the pipeline into B2C and B2B tracks. This is the biggest correction to your proposed structure.**
Your draft pipeline puts *Lead Generation → Lead Cleaning* as mandatory stages between Audience and Content. That is a B2B sequence. Roughly 90% of your revenue is B2C ticket sales to tourists and UAE residents, where there is no "lead generation" stage at all — there is *audience segmentation of an existing opt-in list* plus *paid/organic traffic acquisition*. Forcing every campaign through Apollo will waste days per campaign and produce nothing. The corrected pipeline has a shared spine with a fork at Stage 4.

**2. Never send Apollo-sourced contacts through Mailchimp. This is an account-termination risk, not a best practice.**
Mailchimp's Terms of Use prohibit lists that were purchased, rented, scraped, or otherwise collected without explicit opt-in. Apollo contacts are none of those things — they are cold, third-party-sourced B2B contacts. Uploading them to Mailchimp risks: (a) account suspension with no export, (b) permanent damage to your sending domain reputation, which then poisons your legitimate B2C list. Separate the two systems completely — see §7.3. This single mistake can destroy a year of list-building, and it is the most common way small teams blow themselves up.

**3. Demote open rate. It is no longer a real metric.**
Apple Mail Privacy Protection (and now Gmail/Yahoo image proxying) pre-fetches tracking pixels, so a large share of your "opens" are machines. Open rate is now useful only for *relative* A/B subject-line comparison within a single send. Your primary email KPIs are **CTR, click-to-open rate, and conversion rate**. Judging campaigns on opens will lead you to the wrong conclusions consistently.

**4. Use two repositories, not one.**
`assets-attractions` is public. That is correct and necessary — public is what lets you serve images free over the jsDelivr CDN into Mailchimp emails. But it also means anything you put there is world-readable: margins, supplier pricing, contact lists, campaign strategy, API keys. Split into a public asset repo and a private ops repo. See §8.

**5. Fix the image pipeline before the next campaign.**
Your current summer assets are 680–850 KB each. Gmail clips emails over ~102 KB of HTML and slow-loading images tank mobile engagement in a market where a lot of your traffic is on mobile data. Target: hero ≤150 KB, cards ≤80 KB. This is a 20-minute fix with Squoosh and a permanent fix with a GitHub Action. See §10.

### What you should NOT build

Do not build a custom CRM, a custom email sender, a custom analytics platform, or a UTM-builder web app. Free tools cover all four. Your C#/.NET skill has exactly three high-value applications in this system, listed in §10.

---

## 2. Complete Marketing Pipeline

### 2.1 The corrected pipeline

```
                          ┌─────────────────────────────┐
                          │  STAGE 0: CAMPAIGN INTAKE   │
                          │  Idea → Priority Score      │
                          │  Gate: score ≥ 40           │
                          └──────────────┬──────────────┘
                                         ↓
                          ┌─────────────────────────────┐
                          │  1. RESEARCH                │
                          │  Market, competitor, demand │
                          └──────────────┬──────────────┘
                                         ↓
                          ┌─────────────────────────────┐
                          │  2. OFFER & MARGIN DESIGN   │  ◄── NEW STAGE
                          │  What we sell, at what      │
                          │  price, at what margin      │
                          │  Gate: margin approved      │
                          └──────────────┬──────────────┘
                                         ↓
                          ┌─────────────────────────────┐
                          │  3. INVENTORY & SUPPLIER    │  ◄── NEW STAGE
                          │  Confirm availability,      │
                          │  price validity, blackouts  │
                          │  Gate: supplier confirmed   │
                          └──────────────┬──────────────┘
                                         ↓
                          ┌─────────────────────────────┐
                          │  4. CAMPAIGN PLANNING       │
                          │  Brief, dates, budget, KPI  │
                          └──────────────┬──────────────┘
                                         ↓
                          ┌─────────────────────────────┐
                          │  5. AUDIENCE DEFINITION     │
                          └──────────────┬──────────────┘
                                         ↓
                    ┌────────────────────┴────────────────────┐
                    ↓                                         ↓
        ╔═══════════════════════╗              ╔═══════════════════════╗
        ║   B2C TRACK           ║              ║   B2B TRACK           ║
        ║   (default, ~90%)     ║              ║   (group/trade sales) ║
        ╠═══════════════════════╣              ╠═══════════════════════╣
        ║ 5a. Segment existing  ║              ║ 5b. Apollo ICP build  ║
        ║     Mailchimp list    ║              ║ 6b. Lead generation   ║
        ║ 6a. Plan traffic      ║              ║ 7b. Clean + validate  ║
        ║     (organic/paid/    ║              ║ 8b. Load to COLD      ║
        ║      social/WhatsApp) ║              ║     OUTREACH tool     ║
        ║                       ║              ║     (never Mailchimp) ║
        ╚═══════════╤═══════════╝              ╚═══════════╤═══════════╝
                    └────────────────────┬────────────────────┘
                                         ↓
                          ┌─────────────────────────────┐
                          │  8. CONTENT STRATEGY        │
                          │  Message, angle, hierarchy  │
                          └──────────────┬──────────────┘
                                         ↓
                          ┌─────────────────────────────┐
                          │  9. COPYWRITING             │
                          │  ChatGPT draft → Claude     │
                          │  refine (see §6)            │
                          └──────────────┬──────────────┘
                                         ↓
                          ┌─────────────────────────────┐
                          │ 10. CREATIVE DESIGN         │
                          │  Canva → compress → GitHub  │
                          └──────────────┬──────────────┘
                                         ↓
                          ┌─────────────────────────────┐
                          │ 11. LANDING PAGE            │
                          │  Build + tracking installed │
                          └──────────────┬──────────────┘
                                         ↓
                          ┌─────────────────────────────┐
                          │ 12. EMAIL BUILD             │
                          └──────────────┬──────────────┘
                                         ↓
                          ┌─────────────────────────────┐
                          │ 13. QA & TESTING            │
                          │  Gate: full checklist green │
                          └──────────────┬──────────────┘
                                         ↓
                          ┌─────────────────────────────┐
                          │ 14. LAUNCH                  │
                          └──────────────┬──────────────┘
                                         ↓
                          ┌─────────────────────────────┐
                          │ 15. MONITORING (0–72h)      │
                          │  Deliverability, errors     │
                          └──────────────┬──────────────┘
                                         ↓
                          ┌─────────────────────────────┐
                          │ 16. IN-FLIGHT OPTIMIZATION  │  ◄── MOVED EARLIER
                          │  Resend to non-openers,     │
                          │  fix broken things, shift   │
                          │  budget while campaign LIVE │
                          └──────────────┬──────────────┘
                                         ↓
                          ┌─────────────────────────────┐
                          │ 17. ANALYTICS (post-close)  │
                          └──────────────┬──────────────┘
                                         ↓
                          ┌─────────────────────────────┐
                          │ 18. POST-MORTEM & ARCHIVE   │
                          │  Report + asset archive +   │
                          │  register row closed        │
                          └──────────────┬──────────────┘
                                         ↓
                          ┌─────────────────────────────┐
                          │ 19. FEED THE BACKLOG        │  ◄── NEW STAGE
                          │  Lessons → next intake      │
                          └─────────────────────────────┘
```

### 2.2 What changed from your draft and why

| Change | Reason |
|---|---|
| Added **Stage 0: Intake with priority scoring** | Without a gate, every idea becomes a campaign and you run out of weeks. Forces a decision before work starts. |
| Added **Offer & Margin Design** | Tourism runs on thin margins. A 30% discount campaign that sells out and loses money is the classic failure. Margin must be approved before a single word is written. |
| Added **Inventory & Supplier Confirmation** | You resell third-party attractions. Promoting a sold-out or repriced product produces refunds, bad reviews, and supplier friction. Non-negotiable gate. |
| **Forked B2C/B2B at Stage 5** | Lead Generation and Lead Cleaning are B2B-only. Making them mandatory wastes days on every B2C campaign. |
| Moved **Optimization before Analytics** | Your draft optimizes after analysis, i.e. after the campaign is over. Most recoverable value (resend to non-openers, fix a broken link, shift budget) exists in the first 72 hours while the campaign is live. |
| Added **Feed the Backlog** | Closes the loop explicitly, so lessons become scored intake items instead of forgotten notes. |
| Renamed Documentation → **Post-Mortem & Archive** | Documentation is vague. Archiving assets and closing the register row are specific, checkable actions. |

---

## 3. Tool Stack

### 3.1 Evaluation of your current tools

| Tool | Current Use | Recommended Use | Missing Function | Keep/Replace | Free Alternative | Automation Opportunity |
|---|---|---|---|---|---|---|
| **ChatGPT** | Strategy, planning, brainstorm, research, copy, prompts, process | **Divergent work**: idea generation, research synthesis, first-draft copy, variant generation (20 subject lines), data-shaped tasks. Keep as the *volume* tool. | Nothing critical. Don't use for final copy approval. | **Keep** | Claude free tier, Gemini free | Custom GPT holding your brand voice + offer rules, so you stop re-pasting context |
| **Claude** | Long-form, refinement, strategy review, research, critical eval, docs | **Convergent work**: refine and cut copy, red-team the campaign, write SOPs/documentation, review briefs for gaps, structured docs. Also: **Claude Code for the automation in §10.** | Nothing critical | **Keep** | ChatGPT | Claude Code writing the C# cleaner, GitHub Actions, and Looker Studio setup |
| **Apollo** | B2B lead gen, contact discovery | **B2B track only.** Corporate group bookings, DMCs, travel agencies, hotel concierge, HR/admin heads for staff outings, event planners. Never for B2C. | Not a CRM, not an email verifier you should fully trust, not a Mailchimp source | **Keep, but narrow scope** | LinkedIn Sales Nav (paid), Hunter.io free (25/mo) | CSV → C# cleaner → cold outreach tool (§10) |
| **Canva** | All graphics | Same, plus: **build a locked Brand Kit and 8 campaign templates** so each campaign is a text/image swap, not a redesign. | Automatic image compression (Canva exports are heavy) | **Keep** | Figma free, Photopea | Canva Bulk Create from CSV for multi-attraction cards; Squoosh/GitHub Action for compression |
| **Mailchimp** | Email, audience, automation, analytics | **Opt-in B2C email only.** Plus 3 always-on automations (welcome, browse/abandon, post-visit). | Free tier: no A/B testing on Free plan, 500 contacts / 1,000 sends per month cap, no scheduling on Free | **Keep — but you will outgrow the Free tier fast.** See note below. | MailerLite free (1,000 contacts, 12k sends, **includes automation + A/B**), Brevo free (300/day unlimited contacts) | API → campaign register sync; automations |
| **GitHub** | Asset + code storage, version control | **Split into two repos.** Public = images served via jsDelivr CDN. Private = docs, data, code, reports. Add GitHub Projects as your campaign board. | Project management (available free, unused); image optimization | **Keep, restructure** | — (nothing beats free private repos + CDN) | GitHub Actions: image compression, link checking, asset manifest generation |
| **Visual Studio** | Dev, landing pages, .NET, backend | Landing pages + **three internal tools only** (§10). Resist building more. | — | **Keep, narrow scope** | VS Code (lighter for HTML/CSS work) | — |

> **Mailchimp Free tier reality check:** 500 contacts and 1,000 monthly sends will not run a UAE B2C tourism list, and A/B testing and scheduling are gated. Either budget for Mailchimp Essentials (~$13/mo at low volume) or move to **MailerLite free**, which gives 1,000 contacts, 12,000 monthly emails, automation, and A/B testing at zero cost. If you have fewer than ~800 contacts today, migrating to MailerLite now is cheaper and *more* capable. If your list is already large and warm in Mailchimp, pay for Mailchimp rather than risk a migration hurting deliverability. Decide this in Week 1 — it changes nothing else in this system.

### 3.2 Recommended additions

#### ESSENTIAL — implement in the first 30 days

| Tool | What it does | Why you need it | Stage | Free limits | Connects to |
|---|---|---|---|---|---|
| **Google Analytics 4** | Website + conversion analytics | You currently cannot answer "did the email produce bookings?" Nothing else in the stack can. | 11, 15, 17 | Free, generous | UTMs from Mailchimp; Looker Studio |
| **Microsoft Clarity** | Heatmaps + session recordings | 100% free, unlimited, no sampling. Shows *why* a landing page fails, which GA4 never will. Beats Hotjar's free tier outright. | 11, 16 | Genuinely unlimited | One script tag next to GA4 |
| **Looker Studio** | Dashboards / reporting | Turns GA4 + a Google Sheet into a one-page campaign dashboard. Kills manual reporting. | 17, 18 | Free | GA4 connector, Sheets connector |
| **Google Sheets** | Campaign register, UTM registry, list staging | The spine of the system. Everything references it. | All | Free | Everything |
| **Squoosh** (then a GitHub Action) | Image compression | Your assets are 680–850 KB. Must be ≤150 KB. | 10 | Free, browser-based | Manual now, Action later |
| **jsDelivr** | Free CDN over your public GitHub repo | Serves email images fast and globally without `raw.githubusercontent.com` rate limits. | 10, 12 | Free, no signup | `cdn.jsdelivr.net/gh/user/repo@tag/path` |
| **GitHub Projects** | Campaign kanban board | Free, already in your stack, sits next to the assets. No new SaaS. | 0, 4, all | Free | Issues, repos |
| **Google Search Console** | Organic search performance | Free demand signal for what UAE users actually search for. Feeds Stage 1 research. | 1, 17 | Free | GA4, Looker Studio |

#### USEFUL — months 2–3

| Tool | What it does | Why | Free limits |
|---|---|---|---|
| **Meta Business Suite** | Schedule IG/FB, free | You will post organically; scheduling saves 2h/week | Free |
| **Meta Ad Library** | See every ad competitors run in UAE | Free competitive intelligence on Platinumlist, Headout, Klook, GetYourGuide, Musement | Free, no login |
| **Google Trends** | Seasonality + query demand by UAE region | Validates campaign timing (e.g. when "things to do in Dubai" spikes) | Free |
| **HubSpot Free CRM** | B2B pipeline tracking | Only when B2B leads exceed what a Sheet can track (~roughly 100+ active) | Free forever, 1M contacts |
| **Tally** or **Google Forms** | Forms / lead capture | Group booking enquiry forms on landing pages | Tally free tier is very generous |
| **MillionVerifier / ZeroBounce** | Email verification | Only for the B2B cold list. Not needed for opt-in B2C. | ZeroBounce 100 free/mo; MillionVerifier ~$0.0004/email |
| **OpenRefine** | Bulk data cleaning, fuzzy dedupe | Free, open source, better than Sheets for messy Apollo exports — until your C# tool replaces it | Free, self-hosted |

#### OPTIONAL — only if a specific pain appears

| Tool | When to add |
|---|---|
| **n8n (self-hosted)** | Only when you have 3+ recurring integrations to wire. Free and open source, but it's a server to maintain. Don't add it in month 1. |
| **Buffer / Later free** | Only if you post to channels Meta Business Suite doesn't cover (LinkedIn, TikTok) |
| **Ahrefs Webmaster Tools** | Free for your own verified site; add when SEO becomes a priority channel |
| **Short.io / YOURLS** | Only for print, WhatsApp, and offline QR codes. Do not shorten email links — it hurts deliverability. |
| **Plausible / Umami** | Self-hosted analytics; only if GA4's complexity becomes a real blocker |

**Deliberately not recommended:** Zapier (free tier too thin at 100 tasks), Hotjar (Clarity is free and better), Notion (GitHub Projects covers it, avoid a second home for truth), Trello (same), Semrush/Ahrefs paid (not justified at this stage), any all-in-one "marketing platform."

---

## 4. Detailed Workflow

Every stage below uses the same 13-field format. **Owner** assumes a one-person operation with an optional designer/dev; adjust names to your team.

---

### STAGE 0 — CAMPAIGN INTAKE

| Field | Detail |
|---|---|
| **Purpose** | Stop bad campaigns before they consume a sprint. |
| **Objective** | Convert a raw idea into a scored, ranked backlog item with a go/no-go decision. |
| **Inputs** | Idea (from anywhere: seasonality calendar, supplier offer, sales request, last campaign's lessons) |
| **Tasks** | 1. Create a GitHub Issue from the `campaign-idea` template. 2. Fill the 7 scoring criteria (§12). 3. Compute score. 4. Label `go` / `queue` / `parked`. 5. If `go`, assign a Campaign ID and add a row to the Campaign Register. |
| **Tool** | GitHub Projects + Issues |
| **Free alt** | Google Sheets tab |
| **Exact work** | Score each of 7 criteria 1–5. Apply the formula. ≥40 = run this quarter. 25–39 = queue. <25 = park with a one-line reason. |
| **Output** | Scored issue + Campaign ID + register row with status `IDEA` |
| **Owner** | Marketing Lead (you) |
| **QC checklist** | ☐ All 7 criteria scored ☐ Revenue potential based on a real number, not a feeling ☐ Effort score includes asset creation ☐ Doesn't collide with another live campaign to the same segment |
| **Automation** | GitHub Issue template with the scoring table pre-filled; a simple formula in the register |
| **Common mistakes** | Scoring your favourite idea generously; ignoring effort; running two campaigns at the same list in the same week |
| **KPI** | % of started campaigns that reach LIVE (target ≥90% — if lower, your intake gate is too loose) |

---

### STAGE 1 — RESEARCH

| Field | Detail |
|---|---|
| **Purpose** | Ground the campaign in real demand and real competitive pricing rather than assumption. |
| **Objective** | Produce a 1-page research note answering: who wants this now, what do competitors charge, what language do they use, what is the demand trend. |
| **Inputs** | Campaign idea, Campaign ID |
| **Tasks** | 1. Google Trends: search the core term (e.g. "desert safari Dubai") filtered to UAE, past 12 months — note the seasonal shape. 2. Google Search Console: pull your own top queries and impressions for related pages. 3. Meta Ad Library: search Platinumlist, Headout, Klook, GetYourGuide, Musement, Tripadvisor Experiences — screenshot the ads currently running in UAE, note offers and hooks. 4. Direct price check: open 3 competitor product pages, record price, inclusions, cancellation policy. 5. Review your own last 3 campaign post-mortems for the same audience. 6. ChatGPT: synthesise into 5 audience insights + 3 positioning angles. |
| **Tool** | Google Trends, Search Console, Meta Ad Library, ChatGPT |
| **Free alt** | All already free |
| **Exact work** | Fill the Research section of `campaign-brief.md`. Cap at 90 minutes. Research is the easiest stage to over-invest in. |
| **Output** | `research-note.md` in the campaign folder + competitor price table |
| **Owner** | Marketing Lead |
| **QC checklist** | ☐ At least 3 competitor prices recorded with date ☐ Trend direction stated (rising/flat/falling) ☐ At least one insight that would change the offer ☐ Sources dated (prices go stale) |
| **Automation** | Google Alerts on competitor names; Trends email digest. Do **not** build a scraper — competitor ToS and maintenance cost aren't worth it. |
| **Common mistakes** | Researching for days; researching *after* the offer is already decided; copying competitor pricing without knowing their cost base |
| **KPI** | Research → brief cycle time (target ≤1 working day) |

---

### STAGE 2 — OFFER & MARGIN DESIGN *(new)*

| Field | Detail |
|---|---|
| **Purpose** | Ensure the campaign can make money before anyone writes copy. |
| **Objective** | A specific, defensible offer with an approved margin floor. |
| **Inputs** | Research note, supplier cost sheet, historical conversion data |
| **Tasks** | 1. List candidate products with net cost, RRP, and current margin %. 2. Model the offer: what discount / bundle / added value. 3. Compute post-discount margin per unit and required volume to hit the revenue target. 4. Stress-test: what happens at 50% of forecast volume. 5. Choose the offer mechanic — discount %, bundle, kids-go-free, buy-one-get-one, added value (free transfer, free photo), or urgency-only (no discount). 6. Set the margin floor and write it down. |
| **Tool** | Google Sheets |
| **Free alt** | Excel |
| **Exact work** | Fill this table for every product in the campaign: `Product | Net Cost | RRP | Campaign Price | Unit Margin AED | Margin % | Forecast Units | Forecast Revenue | Forecast GP`. If total forecast GP < the cost of running the campaign, redesign the offer. |
| **Output** | Approved offer sheet with margin floor |
| **Owner** | Marketing Lead + Commercial/Owner sign-off |
| **QC checklist** | ☐ Every product has a net cost, not an assumed one ☐ Margin % after discount ≥ floor ☐ VAT treatment correct (UAE 5%) ☐ Offer is genuinely better than your everyday price ☐ Offer end date set ☐ Terms & conditions drafted (blackout dates, validity, non-refundable) |
| **Automation** | Sheet template with formulas; do not automate the decision |
| **Common mistakes** | Discounting the highest-margin product because it's easiest to sell; forgetting VAT; "20% off everything" with no margin check; no T&Cs, then arguing with customers later |
| **KPI** | Realised gross margin % vs planned (target within 3 points) |

---

### STAGE 3 — INVENTORY & SUPPLIER CONFIRMATION *(new)*

| Field | Detail |
|---|---|
| **Purpose** | Never promote something you cannot deliver. |
| **Objective** | Written confirmation of availability, price validity, and blackout dates for every promoted product across the campaign window. |
| **Inputs** | Approved offer sheet |
| **Tasks** | 1. Email each supplier/attraction: confirm price validity through [end date], allocation available, blackout dates, cancellation terms, and permission to use their imagery. 2. Log responses. 3. Confirm your own booking system reflects the campaign price and any promo code works. 4. Confirm image usage rights in writing — attractions are strict about brand assets. |
| **Tool** | Gmail + Google Sheets tracker |
| **Free alt** | Same |
| **Exact work** | One row per product: `Product | Supplier | Contact | Confirmed? | Price valid to | Blackouts | Image rights | Date confirmed`. No row goes to content without `Confirmed = Yes`. |
| **Output** | Signed-off inventory sheet |
| **Owner** | Operations / Marketing Lead |
| **QC checklist** | ☐ Every promoted product confirmed in writing ☐ Blackout dates reflected in landing page T&Cs ☐ Promo code tested end-to-end with a real test booking ☐ Image rights confirmed |
| **Automation** | Template email; **do not automate supplier relationships** |
| **Common mistakes** | Assuming last season's price holds; promoting during a blackout (Eid, National Day, school holidays are the exact periods attractions restrict); using an attraction's photo without permission |
| **KPI** | Fulfilment failure rate (target 0); refund rate caused by availability (target 0) |

---

### STAGE 4 — CAMPAIGN PLANNING

| Field | Detail |
|---|---|
| **Purpose** | Turn an approved offer into an executable plan with dates, owners, and success criteria. |
| **Objective** | A completed campaign brief that anyone could execute from. |
| **Inputs** | Research note, offer sheet, inventory sheet |
| **Tasks** | 1. Copy `docs/templates/campaign-brief.md` into the campaign folder. 2. Set Campaign ID, name, type, objective, start/end dates, send date/time. 3. Define the single primary KPI and its target number. 4. Define channels and budget. 5. Assign the UTM campaign value (§9) and register it. 6. Build the asset list. 7. Set the sprint dates against the 10-day calendar (§12). |
| **Tool** | GitHub (private repo) + Campaign Register |
| **Free alt** | Google Docs |
| **Exact work** | The brief is not done until it names **one** primary KPI with **one** target number. "Increase awareness and drive bookings" is not a brief. "180 bookings at ≥AED 22 average GP, from a 4,200-contact send + organic social, by 31 Aug" is a brief. |
| **Output** | Completed brief; register status → `PLANNING` |
| **Owner** | Marketing Lead |
| **QC checklist** | ☐ One primary KPI with a number ☐ Start and end dates ☐ Send date avoids Friday and public holidays ☐ UTM campaign value registered and unique ☐ Budget stated (even if AED 0) ☐ Every asset listed with a spec ☐ Landing page URL decided |
| **Automation** | C# `CampaignScaffold` tool creates the folder, copies templates, appends the register row (§10) |
| **Common mistakes** | Multiple "primary" KPIs; no end date so the campaign never closes; sending on a UAE public holiday or Friday |
| **KPI** | Brief completeness score; % campaigns launched on the planned date |

---

### STAGE 5 — AUDIENCE DEFINITION

| Field | Detail |
|---|---|
| **Purpose** | Send the right offer to the right people; suppress the wrong ones. |
| **Objective** | Named, sized, documented segments with inclusion and exclusion rules. |
| **Inputs** | Brief, Mailchimp audience data, past campaign engagement |
| **Tasks (B2C)** | 1. Define segments from tags and behaviour. 2. Size each segment in Mailchimp. 3. Define **suppressions** — this is the step everyone skips: recent purchasers of the same product, people who received a campaign in the last 5 days, unengaged contacts (no open/click in 180 days), and hard bounces. 4. Decide send order/waves. |
| **Tasks (B2B)** | Define the Ideal Customer Profile: industry, company size, seniority, job titles, location. Proceed to §5 (Apollo). |
| **Tool** | Mailchimp segments/tags; Apollo for B2B |
| **Free alt** | MailerLite segments |
| **Exact work (B2C segments to build once, reuse forever)** | `residents-uae`, `tourists-inbound`, `families-with-kids`, `couples`, `adventure-seekers`, `dining-lovers`, `wellness`, `budget-under-100`, `premium`, `lapsed-180d`, `vip-repeat-3plus`, `b2b-trade`. Tag on signup and after every purchase. |
| **Output** | Segment definition table with counts |
| **Owner** | Marketing Lead / CRM |
| **QC checklist** | ☐ Segment sizes recorded (pre-send, for the post-mortem) ☐ Suppression list applied ☐ No contact receives two campaigns within 5 days ☐ Unengaged 180d+ excluded from broad sends ☐ Consent source known for every included contact |
| **Automation** | Mailchimp auto-tagging on purchase via API/webhook; saved segments reused |
| **Common mistakes** | Blasting the whole list every time (fastest route to spam complaints and deliverability collapse); no suppression of recent buyers, who then see a lower price than they paid; emailing dead contacts, which drags your sender reputation down |
| **KPI** | Unsubscribe rate <0.3%; spam complaint rate <0.05%; segment-level CTR spread |

---

### STAGE 6 — LEAD GENERATION *(B2B track only)*

Fully specified in **§5 — Apollo Lead Generation System**.

| Field | Detail |
|---|---|
| **Purpose** | Build a qualified list of UAE decision-makers who book groups. |
| **Objective** | 300–800 verified, relevant contacts per B2B campaign. |
| **Owner** | Marketing Lead |
| **KPI** | Valid email rate ≥95%; reply rate ≥3%; meetings booked |

---

### STAGE 7 — LEAD CLEANING & VALIDATION *(B2B track only)*

| Field | Detail |
|---|---|
| **Purpose** | Protect deliverability and stop wasting sends on junk. |
| **Objective** | A clean, deduplicated, verified CSV ready for cold outreach. |
| **Inputs** | Apollo CSV export |
| **Tasks** | 1. Normalise casing and whitespace. 2. Deduplicate by email, then by company+name. 3. Strip role-based addresses (`info@`, `sales@`, `admin@`, `contact@`, `hello@`) unless deliberately targeted. 4. Strip free-mail domains for B2B (`gmail`, `hotmail`, `yahoo`) — usually noise in a corporate list. 5. Score title relevance; drop non-matches. 6. Verify emails; drop invalid, keep catch-all in a separate low-priority file. 7. Populate merge fields: `FNAME`, `COMPANY`, `TITLE`, `CITY`. 8. Export to the cold-outreach tool's format. |
| **Tool** | **C# `ApolloCleaner` console app** (§10) — this is your highest-value custom build |
| **Free alt** | OpenRefine, or Google Sheets formulas |
| **Exact work** | Run `ApolloCleaner --in raw.csv --out clean.csv --titles titles.txt --region AE`. Review the rejects file manually — that's where you catch a bad filter. |
| **Output** | `clean.csv`, `rejects.csv`, cleaning summary |
| **Owner** | Marketing Lead |
| **QC checklist** | ☐ 0 duplicate emails ☐ 0 role-based addresses ☐ Verification pass rate ≥95% ☐ Random sample of 10 rows manually checked against LinkedIn ☐ Merge fields populated with no blanks (blank `FNAME` produces "Hi ,") |
| **Automation** | The C# tool + a verification API call in the same pass |
| **Common mistakes** | Trusting Apollo's verification blindly; leaving blank merge fields; keeping catch-all domains in the main send |
| **KPI** | Bounce rate <2%; % rows discarded (track it — a sudden jump means your Apollo filters drifted) |

---

### STAGE 8 — CONTENT STRATEGY

| Field | Detail |
|---|---|
| **Purpose** | Decide what to say and in what order before writing anything. |
| **Objective** | A message hierarchy and channel content map. |
| **Inputs** | Brief, research insights, offer |
| **Tasks** | 1. Write the single core message in one sentence. 2. Rank the 3 supporting proof points. 3. Choose the emotional angle (escape, family time, value, novelty, status, urgency). 4. Map content per channel: email, landing page, IG feed, IG story, WhatsApp, website banner. 5. Define the one primary CTA — same verb everywhere. |
| **Tool** | ChatGPT for options → Claude to pressure-test and choose |
| **Free alt** | Either alone |
| **Exact work** | Complete this: *"For [audience], [offer] is the [category] that [benefit], because [proof]. Book by [deadline]."* If you can't fill it, you don't have a campaign yet. |
| **Output** | Message hierarchy + channel content map |
| **Owner** | Marketing Lead |
| **QC checklist** | ☐ One core message, not three ☐ CTA verb identical across all channels ☐ Offer deadline present ☐ Angle matches the segment (families ≠ couples) ☐ Message differentiates from the competitor ads you screenshotted in Stage 1 |
| **Automation** | Prompt template stored in the private repo |
| **Common mistakes** | Listing 12 attractions with equal weight (the reader picks none); different CTAs per channel; leading with the discount when the experience is the actual draw |
| **KPI** | CTOR (measures message-to-audience fit better than any other single number) |

---

### STAGE 9 — COPYWRITING

Fully specified in **§6 — Content Production System**.

| Field | Detail |
|---|---|
| **Output** | `copy.md` containing: subject lines A/B, preview text, email copy, landing page copy, 3 social captions, 2 WhatsApp messages, all CTAs |
| **QC checklist** | ☐ Reads naturally aloud ☐ No unverifiable claims ☐ Prices and dates match the offer sheet exactly ☐ AED formatted consistently ☐ Deadline stated ☐ T&Cs linked ☐ Spelling of every attraction name verified ☐ No em-dash-heavy AI cadence |
| **KPI** | CTR; subject-line A/B lift |

---

### STAGE 10 — CREATIVE DESIGN

Fully specified in **§11.2 — Design System**.

| Field | Detail |
|---|---|
| **Exact work** | Design in Canva from a locked template → export at 2× → compress in Squoosh to target weight → rename to convention → commit to the public asset repo → generate jsDelivr URLs. |
| **QC checklist** | ☐ Every file ≤ its weight budget ☐ Filenames lowercase-hyphenated, no spaces ☐ Text legible at mobile width ☐ Brand colours/fonts from the Brand Kit ☐ Price shown matches the offer sheet ☐ Logo present and clear ☐ Alt text written for every email image |
| **KPI** | Total email weight <100 KB HTML; largest image ≤150 KB; LCP <2.5s on the landing page |

---

### STAGE 11 — LANDING PAGE

Fully specified in **§9.4 and the QA checklist**.

| Field | Detail |
|---|---|
| **Exact work** | Build or clone the page, install GA4 + Clarity, wire the conversion event, set canonical + OG tags, test on real mobile hardware, run PageSpeed Insights. |
| **QC checklist** | See `docs/templates/campaign-qa-checklist.md` |
| **KPI** | Landing page conversion rate; bounce/engagement rate; LCP |

---

### STAGE 12 — EMAIL BUILD

Fully specified in **§7 — Mailchimp System**.

---

### STAGE 13 — QA & TESTING

| Field | Detail |
|---|---|
| **Purpose** | Catch the errors that cannot be undone once sent. |
| **Objective** | A fully green checklist signed by a second pair of eyes. |
| **Tasks** | 1. Send a test to at least 4 inboxes: Gmail, Outlook, Apple Mail, and one mobile-only. 2. Click **every** link and verify the UTM lands correctly in GA4 Realtime. 3. Verify merge tags with a real test contact — check the fallback text. 4. Check dark mode rendering. 5. Check images-off rendering (alt text must carry the message). 6. Complete a real end-to-end test booking including the promo code. 7. Verify unsubscribe and sender details. 8. Second-person review. |
| **Tool** | Mailchimp Preview + real inboxes; GA4 Realtime |
| **Free alt** | Mail-tester.com (free spam score), Litmus/Email on Acid free trials |
| **Exact work** | Do **not** rely on Mailchimp's preview alone. Send to real inboxes. Most catastrophic email errors — broken merge tags, wrong price, dead link — are invisible in preview. |
| **Output** | Signed QA checklist stored in the campaign folder |
| **Owner** | Marketing Lead + one reviewer |
| **QC checklist** | The full checklist in `docs/templates/campaign-qa-checklist.md` |
| **Automation** | GitHub Action link-checker on the email HTML; mail-tester for spam scoring |
| **Common mistakes** | Testing only in Mailchimp preview; not clicking every link; wrong year in the footer; testing the promo code only in staging |
| **KPI** | Post-send error count (target 0); emergency-resend count (target 0) |

---

### STAGE 14 — LAUNCH

| Field | Detail |
|---|---|
| **Tasks** | 1. Confirm segment count one final time. 2. Confirm send time. 3. Schedule (or send). 4. Publish social posts. 5. Publish website banner. 6. Post in the campaign issue: "LIVE at [time], sent to [n] contacts." 7. Update register to `LIVE`. |
| **Send timing (UAE)** | **B2C:** Thursday 17:00–19:00 GST or Friday 09:00–11:00 GST — catches weekend planning (UAE weekend is Sat–Sun). **B2B:** Tuesday or Wednesday 09:00–11:00 GST. **Avoid:** Friday afternoon (Jumu'ah), public holidays, and the first 2 days of Eid. During Ramadan, shift B2C sends to 20:00–22:00 GST (post-iftar engagement is markedly higher). |
| **Owner** | Marketing Lead |
| **QC checklist** | ☐ Correct segment, verified count ☐ Correct time zone (Mailchimp account TZ set to Asia/Dubai) ☐ Tracking enabled ☐ Social scheduled ☐ Landing page live and tested from a fresh browser ☐ Booking system live with correct price |
| **Common mistakes** | Wrong time zone; scheduling and never confirming it sent; landing page still on staging |
| **KPI** | Delivery rate ≥98%; on-time launch |

---

### STAGE 15 — MONITORING (0–72h)

| Field | Detail |
|---|---|
| **Objective** | Detect and fix problems while they're still fixable. |
| **Tasks** | **T+30min:** delivery rate, bounces, first opens/clicks, GA4 Realtime showing traffic on the right UTM. **T+2h:** CTR trajectory, any spam complaints, landing page errors in Clarity. **T+24h:** full metric set, first conversions, Clarity recordings of non-converters. **T+48–72h:** decide on the resend-to-non-openers. |
| **Tool** | Mailchimp reports, GA4 Realtime, Clarity |
| **Owner** | Marketing Lead |
| **Red flags demanding immediate action** | Bounce >5% (list problem — stop remaining sends), spam complaints >0.1% (stop immediately), delivery <95%, zero clicks after 2h with a normal open count (broken link), GA4 showing traffic with no UTM (tracking broken) |
| **Common mistakes** | Sending and walking away; only checking after the weekend, by which point the recoverable window is gone |
| **KPI** | Time-to-detection of any issue (target <2h) |

---

### STAGE 16 — IN-FLIGHT OPTIMIZATION

| Field | Detail |
|---|---|
| **Objective** | Extract the remaining value while the campaign is live. |
| **Tasks** | 1. **Resend to non-openers** at 48–72h with a different subject line — reliably adds 15–30% of the original opens for near-zero effort. 2. Fix anything broken and, if material, send a correction. 3. Shift paid budget to the best-performing creative. 4. Add urgency messaging in the final 48 hours ("ends Sunday"). 5. Adjust the landing page based on Clarity recordings (a CTA below the fold, a confusing price display). |
| **Tool** | Mailchimp resend-to-non-openers, Clarity, GA4 |
| **Owner** | Marketing Lead |
| **QC checklist** | ☐ Resend uses a genuinely different subject ☐ Resend excludes clickers and purchasers ☐ Resend at least 48h after the original ☐ Correction emails only for material errors (wrong price/date), never for typos |
| **Common mistakes** | Resending the identical email (annoys, doesn't convert); resending too soon; sending "oops" emails for trivial mistakes |
| **KPI** | Incremental conversions from optimization actions |

---

### STAGE 17 — ANALYTICS

Fully specified in **§9.5 — KPI Standards**.

| Field | Detail |
|---|---|
| **When** | 3–7 days after the campaign end date (conversions lag clicks). |
| **Tasks** | Pull Mailchimp report → pull GA4 campaign report → pull booking/revenue data → reconcile → compute CPL, CAC, ROI → identify the best subject line, creative, segment, and product → record everything in the register. |
| **Tool** | Mailchimp reports, GA4, Looker Studio dashboard |
| **QC checklist** | ☐ Attribution window stated (recommend 7-day click) ☐ Revenue reconciled against the booking system, not estimated ☐ Compared against the last comparable campaign ☐ Anomalies explained |
| **Common mistakes** | Reporting opens as the headline; not reconciling to actual revenue; comparing a family campaign to a couples campaign |
| **KPI** | ROI, conversion rate, revenue per email sent |

---

### STAGE 18 — POST-MORTEM & ARCHIVE

| Field | Detail |
|---|---|
| **Tasks** | 1. Complete `campaign-post-mortem.md`. 2. Close the register row with results. 3. Archive final assets in the campaign folder with a git tag. 4. Save winning subject lines and creatives into the swipe file. 5. Log lessons as new intake items. |
| **Owner** | Marketing Lead |
| **QC checklist** | ☐ Report completed within 7 days of close ☐ At least 3 specific lessons ☐ Each lesson has an action owner ☐ Swipe file updated ☐ Git tag created (`campaign/2026-bts`) |
| **Common mistakes** | Skipping the post-mortem on successful campaigns (you learn most from wins you can repeat); vague lessons like "improve creative" |
| **KPI** | % campaigns with a post-mortem within 7 days (target 100%) |

---

### STAGE 19 — FEED THE BACKLOG

Convert every lesson into a scored intake item. If a lesson doesn't become a backlog item or a change to an SOP in this document, it will not happen. Update this file when a process changes — it is a living document, not a one-time deliverable.

---

## 5. Apollo Lead Generation System

> **Applies to the B2B track only.** Do not run this for consumer campaigns.

### 5.1 Who you are actually targeting in the UAE

| Buyer segment | Why they buy | Typical titles |
|---|---|---|
| **Corporate HR / Admin** | Staff outings, team-building, employee rewards, family days | HR Manager, HR Director, People & Culture Manager, Office Manager, Admin Manager, Employee Engagement Manager |
| **Travel agencies / DMCs / tour operators** | Reselling attraction tickets to their own clients | Product Manager, Contracting Manager, Operations Manager, Reservations Manager, Managing Director |
| **Hotels** | Concierge recommendations, guest packages | Concierge Manager, Guest Relations Manager, Front Office Manager, Chief Concierge |
| **Event & incentive agencies** | MICE group bookings | Event Manager, Event Director, MICE Manager, Incentive Travel Manager |
| **Schools & nurseries** | School trips | Head of School, Activities Coordinator, Head of Year, Trips Coordinator |
| **Real estate / property management** | Resident engagement events | Community Manager, Resident Experience Manager |

### 5.2 Standard Apollo filter recipe

| Filter | Setting | Reasoning |
|---|---|---|
| **Location** | Person Location = United Arab Emirates. Optionally narrow to Dubai, Abu Dhabi, Sharjah. | Person location, not company HQ — regional offices are what you want |
| **Industry** | Per segment: Hospitality, Leisure/Travel, Hotels, Events Services, Staffing/HR, Education, Real Estate, plus your target verticals for corporate outings (Banking, Construction, Oil & Gas, Logistics — the large-headcount UAE employers) | |
| **Employee count** | Corporate: 200–5,000 (enough headcount for a meaningful group, small enough to reach the decision-maker). Trade: 10–500. | Under 50 employees rarely books groups; over 5,000 has procurement gatekeeping |
| **Job titles** | Use the exact-title lists in §5.1. Prefer including specific titles over broad keywords. | |
| **Seniority** | Manager, Director, VP, Head, Owner. **Exclude** Intern, Entry, Training. | |
| **Contact filters** | Email status = **Verified** only. Has email = Yes. | Non-verified badly hurts bounce rate |
| **Exclusions** | Exclude your existing customers, exclude previously contacted, exclude competitors (Platinumlist, Headout, Klook, GetYourGuide, Musement, Tripadvisor, Viator, Rayna Tours, Arabian Adventures) | |

### 5.3 How many contacts

| Campaign type | Target contacts | Rationale |
|---|---|---|
| Test / new segment | 100–200 | Validate messaging cheaply before scale |
| Standard B2B campaign | 300–800 | Enough for statistical signal, small enough to personalise tier 1 |
| Broad seasonal push | 800–1,500 | Ceiling — beyond this, quality collapses and so does reply rate |

**Never exceed 1,500 per campaign.** Volume beyond that means your filters have gone loose, and reply rate falls faster than volume rises.

### 5.4 Avoiding irrelevant contacts

1. Use **exact job titles**, not keyword searches. "Manager" returns everything.
2. Filter person location, not company location.
3. Verified email status only.
4. Manually spot-check 10 random contacts against LinkedIn before exporting. If more than 2 are wrong, fix the filter and re-run.
5. Exclude departments that never buy: Engineering, IT, Legal, Finance (unless targeting procurement deliberately).
6. Save the search as a named Apollo list: `ICP-{segment}-{emirate}-{yyyymm}`.

### 5.5 Export → clean → segment → send

```
Apollo saved search
   ↓ Export CSV (select fields: First Name, Last Name, Title, Company,
   ↓ Industry, Employee Count, City, Country, Email, LinkedIn URL, Company Website)
raw/apollo-export-{campaign-id}-{yyyymmdd}.csv
   ↓ C# ApolloCleaner  (normalise → dedupe → strip role-based → title score → region check)
clean/staged-{campaign-id}.csv  +  rejects/{campaign-id}-rejects.csv
   ↓ Email verification (MillionVerifier / ZeroBounce)
clean/verified-{campaign-id}.csv   (valid)  +  catchall-{campaign-id}.csv (low priority)
   ↓ Segment by buyer type + seniority tier
   ↓
COLD OUTREACH TOOL  ── NOT MAILCHIMP ──►  Apollo Sequences, or Instantly/Smartlead
                                          on a SEPARATE sending domain
```

### 5.6 The domain rule — read this twice

Send cold B2B outreach from a **separate domain** (e.g. `dubaiticketmagic.co` or `tickets-dtm.com`), never your primary domain. Warm it for 3–4 weeks before real sends. If cold outreach damages that domain's reputation, your main domain — the one carrying booking confirmations and your opt-in newsletter — is untouched. This is the standard professional setup and it costs about $10/year.

Route:
- **Mailchimp** → opt-in contacts only, primary domain.
- **Cold outreach tool** → Apollo contacts, secondary domain.
- A B2B contact who **replies or opts in** may then be added to Mailchimp with consent recorded. That is the only legitimate bridge between the two systems.

### 5.7 Compliance (UAE)

The UAE Federal Decree-Law No. 45 of 2021 (PDPL) governs personal data, and the TDRA regulates electronic marketing. Practically:
- Include a clear opt-out in every cold email and honour it within 48 hours.
- Identify your business clearly with a real physical address.
- Maintain a permanent suppression list of everyone who ever opted out, across all tools.
- Record the source and date for every contact.
- If you email EU/UK residents, GDPR applies regardless of where you are.

This is not legal advice — for a formal compliance review, consult a UAE-qualified advisor. The practices above are the operational baseline.

### 5.8 Worked example — UAE Corporate Staff Outing Campaign

**Goal:** 25 corporate group enquiries for team-building desert and adventure experiences, Sept–Nov 2026.

```
Apollo search: ICP-corporate-hr-dubai-202608
  Person Location    : Dubai, Abu Dhabi (UAE)
  Employee Count     : 200 – 5,000
  Industry           : Banking, Construction, Oil & Gas, Logistics,
                       Information Technology, Real Estate, Healthcare
  Job Titles (exact) : HR Manager, HR Director, Head of HR,
                       People & Culture Manager, Employee Engagement Manager,
                       Office Manager, Admin Manager, Head of Employee Experience
  Seniority          : Manager, Director, Head, VP
  Email Status       : Verified
  Exclude            : previously contacted, existing customers, competitors
  Expected result    : ~600 – 900 contacts
```

**After cleaning:** ~500–700 valid.
**Segmentation:** Tier 1 = Director+ at 1,000+ employees (~80 contacts, manually personalised). Tier 2 = everyone else (templated sequence with company merge fields).
**Sequence:** Day 0 value email → Day 4 case study → Day 9 offer + deadline → Day 16 breakup. Send Tue/Wed 09:00–11:00 GST.
**Targets:** ≥95% valid, ≥40% open, ≥4% reply, ≥25 enquiries, ≥8 bookings.

---

## 6. Content Production System

### 6.1 The division of labour — the rule

**ChatGPT diverges. Claude converges. Canva executes.**

Do not run the same task through both AI tools — that is the duplication trap. Each has one job per step.

| Step | Tool | Why that tool | Output |
|---|---|---|---|
| 1. Research synthesis | **ChatGPT** | Fast, broad, good at pulling many sources into themes | 5 insights, 3 angles |
| 2. Brief pressure-test | **Claude** | Better at finding what's missing and asking the awkward question | Gap list, revised brief |
| 3. Concept generation | **ChatGPT** | Volume — 10 concepts in one pass | 10 concepts |
| 4. Concept selection | **Claude** | Critical evaluation against the brief and the competitor set | 1 chosen concept + rationale |
| 5. Subject lines | **ChatGPT** | 20 variants across styles (curiosity, benefit, urgency, question, number) | 20 candidates |
| 6. Subject-line shortlist | **Claude** | Cuts to 2 A/B candidates, flags spam-trigger language | 2 finalists |
| 7. Email body draft | **ChatGPT** | Fast first draft against your structure | Draft v1 |
| 8. Email body refine | **Claude** | Tightens, removes AI cadence, checks claims and tone | Final copy |
| 9. Landing page copy | **Claude** | Long-form structure and coherence | LP copy |
| 10. Social captions | **ChatGPT** | Volume and platform-native tone | 6 captions |
| 11. WhatsApp / SMS | **ChatGPT** | Short-form volume | 2–3 variants |
| 12. Design brief | **Claude** | Precise, structured specs a designer can execute without questions | Design brief |
| 13. Design | **Canva** | — | Assets |
| 14. Final review | **Claude** | Cross-checks copy against the offer sheet for price/date errors | Sign-off |

### 6.2 The exact sequence

```
Campaign Brief (Stage 4)
   ↓
[ChatGPT]  Research synthesis          → 5 insights, 3 angles
   ↓
[Claude]   Pressure-test the brief     → "what's missing / what's weak"
   ↓
[ChatGPT]  10 campaign concepts        → titles + hooks
   ↓
[Claude]   Select 1, justify           → chosen concept
   ↓
   ├─ [ChatGPT] 20 subject lines  → [Claude] cut to 2 A/B finalists
   ├─ [ChatGPT] preview text ×5   → [Claude] pick 1
   ├─ [ChatGPT] email draft       → [Claude] refine to final
   ├─ [Claude]  landing page copy → [ChatGPT] generate 3 CTA variants
   ├─ [ChatGPT] 6 social captions → [Claude] tone check
   └─ [ChatGPT] WhatsApp variants
   ↓
[Claude]   Design brief (exact specs, per asset)
   ↓
[Canva]    Design from locked templates
   ↓
[Squoosh]  Compress to weight budget
   ↓
[Claude]   Final QA — copy vs. offer sheet, price/date/name verification
   ↓
Final assets → public repo → jsDelivr URLs
```

### 6.3 Reusable prompt scaffolds

Store these in the private repo at `prompts/`. Paste the campaign brief above each.

**ChatGPT — subject lines**
> You are writing email subject lines for Dubai Ticket Magic, a UAE attraction-ticket seller. Campaign: [name]. Offer: [offer]. Audience: [segment]. Deadline: [date].
> Give me 20 subject lines under 45 characters, labelled by style: 5 curiosity, 5 benefit-led, 5 urgency, 5 number/specificity. No emoji in more than 5. Avoid: FREE in caps, multiple exclamation marks, "Act now", "Limited time only". Include one that names a specific attraction and one that names a specific price.

**Claude — refine email copy**
> Here is a draft marketing email for Dubai Ticket Magic. Refine it: cut 30% of the words, remove AI-sounding cadence (no em-dash chains, no "In today's fast-paced world", no triads of adjectives), make every claim specific and verifiable, and ensure the CTA verb is identical throughout. Verify every price and date against the offer sheet below and flag any mismatch. Keep the UAE audience in mind — English-first, but a mixed-nationality resident and tourist readership, so avoid idioms that don't travel.
> [draft] / [offer sheet]

**Claude — design brief**
> Write a design brief for the following assets for campaign [name]. For each asset specify: exact pixel dimensions, maximum file weight, headline text (verbatim), subheadline, price treatment, CTA button text, required logo placement, image subject, and mood. Assume the designer has the Brand Kit and has not read the campaign brief.
> Assets needed: [list]

### 6.4 Rules that prevent AI-generated copy from reading like AI-generated copy

1. Give the AI the actual offer sheet — invented prices are the single most damaging error.
2. Ban filler openings ("In today's...", "Imagine a world where...").
3. One idea per sentence; vary sentence length deliberately.
4. Name real things: "Zayed National Museum", not "world-class cultural attractions".
5. Read the final email aloud. If you'd never say it to a customer, rewrite it.
6. Keep a swipe file of your own best-performing subject lines and feed it in as style reference.

---

## 7. Mailchimp System

### 7.1 Account setup (once)

| Setting | Value |
|---|---|
| Time zone | Asia/Dubai (GST, UTC+4) |
| Sender name | `Dubai Ticket Magic` (consistent forever — recognition drives opens) |
| From address | `hello@` or `offers@` your primary domain. **Never** a no-reply. |
| Reply-to | A monitored inbox |
| Authentication | **SPF, DKIM, and DMARC configured and verified.** Gmail and Yahoo now require DMARC for bulk senders. Non-negotiable. |
| Physical address | Real UAE business address in the footer (legally required) |
| Double opt-in | **On.** Costs some signups, protects deliverability permanently. |
| Archive bar | Off |

### 7.2 Audience architecture

**One audience. Not many.** Mailchimp bills per audience and duplicate contacts across audiences cost you twice and fracture reporting.

Structure within that one audience:

| Layer | Use | Examples |
|---|---|---|
| **Tags** | Immutable facts and history | `src-website`, `src-popup`, `src-booking`, `src-event`, `purchased-desert`, `purchased-dining`, `campaign-bts-2026`, `b2b-trade` |
| **Groups** (visible preferences) | Self-declared interests the contact controls | Interests: Family / Couples / Adventure / Dining / Wellness / Culture |
| **Segments** (dynamic rules) | Send targeting, computed at send time | `residents-uae`, `lapsed-180d`, `vip-repeat-3plus`, `engaged-90d` |
| **Merge fields** | Personalisation | `FNAME`, `LNAME`, `CITY`, `EMIRATE`, `LANG`, `LASTBOOK`, `INTEREST` |

Suppression segment to build once and apply to every broad send:
`(Email marketing status = subscribed) AND NOT (tagged campaign-{current}) AND NOT (purchased-{product} in last 30 days) AND (opened OR clicked in last 180 days)`

### 7.3 The hard rule

**Only contacts who explicitly opted in go into Mailchimp.** Apollo exports, scraped lists, purchased lists, and event badge scans without consent do not. Every contact must have a recorded source and consent date. See §5.6 for the correct B2B route.

### 7.4 Campaign naming convention

```
{yyyy}-{mm}-{campaign-code}-{channel}-{variant}

2026-08-BTS-email-main
2026-08-BTS-email-resend
2026-08-BTS-email-b2b        (only if the B2B contacts are opted in)
2026-12-NDAY-email-main
2026-12-NDAY-automation-welcome
```

### 7.5 Standard email structure

| # | Block | Spec | Notes |
|---|---|---|---|
| 1 | **Preheader / preview text** | 40–90 chars | Continues the subject, never repeats it. The most under-used real estate in email. |
| 2 | **Header** | Logo, 600×200 (export 1200×400), ≤40 KB | Link to homepage with UTM |
| 3 | **Hero** | 600×400 (export 1200×800), ≤150 KB | Headline + offer + primary CTA **above the fold** |
| 4 | **Offer statement** | Text | Price, discount, deadline. Text, not baked into an image — images-off must still convey it. |
| 5 | **Primary CTA** | Bulletproof button, ≥44px tall | Text, not an image |
| 6 | **Product/experience cards** | 3–6 max, 290×290 or 600×300 each, ≤80 KB | Name, one-line benefit, price, individual CTA |
| 7 | **Social proof** | Text/small image | Rating, review count, or one short quote |
| 8 | **Secondary CTA** | Repeat of primary | Bottom-of-email clicks are real |
| 9 | **Urgency/deadline** | Text | "Offer ends 31 August" |
| 10 | **Footer** | Address, social, preferences, **unsubscribe** | Never hide or shrink the unsubscribe — burying it drives spam complaints instead |

Constraints: total HTML <100 KB (Gmail clips above ~102 KB and hides your footer, which breaks the unsubscribe link). 600px content width. Alt text on every image. Minimum 14px body text, 16px on mobile.

### 7.6 A/B testing discipline

Test **one variable at a time**:
1. Subject line (start here — biggest and easiest lever)
2. Preview text
3. Hero image
4. CTA wording
5. Send time
6. Offer framing ("30% off" vs "Save AED 90")

Rules: minimum ~1,000 contacts per variant for a meaningful read, 4-hour test window, winner by **click rate** not open rate, and log every result in the swipe file. Below ~2,000 total contacts, formal A/B is statistically meaningless — test sequentially across campaigns instead. **Note: A/B testing requires a paid Mailchimp plan; MailerLite includes it free.**

### 7.7 Three always-on automations (build once, run forever)

| Automation | Trigger | Content | Value |
|---|---|---|---|
| **Welcome series** (3 emails) | Signup | D0: welcome + best-sellers + first-purchase incentive. D3: "top 5 things to do in Dubai this month". D7: personalised by declared interest. | Highest-engagement emails you will ever send |
| **Post-purchase / post-visit** (2 emails) | Purchase | D+1: booking tips and what to bring. D+7: review request + a related experience | Drives repeat purchase and review volume |
| **Win-back** (2 emails) | 180 days inactive | E1: "we miss you" + a strong offer. E2: final, then auto-unsubscribe if unopened | Protects deliverability by clearing dead weight |

### 7.8 Reusable Mailchimp checklist

See `docs/templates/campaign-qa-checklist.md` — Section B.

---

## 8. GitHub Structure

### 8.1 Two repositories

**Why:** `assets-attractions` is public, which is exactly what you want for free CDN image delivery. It is exactly what you do not want for margins, contact data, and API keys.

#### Repo 1 — `assets-attractions` (PUBLIC — images only)

```
assets-attractions/
├── README.md                      # how to build a jsDelivr URL, naming rules, weight budgets
├── brand/
│   ├── logo/
│   │   ├── ticket-magic-logo-primary.png
│   │   ├── ticket-magic-logo-white.png
│   │   └── ticket-magic-logo-icon.png
│   ├── colors.md
│   └── fonts.md
├── campaigns/
│   └── 2026/
│       ├── 06-summer-is-here/
│       │   ├── email/
│       │   │   ├── summer-2026-email-header-1200x400.png
│       │   │   ├── summer-2026-email-hero-1200x800.jpg
│       │   │   └── summer-2026-email-card-desert-580x580.jpg
│       │   ├── social/
│       │   │   ├── summer-2026-ig-feed-1080x1350.jpg
│       │   │   └── summer-2026-ig-story-1080x1920.jpg
│       │   ├── web/
│       │   │   └── summer-2026-web-banner-1920x600.jpg
│       │   └── manifest.json          # auto-generated: filename → CDN URL → bytes
│       ├── 08-back-to-school/
│       └── 12-national-day/
├── attractions/                    # reusable, campaign-independent product imagery
│   ├── desert-safari/
│   ├── louvre-abu-dhabi/
│   ├── zayed-national-museum/
│   └── tandem-skydive/
└── .github/workflows/
    ├── optimize-images.yml         # auto-compress on push
    └── generate-manifest.yml       # emit manifest.json with CDN URLs
```

#### Repo 2 — `marketing-ops` (PRIVATE — everything else)

```
marketing-ops/
├── README.md
├── docs/
│   ├── marketing-campaign-os.md    # this document
│   ├── brand-voice.md
│   ├── sops/
│   └── templates/
│       ├── campaign-brief.md
│       ├── campaign-qa-checklist.md
│       └── campaign-post-mortem.md
├── campaigns/
│   └── 2026/
│       └── 08-back-to-school/
│           ├── brief.md
│           ├── research-note.md
│           ├── offer-sheet.csv          # margins — NEVER public
│           ├── copy.md
│           ├── design-brief.md
│           ├── qa-checklist.md
│           ├── post-mortem.md
│           └── reports/
│               ├── mailchimp-export.csv
│               └── ga4-export.csv
├── email/
│   └── templates/                       # HTML email templates
├── landing-pages/
├── data/
│   ├── raw/          # .gitignored — Apollo exports, PII
│   ├── clean/        # .gitignored
│   └── schemas/      # committed — column definitions only
├── automation/
│   ├── ApolloCleaner/                   # C# console app
│   ├── CampaignScaffold/
│   └── MailchimpReporter/
├── prompts/                             # reusable ChatGPT/Claude prompts
├── swipe-file/                          # winning subject lines, creatives, competitor ads
└── .gitignore
```

### 8.2 What goes where

| Store in GitHub (public) | Store in GitHub (private) | **Never in GitHub** |
|---|---|---|
| Optimised campaign images | Briefs, copy, research | API keys, tokens, passwords |
| Brand logos and assets | Offer sheets and margins | Contact lists / any PII |
| Email HTML templates | Post-mortems and reports | Apollo exports |
| Landing page source | Automation source code | Supplier contracts |
| Documentation of conventions | Prompts and swipe file | Raw Canva files (use Canva's own storage) |
| | Exported metric CSVs | Video/large binaries (use Drive) |

### 8.3 The `.gitignore` you need in the private repo

```gitignore
data/raw/
data/clean/
**/*-contacts.csv
**/*-export.csv
**/apollo-*.csv
.env
appsettings.Development.json
*.pfx
secrets/
```

### 8.4 jsDelivr CDN — how to serve images into email

```
https://cdn.jsdelivr.net/gh/kennethtablang/assets-attractions@{tag-or-commit}/campaigns/2026/08-back-to-school/email/bts-2026-email-hero-1200x800.jpg
```

- Use a **git tag or commit SHA**, not `@main`. jsDelivr caches `@main` for up to 7 days — if you swap an image after sending, subscribers may see either version. A pinned tag is immutable and safe.
- Tag each campaign at asset-freeze: `git tag campaign/2026-bts && git push --tags`.
- Never use `raw.githubusercontent.com` in email. It is not a CDN, it's rate-limited, and some corporate mail filters block it.

### 8.5 Migrating your current repo (a 15-minute job)

Your existing files need three fixes: spaces in filenames, no size optimisation, and a flat structure.

| Current | Target |
|---|---|
| `assets/summer_is_here_campaign/National History Museum.jpg` (850 KB) | `campaigns/2026/06-summer-is-here/email/summer-2026-email-card-natural-history-580x580.jpg` (≤80 KB) |
| `assets/summer_is_here_campaign/ticketmagiclogo.png` | `brand/logo/ticket-magic-logo-primary.png` |
| `assets/summer_is_here_campaign/Private Charter Posiedon.png` | `campaigns/2026/06-summer-is-here/email/summer-2026-email-card-private-charter-poseidon-580x580.jpg` |

(Note: "Posiedon" is misspelled — it should be "Poseidon". Worth fixing before it reaches a customer.)

---

## 9. Tracking & Analytics

### 9.1 UTM naming convention

**Rules:** all lowercase, underscores inside values, hyphens never mixed in, no spaces, no campaign name changes mid-flight. One UTM campaign value = one campaign, forever.

```
utm_source   = where the click came from      → mailchimp, facebook, instagram, whatsapp, google, tiktok, linkedin, partner_hotel
utm_medium   = the channel type                → email, social_organic, social_paid, cpc, referral, sms, qr, display
utm_campaign = {campaign_code}_{yyyy}          → bts_2026, summer_2026, nday_2026, xmas_2026, ramadan_2027
utm_content  = which element was clicked       → hero_cta, card_desert, footer_cta, header_logo, subject_a, story_swipeup
utm_term     = keyword (paid search only)      → things_to_do_dubai
```

### 9.2 Canonical examples

```
# Mailchimp email, hero button
https://dubaiticketmagic.com/back-to-school?utm_source=mailchimp&utm_medium=email&utm_campaign=bts_2026&utm_content=hero_cta

# Mailchimp email, a specific product card
...?utm_source=mailchimp&utm_medium=email&utm_campaign=bts_2026&utm_content=card_desert_safari

# Resend to non-openers (same campaign, distinguished by content)
...?utm_source=mailchimp&utm_medium=email&utm_campaign=bts_2026&utm_content=resend_hero_cta

# Instagram story, organic
...?utm_source=instagram&utm_medium=social_organic&utm_campaign=bts_2026&utm_content=story_swipeup

# Meta paid, creative variant B
...?utm_source=facebook&utm_medium=social_paid&utm_campaign=bts_2026&utm_content=carousel_b

# WhatsApp broadcast
...?utm_source=whatsapp&utm_medium=sms&utm_campaign=bts_2026&utm_content=broadcast_1

# Printed flyer QR code
...?utm_source=flyer&utm_medium=qr&utm_campaign=bts_2026&utm_content=mall_standee
```

### 9.3 Campaign codes (register these once, reuse yearly)

| Campaign | Code | Typical window |
|---|---|---|
| Summer | `summer` | Jun–Aug (indoor/staycation angle — this is UAE low season for inbound, high season for resident staycations) |
| Back to School | `bts` | Aug (schools reopen late Aug) |
| UAE National Day / Eid Al Etihad | `nday` | Late Nov – 3 Dec |
| Christmas | `xmas` | Dec |
| New Year | `nye` | Late Dec – 1 Jan |
| Dubai Shopping Festival | `dsf` | Dec–Jan |
| Valentine's Day | `vday` | Early–mid Feb |
| Ramadan | `ramadan` | Shifts ~11 days earlier each year — **check the date annually** |
| Eid Al Fitr | `eidfitr` | End of Ramadan |
| Eid Al Adha | `eidadha` | ~70 days after Eid Al Fitr |
| Spring Break | `spring` | Mar–Apr |
| Weekend Deals | `weekend` | Recurring |
| Under AED 50 / 100 | `under50` / `under100` | Recurring |
| Dining | `dining` | Recurring |
| Couples | `couples` | Recurring |
| Family | `family` | Recurring |

**Maintain a UTM Registry tab in the campaign register.** One row per unique UTM combination used, with the campaign ID and date. This is what stops GA4 filling up with `Summer2026`, `summer_2026`, and `summer-2026` as three separate campaigns — the most common tracking failure there is.

### 9.4 Cross-channel tracking setup

| Channel | Tracking method | Notes |
|---|---|---|
| **Email** | Mailchimp campaign settings → enable Google Analytics link tracking, set `utm_campaign` there once; it appends to all links. Override `utm_content` per link manually. | Verify in GA4 Realtime during QA |
| **Website** | GA4 via Google Tag Manager (free) + Microsoft Clarity | Set up a `purchase`/`booking_complete` conversion event with value |
| **Social organic** | Manual UTMs on every link in bio and story | Use a link-in-bio page you control so you get the click data |
| **Paid** | Meta: enable URL parameters at ad-set level. Google Ads: auto-tagging ON (uses gclid, do not add manual UTMs on top). | |
| **Landing pages** | GA4 + Clarity on every page; conversion event on the confirmation page | Confirmation page must be a distinct URL for reliable conversion counting |
| **WhatsApp / offline** | Shortened UTM link or QR code | This is the only place a shortener is appropriate |

### 9.5 KPI standards

#### Email (travel & hospitality benchmarks)

| Metric | Poor | Acceptable | Good | Notes |
|---|---|---|---|---|
| Delivery rate | <95% | 97% | >98.5% | Below 95% = list health problem |
| Open rate | <15% | 20–25% | >30% | **Inflated by privacy pre-fetching. Use for relative A/B only.** |
| Click-through rate | <1% | 1.5–2.5% | >3% | **Your primary email KPI** |
| Click-to-open rate | <5% | 8–12% | >15% | Best single measure of message-audience fit |
| Bounce rate | >3% | <2% | <0.5% | Hard bounces above 2% will get you throttled |
| Unsubscribe rate | >0.5% | <0.3% | <0.1% | |
| Spam complaints | >0.1% | <0.05% | <0.02% | Above 0.3% and mailbox providers start blocking |
| Conversion rate (of clickers) | <1% | 2–4% | >5% | |

#### Website

| Metric | Target |
|---|---|
| Landing page conversion rate | 2–5% (offer-dependent) |
| Engagement rate (GA4) | >55% |
| Avg engagement time | >45s |
| LCP (Largest Contentful Paint) | <2.5s |
| Mobile share of traffic | Expect 70–85% in UAE — design mobile-first |

#### Business

| Metric | Formula | Target |
|---|---|---|
| Cost per lead | Total spend ÷ leads | Track trend, not absolute |
| Customer acquisition cost | Total spend ÷ new customers | < 25% of first-order gross profit |
| ROI | (Revenue − Cost) ÷ Cost | Email-only campaigns should exceed 10:1 |
| Revenue per email sent | Revenue ÷ emails delivered | Best single cross-campaign comparator |
| Repeat purchase rate | Repeat customers ÷ total | Track quarterly |

#### Which KPI matters at which stage

| Stage | Primary KPI | Why |
|---|---|---|
| 0–4 Intake→Planning | Priority score, brief completeness | Are we doing the right thing |
| 5–7 Audience/Leads | Segment size, valid email rate | Is the list real |
| 8–10 Content/Design | Asset weight, on-time delivery | Is it fast and ready |
| 11–13 LP/Email/QA | Page speed, QA pass rate | Is it correct |
| 14–15 Launch/Monitor | Delivery rate, bounce, spam complaints | Did it arrive safely |
| 16 Optimize | CTR, CTOR | Is the message landing |
| 17–18 Analytics/Post-mortem | Conversion rate, revenue, ROI | Did it make money |

---

## 10. Automation Opportunities

### AUTOMATE NOW (weeks 1–4)

| # | Automation | Tool | Effort | Value |
|---|---|---|---|---|
| 1 | **Image compression on push** | GitHub Action (`calibreapp/image-actions` or a `sharp` script) — auto-compresses and opens a PR | 1h | **Very high.** Permanently fixes the 850 KB problem. |
| 2 | **Asset manifest generation** | GitHub Action emits `manifest.json` mapping filename → jsDelivr URL → byte size | 1h | High. Stops hand-building CDN URLs and catches oversized files. |
| 3 | **Mailchimp welcome / post-purchase / win-back automations** | Mailchimp native | 3h once | **Very high.** Runs forever with no further work. |
| 4 | **GA4 → Looker Studio campaign dashboard** | Looker Studio, free connector | 2h once | High. Kills manual reporting for good. |
| 5 | **`ApolloCleaner` C# console app** | .NET 8 console | 4–6h | High **if you run B2B regularly**. Skip if B2B is occasional — use OpenRefine instead. |

### AUTOMATE LATER (months 2–6, only when the pain is real)

| # | Automation | Trigger to build it |
|---|---|---|
| 6 | **`CampaignScaffold` dotnet tool** — creates the folder tree, copies templates, appends the register row | After ~5 campaigns, when the setup tedium is proven |
| 7 | **`MailchimpReporter`** — Mailchimp API → campaign metrics → SQL Server / Sheets → Looker Studio | When you have 10+ campaigns to compare and manual export hurts |
| 8 | **Link + UTM checker GitHub Action** on email HTML — fails the build on a 404 or a malformed UTM | After the first broken-link incident |
| 9 | **Mailchimp ↔ booking system tag sync** (webhook → tag purchasers) | When segmentation by purchase history becomes a bottleneck |
| 10 | **n8n instance** for multi-tool glue | Only when you have 3+ recurring integrations. Not before. |

### DO NOT AUTOMATE

| Thing | Why not |
|---|---|
| **Offer and margin decisions** | Commercial judgement. Automating this automates losing money. |
| **Copy approval** | AI drafts; a human signs off on price, date, and claim accuracy. |
| **Audience strategy** | Requires market context no rule engine has. |
| **QA sign-off** | The entire point is a human second look. |
| **Supplier relationships** | Automated supplier emails damage the relationships your margin depends on. |
| **Cold outreach personalisation at scale** | Mass "personalisation" reads as mass. Tier 1 gets manual attention or it isn't worth sending. |
| **Post-mortem interpretation** | A dashboard shows what happened. Only a person can say why. |
| **A custom UTM builder web app** | A Google Sheet with a `CONCATENATE` formula does this in 10 minutes. |
| **A custom CRM** | HubSpot Free exists and is better than anything you'd build in a month. |
| **A custom email sending platform** | Deliverability is a decade of accumulated domain reputation engineering. Never build this. |

### Your three highest-value C#/.NET builds

**1. `ApolloCleaner` (build first, if B2B is recurring)**
```
dotnet run -- --in raw/apollo-export.csv --out clean/staged.csv \
              --titles config/target-titles.txt --region AE --min-title-score 2

Pipeline: read CSV (CsvHelper) → trim/normalise casing → dedupe by email
        → dedupe by (company + lastname) → drop role-based prefixes
        → drop free-mail domains → score title against target list
        → validate country/city → validate email syntax + MX record
        → populate merge fields → write clean.csv + rejects.csv + summary.txt
```
Rejects must be written to a separate file with a reason column — that's how you catch a filter that has gone wrong.

**2. `CampaignScaffold` (build second)**
```
dotnet run -- new --id 2026-08-BTS --name "Back to School 2026" --type seasonal
→ creates private-repo campaign folder from templates
→ creates public-repo asset folders
→ appends a row to campaign-register.csv
→ opens a GitHub Issue from the campaign template
```

**3. `MailchimpReporter` (build third)**
```
GET /campaigns/{id}/reports  →  flatten to a row  →  append to Sheets/SQL
Scheduled by GitHub Actions cron. Feeds the Looker Studio dashboard.
```

Everything else: use the free tool.

---

## 11. Campaign Checklists

The full working checklists live in `docs/templates/campaign-qa-checklist.md`. Summary of the four phases:

### BEFORE CAMPAIGN
Research note complete · Offer designed and margin approved · Supplier and inventory confirmed in writing · Brief complete with one KPI and one number · Audience segmented and sized · Suppressions defined · Content strategy set · Copy written and verified against the offer sheet · Assets designed, compressed, named, committed · Landing page built and tracking installed · UTMs registered

### DURING BUILD
Email built from template · Every link carries the correct UTM · Merge tags tested with a real contact · Mobile rendering verified on real hardware · Dark mode checked · Images-off checked · Alt text on every image · Total HTML <100 KB · Spam score checked (mail-tester) · Test sent to 4+ real inboxes · End-to-end test booking completed including the promo code

### LAUNCH
Segment count confirmed · Send time correct in Asia/Dubai · Not a Friday, not a public holiday · Tracking enabled · Social scheduled · Website banner live · Landing page live from a fresh browser · Booking system showing the campaign price · Launch logged in the campaign issue

### AFTER LAUNCH
T+30min health check · T+2h CTR and complaints · T+24h full metrics · T+48–72h resend to non-openers · In-flight fixes applied · Post-close analytics pulled and reconciled to real revenue · Post-mortem written within 7 days · Assets archived and git-tagged · Swipe file updated · Lessons converted to backlog items

---

## 12. Weekly Workflow

### 12.1 The realistic cadence

One person cannot run a full campaign every week. The sustainable rhythm is **one major campaign per 2 weeks**, with always-on automations and organic social filling the gaps. Attempting weekly majors is the most common reason a system like this gets abandoned in month two.

### 12.2 The 10-working-day sprint

UAE work week: **Monday–Friday** (weekend Sat–Sun). Consumer booking behaviour peaks Thursday evening through Sunday — which is why sends land Thursday/Friday.

| Day | Focus | Deliverable | Stages |
|---|---|---|---|
| **Mon (D1)** | Intake + Research | Scored intake, research note | 0, 1 |
| **Tue (D2)** | Offer + Suppliers | Approved offer sheet, supplier confirmations sent | 2, 3 |
| **Wed (D3)** | Planning + Audience | Completed brief, segments defined and sized | 4, 5 |
| **Thu (D4)** | Leads *(B2B only)* / Content strategy | Clean list **or** message hierarchy | 6, 7, 8 |
| **Fri (D5)** | Copywriting | `copy.md` complete — subject lines, email, LP, social | 9 |
| **Sat–Sun** | — | *Rest. Monitor the previous campaign if one is live.* | 15 |
| **Mon (D6)** | Design | All assets designed, compressed, committed, CDN URLs live | 10 |
| **Tue (D7)** | Landing page | Page live with GA4 + Clarity + conversion event | 11 |
| **Wed (D8)** | Email build | Campaign built in Mailchimp, all links UTM'd | 12 |
| **Thu (D9)** | QA + Launch | Checklist green, **campaign sent 17:00–19:00 GST** | 13, 14 |
| **Fri (D10)** | Monitor | T+2h and T+24h health checks | 15 |
| **Sat–Sun** | Light monitoring | Weekend is peak booking traffic — watch, don't sleep on it | 15 |
| **Mon (D11 = D1 of next sprint)** | Optimize previous + intake next | Resend to non-openers; start the next campaign's research | 16, 0 |
| **+7 days after close** | Analytics + Post-mortem | Report complete, register closed, assets tagged | 17, 18, 19 |

### 12.3 Fixed weekly rituals (30 min each, non-negotiable)

| When | Ritual |
|---|---|
| Monday 09:00 | Review the campaign board; move statuses; confirm this sprint's dates |
| Wednesday 09:00 | Deliverability check: bounce rate, complaint rate, list growth |
| Friday 16:00 | Update the campaign register; commit and push everything |
| Last Friday of month | Monthly review: all campaign KPIs, list health, top 3 lessons |

---

## 13. Campaign Post-Mortem

Full template: `docs/templates/campaign-post-mortem.md`. Structure:

1. **Header** — Campaign ID, name, type, dates, owner, status
2. **Objective vs. result** — the one KPI, target vs. actual, variance %
3. **Audience** — segments, sizes, suppressions applied
4. **Offer** — what was offered, planned vs. realised margin
5. **Channels & spend** — per channel: spend, sessions, conversions, revenue, ROI
6. **Email performance** — the full metric table with benchmark comparison
7. **Website performance** — sessions, conversion rate, LCP, top exit points
8. **Business results** — leads, bookings, revenue, GP, CAC, ROI
9. **What worked** — best subject line, best creative, best segment, best product, with numbers
10. **What didn't** — with numbers
11. **Problems** — what broke, root cause, prevention
12. **Lessons learned** — 3–5 specific, actionable items, each with an owner
13. **Recommendations for next campaign**
14. **Assets archived** — git tag, folder path, CDN base URL

**Rule: no campaign is `COMPLETED` until the post-mortem exists.** The register enforces this.

---

## 14. Campaign Status System

| Status | Meaning | Exit criteria — all must be true to advance |
|---|---|---|
| `IDEA` | Captured, not evaluated | Scored on all 7 criteria |
| `RESEARCH` | Score ≥40, being researched | Research note complete with ≥3 competitor prices |
| `PLANNING` | Offer and plan being built | Offer sheet margin-approved **AND** suppliers confirmed in writing **AND** brief complete with one numeric KPI |
| `AUDIENCE` | Targeting being defined | Segments named, sized, suppressions defined; B2B list cleaned and verified if applicable |
| `CONTENT` | Copy in production | `copy.md` complete; every price and date verified against the offer sheet |
| `DESIGN` | Creative in production | All assets designed, compressed within budget, correctly named, committed, CDN URLs generated |
| `LANDING_PAGE` | Page in build | Page live, GA4 + Clarity firing, conversion event tested, mobile verified, LCP <2.5s |
| `EMAIL_BUILD` | Email in build | Built, all links UTM'd, merge tags tested, HTML <100 KB |
| `QA` | Under review | Full QA checklist green, signed by a second person, test booking completed end-to-end |
| `SCHEDULED` | Queued to send | Segment count confirmed, send time confirmed in Asia/Dubai, social scheduled |
| `LIVE` | Sent, running | Campaign end date reached |
| `ANALYZING` | Collecting results | Data pulled and reconciled to actual revenue |
| `COMPLETED` | Closed | Post-mortem written, register closed, assets git-tagged, lessons in the backlog |
| `PARKED` | Deprioritised | (terminal — with a one-line reason) |
| `CANCELLED` | Stopped | (terminal — with a one-line reason) |

**Never skip a gate.** The gates exist because each one represents a specific way campaigns fail: unapproved margins, unconfirmed inventory, untested links, unmeasured results.

---

## 15. Campaign Priority System

### 15.1 The scoring formula

Score each criterion **1–5**, then:

```
SCORE = (Revenue Potential      × 3)
      + (Conversion Likelihood  × 2)
      + (Audience Size          × 2)
      + (Seasonal Urgency       × 2)
      + (Offer Strength         × 2)
      + (Asset Readiness        × 1)
      − (Effort Required        × 2)

Range: 2 (worst) to 58 (best)
```

### 15.2 Scoring guide

| Criterion | 1 | 3 | 5 |
|---|---|---|---|
| **Revenue Potential** | <AED 10k | AED 25–50k | >AED 100k |
| **Conversion Likelihood** | Unproven audience/offer | Similar campaign converted OK before | Proven repeat winner |
| **Audience Size** | <500 reachable | 2,000–5,000 | >10,000 |
| **Seasonal Urgency** | No time pressure | Relevant this quarter | Window closes in <4 weeks and won't return for a year |
| **Offer Strength** | Same as everyday price | Modest, credible saving | Genuinely exceptional / exclusive |
| **Asset Readiness** | Everything from scratch | Some reusable assets | Templates + imagery ready |
| **Effort Required** *(subtracted)* | Under 3 days | ~1 sprint | Multi-week, new build, external dependencies |

### 15.3 Decision thresholds

| Score | Decision |
|---|---|
| **≥ 40** | **Run this quarter.** Schedule into the next available sprint. |
| **25 – 39** | **Queue.** Revisit monthly, or when seasonality raises the urgency score. |
| **< 25** | **Park** with a one-line reason. Do not silently drop — parked ideas score differently next season. |

### 15.4 Worked examples

| Campaign | Rev | Conv | Aud | Urg | Offer | Ready | Effort | Score | Decision |
|---|---|---|---|---|---|---|---|---|---|
| Back to School 2026 | 4 | 4 | 4 | 5 | 4 | 4 | 2 | **12+8+8+10+8+4−4 = 46** | **Run** |
| UAE National Day 2026 | 5 | 4 | 5 | 4 | 4 | 3 | 3 | **15+8+10+8+8+3−6 = 46** | **Run** |
| Attractions Under AED 100 | 3 | 4 | 5 | 2 | 3 | 5 | 1 | **9+8+10+4+6+5−2 = 40** | **Run** (great filler — low effort, always-on) |
| Corporate Staff Outings (B2B) | 4 | 2 | 2 | 3 | 3 | 2 | 4 | **12+4+4+6+6+2−8 = 26** | **Queue** |
| New Wellness Vertical Launch | 2 | 1 | 2 | 1 | 2 | 1 | 5 | **6+2+4+2+4+1−10 = 9** | **Park** |

### 15.5 Additional scheduling rules

1. **Never run two campaigns to the same segment within 5 days.** Frequency drives unsubscribes faster than any other factor.
2. **A tie is broken by effort** — lower effort wins, because it frees the sprint.
3. **Recurring low-effort campaigns** (`under50`, `under100`, `weekend`) are the filler between majors. Build them once as templates and re-run with fresh products.
4. **Reserve ~20% of sprints for testing** — new segments, new offer mechanics, new channels. Otherwise you optimise a local maximum forever.

---

## 16. 30-Day Implementation Plan

Starting **7 August 2026**. Sequenced so that the pilot campaign (Back to School — UAE schools reopen late August) launches inside the window rather than after it.

### Week 1 (Aug 7–14) — Foundation + pilot fast-track

| Day | Task | Time | Output |
|---|---|---|---|
| D1 | **Decide Mailchimp Essentials vs. MailerLite free.** Check your contact count and whether you need A/B and scheduling. | 30m | Decision made |
| D1 | Verify SPF, DKIM, DMARC on your sending domain. Fix if missing. | 1h | Authentication green |
| D1 | Create the private `marketing-ops` repo; commit this document and the templates | 30m | Repo live |
| D2 | Restructure `assets-attractions`: new folder tree, rename all files to convention, fix "Posiedon" | 1h | Clean public repo |
| D2 | Compress all existing assets in Squoosh to the weight budgets; re-commit | 1h | Assets ≤150 KB |
| D2 | Tag the summer campaign, generate jsDelivr URLs, verify one loads | 30m | CDN working |
| D3 | Install GA4 + Microsoft Clarity on the site; create the booking conversion event | 2h | Analytics live |
| D3 | Create the Campaign Register in Google Sheets from §17 | 1h | Register live |
| D4 | Set up GitHub Projects board with the 15 statuses | 1h | Board live |
| D4 | Build the Canva Brand Kit (colours, fonts, logo) + 4 core templates (email header, email hero, IG feed, IG story) | 3h | Templates locked |
| D5 | **Run Stages 0–4 for Back to School 2026**: score, research, offer + margin, supplier confirmations, brief | 4h | Brief complete |

### Week 2 (Aug 15–21) — Pilot execution

| Day | Task | Output |
|---|---|---|
| D8 | Audience: build the 12 standard segments and the suppression segment in Mailchimp | Segments live |
| D9 | Content: run the full ChatGPT → Claude sequence (§6). Produce `copy.md`. | Copy done |
| D10 | Design: BTS assets from templates, compressed, committed, CDN URLs | Assets live |
| D11 | Landing page + tracking + Clarity; run PageSpeed Insights | Page live |
| D12 | Email build; QA checklist; test sends to 4 real inboxes; end-to-end test booking | QA green |
| D13 (Thu) | **LAUNCH — 17:00–19:00 GST** | Campaign live |
| D14 | T+2h and T+24h monitoring | Health confirmed |

### Week 3 (Aug 22–28) — Automate + measure

| Day | Task | Output |
|---|---|---|
| D15 | Resend to non-openers with a new subject line | Incremental conversions |
| D16 | Build the GitHub Action for image compression | Auto-optimization live |
| D17 | Build the Looker Studio campaign dashboard (GA4 + register Sheet) | Dashboard live |
| D18 | Build Mailchimp's three always-on automations (welcome, post-purchase, win-back) | Automations live |
| D19 | Pull BTS analytics; reconcile revenue against the booking system | Data in hand |
| D20 | **Write the BTS post-mortem.** Tag assets. Update the swipe file. | First closed loop |

### Week 4 (Aug 29 – Sep 6) — Second campaign at full process + refine

| Day | Task | Output |
|---|---|---|
| D22 | Intake and score the Q4 slate: National Day, Christmas, NYE, DSF | Scored backlog |
| D23 | Run Stages 0–4 for **UAE National Day 2026** (send window: late Nov) | Brief complete |
| D24 | Build the `ApolloCleaner` C# tool **only if** B2B is a genuine priority; otherwise skip and use OpenRefine | Tool or a documented decision to skip |
| D25 | Refine this document with everything the pilot taught you | MCOS v1.1 |
| D26 | Build the reusable "Attractions Under AED 100" template campaign as always-on filler | Reusable campaign |
| D27 | Monthly review: list health, KPIs, top 3 lessons | Review complete |
| D28–30 | Buffer. Something will overrun. | — |

### The definition of done for these 30 days

- ☐ Two repos live, correctly structured, assets compressed and CDN-served
- ☐ GA4 + Clarity + Looker Studio dashboard operational
- ☐ Campaign Register with at least 2 campaigns tracked end-to-end
- ☐ 12 Mailchimp segments + suppression segment built
- ☐ 3 always-on automations running
- ☐ Canva Brand Kit + 4 locked templates
- ☐ **One campaign taken through all 19 stages with a written post-mortem**
- ☐ Image compression automated
- ☐ Q4 backlog scored and scheduled

That last checkbox — one full loop, closed — matters more than all the others. A system that has run once is a system. A system that has only been designed is a document.

---

## 17. Campaign Record Structure

The register lives at `docs/campaign-register.csv` (private repo) and mirrors to Google Sheets. Fields added to your draft are marked **NEW**.

| # | Field | Example | Notes |
|---|---|---|---|
| 1 | `campaign_id` | `DTM-2026-08-BTS` | `{brand}-{yyyy}-{mm}-{code}` |
| 2 | `campaign_name` | Back to School 2026 | |
| 3 | `campaign_code` | `bts` | Matches the UTM campaign root |
| 4 | `campaign_type` | seasonal / promo / product-launch / always-on / b2b | |
| 5 | `track` | **NEW** — b2c / b2b / both | Determines which pipeline branch |
| 6 | `objective` | 180 bookings at ≥AED 22 GP | Must contain a number |
| 7 | `primary_kpi` | **NEW** — bookings | Exactly one |
| 8 | `kpi_target` | **NEW** — 180 | |
| 9 | `priority_score` | **NEW** — 46 | From §15 |
| 10 | `status` | LIVE | From §14 |
| 11 | `start_date` / `end_date` | 2026-08-13 / 2026-08-31 | |
| 12 | `send_datetime` | **NEW** — 2026-08-13 18:00 GST | |
| 13 | `target_audience` | Families with school-age children, UAE residents | |
| 14 | `target_location` | Dubai, Abu Dhabi, Sharjah | |
| 15 | `target_industry` | *(B2B only)* | |
| 16 | `offer` | 25% off family passes | |
| 17 | `offer_mechanic` | **NEW** — percentage-discount | discount / bundle / added-value / urgency-only |
| 18 | `margin_floor_pct` | **NEW** — 18% | **Private repo only** |
| 19 | `products` | Desert Safari, Louvre AD, Skydive | |
| 20 | `supplier_confirmed` | **NEW** — Yes (2026-08-09) | Gate for Stage 3 |
| 21 | `landing_page_url` | /back-to-school | |
| 22 | `email_campaign_name` | 2026-08-BTS-email-main | |
| 23 | `creative_assets_path` | **NEW** — campaigns/2026/08-back-to-school/ | |
| 24 | `cdn_base_url` | **NEW** — jsDelivr URL at the pinned tag | |
| 25 | `git_tag` | **NEW** — campaign/2026-bts | |
| 26 | `apollo_list` | *(B2B only)* | |
| 27 | `mailchimp_segment` | residents-families-engaged90 | |
| 28 | `audience_size_sent` | **NEW** — 4,182 | Record pre-send |
| 29 | `suppressions_applied` | **NEW** — recent-buyers, lapsed-180d | |
| 30 | `utm_campaign` | `bts_2026` | Must be unique |
| 31 | `owner` | Kenneth Tablang | |
| 32 | `budget_aed` | 0 | |
| 33 | `spend_actual_aed` | **NEW** | |
| 34–41 | `delivered`, `open_rate`, `ctr`, `ctor`, `bounce_rate`, `unsub_rate`, `spam_rate`, `conv_rate` | **NEW** — split out | One column each so the dashboard can chart them |
| 42 | `sessions` / `conversions` | **NEW** | From GA4 |
| 43 | `revenue_aed` / `gross_profit_aed` | **NEW** | Reconciled to the booking system |
| 44 | `roi` | **NEW** | (Revenue − Cost) ÷ Cost |
| 45 | `best_subject_line` | **NEW** | Feeds the swipe file |
| 46 | `best_creative` | **NEW** | |
| 47 | `best_segment` | **NEW** | |
| 48 | `lessons_learned` | Link to post-mortem | |
| 49 | `post_mortem_url` | **NEW** | Required before `COMPLETED` |

---

## Appendix A — UAE Campaign Calendar

| Period | Campaign | Notes |
|---|---|---|
| Jan | New Year, DSF continues | Peak inbound tourism season |
| Feb | Valentine's Day, Ramadan prep | Couples + dining focus |
| **Feb–Mar 2027** | Ramadan | **Date shifts ~11 days earlier annually — verify each year.** Shift sends to 20:00–22:00 GST post-iftar. Tone down overt discounting; emphasise family and iftar experiences. |
| Mar–Apr | Eid Al Fitr, Spring Break | Major booking peak. Attraction blackouts are common — confirm early. |
| Apr–May | Spring, shoulder season | |
| May–Jun | Eid Al Adha, Summer launch | |
| **Jun–Aug** | Summer | UAE **low** season for inbound tourism, **high** for resident staycations. Pivot to indoor, waterpark, mall, and hotel-package angles. Heat is the story — sell escape from it. |
| **Late Aug** | **Back to School** | Schools reopen late Aug. Last-chance family outing angle. |
| Sep–Oct | Autumn return, weather improves | Outdoor experiences come back |
| Oct | Halloween | Growing in UAE, strong with families and expats |
| **Late Nov – 3 Dec** | **UAE National Day / Eid Al Etihad** | Largest domestic campaign of the year. Patriotic theming, long weekend. |
| Dec | Christmas, DSF launch, NYE | Peak season, peak competition, peak spend |

## Appendix B — Asset Specifications

| Asset | Design size | Export | Max weight | Format |
|---|---|---|---|---|
| Email header | 600×200 | 1200×400 @2× | 40 KB | PNG (logo) |
| Email hero | 600×400 | 1200×800 @2× | 150 KB | JPG q80 |
| Email product card (2-col) | 290×290 | 580×580 @2× | 80 KB | JPG q80 |
| Email product card (full) | 600×300 | 1200×600 @2× | 100 KB | JPG q80 |
| Website hero banner | 1920×600 | 1920×600 | 200 KB | WebP + JPG fallback |
| Website card | 800×600 | 800×600 | 100 KB | WebP |
| Open Graph / social share | 1200×630 | 1200×630 | 150 KB | JPG |
| Instagram feed (square) | 1080×1080 | — | 300 KB | JPG |
| Instagram feed (portrait) | 1080×1350 | — | 300 KB | JPG — **best organic reach** |
| Instagram / Facebook story | 1080×1920 | — | 300 KB | JPG — keep text in the middle 60% |
| Facebook feed | 1200×630 | — | 300 KB | JPG |
| LinkedIn (B2B) | 1200×627 | — | 300 KB | JPG |
| WhatsApp broadcast | 1080×1080 | — | 200 KB | JPG |
| Poster (print A4) | 2480×3508 @300dpi | — | — | PDF (CMYK) |

**Filename convention:** `{campaign-code}-{yyyy}-{channel}-{asset-type}-{descriptor}-{WxH}.{ext}`
All lowercase, hyphens only, no spaces, no special characters.
Example: `bts-2026-email-hero-family-desert-1200x800.jpg`
