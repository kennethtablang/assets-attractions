# Photomagic outreach

Campaign files for **Photomagic** (photomagic.io), the instant event photo
delivery product. This is a **separate pipeline from Ticket Magic's Event
Management System outreach**, which lives in [`../outreach/`](../outreach/).

Do not put a Photomagic letter in `../outreach/` or a Ticket Magic letter here.
They use different templates, different senders, different WhatsApp numbers and
different Mailchimp audiences. The full reasoning is in
[`docs/photomagic-campaign-workflow.md`](../../docs/photomagic-campaign-workflow.md).

## Build from

`email/templates/email-photomagic.html`. Copy it, never edit the original.

## Layout

One folder per segment, one file per version, mirroring the EMS outreach
convention:

```
01-photographers-studios/                  no folder yet
02-event-planners-teams/                   BUILT, 4 letters, CARD layout
  02-event-planners-va-same-day.html
  02-event-planners-vb-selfie-search.html
  02-event-planners-vc-private-galleries.html
  02-event-planners-vd-photo-selection.html
  README.md
03-venues-hospitality/                     BUILT, 4 letters, CARD layout
  03-venues-va-selfie-search.html
  03-venues-vb-same-day.html
  03-venues-vc-private-galleries.html
  03-venues-vd-photo-selection.html
  README.md
04-schools-education/        EduMagic      BUILT, 3 letters, CARD layout
  04-schools-va-private-galleries.html
  04-schools-vb-same-day.html
  04-schools-vc-photo-selection.html
  README.md
05-wedding-planners/                       BUILT, 4 letters, CARD layout
  05-wedding-planners-va-photo-selection.html
  05-wedding-planners-vb-same-day.html
  05-wedding-planners-vc-selfie-search.html
  05-wedding-planners-vd-private-galleries.html
  README.md
06-sports-races-academies/                 B and C BUILT, no A
  06-sports-vb-same-day.html
  06-sports-vc-private-galleries.html
  README.md
07-corporate-hr-internal/                  B and C BUILT, no A
  07-corporate-hr-vb-same-day.html
  07-corporate-hr-vc-photo-selection.html
  README.md
08-nonprofits-community/                   B and C BUILT, no A
  08-nonprofits-vb-private-galleries.html
  08-nonprofits-vc-selfie-search.html
  README.md
09-real-estate-launches/                   A BUILT, B and C to come
  09-real-estate-va-same-day.html
  README.md
```

**Nine segments have a plan. Eight have letters, and four are complete.**

| Segment | Built | Missing |
|---|---|---|
| 02 event planners | A, B, C, **D** | nothing |
| 03 venues | A, B, C, **D** | nothing |
| 04 schools | A, B, C | nothing, and **no D is possible**, see below |
| 05 wedding planners | A, B, C, **D** | nothing |
| 06 sports | B, C | **A, the control** |
| 07 corporate HR | B, C | **A, the control** |
| 08 nonprofits | B, C | **A, the control** |
| 09 real estate | **A** | B and C, both challengers |

Campaign 01 also carries a fourth version now, `01-launch-vd-private-galleries.html`,
leading on the control the other three never mention.

**Segments 03, 04 and 05 now run the three-way test their plans describe.** In
all three, Version A is the control the targeting doc predicts will win and
Version B leads on same-day delivery. Version C leads on private galleries in
03, on client photo selection in 04, and on AI selfie search in 05, which is the
feature each plan's table assigns it.

**Segments 02, 03 and 05 and campaign 01 now carry a fourth version, and every
one of them leads on the feature its own plan deliberately left out.** That is
the point of them: each plan's omission is a written prediction about an
audience, and a Version D is the cheapest way to find out whether the prediction
was right. If D loses, the plan was right and the pipeline has a result instead
of an assumption. **Do not promote a D to control on one send.**

| Segment | D leads on | The omission it tests |
|---|---|---|
| campaign 01 | private galleries, as "the control" | A, B and C are all about what the product does for the reader; none is about what the sender keeps |
| 02 event planners | client photo selection | the audience doc assigns selection to segments 01 and 05 |
| 03 venues | client photo selection, as **permission not proofing** | "a venue hosts the event, it does not proof the shoot", which stays true |
| 05 wedding planners | private galleries, **without the compliance register** | "a couple hears it as a feature for somebody else's compliance department" |

**Adding a D changes the arithmetic in every one of those folders.** Each version
now gets a quarter rather than a third, and the subject test inside each file
halves that again, so a cell is an eighth of the segment. Segment 05 is the worst
case: its Apollo filter runs 1 to 30 employees and eight cells is very likely
more than the list can carry. Every folder's README now says so, and every one
names the alternative: hold D back and run it as the follow-up to whichever of A,
B or C wins, which is a sequence and not a test.

