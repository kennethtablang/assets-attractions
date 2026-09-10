# Segment 02: Event planners and event management teams

**Campaign ID** `PM-2026-09-PLANNERS` · **UTM** `photomagic_planners_2026`
**Layout** [`email/templates/email-photomagic-card.html`](../../templates/email-photomagic-card.html), by way of [`../01-launch/`](../01-launch/)
**Audience** [`apollo-audience-targeting.md`](../apollo-audience-targeting.md), section 3, "02. Event planners and event management teams"
**Workflow** [`docs/photomagic-campaign-workflow.md`](../../../docs/photomagic-campaign-workflow.md)

A three-version first approach to event agencies and in-house event teams,
sourced from an Apollo search.

## The body is a clone of Campaign 01

These files were built from `../01-launch/01-launch-va-moments.html`, **not** from
the template. Cloning the shipped sibling is the house rule across this
repository, and it is why the two campaigns are guaranteed to share a layout
rather than merely intended to: same blocks, same order, same measurements, same
feature shots, same 441-line body. Every difference is a sentence.

**If you restyle one, restyle both.** A padding change here that does not land in
`../01-launch/` leaves two campaigns that look like one brand in the repo and
like two in an inbox.

## The list is cold and the layout is the warm one

The dark card is the celebratory register. The workflow doc pairs it with a warm
list and pairs cold outreach with `email-photomagic.html`, the flat white letter.
This campaign uses the card layout on an Apollo-sourced list, which is a
deliberate departure decided for this batch.

**What that costs, so nobody is surprised by the numbers:** a stranger's first
email looking like a product announcement sets a different expectation than a
plain note from a person, and cold reply rates on a designed email are usually
lower than on a plain one even when the click rate is higher.

**Judge this batch against Campaign 01**, which shares its layout, rather than
against the EMS cold letters in `../../outreach/`, which do not. If the reply rate
comes back poor, **the layout is the first thing to test, not the copy**. A flat
version of the winning letter is a cheap experiment, and `email-photomagic.html`
already exists for it.

## Segment 01 does not exist yet

The folder plan in [`../README.md`](../README.md) puts photographers and studios
at 01 and this batch was built before it. That is the order the work happened in,
not a mistake. **Do not renumber this folder to close the gap:** the number ties
to the Apollo saved search and to the campaign ID, and both are easier to keep
stable than to migrate.

Segment 02 here is event planners. Segment 02 in [`../../outreach/`](../../outreach/)
is hospitality, a different product on a different list. The number means nothing
across the two.

## The four versions

| File | Leads on | Headline |
|---|---|---|
| `02-event-planners-va-same-day.html` | **Same-day delivery** (control) | Your Client Sees the Photos **Before They Leave** |
| `02-event-planners-vb-selfie-search.html` | **AI selfie search** | Every Guest Finds **Themselves** |
| `02-event-planners-vc-private-galleries.html` | **Private galleries** | One Private Gallery for **Every Client Event** |
| `02-event-planners-vd-photo-selection.html` | **Client photo selection** | Your Client Picks **the Final Set** |

**A is the control because the audience doc says so.** Section 3.02 reads: "They
do not shoot, they commission. They buy Photomagic to look good to their own
client, which makes the same-day angle the whole pitch." B and C are challengers
to that claim. If either wins, the audience doc is wrong about this segment,
which is a more useful finding than a feature preference.

**Client selection was the feature no version led on**, deliberately. The
audience doc assigns it to wedding and portrait studios, which is segment 01 and
segment 05, and leading on it here would test a feature this segment was never
expected to want.

**Version D now runs exactly that cell, and it is a test of the plan rather than
of the copy.** The assignment above is a prediction about an audience, written
down before anything was sent, and the cheapest way to find out whether a
prediction is right is to run the case it rules out. If D loses, the audience doc
was right and the pipeline has a documented result instead of an assumption. If D
wins, the audience doc is wrong about who wants selection, and that finding is
worth more than this segment's reply rate, because segments 04, 05 and 07 are all
built on the same assignment. **Do not promote D to control on one send.** One
result against a written prediction is a reason to run it again.

**D's boundary against A and C.** A owns the clock: nothing in D says same day,
before they leave, or in real time. C owns the container: nothing in D says
login, public link, drive, forwarding, or who can see what. D is the only version
about photographs being stopped before they move, which is the approval step and
sits upstream of all three.

## What is under test

