# B2B Outreach Emails — Version A

Two paste-ready Mailchimp emails built from `email/templates/email.html`, with copy taken
verbatim from `email/templates/TicketMagic_Email_Copy_Library (1).docx`.

| File | Copy source | Segment | Goal |
|---|---|---|---|
| `01-organizer-platform-pitch-va.html` | Email 1 — Organizer Platform Pitch, **Version A** | Events Services / Entertainment · Dubai & Abu Dhabi | Organizers run ticketing on Ticket Magic |
| `02-attraction-listing-invite-va.html` | Email 2 — Attraction Listing Invite, **Version A** | Attractions / Leisure / Travel & Tourism · UAE-wide | Onboard supply-side listings |

Both are `PLANNING` — nothing has been sent, and neither is in `docs/campaign-register.csv` yet.

---

## Subject and preheader

Set these in Mailchimp; they are not in the HTML except as reference in the file header.

**Email 1**
- Subject: `Sell out your next event?`
- Preheader: `Registration, QR check-in, and live sales in one dashboard.` *(58 chars)*

**Email 2**
- Subject: `Put your attraction in front of UAE event-goers`
- Preheader: `List your attraction on Ticket Magic — no upfront cost.` *(55 chars)*

Both preheaders sit inside the 40–90 char window in `marketing-campaign-os.md` §, and neither
repeats its subject. Neither subject contains a variable, so there is nothing to configure and
nothing that can send as a blank.

---

## Personalisation: there isn't any, deliberately

**These emails contain no merge tags.** Every recipient receives byte-identical copy. There is
no audience field to create, no default value to set, and no way for a blank to appear
mid-sentence.

The copy library's `{First Name}` / `{Company}` / `{Job Title}` / `{City}` tokens were resolved
into real wording instead. Five edits, all forced by removing the variables:

| Library line | Sent as |
|---|---|
| `Hi {First Name},` | `Hi there,` |
| `Running events in {City} means…built for the UAE market.` | `Running events in the UAE means…built for **this** market.` |
| `As {Job Title} at {Company}, you'd get:` | `Here's what you'd get:` |
| `We'd like to list {Company} so travelers…` | `We'd like to list **your attraction** so travelers…` |
| `If reaching more visitors in {City}…` | `If reaching more visitors **across the UAE**…` |

The second row is the only one that touches wording the variable didn't occupy: with `{City}`
resolved to "the UAE", the original "built for the UAE market" put *UAE* twice in one short
paragraph, so the closing phrase became "built for this market".

Subject lines changed for the same reason — `Sell out your next {City} event, {First Name}?`
became `Sell out your next event?`, and `Put {Company} in front of UAE event-goers` became
`Put your attraction in front of UAE event-goers`.

### The four tags still in the footer are not personalisation

`*|UNSUB|*`, `*|UPDATE_PROFILE|*`, `*|LIST:ADDRESS|*` and `*|CURRENT_YEAR|*` are Mailchimp
**system** tags. They are legally required, the base template forbids replacing them, and they
resolve automatically on send with nothing to configure. They will look unresolved in preview —
that is expected and is not a bug.

### If you later want personalisation back

