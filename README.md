# assets-attractions

Public asset repository for **Dubai Ticket Magic / Pure Magic** marketing campaigns.

> ⚠️ **This repository is public.** It exists to serve images over a free CDN into emails and landing pages.
> Never commit here: contact lists, Apollo exports, margins, supplier pricing, contracts, API keys, or any campaign strategy.
> Those belong in the private `marketing-ops` repository.

The full operating system this repo supports is documented in [`docs/marketing-campaign-os.md`](docs/marketing-campaign-os.md).

**Photomagic runs a separate pipeline.** Photomagic (photomagic.io) is a different
product with a different audience, sender, template and Mailchimp list. Its workflow is
[`docs/photomagic-campaign-workflow.md`](docs/photomagic-campaign-workflow.md); do not
read the Ticket Magic operating system as if it covers it.

---

## Folder structure

```
brand/                       Logos, colour and font references
attractions/                 Reusable, campaign-independent product imagery
campaigns/{yyyy}/{mm}-{slug}/
  ├── email/                 Email header, hero, product cards
  ├── social/                Instagram feed, story, Facebook, LinkedIn
  ├── web/                   Website banners, OG images
  └── manifest.json          Generated: filename → CDN URL → byte size
```

---

## Filename convention

```
{campaign-code}-{yyyy}-{channel}-{asset-type}-{descriptor}-{WxH}.{ext}
```

**All lowercase. Hyphens only. No spaces. No special characters.**

Spaces in filenames become `%20` in URLs and break in some email clients and CDNs — this is not a style preference.

```
✅ bts-2026-email-hero-family-desert-1200x800.jpg
✅ summer-2026-ig-story-1080x1920.jpg
✅ ticket-magic-logo-primary.png

❌ National History Museum.jpg
❌ Private Charter Posiedon.png
```

---

## Weight budgets — enforced

| Asset | Design size | Export | Max weight | Format |
|---|---|---|---|---|
| Email header | 600×200 | 1200×400 | **40 KB** | PNG |
| Email hero | 600×400 | 1200×800 | **150 KB** | JPG q80 |
| Email card (2-col) | 290×290 | 580×580 | **80 KB** | JPG q80 |
| Email card (full) | 600×300 | 1200×600 | **100 KB** | JPG q80 |
| Website hero banner | 1920×600 | 1920×600 | **200 KB** | WebP + JPG |
| Website card | 800×600 | 800×600 | **100 KB** | WebP |
| Open Graph | 1200×630 | 1200×630 | **150 KB** | JPG |
| Instagram feed (portrait) | 1080×1350 | — | **300 KB** | JPG |
| Instagram / FB story | 1080×1920 | — | **300 KB** | JPG |
| Facebook feed | 1200×630 | — | **300 KB** | JPG |
| LinkedIn | 1200×627 | — | **300 KB** | JPG |
| WhatsApp broadcast | 1080×1080 | — | **200 KB** | JPG |

**Why this matters:** Gmail clips emails above ~102 KB of HTML, which hides the footer and breaks the unsubscribe link. Heavy images also tank engagement on mobile data — and 70–85% of UAE traffic is mobile.

Compress with [Squoosh](https://squoosh.app) before committing, or let the `optimize-images` workflow handle it.

---

## Serving images via CDN

Use **jsDelivr**, which serves any public GitHub repo over a global CDN for free:

```
https://cdn.jsdelivr.net/gh/kennethtablang/assets-attractions@{tag}/campaigns/2026/08-back-to-school/email/bts-2026-email-hero-1200x800.jpg
```

**Rules:**

1. **Always pin to a git tag or commit SHA — never `@main`.**
   jsDelivr caches `@main` for up to 7 days. If you replace an image after sending an email, some subscribers see the old version and some see the new one. A pinned tag is immutable.

2. **Tag at asset freeze**, before the email is built:
   ```bash
   git tag campaign/2026-bts
   git push origin campaign/2026-bts
   ```

3. **Never use `raw.githubusercontent.com` in email.** It is not a CDN, it is rate-limited, and some corporate mail filters block it.

---

## Adding a campaign

```bash
mkdir -p campaigns/2026/08-back-to-school/{email,social,web}
# add assets, correctly named and compressed
git add campaigns/2026/08-back-to-school
git commit -m "Add Back to School 2026 campaign assets"
git tag campaign/2026-bts && git push origin main --tags
```

Then generate CDN URLs from the pinned tag and record the base URL in the campaign register.
