# Express Copy Prompt Pack

> Paste-ready. Do not write prompts on the day — that's where the hour goes.
> Fill the `[BRACKETS]`, paste, done. Target: full email copy in 45 minutes.

**Standing context — paste this above every prompt below:**

```
CONTEXT
Brand: Dubai Ticket Magic — we sell tickets to attractions, tours, dining
and experiences across the UAE (Dubai, Abu Dhabi, Sharjah).
Audience: mixed-nationality UAE residents and inbound tourists. English-first,
but many readers are non-native speakers — avoid idioms that don't travel.
Currency is always written "AED 199".
Voice: warm, direct, specific. We name real attractions, never
"world-class experiences". No hype, no exclamation stacking.
Never invent a price, date, or inclusion. Use only what I give you below.
```

---

## Prompt 1 — Subject lines *(ChatGPT, 5 min)*

```
Write 20 email subject lines for this campaign.

Campaign: [NAME]
Offer: [OFFER, verbatim from brief §1]
Products: [PRODUCT LIST]
Audience: [SEGMENT]
Deadline: [DATE]

Rules:
- Under 45 characters each
- Label by style: 5 curiosity, 5 benefit-led, 5 urgency, 5 specific-number
- Emoji in no more than 5
- At least one names a specific attraction
- At least one names a specific price
- Avoid: FREE in caps, multiple exclamation marks, "Act now",
  "Don't miss out", "Limited time only"

Output as a numbered list, style labelled.
```

## Prompt 2 — Shortlist *(Claude, 3 min)*

```
Here are 20 subject lines for [CAMPAIGN]. Audience: [SEGMENT].

Cut to the 2 strongest as an A/B pair. They must test a genuine
difference (e.g. benefit vs urgency), not be near-duplicates.
Flag any that risk spam filtering.
Then write 3 preview text options for the winner — 40–90 characters,
each continuing the subject rather than repeating it.

[PASTE 20 LINES]
```

## Prompt 3 — Email body *(ChatGPT, 10 min)*

```
Write the body copy for this marketing email.

Offer: [OFFER]
Deadline: [DATE]
Products: [NAME — BENEFIT — PRICE, one per line]
Audience: [SEGMENT]
CTA verb: [e.g. "Book now"]
Landing page: [URL]

Structure:
1. Headline — max 8 words
2. Subheadline — max 15 words
3. Body — 2 short paragraphs, max 60 words total
4. One line per product: name, one specific benefit, price
5. Urgency line naming the deadline
6. CTA button text — 2-4 words, same verb throughout

Constraints:
- Do not open with "In today's...", "Imagine...", or a rhetorical question
- One idea per sentence, vary sentence length
- Every claim must be verifiable from what I gave you
- Do not invent prices, inclusions, or dates
```

## Prompt 4 — Refine *(Claude, 10 min — this is the quality step)*

```
Refine this marketing email draft.

1. Cut 30% of the words without losing meaning
2. Remove AI cadence: no em-dash chains, no adjective triads,
   no "elevate/unlock/discover/seamless/curated"
3. Make every claim specific
4. Ensure the CTA verb is identical in every instance
5. VERIFY every price, date and attraction name against the offer
   sheet below and FLAG any mismatch explicitly before your rewrite
6. Check it reads naturally aloud to a UAE audience

Return: (a) any mismatches found, then (b) the refined copy.

DRAFT:
[PASTE]

OFFER SHEET (source of truth):
[PASTE brief §1 table]
```

## Prompt 5 — Flash email *(ChatGPT, 90-second lane)*

```
Write a short flash-offer email. Text-led, no product grid.

Offer: [OFFER]
Deadline: [DATE — usually 48-72h]
Product: [SINGLE PRODUCT]
Price: [WAS] → [NOW]
Link: [URL]

Give me:
- Subject line under 40 chars conveying genuine urgency
- Preview text
- Headline, max 6 words
- 40 words of body maximum
- CTA, 2-3 words

Urgency must come from the real deadline and the real saving,
not from manufactured pressure.
```

## Prompt 6 — Social + WhatsApp *(ChatGPT, 5 min)*

```
From this email copy, write:
- 3 Instagram captions (max 125 chars before the fold, 3-5 hashtags,
  UAE-relevant)
- 1 Instagram story frame (max 12 words, works as text over an image)
- 2 WhatsApp broadcast messages (max 50 words, conversational,
  link at the end)

Keep the same offer, deadline and CTA verb.

[PASTE EMAIL COPY]
```

## Prompt 7 — Final check *(Claude, 3 min — run before QA)*

```
Cross-check this finished email against the offer sheet.
List ONLY mismatches and errors — no praise, no suggestions.

Check: every price, every date, every attraction name spelling,
discount arithmetic, promo code, currency format (AED 199),
CTA verb consistency, and any leftover placeholder text.

If everything matches, reply exactly: "No mismatches found."

EMAIL: [PASTE]
OFFER SHEET: [PASTE]
```

---

## Speed notes

- **Prompt 4 and Prompt 7 are the ones you cannot skip.** They catch the price and date errors that make an email unrecoverable.
- Paste your swipe file of past winning subject lines into Prompt 1 as style reference. Output quality rises sharply.
- If you find yourself editing an output more than twice, the input was underspecified — go back and add detail rather than iterating.
- Save each campaign's filled prompts into the campaign folder. Next time it's an edit, not a rewrite.
