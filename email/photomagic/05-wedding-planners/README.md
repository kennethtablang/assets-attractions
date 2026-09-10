# Segment 05: Wedding planners and bridal

**Status** Versions A, B and C built. Complete.
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

## The four versions

| Version | Leads on | Why |
|---|---|---|
| **A** (control) | Client photo selection | Proofing and shortlisting is the conversation this segment is already having every week, and it is the only segment where selection is the lead promise. |
| **B** | Same-day delivery | Challenger. |
| **C** | AI selfie search | Challenger. |
| **D** | Private galleries | Challenger, and a test of the omission below rather than of a feature. |

**The plan omitted private galleries**, on the grounds that a couple hears it as
a feature for somebody else's compliance department. **That objection is to a
register, not to a capability**, and Version D takes it seriously: the feature is
sold in the couple's own language, and the words *private, secure, security,
access, control, permission, authorised, compliance, data* and *policy* appear
nowhere in the copy it wrote. The headline says the photographs stay with the
wedding. If D loses, the omission was right however it is worded. If D wins, the
objection was to the vocabulary alone, which segment 08 could borrow.

A is the control because the targeting doc predicts it will win here. B and C are
challengers. **If a challenger wins, the targeting doc was wrong about this
segment**, which is a more useful finding than a feature preference and is the
reason the prediction is written down before the send rather than after.

Filenames, following the convention segment 02 already uses. All four exist:

```
05-wedding-planners-va-photo-selection.html    BUILT, the control
05-wedding-planners-vb-same-day.html           BUILT, challenger
05-wedding-planners-vc-selfie-search.html      BUILT, challenger
05-wedding-planners-vd-private-galleries.html  BUILT, challenger
```

**This is a four-way test now, and this folder is where that hurts most.** The
Apollo filter here runs 1 to 30 employees, so it is the thinnest list in the
pipeline before it is split at all. Four versions split two ways by subject is
**eight cells out of one search**, which is very likely more cells than the list
can carry. Pick one subject per version, and if four cells is still too many,
hold D back as the follow-up to whichever of A, B or C wins. That is a sequence,
not a test, and its numbers are not comparable.

## What Version D says

| | |
|---|---|
| **File** | [`05-wedding-planners-vd-private-galleries.html`](05-wedding-planners-vd-private-galleries.html) |
| **Leads on** | private galleries, in the couple's language |
| **Headline** | The Photos Stay With the Wedding |
| **Hero chip** | "Private Galleries". The one place the word survives, and a deliberate exception |
| **Subjects** | 💞 Only your guest list sees them / 👰 Photos stay with the wedding |
| **Offer** | Free plan, inherited from Version A unchanged |

Built from `05-wedding-planners-vc-selfie-search.html`. The same nine copy slots
moved that Version C moved from Version B, and nothing else did. It carries the
segment's three "couple, not client" lines unchanged.

**The chip is the exception to the vocabulary rule and it is not a slip.** The
chip is the version marker, so it has to name the module or the one visible
signal that tells you which letter produced a reply is gone. Two words in a
rounded label read as a category tag; the sentences underneath are where the
register is held.

**The warm emoji are carrying real weight.** A padlock in front of either subject
line would undo the register decision in one character. U+1F512 was available and
was deliberately not used. Do not add it.

**The boundary against Version C is finding versus admitting.** C is a guest
finding their own frames in a gallery they can already open; D is who can open it
at all. D never mentions selfies, faces, matching or scrolling.

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

## What Version C says

| | |
|---|---|
| **File** | [`05-wedding-planners-vc-selfie-search.html`](05-wedding-planners-vc-selfie-search.html) |
| **Leads on** | AI selfie search |
| **Headline** | One Selfie, and They Find Themselves |
| **Hero chip** | the version marker, so a reply that quotes it names the version |
| **Subjects** | 💒 Stop the photo requests / 🔎 Guests find their own shots |
| **Offer** | Free plan, inherited from Version A unchanged |

Built from `05-wedding-planners-vb-same-day.html`. The same nine copy slots
moved that Version B moved from Version A, and nothing else did.

**The guest is the subject and the planner is the reader**, and that
distinction carries the whole letter. Nothing here is a feature the planner
uses. It is a fortnight of "which photos am I in" messages the planner stops
receiving, which is why subject A is written about the reader rather than about
the wedding. It is the only subject line in this segment that is.

If this version wins, the finding is that selection is the couple's problem and
the photographer's problem, while the thing that actually reaches the planner is
three hundred guests wanting their own photographs one message at a time.

## The three segment lines

**Version A departs from segment 02's held-identical body in three lines**, all
of them changing "the client" to "the couple". That is this segment's whole
vocabulary argument. The header comment of the Version A file lists them.
**Versions B and C carry all three**: they belong to the segment, not to the
version.

**Bullet 7 and showcase card 2 both state the selfie-search promise and are
held identical anyway**, including in Version C, which leads on it. Rewriting
them to match that hero would put a body variable into a test carrying only a
lead-promise variable.

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
