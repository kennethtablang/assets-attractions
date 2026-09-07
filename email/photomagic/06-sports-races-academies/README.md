# Segment 06: Sports, races and academies

**Status** Versions B and C built. **Version A, the control, is not.** See [What is built](#what-is-built).
**Audience** [`apollo-audience-targeting.md`](../apollo-audience-targeting.md), section 3, "06. Sports, races and academies"
**Layout** [`email/templates/email-photomagic-card.html`](../../templates/email-photomagic-card.html), the dark card, by way of [`../03-venues-hospitality/`](../03-venues-hospitality/)
**Campaign ID** `PM-2026-09-SPORTS` · **UTM** `photomagic_sports_2026`
**Workflow** [`docs/photomagic-campaign-workflow.md`](../../../docs/photomagic-campaign-workflow.md)

Road races, tournaments, leagues, academies.

## Focus

**The strongest selfie-search case the product has**, and it is worth being
precise about why.

A marathon photographer shoots five thousand runners. The incumbent solution
is bib-number search, which fails whenever the bib is obscured by an arm, a
jacket, a water station or another runner, and that is a large fraction of
frames. A selfie does not depend on the bib being visible at all.

This is the one segment where the feature is not a convenience but a straight
replacement for a tool they already run and already complain about.

## Target

| | |
|---|---|
| **Titles** | Race Director, Event Director, Founder, Owner, Operations Manager, Marketing Manager, Head of Marketing, Community Manager, Academy Director, Club Manager, General Manager, Head of Events |
| **Employee count** | 1 to 100 |
| **Geography** | UAE core first: Dubai, Abu Dhabi, Sharjah, then the northern emirates. Ring 2 only once the core is exhausted. Search on **company** location, not contact location. |
| **Saved search** | `PM-06-sports-UAE-<yyyymm>`, one per geography, logged in the campaign register with its result count and the date it was run |

The full keyword blocks, industry values and exclusions live in the targeting
doc. They are not duplicated here, because a filter recipe copied into nine
folders is a filter recipe that will disagree with itself within a month.

## The three versions to build

| Version | Leads on | Why |
|---|---|---|
| **A** (control) | AI selfie search | See above. Lead hard, and do not bury it under a delivery promise. |
| **B** | Same-day delivery | Challenger. |
| **C** | Private galleries | Challenger. |

**Omits client photo selection.** Nobody proofs a race.

A is the control because the targeting doc predicts it will win here. B and C are
challengers. **If a challenger wins, the targeting doc was wrong about this
segment**, which is a more useful finding than a feature preference and is the
reason the prediction is written down before the send rather than after.

Filenames, following the convention segment 02 already uses. B and C exist;
A does not:

```
06-sports-va-selfie-search.html
06-sports-vb-same-day.html
06-sports-vc-private-galleries.html
```

## What is built

| Version | File | Leads on | Headline | Subjects |
|---|---|---|---|---|
| **A** (control) | **not built** | AI selfie search | | |
| **B** | [`06-sports-vb-same-day.html`](06-sports-vb-same-day.html) | same-day delivery | Photos in Their Hands Before the Drive Home | 🏁 Photos before the drive home / 🥇 Race photos, same day |
| **C** | [`06-sports-vc-private-galleries.html`](06-sports-vc-private-galleries.html) | private galleries | One Private Gallery Per Race | 🏅 One gallery per race / 🎽 Every race, its own gallery |

**Nothing here can run as a test until Version A exists.** B and C are
challengers, and two challengers with nothing to challenge is two letters rather
than an experiment. Build `06-sports-va-selfie-search.html` first, cloning one of the two files
above, then split the segment into even random thirds and send all three at the
same time of day.

**Six lines of the shared body belong to this segment, not to a version**,
because segment 02's body talks about clients and shortlists, and a race
director has entrants. Both files carry the identical set and a future Version A
must too; they are listed and justified in the header comment of the Version B
file.

**Version C has a second job.** The plan requires youth academies to be split out
of this list and handled with segment 04's posture. Version A leads on face
matching and **cannot go to that sub-list**; Version C can, and it is the better
of the two safe letters because access control is what a youth academy is asking
about. If you use it that way, it is **not a test cell** and must be excluded
from the version comparison, and its selfie bullet should be cut first. The
Version C header explains both points in full.

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

**Season.** UAE outdoor sport runs roughly October to April and the race
calendar is nearly empty in summer. Send in season or do not send.

**Minors.** An academy is a school in everything but name. Apply segment 04's
posture to any part of the list that returns youth academies, and split them
out rather than sending them the selfie-search letter. This is the one
segment whose Apollo list will contain contacts that must receive a different
letter than the rest of it, so the split has to happen before the send and
not after somebody notices.

## Before anything here can send

The blockers that hold the rest of this pipeline apply here too, and none of
them is segment specific:

| | Status |
|---|---|
| `{{POSTAL_ADDRESS}}` | **Outstanding.** photomagic.io publishes no postal address. One is legally required in bulk commercial email. It cannot be invented or borrowed from Ticket Magic's office. |
| Version A | **Not built.** The control is missing, so the A/B/C test cannot run. |
| Free plan vs 7-day trial | **Unresolved, and these letters take a side.** Campaign 01 says 7-day trial, segment 02 says free plan. B and C follow segment 02: the badge says "Free Plan Included", the button leads on the free plan, and the pricing strip shows the permanent Free tier. Still settle it against the live signup flow. |
| Prices and quotas | **Read off the live page 2026-09-01** and inherited from segment 02: Free $0, Pro $55, Corporate $150. Re-check every figure on send day. |
| Register the campaign | **Outstanding.** No row in [`docs/campaign-register.csv`](../../../docs/campaign-register.csv) yet for `PM-2026-09-SPORTS`. |

Plus the two that apply to every cold Photomagic send:

- **Apollo contacts never enter Mailchimp.** Cold third-party contacts in an
  opt-in audience is an account-termination risk, not a style preference.
- **Reply-To `inquiry@photomagic.io`**, from a photomagic.io address, never a
  Ticket Magic inbox.
