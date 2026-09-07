# Segment 05: Wedding planners and bridal

**Status** Versions A and B built. C outstanding.
**Audience** [`apollo-audience-targeting.md`](../apollo-audience-targeting.md), section 3, "05. Wedding planners and bridal"
**Layout** [`email/templates/email-photomagic-card.html`](../../templates/email-photomagic-card.html), the dark card, by way of [`../02-event-planners-teams/`](../02-event-planners-teams/)
**Campaign ID** `PM-2026-09-WEDDINGS` · **UTM** `photomagic_weddings_2026`
**Workflow** [`docs/photomagic-campaign-workflow.md`](../../../docs/photomagic-campaign-workflow.md)

Weddings, engagements, and the whole run of events around them.

## Focus

Adjacent to segments 01 and 02 but a different vocabulary and a different
season, which is why it gets its own search rather than a keyword bolted onto
photographers. This segment already talks to couples about proofing and
picking favourites, so the product's selection feature arrives in language
they use rather than language they have to learn.

## Target

| | |
|---|---|
| **Titles** | Wedding Planner, Owner, Founder, Creative Director, Lead Planner, Client Manager, Operations Manager |
| **Employee count** | 1 to 30 |
| **Geography** | UAE core first: Dubai, Abu Dhabi, Sharjah, then the northern emirates. Ring 2 only once the core is exhausted. Search on **company** location, not contact location. |
| **Saved search** | `PM-05-weddings-UAE-<yyyymm>`, one per geography, logged in the campaign register with its result count and the date it was run |

The full keyword blocks, industry values and exclusions live in the targeting
doc. They are not duplicated here, because a filter recipe copied into nine
folders is a filter recipe that will disagree with itself within a month.

## The three versions to build

| Version | Leads on | Why |
|---|---|---|
| **A** (control) | Client photo selection | Proofing and shortlisting is the conversation this segment is already having every week, and it is the only segment where selection is the lead promise. |
| **B** | Same-day delivery | Challenger. |
| **C** | AI selfie search | Challenger. |

**Omits private galleries.** A couple hears it as a feature for somebody else's compliance department.

A is the control because the targeting doc predicts it will win here. B and C are
challengers. **If a challenger wins, the targeting doc was wrong about this
segment**, which is a more useful finding than a feature preference and is the
reason the prediction is written down before the send rather than after.

Filenames, following the convention segment 02 already uses. A and B exist;
C does not yet:

```
05-wedding-planners-va-photo-selection.html  BUILT, the control
05-wedding-planners-vb-same-day.html         BUILT, challenger
05-wedding-planners-vc-selfie-search.html    not built
```

**A and B together are a two-way test, not the three-way one above.** That is
sendable as it stands. It is just not the whole experiment.

## The body is a clone of segment 02

Version A was built from
[`../02-event-planners-teams/02-event-planners-va-same-day.html`](../02-event-planners-teams/02-event-planners-va-same-day.html),
**not** from the template. Cloning the shipped sibling is the house rule across
this repository, and it is why these campaigns are guaranteed to share a layout
rather than merely intended to: same blocks, same order, same measurements, same
feature shots, same 441-line body.

**If you restyle one, restyle all of them.** That is now campaign 01, segment 02,
and segments 03, 04 and 05.

## The list is cold and the layout is the warm one

The workflow doc pairs the dark card with a warm list and pairs cold outreach
with [`email-photomagic.html`](../../templates/email-photomagic.html), the flat
white letter. This campaign uses the card layout on an Apollo-sourced list, the
same deliberate departure segment 02 made and recorded.

**What that costs, so nobody is surprised by the numbers:** a stranger's first
email looking like a product announcement sets a different expectation than a
plain note from a person, and cold reply rates on a designed email are usually
lower than on a plain one even when the click rate is higher.

**Judge this against segment 02 and campaign 01**, which share its layout, rather
than against the EMS cold letters in [`../../outreach/`](../../outreach/), which
do not. If the reply rate comes back poor, **the layout is the first thing to
test, not the copy**, and the light template already exists for that experiment.

