# Segment 04: Schools and education (EduMagic)

**Status** Versions A, B and C built. Complete.
**Audience** [`apollo-audience-targeting.md`](../apollo-audience-targeting.md), section 3, "04. Schools and education (EduMagic)"
**Layout** [`email/templates/email-photomagic-card.html`](../../templates/email-photomagic-card.html), the dark card, by way of [`../02-event-planners-teams/`](../02-event-planners-teams/)
**Campaign ID** `PM-2026-09-SCHOOLS` · **UTM** `photomagic_schools_2026`
**Workflow** [`docs/photomagic-campaign-workflow.md`](../../../docs/photomagic-campaign-workflow.md)

Graduations, sports days, recitals, school trips.

## Focus

Distinct enough in language and in privacy posture that it carries its own
product name. The letter is not selling photo delivery to a school, it is
selling controlled photo delivery, and the control is the product.

## Target

| | |
|---|---|
| **Titles** | Marketing Manager, Head of Marketing, Head of Admissions, Admissions Manager, Communications Manager, Head of Communications, Alumni Relations Manager, Student Life Coordinator, Principal, School Director, Events Coordinator |
| **Employee count** | 20 to 500 |
| **Geography** | UAE core first: Dubai, Abu Dhabi, Sharjah, then the northern emirates. Ring 2 only once the core is exhausted. Search on **company** location, not contact location. |
| **Saved search** | `PM-04-schools-UAE-<yyyymm>`, one per geography, logged in the campaign register with its result count and the date it was run |

The full keyword blocks, industry values and exclusions live in the targeting
doc. They are not duplicated here, because a filter recipe copied into nine
folders is a filter recipe that will disagree with itself within a month.

## The three versions

| Version | Leads on | Why |
|---|---|---|
| **A** (control) | Private galleries | The first question a school asks about any photo tool is who can see the pictures. Answer it in the headline or do not send. |
| **B** | Same-day delivery | Challenger. |
| **C** | Client photo selection | Challenger. |

**Omits ai selfie search.** See the rule below. This omission is not a preference.

A is the control because the targeting doc predicts it will win here. B and C are
challengers. **If a challenger wins, the targeting doc was wrong about this
segment**, which is a more useful finding than a feature preference and is the
reason the prediction is written down before the send rather than after.

Filenames, following the convention segment 02 already uses. All three exist:

```
04-schools-va-private-galleries.html  BUILT, the control
04-schools-vb-same-day.html           BUILT, challenger
04-schools-vc-photo-selection.html    BUILT, challenger
```

**This is the three-way test the table above describes.**

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
| **File** | [`04-schools-vc-photo-selection.html`](04-schools-vc-photo-selection.html) |
| **Leads on** | client photo selection |
| **Headline** | You Pick the Photos Before They Go Out |
| **Hero chip** | "Photo Selection", not "Client Photo Selection". See below. |
| **Subjects** | 📝 You pick what parents see / ⭐ Shortlist before you share |
| **Offer** | Free plan, inherited from Version A unchanged |

Built from `04-schools-vb-same-day.html`. The same nine copy slots moved that
Version B moved from Version A, and nothing else did.

**The chip drops the word "client" because this segment already did.** Showcase
card 3 was renamed "Photo selection" in Version A, since a school does not have
a client, and it is held identical across the segment. A chip reading "Client
Photo Selection" above a showcase card reading "Photo selection" would disagree
with itself on one screen. Segment 05 keeps the full name in its own chip, and
that is not an inconsistency to fix: a wedding planner has a client.

**Who selects is also different here.** Everywhere else the client shortlists
and the photographer delivers. In a school the staff who ran the event decide
what leaves the school before any family sees it, so selection is an approval
step and the letter treats it as one.

**The opening card still names the private gallery**, exactly as Version B's
does. A letter about choosing photographs of children that never says where the
chosen ones go reads as a company that has not thought about it. Naming it once
in a supporting sentence is not leading on it.

**Version C was the last slot where a selfie-search letter could have appeared,
and it is not there either.** Neither subject line and none of the nine moved
copy slots mentions faces or search. The capability is still named once in
showcase card 2, held identical across the segment, because the showcase
describes the product rather than the pitch.

## The nine segment lines, and step 3

**Version A departs from segment 02's held-identical body in nine lines**,
because segment 02 sells a guest list as a lead list and that is the wrong claim
in a school inbox. Every departure is listed and justified in the header comment
of the Version A file. **Versions B and C carry all nine unchanged**: they
belong to the segment, not to the version. Version B's header lists them again,
with the reason each one survives a same-day pitch.

**One of them will look wrong in any version that is not A, and is still
right.** How It Works step 3 is called "Share with your list" rather than
"Deliver the same day". Version B leads on same-day delivery and still does not
touch it, because changing it would put a body variable into a test carrying
only a lead-promise variable. **Version C has the same problem with showcase
card 3**, which is the selection feature stated in the showcase and is likewise
held identical.

## What Version B says

| | |
|---|---|
| **File** | [`04-schools-vb-same-day.html`](04-schools-vb-same-day.html) |
| **Leads on** | same-day delivery |
| **Headline** | Photos to Parents the Same Day |
| **Hero chip** | the version marker, so a reply that quotes it names the version |
| **Subjects** | 🎒 Photos home the same day / 🔔 Sports day photos, tonight |
| **Offer** | Free plan, inherited from Version A unchanged |

Eight copy slots moved from Version A and nothing else did. **The opening card
still names the private gallery in its second sentence**, on purpose: a speed
promise sent to a school with no mention of who can open the gallery reads as a
company that has not thought about it, and this segment does not forgive that.
Neither subject line, and no line of the copy, mentions faces or search.

## What Version A says

| | |
|---|---|
| **File** | [`04-schools-va-private-galleries.html`](04-schools-va-private-galleries.html) |
| **Leads on** | private galleries |
| **Headline** | A Private Gallery, Not a Public Link |
| **Hero chip** | the version marker, so a reply that quotes it names the version |
| **Subjects** | 🎓 Photos, only for your list / 🏫 Only your parents see them |
| **Offer** | Free plan, with segment 02's pricing strip inherited unchanged |

## Watch for

**Children's images carry consent obligations the other segments do not.**
Do not send this segment copy that implies open or public galleries. Lead on
access control, or do not send to this segment at all.

### There is no selfie-search version for this segment

Every other segment gets a face-search letter. This one does not, and the
reason is worth stating in full so nobody adds it back as an improvement.

Running face recognition against photographs of children is the single claim
in this product most likely to end a conversation with a school, and a cold
email is the worst possible place to raise it. The capability still appears
in the feature showcase, because the showcase is held identical across a
segment's three versions and describes the product rather than the pitch.
Nothing leads on it, no subject line mentions it, and the letter never asks a
school to picture it.

If somebody later decides schools should get a selfie-search version, that is
a product and legal conversation first and a copy decision second.

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
