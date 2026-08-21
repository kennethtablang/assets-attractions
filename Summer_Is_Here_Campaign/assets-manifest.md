# Assets Manifest — Summer Is Here

> **👉 This is the file to fill in.** Everything else is blocked on it.
> Replace every `⬜` with a real value. Leave a row out entirely if the product isn't in the campaign.

---

## 1. Products

One row per attraction. **Product name**, **booking link**, and **prices** are what I need most — the CDN column I generate myself once the repo is tagged.

### Product 1 — Desert Safari

| Field | Value |
|---|---|
| Exact customer-facing name | ⬜ *(e.g. "Evening Desert Safari with BBQ Dinner")* |
| One-line benefit (max 8 words) | ⬜ |
| Normal price (AED) | ⬜ |
| Campaign price (AED) | ⬜ |
| Net cost to us (AED) — *private* | ⬜ |
| Booking page URL | ⬜ |
| Source image | `assets/summer_is_here_campaign/Desert.jpg` |
| Image cleared for use? | ⬜ Yes / No |
| Available through 31 Aug, no blackouts? | ⬜ Yes / No |

### Product 2 — Louvre Abu Dhabi

| Field | Value |
|---|---|
| Exact customer-facing name | ⬜ |
| One-line benefit | ⬜ |
| Normal price (AED) | ⬜ |
| Campaign price (AED) | ⬜ |
| Net cost (AED) — *private* | ⬜ |
| Booking page URL | ⬜ |
| Source image | `assets/summer_is_here_campaign/Louvre.jpg` |
| Image cleared for use? | ⬜ |
| Available, no blackouts? | ⬜ |

### Product 3 — Zayed National Museum

| Field | Value |
|---|---|
| Exact customer-facing name | ⬜ |
| One-line benefit | ⬜ |
| Normal price (AED) | ⬜ |
| Campaign price (AED) | ⬜ |
| Net cost (AED) — *private* | ⬜ |
| Booking page URL | ⬜ |
| Source image | `assets/summer_is_here_campaign/Zayed National Museum.jpg` |
| Image cleared for use? | ⬜ |
| Available, no blackouts? | ⬜ |

### Product 4 — Natural / National History Museum ❓

> **Please confirm the name.** The file is `National History Museum.jpg`, but the Saadiyat attraction is the **Natural** History Museum Abu Dhabi. If it's that one, the filename is wrong and I'll fix it.

| Field | Value |
|---|---|
| Correct name | ⬜ |
| One-line benefit | ⬜ |
| Normal price (AED) | ⬜ |
| Campaign price (AED) | ⬜ |
| Net cost (AED) — *private* | ⬜ |
| Booking page URL | ⬜ |
| Source image | `assets/summer_is_here_campaign/National History Museum.jpg` |
| Image cleared for use? | ⬜ |
| Available, no blackouts? | ⬜ |

### Product 5 — Tandem Skydive

| Field | Value |
|---|---|
| Exact customer-facing name | ⬜ *(Palm dropzone or Desert dropzone?)* |
| One-line benefit | ⬜ |
| Normal price (AED) | ⬜ |
| Campaign price (AED) | ⬜ |
| Net cost (AED) — *private* | ⬜ |
| Booking page URL | ⬜ |
| Source image | `assets/summer_is_here_campaign/tandemskydive.jpg` |
| Image cleared for use? | ⬜ |
| Available, no blackouts? | ⬜ |

### Product 6 — Private Charter Poseidon

> Filename reads **"Posiedon"** — misspelled. I'll correct it to "Poseidon" unless the vessel is genuinely spelled that way.

| Field | Value |
|---|---|
| Exact customer-facing name | ⬜ |
| One-line benefit | ⬜ |
| Normal price (AED) | ⬜ |
| Campaign price (AED) | ⬜ |
| Net cost (AED) — *private* | ⬜ |
| Booking page URL | ⬜ |
| Capacity / duration | ⬜ |
| Source image | `assets/summer_is_here_campaign/Private Charter Posiedon.png` |
| Image cleared for use? | ⬜ |
| Available, no blackouts? | ⬜ |

### Product 7 — "Wikit" ❓

> **I don't know what this is.** Attraction? Waterpark? Brand? Tell me and I'll fill the rest.

| Field | Value |
|---|---|
| What is it? | ⬜ |
| Exact customer-facing name | ⬜ |
| One-line benefit | ⬜ |
| Normal price (AED) | ⬜ |
| Campaign price (AED) | ⬜ |
| Net cost (AED) — *private* | ⬜ |
| Booking page URL | ⬜ |
| Source image | `assets/summer_is_here_campaign/Wikit.png` |
| Image cleared for use? | ⬜ |
| Available, no blackouts? | ⬜ |

---

## 2. Campaign-level inputs

| Field | Value | Notes |
|---|---|---|
| Landing page URL | ⬜ | Does a summer page exist, or send traffic to the homepage? |
| Promo code | ⬜ | Leave blank if the price is already discounted at checkout |
| Offer deadline | **31 Aug 2026** | ✅ Locked |
| Send date | **Thu 13 Aug 2026, 17:00–19:00 GST** | ✅ Locked |
| Brand colour (hex) | ⬜ | Template currently uses placeholder `#C8102E` |
| Website URL | ⬜ | e.g. `https://dubaiticketmagic.com` |
| Is `assets-attractions` repo public? | ⬜ Yes / No | **Must be public** for CDN image links to work |
| Mailchimp segment to send to | ⬜ | e.g. UAE residents, families |
| Approximate list size | ⬜ | Determines whether A/B testing is worth running |

---

## 3. Image URLs — I generate these, don't fill them in

Once you confirm the repo is public and I've compressed and renamed the assets, I'll tag the campaign and produce URLs in this form:

```
https://cdn.jsdelivr.net/gh/kennethtablang/assets-attractions@campaign/2026-summer/campaigns/2026/08-summer-is-here/email/summer-2026-email-card-desert-safari-580x580.jpg
```

| Asset | Target spec | CDN URL |
|---|---|---|
| Logo | 1200×400, ≤40 KB | *(generated)* |
| Hero | 1200×800, ≤150 KB | *(generated)* |
| Card — Desert Safari | 580×580, ≤80 KB | *(generated)* |
| Card — Louvre | 580×580, ≤80 KB | *(generated)* |
| Card — Zayed National Museum | 580×580, ≤80 KB | *(generated)* |
| Card — History Museum | 580×580, ≤80 KB | *(generated)* |
| Card — Tandem Skydive | 580×580, ≤80 KB | *(generated)* |
| Card — Private Charter | 580×580, ≤80 KB | *(generated)* |
| Card — Wikit | 580×580, ≤80 KB | *(generated)* |

**Note on current file sizes:** every source image is 680–850 KB. They must come down to ≤80 KB for cards and ≤150 KB for the hero, or Gmail will clip the email and break the unsubscribe link. I'll handle the compression.

---

## 4. A note on card count

Seven products is more than an email should carry. Six is the practical ceiling, and 3–4 converts better — a long grid makes readers choose nothing.

**Suggested:** pick **4 hero products** for the email, and let the landing page carry all seven. Tell me which four, or I'll propose a mix once I see the prices.
