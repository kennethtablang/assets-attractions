# Segment 07: Corporate HR, internal comms and employer brand

**Status** Versions B and C built. **Version A, the control, is not.** See [What is built](#what-is-built).
**Audience** [`apollo-audience-targeting.md`](../apollo-audience-targeting.md), section 3, "07. Corporate HR, internal comms and employer brand"
**Layout** [`email/templates/email-photomagic-card.html`](../../templates/email-photomagic-card.html), the dark card, by way of [`../03-venues-hospitality/`](../03-venues-hospitality/)
**Campaign ID** `PM-2026-09-CORPHR` · **UTM** `photomagic_corphr_2026`
**Workflow** [`docs/photomagic-campaign-workflow.md`](../../../docs/photomagic-campaign-workflow.md)

Staff parties, annual days, town halls, long-service awards, family days.

## Focus

**This segment is found by job title, not by industry.** The company can be a
bank, a contractor, a logistics firm or a software house. What makes it a
prospect is that somebody inside it owns the employee-experience budget and
runs four photographed events a year on it.

Filtering by industry here produces noise. Filter by title and headcount, and
let the industry fall where it falls. That is also why this segment has no row
in the industry table and no useful NAICS code: the code describes the
employer, and the job is the qualifier.

## Target

| | |
|---|---|
| **Titles** | Head of Internal Communications, Internal Communications Manager, Employer Brand Manager, Employee Engagement Manager, People and Culture Manager, Head of People, Culture Manager, HR Manager, HR Director, Head of HR, CSR Manager, Sustainability Manager, Office Manager, Executive Assistant |
| **Employee count** | 200 to 2,000. See the warning below: this deliberately breaks the usual cap. |
| **Geography** | UAE core first: Dubai, Abu Dhabi, Sharjah, then the northern emirates. Ring 2 only once the core is exhausted. Search on **company** location, not contact location. |
| **Saved search** | `PM-07-corphr-UAE-<yyyymm>`, one per geography, logged in the campaign register with its result count and the date it was run |

The full keyword blocks, industry values and exclusions live in the targeting
doc. They are not duplicated here, because a filter recipe copied into nine
folders is a filter recipe that will disagree with itself within a month.

## The three versions to build

| Version | Leads on | Why |
|---|---|---|
| **A** (control) | Private galleries | Staff photographs are internal by default, and the first question this buyer asks is who else can see them. |
| **B** | Same-day delivery | Challenger. |
| **C** | Client photo selection | Challenger. |

**Omits ai selfie search.** Face recognition applied to a company's own employees is a works-council and data-protection conversation, not a cold email opener.

A is the control because the targeting doc predicts it will win here. B and C are
challengers. **If a challenger wins, the targeting doc was wrong about this
segment**, which is a more useful finding than a feature preference and is the
reason the prediction is written down before the send rather than after.

Filenames, following the convention segment 02 already uses. B and C exist;
A does not:

```
07-corporate-hr-va-private-galleries.html
07-corporate-hr-vb-same-day.html
07-corporate-hr-vc-photo-selection.html
```

## What is built

| Version | File | Leads on | Headline | Subjects |
|---|---|---|---|---|
| **A** (control) | **not built** | private galleries | | |
| **B** | [`07-corporate-hr-vb-same-day.html`](07-corporate-hr-vb-same-day.html) | same-day delivery | The Photos Land Before Monday | 🏢 Recap ready before Monday / 💼 Photos before people leave |
| **C** | [`07-corporate-hr-vc-photo-selection.html`](07-corporate-hr-vc-photo-selection.html) | photo selection | Approve Every Photo Before It Goes Out | ✅ Approve before it goes out / 👀 A second look before publish |

**Nothing here can run as a test until Version A exists.** B and C are
challengers, and two challengers with nothing to challenge is two letters rather
than an experiment. Build `07-corporate-hr-va-private-galleries.html` first, cloning one of the two
files above, then split the segment into even random thirds and send all three
at the same time of day.

**Seven lines of the shared body belong to this segment, not to a version**,
because two of them are corrections, not rewordings: segment 02's body sold lead
capture on a company's own employees and promised face matching across staff.
Both files carry the identical set and a future Version A must too; they are
listed and justified in the header comment of the Version B file.

**The hero chip says "Photo Selection", not "Client Photo Selection".** An
internal comms team has no client, and the word costs the chip its meaning in the
two seconds it gets. [`../05-wedding-planners/`](../05-wedding-planners/) keeps
the product's full name for the same feature because a wedding planner genuinely
has clients. The filename and `utm_content` still say `photo_selection`, so
nothing in the reporting is ambiguous.

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

**This is the one segment that deliberately breaks the size exclusion in
section 8 of the targeting doc.** The usual rule caps a list at 1,000
employees because the buying cycle costs more than the contract. Here the
headcount is the qualifier rather than the disqualifier: a 1,500 person
company has an engagement manager, a discretionary budget and an annual day,
and the photos never leave the building, so no procurement is triggered.

**That reasoning is the largest unverified claim in the whole pipeline.** It
holds only while the buyer really can spend on a card. Verify it on the first
fifty contacts before scaling the list. If these purchases turn out to route
through procurement, this segment is not a fit at this price and should be
dropped rather than nurtured.

Section 8 also excludes HR roles by default. This segment is the exception
that exclusion already names. Do not apply both.

## Before anything here can send

The blockers that hold the rest of this pipeline apply here too, and none of
them is segment specific:

| | Status |
|---|---|
| `{{POSTAL_ADDRESS}}` | **Outstanding.** photomagic.io publishes no postal address. One is legally required in bulk commercial email. It cannot be invented or borrowed from Ticket Magic's office. |
| Version A | **Not built.** The control is missing, so the A/B/C test cannot run. |
| Free plan vs 7-day trial | **Unresolved, and these letters take a side.** Campaign 01 says 7-day trial, segment 02 says free plan. B and C follow segment 02: the badge says "Free Plan Included", the button leads on the free plan, and the pricing strip shows the permanent Free tier. Still settle it against the live signup flow. |
| Prices and quotas | **Read off the live page 2026-09-01** and inherited from segment 02: Free $0, Pro $55, Corporate $150. Re-check every figure on send day. |
| Register the campaign | **Outstanding.** No row in [`docs/campaign-register.csv`](../../../docs/campaign-register.csv) yet for `PM-2026-09-CORPHR`. |

Plus the two that apply to every cold Photomagic send:

- **Apollo contacts never enter Mailchimp.** Cold third-party contacts in an
  opt-in audience is an account-termination risk, not a style preference.
- **Reply-To `inquiry@photomagic.io`**, from a photomagic.io address, never a
  Ticket Magic inbox.