## When you build C

**Clone `05-wedding-planners-vb-same-day.html` or the Version A file, not the
template.** Either is a shipped sibling for this segment, and both carry the
same 441-line body as segment 02 and campaign 01. Cloning the template instead
would put a layout variable into an A/B/C test that is supposed to carry only a
copy variable.

Version C leads on **AI selfie search**, per the table above.
The slots that may differ, and the long list of what is held byte-identical,
are written out in the header comment of the Version A file.

**Version A departs from segment 02's held-identical body in three lines**, all
of them changing "the client" to "the couple". That is this segment's whole
vocabulary argument. The header comment of the Version A file lists them.
**Version B already carries all three and Version C must too**: they belong to
the segment, not to the version.

## What Version B says

| | |
|---|---|
| **File** | [`05-wedding-planners-vb-same-day.html`](05-wedding-planners-vb-same-day.html) |
| **Leads on** | same-day delivery |
| **Headline** | The Couple Has the Photos the Same Night |
| **Hero chip** | the version marker, so a reply that quotes it names the version |
| **Subjects** | 💐 Photos before the last dance / 🎊 Same night, not next month |
| **Offer** | Free plan, inherited from Version A unchanged |

Eight copy slots moved from Version A and nothing else did.

**What this letter promises, and what it does not.** Not an edited wedding album
the same night. It promises that the guests and the couple have shareable
photographs from the reception before they leave it, while the edit runs on its
own timetable. A planner reads a same-day claim against a delivery schedule they
know well, and an overstated one loses the reply on the first sentence. If
somebody strengthens this copy later, that is the line to keep honest.

## What Version A says

| | |
|---|---|
| **File** | [`05-wedding-planners-va-photo-selection.html`](05-wedding-planners-va-photo-selection.html) |
| **Leads on** | client photo selection |
| **Headline** | Let the Couple Pick Their Own Favorites |
| **Hero chip** | the version marker, so a reply that quotes it names the version |
| **Subjects** | 💍 Let the couple shortlist / 💌 One gallery, one final list |
| **Offer** | Free plan, with segment 02's pricing strip inherited unchanged |

## Watch for

**The sharpest seasonality in the pipeline.** UAE wedding season runs roughly
October to April and this segment is close to unreachable in July. A flat
result in August means the month, not the message. Do not draw a conclusion
about the copy from an out-of-season send.

## Before anything here can send

The blockers that hold the rest of this pipeline apply here too, and none of
them is segment specific:

| | Status |
|---|---|
| `{{POSTAL_ADDRESS}}` | **Outstanding.** photomagic.io publishes no postal address. One is legally required in bulk commercial email. It cannot be invented or borrowed from Ticket Magic's office. |
| Free plan vs 7-day trial | **Unresolved, and Version A takes a side.** Campaign 01 says 7-day trial, segment 02 says free plan. Version A follows segment 02: the badge says "Free Plan Included", the button leads on the free plan, and the pricing strip below it shows the permanent Free tier, so nothing promised is contradicted one screen later. Still settle it against the live signup flow, then make every campaign say the same thing. |
| Prices and quotas | **Read off the live page 2026-09-01** and inherited from segment 02: Free $0, Pro $55, Corporate $150. Re-check every figure on send day. A sent email is frozen and a wrong price is a refund conversation later. |
| Register the campaign | **Outstanding.** No row in [`docs/campaign-register.csv`](../../../docs/campaign-register.csv) yet. Campaign 01 and segment 02 have none either; add them together rather than leaving the register describing part of the pipeline. |

Plus the two that apply to every cold Photomagic send:

- **Apollo contacts never enter Mailchimp.** Cold third-party contacts in an
  opt-in audience is an account-termination risk, not a style preference.
- **Reply-To `inquiry@photomagic.io`**, from a photomagic.io address, never a
  Ticket Magic inbox.
