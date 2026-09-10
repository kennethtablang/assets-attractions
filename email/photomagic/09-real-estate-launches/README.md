# Segment 09: Real estate launches and handovers

**Status** Version A BUILT, the control. B and C not built yet.
**Audience** [`apollo-audience-targeting.md`](../apollo-audience-targeting.md), section 3, "09. Real estate launches and handovers"
**Layout when built** [`email/templates/email-photomagic-card.html`](../../templates/email-photomagic-card.html), cloned from a shipped sibling
**Workflow** [`docs/photomagic-campaign-workflow.md`](../../../docs/photomagic-campaign-workflow.md)

Off-plan launches, sales gallery openings, broker roadshows, handovers.

## Focus

**The most UAE-specific segment in the pipeline**, which is both why it exists
and why it is last. Developers run a dense photographed event calendar,
brokers are commission funded and buy their own tools without asking anyone,
and launch photography has a publication deadline measured in days because the
listing goes live either way.

## Target

| | |
|---|---|
| **Titles** | Marketing Manager, Head of Marketing, Brand Manager, Events Manager, Head of Events, Head of Sales, Sales Director, Broker Relations Manager, Community Manager, Managing Director, Founder |
| **Employee count** | 5 to 500 |
| **Geography** | UAE core first: Dubai, Abu Dhabi, Sharjah, then the northern emirates. Ring 2 only once the core is exhausted. Search on **company** location, not contact location. |
| **Saved search** | `PM-09-realestate-UAE-<yyyymm>`, one per geography, logged in the campaign register with its result count and the date it was run |

The full keyword blocks, industry values and exclusions live in the targeting
doc. They are not duplicated here, because a filter recipe copied into nine
folders is a filter recipe that will disagree with itself within a month.

## The three versions

| Version | Leads on | Why |
|---|---|---|
| **A** (control) | Same-day delivery | The listing and the press coverage have a deadline the photographs either make or miss. |
| **B** | Private galleries | Challenger, NOT BUILT. |
| **C** | AI selfie search | Challenger, NOT BUILT. |

**One letter is not a test.** Until a challenger exists there is nothing to
compare Version A against, and a send now measures the segment rather than the
promise. That is a legitimate thing to do on a new segment and it is not what
this plan describes, so decide which you are doing before you send. Segments 06,
07 and 08 have the opposite problem: challengers with no control. This one is the
right way round, because the control is the letter worth sending on its own.

**Omits client photo selection.** A launch is not proofed, it is published.

A is the control because the targeting doc predicts it will win here. B and C are
challengers. **If a challenger wins, the targeting doc was wrong about this
segment**, which is a more useful finding than a feature preference and is the
reason the prediction is written down before the send rather than after.

Filenames, following the convention segment 02 already uses:

```
09-real-estate-va-same-day.html           BUILT, the control
09-real-estate-vb-private-galleries.html  challenger, NOT BUILT
09-real-estate-vc-selfie-search.html      challenger, NOT BUILT
```

## The seven segment lines Versions B and C must carry

Version A turned a hospitality letter into a real estate one in seven lines of
the otherwise shared body. They belong to the **segment**, not to the version, so
B and C carry all seven unchanged when they are built:

| Line | Segment 03 said | This segment says |
|---|---|---|
| showcase card 3 name | Client selection | **Photo selection** |
| showcase card 3 copy | Your client shortlists and approves | **Your marketing team** shortlists and approves |
| column 1 heading | For Your Events | **For Your Launches** |
| column 2 heading | For Your Clients | **For Your Brokers** |
| How It Works step 3 copy | your client is sharing them from the room | **your brokers** are sharing them from the room |
| closing band heading | Try it on your next function | **Try it on one launch** |
| permission line | hotels, venues and hospitality teams | **developers, brokerages and property marketing teams** |

"Client selection" became "Photo selection" for the reason segment 04 made the
same change: a developer running its own launch has no client in the sense a
hotel does. Any future selection letter here must use the shortened chip to
match.

**"For Your Brokers" is the one worth arguing about.** The room at an off-plan
launch or a roadshow is mostly brokers, and Broker Relations Manager is a target
title above, so the column names the audience the letter is about. It is the
wrong word for a handover, where the room is buyers. If handovers turn out to be
the better half of the list, that heading is the first line to revisit, and it
moves for the whole segment rather than for one version.

## The nine slots B and C may vary

This segment follows the segment 03, 04 and 05 convention, **not segment 02's**:
the CTA lead line is HELD and the closing band paragraph MOVES. Segment 02 does
the opposite. Both are correct inside their own folder.

1. `<title>` 2. preheader 3. hero chip 4. headline, including which words carry
the orange span 5. hero subhead 6. opening card heading 7. opening card
paragraph 8. the closing band paragraph 9. `utm_content` on both buttons, twice
each

That is nine slots across twelve lines: body indices 10, 50, 85, 90, 93, 105,
108, 354, 360, 379, 382 and 387, counting from the DOCTYPE.

## Campaign identity

| | |
|---|---|
| **Campaign ID** | `PM-2026-09-REALESTATE` |
| **UTM campaign** | `photomagic_realestate_2026` |

The UTM campaign string is the only thing separating this from the EMS campaign
covering the same industry if both pipelines report into one analytics property.

## When you build it

**Clone a shipped sibling, never the template.** That is the house rule across
this repository and it is why the campaigns are guaranteed to share a layout
rather than merely intended to.

**Version A was cloned from
[`../03-venues-hospitality/03-venues-vb-same-day.html`](../03-venues-hospitality/03-venues-vb-same-day.html)**,
because that file already leads on same-day delivery, so the structure of the
argument transferred and only the room changed. Build B and C from
`09-real-estate-va-same-day.html` rather than going back to segment 03, so the
seven segment lines above come along automatically.

All three versions of a segment are **structurally identical** and differ only in
the lead promise: title, preheader, hero chip, headline, hero subhead, opening
card heading, opening card paragraph, the lead line above the button, and
`utm_content` on both buttons. Everything else, including all four feature cards,
is held byte-identical. Segment 02's README carries the verification script.

## Watch for

**This is the segment most likely to collide with Ticket Magic.** EMS outreach
segment 03 is real estate and is being sold an Event Management System to the
same job titles at the same UAE developers and brokerages.

Rule 2 of the targeting doc applies at full force: a company can be in both
lists, but it holds two sender identities and two independent opt-outs, and
the two letters must not arrive in the same week.

**Diff this Apollo list against the EMS segment 03 list before importing
either.** Nothing in either tool will warn you, and the failure looks like a
prospect receiving two cold emails from one building about two products with
no visible relationship.

## Before anything here can send

Both blockers that hold the rest of this pipeline apply here too, and neither is
segment specific:

| | Status |
|---|---|
| `{{POSTAL_ADDRESS}}` | **Outstanding.** photomagic.io publishes no postal address. One is legally required in bulk commercial email. It cannot be invented or borrowed from Ticket Magic's office. |
| Free plan vs 7-day trial | **Unresolved.** Campaign 01 and segment 02 currently say different things. Settle it against the live signup flow before adding a third campaign to the disagreement. |

Plus the two that apply to every cold Photomagic send:

- **Apollo contacts never enter Mailchimp.** Cold third-party contacts in an
  opt-in audience is an account-termination risk, not a style preference.
- **Reply-To `inquiry@photomagic.io`**, from a photomagic.io address, never a
  Ticket Magic inbox.
