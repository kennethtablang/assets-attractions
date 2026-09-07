# Segment 09: Real estate launches and handovers

**Status** Plan only. No letters built yet.
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

## The three versions to build

| Version | Leads on | Why |
|---|---|---|
| **A** (control) | Same-day delivery | The listing and the press coverage have a deadline the photographs either make or miss. |
| **B** | Private galleries | Challenger. |
| **C** | AI selfie search | Challenger. |

**Omits client photo selection.** A launch is not proofed, it is published.

A is the control because the targeting doc predicts it will win here. B and C are
challengers. **If a challenger wins, the targeting doc was wrong about this
segment**, which is a more useful finding than a feature preference and is the
reason the prediction is written down before the send rather than after.

Planned filenames, following the convention segment 02 already uses:

```
09-real-estate-va-same-day.html
09-real-estate-vb-private-galleries.html
09-real-estate-vc-selfie-search.html
```

## When you build it

**Clone a shipped sibling, never the template.** That is the house rule across
this repository and it is why the campaigns are guaranteed to share a layout
rather than merely intended to. Today the only shipped Photomagic letters are
[`../02-event-planners-teams/`](../02-event-planners-teams/) and
[`../01-launch/`](../01-launch/); clone whichever is most current and check all
of them again afterwards.

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