**Only the lead promise.** Ten slots differ between the four files:

1. `<title>` 2. preheader 3. hero chip 4. headline, including which words carry
the orange span 5. hero subhead 6. opening card heading 7. opening card
paragraph 8. the lead line above the primary button 9. `utm_content` on the
primary button (twice) 10. `utm_content` on the closing button (twice)

So ten slots across twelve lines.

**Held byte-identical:** the header bar and badge, the four feature shots with
their names and captions, both benefit columns and all eight bullets, the three
How It Works steps, the band photograph, the testimonial, the whole pricing
strip, the button text, the button destinations, the closing band copy, the
footer, the permission line, and every measurement.

The showcase being identical is the point, and it is the thing most likely to get
"improved" later. All four versions sell the same product and show the same four
features; what differs is which one the letter walks in leading with.

**Version D's promise is showcase card 3, and that card is still held
identical.** So is bullet 6, "Shortlist and approve in one place". Rewriting
either to match D's hero would put a body variable into a test that carries only
a lead-promise variable. This is the mirror of a problem the other three already
have: C does not touch showcase card 4 and B does not touch showcase card 2, for
the same reason. It looks like an oversight in every version and is correct in
all of them.

**The split is quarters now, not thirds.** Every note written when there were
three versions still says thirds. Four versions split two ways by subject is
eight cells out of one search: count the list first, or hold D back as the
follow-up to whichever of A, B or C wins.

Verify before you send:

```bash
python - <<'PY'
import io, glob
B = {}
for f in sorted(glob.glob("02-event-planners-v*.html")):
    t = io.open(f, encoding="utf-8").read()
    B[f] = t[t.index("<!DOCTYPE"):].splitlines()
skip = {10, 50, 85, 90, 93, 105, 108, 351, 354, 360, 382, 387}   # the ten slots
ref = [l for i, l in enumerate(list(B.values())[0]) if i not in skip]
for f, lines in B.items():
    print(f, "IDENTICAL" if [l for i, l in enumerate(lines) if i not in skip] == ref
          else "DIFFERS <-- investigate")
PY
```

Three `IDENTICAL` lines, or someone improved one file and not the others and the
result will not mean what the report says.

## The hero chip is the version marker

Campaign 01 uses that chip for "Now Live", which is a launch announcement and
says nothing on a cold letter, so it carries the feature under test here instead:
**Same-Day Delivery**, **AI Selfie Search**, **Private Galleries**. It is the one
place above the fold where the three versions differ visibly, so a reply that
quotes it tells you which version produced it.

The **header badge is not the marker** and is identical in all three. It says
"Free Plan Included", which is the offer, not the version.

## Two claims changed from Campaign 01

Campaign 01 puts "Free 7 Day Trial" in the header badge and "Try Photomagic free
for 7 days, no credit card required" above the button, then shows a pricing strip
whose first tier is a **permanent Free at $0 for one event**. Those are two
different offers sitting one screen apart, and a reader comparing them has to
decide which is true.

This batch says "Free Plan Included" and leads the button on the free plan, which
is what the strip below it actually shows. Nothing is promised that the pricing
strip does not.

**If Photomagic genuinely runs a seven-day trial on top of the free tier, this is
worth reverting and Campaign 01 is right.** Check the live signup flow, not the
marketing page, then make both campaigns say the same thing.

## Attribution: this batch improves on Campaign 01

Campaign 01 sends `utm_content=card_cta` from all three of its versions, so its
click data cannot tell them apart. Here the version rides in `utm_content` on both
buttons: `card_cta_va_same_day`, `closing_cta_va_same_day`, and so on.

That is the one convention this batch does not inherit, and it costs nothing:
same layout, same destinations, one longer string. **Consider backfilling
Campaign 01 the same way before it sends.**

The subject variant is still invisible in link data. Read it off the sending
report.

## Sending

Split the segment into **even random thirds**, all at the same time of day.
Sending C a week later to non-openers is a follow-up, not a test, and it puts one
planner in front of three cold letters from a company they do not know.

- **Reply-To** `inquiry@photomagic.io`, never a Ticket Magic inbox
- **From** a photomagic.io address, authenticated as photomagic.io

**This list is cold and Apollo-sourced, which decides where it sends from.** Cold
third-party contacts in an opt-in Mailchimp audience is an account-termination
risk, not a style preference. Send from the cold outreach tool. Photomagic's
Mailchimp audience is for people who opted in. If you send from a tool other than
Mailchimp, swap `*|UNSUB|*` and `*|UPDATE_PROFILE|*` for that tool's own opt-out
tokens; nothing else resolves Mailchimp syntax.

