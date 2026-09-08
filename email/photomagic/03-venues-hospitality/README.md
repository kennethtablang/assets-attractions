# Segment 03: Venues and hospitality

**Status** Versions A, B and C built. Complete.
**Audience** [`apollo-audience-targeting.md`](../apollo-audience-targeting.md), section 3, "03. Venues and hospitality"
**Layout** [`email/templates/email-photomagic-card.html`](../../templates/email-photomagic-card.html), the dark card, by way of [`../02-event-planners-teams/`](../02-event-planners-teams/)
**Campaign ID** `PM-2026-09-VENUES` · **UTM** `photomagic_venues_2026`
**Workflow** [`docs/photomagic-campaign-workflow.md`](../../../docs/photomagic-campaign-workflow.md)

Hotels, ballrooms, clubs, attractions.

## Focus

The photographs are a guest-experience asset and a marketing asset at the
same time, which is why the buyer usually sits in marketing rather than in
operations. A venue does not shoot and does not proof: it hosts, and it wants
the night to look like something worth booking again.

## Target

| | |
|---|---|
| **Titles** | Director of Sales and Marketing, Marketing Manager, Head of Marketing, Director of Events, Banquet Manager, Catering Sales Manager, Guest Experience Manager, Guest Relations Manager, Social Media Manager, Brand Manager, General Manager, Operations Manager |
| **Employee count** | 10 to 500, with the decision maker check applied. A large chain needs a named marketing contact, not a head office switchboard. |
| **Geography** | UAE core first: Dubai, Abu Dhabi, Sharjah, then the northern emirates. Ring 2 only once the core is exhausted. Search on **company** location, not contact location. |
| **Saved search** | `PM-03-venues-UAE-<yyyymm>`, one per geography, logged in the campaign register with its result count and the date it was run |

The full keyword blocks, industry values and exclusions live in the targeting
doc. They are not duplicated here, because a filter recipe copied into nine
folders is a filter recipe that will disagree with itself within a month.

## The three versions

| Version | Leads on | Why |
|---|---|---|
| **A** (control) | AI selfie search | High guest counts are exactly where selfie search wins, and a ballroom at capacity is the clearest version of the problem it solves. |
| **B** | Same-day delivery | Challenger. |
| **C** | Private galleries | Challenger. |

**Omits client photo selection.** A venue hosts the event, it does not proof the shoot.

A is the control because the targeting doc predicts it will win here. B and C are
challengers. **If a challenger wins, the targeting doc was wrong about this
segment**, which is a more useful finding than a feature preference and is the
reason the prediction is written down before the send rather than after.

Filenames, following the convention segment 02 already uses. All three exist:

```
03-venues-va-selfie-search.html      BUILT, the control
03-venues-vb-same-day.html           BUILT, challenger
03-venues-vc-private-galleries.html  BUILT, challenger
```

**This is the three-way test the table above describes**, and it is the second
segment in the pipeline to reach that state after segment 02.

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
| **File** | [`03-venues-vc-private-galleries.html`](03-venues-vc-private-galleries.html) |
| **Leads on** | private galleries |
| **Headline** | Every Function Gets Its Own Gallery |
| **Hero chip** | the version marker, so a reply that quotes it names the version |
| **Subjects** | 🍾 One gallery per function / 🔐 Who can open your photos? |
| **Offer** | Free plan, inherited from Version A unchanged |

Built from `03-venues-vb-same-day.html`. The same nine copy slots moved that
Version B moved from Version A, and nothing else did, so all three versions of
this segment differ in exactly nine places.

**It frames access as something the venue's clients ask for, not as
compliance,** and it never uses the word. That is the difference between this
letter and segment 04's control, which leads on the same feature into an
audience that raises the question itself. A hotel does not.

**Two of the nine slots are held identical anyway in this segment.** The lead
line above the primary button and the closing band heading both say "function"
rather than "event", which is what a hotel or a ballroom calls the thing it
hosts. That word belongs to the segment, not to the version, so all three
versions carry it. Version C's first subject line and its headline use it too.

## What Version B says

| | |
|---|---|
| **File** | [`03-venues-vb-same-day.html`](03-venues-vb-same-day.html) |
| **Leads on** | same-day delivery |
| **Headline** | The Night Is Online Before It Ends |
| **Hero chip** | the version marker, so a reply that quotes it names the version |
| **Subjects** | 🥂 Photos before the night ends / 🌃 Your venue, posted tonight |
| **Offer** | Free plan, inherited from Version A unchanged |

Eight copy slots moved from Version A and nothing else did. If it wins, the
targeting doc was wrong about this segment: the complaint would be the calendar
rather than the pile, which would also change what leads in segments 06, 07 and
08, all modelled on this one.

## What Version A says

| | |
|---|---|
| **File** | [`03-venues-va-selfie-search.html`](03-venues-va-selfie-search.html) |
| **Leads on** | AI selfie search |
| **Headline** | Every Guest Finds Their Own Photos |
| **Hero chip** | the version marker, so a reply that quotes it names the version |
| **Subjects** | 🏨 Every guest finds themselves / 👥 Thousands of photos, sorted |
| **Offer** | Free plan, with segment 02's pricing strip inherited unchanged |

## Watch for

**The buyer sits in two different chairs and they read a letter differently.**
A banquet manager wants the gate to move. A marketing manager wants the
content. The A/B/C split above leans marketing, so check which titles the
Apollo list actually returned before reading the result: a weak number may
mean the list came back operations-heavy rather than that the promise lost.

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