**Segment 04 is the one segment that cannot have a Version D, and that is not an
oversight.** Its three versions already use private galleries, same-day delivery
and client photo selection. The only feature left is AI selfie search, and that
segment's README rules it out in full: running face recognition against
photographs of children is the single claim in this product most likely to end a
conversation with a school, and a cold email is the worst place to raise it.
Adding it "is a product and legal conversation first and a copy decision second".
Segment 04 stays at three.

**Segments 06, 07 and 08 have challengers and no control**, which is the one
shape in this table that cannot be sent as a test: two challengers with nothing
to challenge is two letters rather than an experiment. Each of those six files
says so in the first lines of its header comment, and names the Version A file
that has to exist first. Build those three before sending any of the six.

Folder 09 holds a README and nothing else: focus, target titles, employee count,
the saved-search name, and which three of the four product features its A/B/C
versions lead on. It says what to clone when somebody builds it.

**Every letter in this folder is on the dark card template**, cloned sibling to
sibling: campaign 01, then segment 02 from it, then segment 03 from segment 02,
then segments 04 to 08 from segment 03, each Version B in segments 03 to 05 from
its own Version A, and each Version C in those three from its own Version B.
They share one 441-line body, so a restyle has to land in all twenty-one or the
pipeline looks like one brand in the repo and several in an inbox.

**A handful of body lines differ per segment, and every one is deliberate.**
Segment 02's body sells a guest list as a lead list, which is right for an event
agency, wrong for a school, wrong for a company's own staff, and right again for
a fundraiser chasing donor stewardship. Segments 04, 05, 06, 07 and 08 each
change between three and nine lines for reasons their Version B or Version A
header comment sets out line by line. Those belong to the **segment**, not to the
version, so all three versions of a segment carry the identical set.

**Segment 04's step 3 is the case that looks like a bug and is not.** How It
Works step 3 is named "Share with your list" rather than "Deliver the same day",
and segment 04's Version B leads on same-day delivery and still does not touch
it. Changing it would put a body variable into a test that is supposed to carry
only a lead-promise variable.

**`email-photomagic.html`, the light template, is still unused.** The workflow doc
pairs it with cold outreach and pairs the card with warm lists, so every cold
campaign here is a deliberate departure from that pairing, made first by segment
02 and inherited since. If cold reply rates come back poor, **a flat version of
the winning letter is the cheap experiment**, and the template is sitting there
for it.

**Segment 01 has no folder at all**, which makes it the only gap in the run. It
is the core segment on paper and the one the targeting doc flags as most likely
to come back thin in Apollo, so it is worth a result count before a letter.

The full plan, including the four expansion candidates that were considered for
06 to 09 and rejected, is section 3 of
[`apollo-audience-targeting.md`](apollo-audience-targeting.md).

**Two numbering schemes share this folder, and they collide.** The list above is
*segments*, cold outreach split by who the letter goes to. `01-launch/` is not
one of them: it is a *campaign*, a warm announcement to a list that already knows
the name, and it happens to start with the same digits. Read the folder's own
README before assuming which kind it is.

**Segment 02 was built before segment 01.** That is the order the work happened
in, not a mistake. Do not renumber to close the gap: a segment number ties to an
Apollo saved search and to a campaign ID, and both are easier to keep stable than
to migrate.

**Segment numbers are Photomagic's own and start at 01.** They do not continue
from the EMS's nine segments. `01` here is photographers; `01` in `../outreach/`
is events services. The number means nothing across the two products.

Within a segment, versions A, B and C are structurally identical and differ only
in the feature they lead on, so a difference in reply rate is attributable to the
copy and nothing else. If you edit the layout of one, edit all of them.

## Who to send it to

[`apollo-audience-targeting.md`](apollo-audience-targeting.md) holds the Apollo
filter recipe for all five segments: industries, keyword blocks, job titles,
NAICS and SIC codes, technology filters, geography rings and the exclusion list.
It is a recipe, not a verified list. Nothing in it has been run in Apollo yet,
and section 10 says what to check before it drives a send.

**Apollo contacts never go into Mailchimp.** Cold third-party contacts in an
opt-in audience is an account-termination risk, not a style preference.

## Before sending

Run the five checks in section 4, step 7 of the workflow doc. The two that catch
the most:

- `grep -c '{{' yourfile.html` must return **0** on a file that is ready to send.
  The asset commit SHA is a token on purpose, so an unpinned image trips this
  check.
- **Every letter in this folder currently returns 1**, and the one hit is the
  postal address. That is the expected state today, not an oversight, which is
  why the count matters more than the presence: 1 means only the known blocker
  is open, and anything above 1 means something else is unresolved too.
- The postal address token is a **legal blocker**, not a placeholder to tidy up
  later. photomagic.io publishes no postal address; find the registered one.