### Subject lines

Each version carries two, listed at the top of its file. Three versions split two
ways is **six cells out of one Apollo segment**, and a UAE event-agency list
filtered to 2 to 200 employees is not big.

**Pick one subject per version** and keep the spare for the resend. If you do run
the subject test, run it on all three or you are comparing a two-cell average
against single cells.

Nothing here reuses Campaign 01's sparkle or camera marks, so a contact on both
lists does not get two letters wearing the same emoji. **The layout is now shared
as well**, so if the two sends overlap in time, check the lists are actually
disjoint rather than assuming it.

Judge by **reply rate**, not open rate. Apple Mail Privacy Protection inflates
opens enough that a subject can win the open and lose the send.

## The testimonial is unusually well aimed here

Steevan Vas, verbatim from the live site: *"I have recently used Photo Magic for
my event. The client was very impressed and is super happy with the output."*

**That is this segment's buyer talking.** It is the only one of the site's three
reviews that describes running an event *for a client* and being judged on the
client's reaction, which is the whole job of an event agency. That is why it
stays rather than being swapped for something planner-specific.

Do not replace it with an unattributed quote. This reader is one search away from
checking, and the quote is on photomagic.io where they will find it.

## Before this can send

Images are pinned to **`79584fd`**, the commit Campaign 01 pins to. It is on
`origin/outreach/all-segments` and `origin/photomagic/launch-campaign`, and all
seven URLs returned `200` with an image content type when these files were built.

| | Status |
|---|---|
| Asset SHA ×7 | **Resolved.** Pinned to `79584fd`, verified against the CDN. |
| Free plan vs 7-day trial | **Unresolved.** This batch and Campaign 01 currently say different things. Check the live signup flow and align them. |
| Prices and quotas | **Read off the live page 2026-09-01.** Re-check on send day. A sent email is frozen and a wrong price is a refund conversation later. |
| `{{POSTAL_ADDRESS}}` | **Outstanding.** photomagic.io publishes a phone number and an email address and no postal address. One is legally required in bulk commercial email. It cannot be invented or borrowed from Ticket Magic's office. |

Searching any of the three files for `{{` returns **exactly one line**, and that
line is the address. It is not a placeholder to tidy up later; it is the reason
this campaign cannot send, and it is the same blocker Campaign 01 sits behind.

```bash
# every image resolves on the CDN, not just on disk
grep -oh 'https://cdn.jsdelivr.net[^"]*' *.html | sort -u | \
  while read u; do curl -s -o /dev/null -w "%{http_code} %{content_type} $u\n" "$u"; done

# no em dashes, en dashes or smart quotes anywhere (house rule)
grep -lP '[\x{2014}\x{2013}\x{2018}\x{2019}\x{201C}\x{201D}]' *.html

# no Ticket Magic leakage IN THE LETTER, and no leftover launch UTM. The comment
# header names ticketmagic.me, Saheel Tower, wa.me and both Ticket Magic numbers
# on purpose, as the things not to use, so scope the grep below the markup
# declaration or it hits the header and you learn to ignore a check worth keeping.
for f in *.html; do echo -n "$f "; \
  sed -n '/<!DOCTYPE/,$p' "$f" | grep -ic 'ticketmagic\|saheel\|wa\.me\|971527064878\|971529521204\|photomagic_launch'; done

# under the Gmail clipping threshold
wc -c *.html            # each must be < 102000
```

Then a **real seed send**, not a preview: `*|UNSUB|*` resolves on send and looks
broken in preview, and it sits inside an `href`, so an unresolved tag leaves the
footer looking correct while the unsubscribe link is dead.

**Merge with a real merge commit, not a squash.** A squash replays the asset bytes
under a new commit and leaves the pin dangling at a SHA on no branch. jsDelivr
serves from cache for a while and then stops: it passes every check today and
fails silently later.

## Register it

Not yet registered. Add a row to
[`docs/campaign-register.csv`](../../../docs/campaign-register.csv) with campaign
ID `PM-2026-09-PLANNERS`. The `PM-` prefix is Photomagic; `DTM-` is Ticket Magic
and must not be reused here. Campaign 01 has no row either, so add both together
rather than leaving the register describing half the pipeline.
