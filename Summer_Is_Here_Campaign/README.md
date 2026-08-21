# Summer Is Here — Campaign Folder

**Campaign ID:** DTM-2026-08-SUMMER
**Status:** `PLANNING` — blocked on inputs (see below)
**Created:** 2026-08-07
**Owner:** Kenneth Tablang

---

## ✅ Decision: Final Weeks push

Confirmed 7 Aug 2026. This runs as a **last-chance campaign**, not a season opener.

| | |
|---|---|
| **Angle** | Closing window — the last free weekends before school starts. **Not discount-led.** |
| **Customer-facing name** | "Last Weeks of Summer" *(internal ID stays `SUMMER`)* |
| **Send** | **Thursday 13 August 2026, 17:00–19:00 GST** *(verified: 13 Aug 2026 is a Thursday)* |
| **Offer window** | 8 Aug → 31 Aug 2026 |
| **Runway** | ~3 weeks |

**Why this angle works:** the school-reopening deadline is real. You don't have to manufacture scarcity — families genuinely have a small, closing window. Sell the window, not the price.

**Why send by 13 Aug:** Back to School emails are about to flood every inbox in the UAE. Going a week ahead of that wave is worth more than a few extra days of prep.

> ⏱️ **That is 6 days from today.** The schedule in `brief.md` §9 is tight but workable — it depends on `assets-manifest.md` coming back quickly.

---

## What's in this folder

| File | Purpose | Status |
|---|---|---|
| `brief.md` | The campaign plan — offer, audience, message, schedule | ⬜ Blocked on your input |
| `assets-manifest.md` | **The file I need you to fill in** — product names, prices, booking links, image URLs | ⬜ Awaiting you |
| `copy.md` | Email + landing page + social copy | ⬜ Blocked on brief |
| `qa-checklist.md` | Pre-send checks | ⬜ Not started |
| `email/email.html` | Ready-to-paste Mailchimp email, 7 product slots | ⬜ Tokens blank |
| `post-mortem.md` | Created after the campaign closes | — |

---

## Products in this campaign

Taken from `assets/summer_is_here_campaign/`. Seven products, all needing details from you:

| # | Asset file | Likely product | Needs confirming |
|---|---|---|---|
| 1 | `Desert.jpg` | Desert Safari | Full product name, which operator |
| 2 | `Louvre.jpg` | Louvre Abu Dhabi | Ticket type (adult/family) |
| 3 | `Zayed National Museum.jpg` | Zayed National Museum | — |
| 4 | `National History Museum.jpg` | Natural History Museum Abu Dhabi? | **Filename may be wrong** — "National" vs "Natural" |
| 5 | `tandemskydive.jpg` | Tandem Skydive Dubai | Palm or Desert dropzone? |
| 6 | `Private Charter Posiedon.png` | Private Charter Poseidon | **"Posiedon" is misspelled** in the filename |
| 7 | `Wikit.png` | ⬜ Unknown | **I don't know what this is** — please tell me |

---

## 🔴 What I need from you before this can move

Fill in **`assets-manifest.md`** — it's a table, one row per product. For each I need:

1. **Exact product name** as it should appear to customers
2. **Booking page URL** on your site
3. **Normal price** and **campaign price** in AED
4. **Confirmation the image is cleared for use**

Then separately:

5. **Is the repo `assets-attractions` public?** (needed for the CDN image links to work)
6. **Your brand colour** — hex code. The email template has a placeholder red in it.
7. **Landing page URL** — does one exist for this campaign, or does traffic go to the homepage?
8. **What is "Wikit"?**

Once that's in, I can generate the CDN image URLs, finish the brief, write the copy, and hand you a paste-ready email.

---

## What happens after you fill that in

| Step | Who | Time |
|---|---|---|
| Generate CDN image URLs from a pinned git tag | Me | 10 min |
| Finish brief §1–§6 | Me | 20 min |
| Margin check + supplier confirmation | **You** — see brief §2 and §3 | 1 hr |
| Write copy via the prompt pack | Me | 45 min |
| Compress + rename assets | Me | 30 min |
| Fill the email template | Me | 30 min |
| QA + test booking | **You** | 45 min |
| Schedule and send | You | 15 min |

Two gates are yours and cannot be delegated: **margin approval** (brief §2) and **supplier confirmation** (brief §3). Nothing sends until both are signed.