Mailchimp has no inline fallback syntax for audience fields — there is no `*|FNAME:there|*`; the
colon form works only on system tags. The supported route is a plain `*|FNAME|*` plus a
[Default merge tag value](https://mailchimp.com/help/set-default-merge-values/) set per field in
Audience settings. Worth knowing that a first-name default reads badly in a subject line
("Sell out your next event, there?"), which is part of why the tagless version is cleaner here.

**Sending from Apollo instead?** Nothing to convert in the body. Just delete the four footer
system tags and put a real opt-out line in their place — Apollo won't resolve them, and a dead
unsubscribe link is a legal problem, not a cosmetic one.

---

## Images

One image per email: the logo. Pinned to an immutable commit SHA, per the template's rule.

```
https://cdn.jsdelivr.net/gh/kennethtablang/assets-attractions@ec8ba53204c68457e9ff5c02539eb771d79d942d/assets/summer_is_here_campaign/ticketmagiclogo.png
```

Verified live: **HTTP 200, `image/png`, 17,064 bytes** — byte-identical to the file on disk, so
the repo is public and jsDelivr is serving it. `ec8ba53` is the commit that added the logo to
`assets/summer_is_here_campaign/`; it is already on `origin/main`, so no tag or push is needed.

Neither email uses a hero photo. There is no cleared B2B photography in the repo, and a
stock-looking crowd shot on a cold partnership pitch reads as an ad, not as a note from a person.
Both heroes are type-led instead.

---

## Design notes — the deliberate departures from the base template

| Change | Why |
|---|---|
| Logo sits on a **cream** header, not the navy bar | The PNG is transparent with black linework and a gold frame. On navy the outline disappears. It needs a light ground — a 5px yellow rule caps the email so the header still reads as a bar. |
| Header badge wrapped in its own nested table | `background-color` on an `align="right"` cell fills the entire cell, so the badge stretched edge to edge. The base template has the same latent bug. |
| Product cards → **module cards** (Email 1) and a **You control / We handle** split (Email 2) | These emails sell a platform, not seven attractions. No prices, no images, no card links. |
| Urgency strip **dropped** (Email 1), **repurposed** (Email 2) | Neither offer has a deadline. Email 2's yellow strip carries "There's no upfront cost — we succeed when you do" instead of invented scarcity. |
| Primary CTA is a `mailto:`, not a booking link | The copy's ask is "just reply". The button is a nudge; the real mechanism is the Reply-To header. |
| Footer recipient line rewritten | The template says *"you signed up at ticketmagic.me"*. For cold B2B prospecting that is **false**. Both files now say the recipient is on a UAE organiser / attraction list, and invite a forward: *"Not the right person? Reply and tell us who is."* |
| A sentence pulled out of each letter into a graphic block | The marketplace/control line (Email 1) and the no-upfront-cost line (Email 2) each appear **once** — in the teal quote and the yellow strip. They are not repeated in the body. |

Palette, fonts, perforation motif, mobile breakpoint, mso button fallbacks, and Block 9 are
unchanged from the house template.

---

## QA status

| Check | Email 1 | Email 2 |
|---|---|---|
| Total HTML size (Gmail clips ~102 KB) | 21.3 KB | 21.8 KB |
| `{{TOKEN}}` placeholders remaining | 0 | 0 |
| Personalisation variables remaining | 0 | 0 |
| Footer system tags present and untouched | ✅ 4/4 | ✅ 4/4 |
| `<tr>`/`<td>`/`<table>` balanced | ✅ | ✅ |
| mso conditional blocks paired | ✅ 5/5 | ✅ 5/5 |
| Rendered desktop 600px | ✅ | ✅ |
| Rendered mobile 420px — cards stack, no h-scroll | ✅ | ✅ |
| Logo URL returns 200 | ✅ | ✅ |
| Unsubscribe + `LIST:ADDRESS` present | ✅ | ✅ |

Not yet done — these need a real Mailchimp account and a test list, per
`docs/marketing-campaign-os.md` (QA stage):

- [ ] Seed test to Gmail, Outlook desktop, Apple Mail, and one mobile-only inbox
- [ ] Dark-mode render check (Apple Mail / Outlook.com)
- [ ] Images-off render — alt text is only `Ticket Magic`; confirm the email still makes sense
- [ ] Click every link, confirm the UTM lands in GA4 Realtime
- [ ] Second-person review

---

## Open items — I picked a default for each rather than blocking

| # | Item | What I used | Change it if… |
|---|---|---|---|
| 1 | **Reply address** | `support@ticketmagic.me` — the only address in the house footer | A `partnerships@` inbox exists. Email 2 is signed "Partnerships, Ticket Magic", so a shared support queue is the weaker option. Update the two `mailto:` links and set Mailchimp's Reply-To to match. |
| 2 | **Website domain** | `https://dubai.ticketmagic.me` — **verified live, HTTP 200**; `ticketmagic.me` redirects to it | Nothing. But note `marketing-campaign-os.md` §9.1 uses `dubaiticketmagic.com` in its UTM examples and **that domain does not resolve** — the doc is stale and will mislead the next person who builds from it. |
| 3 | **UTM campaign values** | `organizer_pitch_2026` and `attraction_listing_2026` | You prefer shorter codes. Whatever you choose, register it — §9.1 says one UTM campaign value is one campaign, forever. Neither is in `campaign-register.csv` yet. |
| 4 | **Logo resolution** | 147 × 75 source, displayed at 120px | It will look soft on retina. A 2× export (~360 × 184, ≤40 KB) dropped in at the same path would fix it. `ticetmagiclogo.png` in the same folder is 500 × 250 but has an **opaque** background and a misspelled filename, so it is not a drop-in substitute. |
| 5 | **British vs American spelling** | Library copy left **verbatim** (`travelers`); my added UI text is British (`organisers`, `travellers`) | You want one convention throughout. Say which and I'll normalise both files. |

---

## A note on the format

These two emails ask for a **reply**, and heavily designed HTML measurably underperforms plain
text on reply-goal B2B outreach — a branded template reads as a broadcast, and people answer
notes, not broadcasts. You asked for a layout, so that is what these are, and they are built
properly. But the highest-value test here is not Version A vs B vs C. It is **this design
versus the same Version A copy sent as plain text from a person's own address.**

`plain-text.md` in this folder has both, ready to paste, if you want to run that.
