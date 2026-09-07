# Segment 08: Nonprofits, charity galas and community events

**Status** Versions B and C built. **Version A, the control, is not.** See [What is built](#what-is-built).
**Audience** [`apollo-audience-targeting.md`](../apollo-audience-targeting.md), section 3, "08. Nonprofits, charity galas and community events"
**Layout** [`email/templates/email-photomagic-card.html`](../../templates/email-photomagic-card.html), the dark card, by way of [`../03-venues-hospitality/`](../03-venues-hospitality/)
**Campaign ID** `PM-2026-09-NONPROFITS` · **UTM** `photomagic_nonprofits_2026`
**Workflow** [`docs/photomagic-campaign-workflow.md`](../../../docs/photomagic-campaign-workflow.md)

Fundraising galas, awards nights, community iftars, volunteer days.

## Focus

**The pitch is the news cycle, not the photography.** A fundraiser's thank-you
email goes out within forty-eight hours or it does not go out at all, and the
photographs are what makes it worth opening. A gallery that arrives the
following week arrives after the moment the whole event was staged to create.

## Target

| | |
|---|---|
| **Titles** | Executive Director, Development Manager, Head of Fundraising, Fundraising Manager, Communications Manager, Head of Communications, Marketing Manager, Events Manager, Programme Manager, Program Manager, Community Manager, Founder |
| **Employee count** | 2 to 200 |
| **Geography** | UAE core first: Dubai, Abu Dhabi, Sharjah, then the northern emirates. Ring 2 only once the core is exhausted. Search on **company** location, not contact location. |
| **Saved search** | `PM-08-nonprofits-UAE-<yyyymm>`, one per geography, logged in the campaign register with its result count and the date it was run |

The full keyword blocks, industry values and exclusions live in the targeting
doc. They are not duplicated here, because a filter recipe copied into nine
folders is a filter recipe that will disagree with itself within a month.

## The three versions to build

| Version | Leads on | Why |
|---|---|---|
| **A** (control) | Same-day delivery | See above. The deadline is the product here. |
| **B** | Private galleries | Challenger. |
| **C** | AI selfie search | Challenger. |

**Omits client photo selection.** There is no client to proof for.

A is the control because the targeting doc predicts it will win here. B and C are
challengers. **If a challenger wins, the targeting doc was wrong about this
segment**, which is a more useful finding than a feature preference and is the
reason the prediction is written down before the send rather than after.

Filenames, following the convention segment 02 already uses. B and C exist;
A does not:

```
08-nonprofits-va-same-day.html
08-nonprofits-vb-private-galleries.html
08-nonprofits-vc-selfie-search.html
```

## What is built

| Version | File | Leads on | Headline | Subjects |
|---|---|---|---|---|
| **A** (control) | **not built** | same-day delivery | | |
| **B** | [`08-nonprofits-vb-private-galleries.html`](08-nonprofits-vb-private-galleries.html) | private galleries | A Gallery Only Your Guests Can Open | 🤝 A gallery only guests open / 🔑 Who sees your gala photos? |
| **C** | [`08-nonprofits-vc-selfie-search.html`](08-nonprofits-vc-selfie-search.html) | AI selfie search | One Selfie, and They Find Themselves | 🙌 Guests find themselves / 💬 Photos your donors share |

**Nothing here can run as a test until Version A exists.** B and C are
challengers, and two challengers with nothing to challenge is two letters rather
than an experiment. Build `08-nonprofits-va-same-day.html` first, cloning one of the two files
above, then split the segment into even random thirds and send all three at the
same time of day.

**Four lines of the shared body belong to this segment, not to a version**,
because segment 02's body happens to fit a fundraiser well, so this is the
lightest set of segment edits in the pipeline. Both files carry the identical
set and a future Version A must too; they are listed and justified in the header
comment of the Version B file.

**One line was deliberately left alone.** Showcase card 4 still says the guest
login means "the data stays with you and follow up is a real list". That sentence
was cut from segments 04 and 07, where lead capture on schoolchildren or on staff
is the wrong claim. Here it is the right one: donor stewardship is the job. Do
not "fix" it to match them.

**Version C is the one to hold back** if the Apollo list returns direct-service
charities rather than galas and awards nights. Face search across beneficiary
photographs is a different conversation than face search across a ballroom of
donors, and the copy stays on guests and donors for exactly that reason.

## When you build Version A

**Clone one of the letters above, never the template.** That is the house rule
across this repository and it is why these campaigns are guaranteed to share a
layout rather than merely intended to: campaign 01, segment 02 and segments 03
through 08 all carry the same 441-line body. If you restyle one, restyle all of
them.

Only these slots may differ between A, B and C: title, preheader, hero chip,
headline (including which words carry the orange span), hero subhead, opening
card heading, opening card paragraph, the lead line above the primary button, the
closing band heading, the closing band paragraph, and `utm_content` on both
buttons. Everything else, including all four feature shots, both benefit columns,
the three steps, the band photograph, the testimonial and the whole pricing
strip, is held byte-identical.

All three versions of a segment are **structurally identical** and differ only in
the lead promise: title, preheader, hero chip, headline, hero subhead, opening
card heading, opening card paragraph, the lead line above the button, and
`utm_content` on both buttons. Everything else, including all four feature cards,
is held byte-identical. Segment 02's README carries the verification script.

## Watch for

**Price sensitivity is real here and the letters must respect it.** Lead on
the free tier and let the pricing strip do the rest. Do not open a nonprofit
letter on Corporate at 150 dollars a month.

**A meaningful share of UAE charities are government linked or royal
foundations**, which reintroduces exactly the procurement cycle this ICP is
built to avoid. Expect to split the list into independents and government
linked, and expect the independents to be the ones that reply.

## Before anything here can send

The blockers that hold the rest of this pipeline apply here too, and none of
them is segment specific:

| | Status |
|---|---|
| `{{POSTAL_ADDRESS}}` | **Outstanding.** photomagic.io publishes no postal address. One is legally required in bulk commercial email. It cannot be invented or borrowed from Ticket Magic's office. |
| Version A | **Not built.** The control is missing, so the A/B/C test cannot run. |
| Free plan vs 7-day trial | **Unresolved, and these letters take a side.** Campaign 01 says 7-day trial, segment 02 says free plan. B and C follow segment 02: the badge says "Free Plan Included", the button leads on the free plan, and the pricing strip shows the permanent Free tier. Still settle it against the live signup flow. |
| Prices and quotas | **Read off the live page 2026-09-01** and inherited from segment 02: Free $0, Pro $55, Corporate $150. Re-check every figure on send day. |
| Register the campaign | **Outstanding.** No row in [`docs/campaign-register.csv`](../../../docs/campaign-register.csv) yet for `PM-2026-09-NONPROFITS`. |

Plus the two that apply to every cold Photomagic send:

- **Apollo contacts never enter Mailchimp.** Cold third-party contacts in an
  opt-in audience is an account-termination risk, not a style preference.
- **Reply-To `inquiry@photomagic.io`**, from a photomagic.io address, never a
  Ticket Magic inbox.
