# Campaign 01: Photomagic Launch

**Campaign ID** `PM-2026-10-LAUNCH` · **UTM** `photomagic_launch_2026`
**Template** [`email/templates/email-photomagic-card.html`](../../templates/email-photomagic-card.html)
**Workflow** [`docs/photomagic-campaign-workflow.md`](../../../docs/photomagic-campaign-workflow.md)

A three-version launch announcement for a **warm** Photomagic list: people who
enquired, asked for early access, or met the team at an event.

## Why the dark template

`email-photomagic-card.html` is the celebratory register. `email-photomagic.html`
is the cold B2B letter. This campaign announces something to people who already
know the name, so it gets the dark violet ground and the orange button.

**If this list turns out to be cold, rebuild on the light template rather than
softening the copy here.** The register is the decision, not the wording.

## The four versions

| File | Leads on | Headline |
|---|---|---|
| `01-launch-va-moments.html` | **The memory** (control) | Capture the Best **Moments** of Your Life |
| `01-launch-vb-same-day.html` | **The speed** | Deliver Event Photos **the Same Day** |
| `01-launch-vc-selfie-search.html` | **The capability** | One Selfie, Every **Photo** of You |
| `01-launch-vd-private-galleries.html` | **The control** | One Private Gallery for **Every Event** |

Version A is the message the design was drawn around, which is why it is the
control. B, C and D are challengers.

**A, B and C are all about what the product does for the person holding the
phone. D is the only one about what the sender keeps**: the gallery has a door,
the person who ran the event decides who comes through it, and the guest list
that results belongs to them rather than to whoever the link was forwarded to
next. Its boundary against C is finding versus admitting, and the copy holds it:
D never mentions selfies, faces or scrolling, and C never mentions a login or a
link that travels.

## What is under test

**Only the lead promise.** Exactly seven lines differ between the four files:

1. `<title>` 2. preheader 3. headline 4. hero subhead
5. card title 6. card intro 7. CTA lead line

**Held byte-identical:** the header bar, the four feature shots and captions,
both benefit columns and all eight bullets, the three How It Works steps, the
band photograph, the testimonial, the pricing strip, the button text, the button
URL, the closing band, the footer, and every measurement in the layout.

That is what makes this a test rather than four different emails. Verify before
you send. The script globs `01-launch-v*.html`, so it already picks up Version D:

```bash
python - <<'PY'
import io, glob
L = {}
for f in sorted(glob.glob("01-launch-v*.html")):
    t = io.open(f, encoding="utf-8").read()
    L[f] = t[t.index("<!DOCTYPE"):].splitlines()
skip = {10, 50, 90, 93, 105, 108, 351}        # the seven intended variables
ref = [l for i, l in enumerate(list(L.values())[0]) if i not in skip]
for f, lines in L.items():
    other = [l for i, l in enumerate(lines) if i not in skip]
    print(f, "IDENTICAL" if other == ref else "DIFFERS <-- investigate")
PY
```

If that prints anything but `IDENTICAL` four times, someone improved one file
and not the others, and the result will not mean what the report says.

**The version is invisible in link data, and D does not change that.** This
campaign holds the button URL byte-identical across its versions, so all four
send `utm_content=card_cta` and `utm_content=closing_cta`. Read the version off
the sending report, never off the clicks. Segment 02 solved this differently by
putting the version in `utm_content`; do not import that here without changing
all four files together.

**The chip is not the version marker here either.** It says "Now Live", which is
the launch, not the version, and it is identical in all four.

## Sending

Split the list into **even random quarters**, all at the same time of day.
Sending D a week later to non-openers is a follow-up, not a test, and it puts
the same person in front of four launch emails.

- **Reply-To** `inquiry@photomagic.io`, never a Ticket Magic inbox
- **From** a photomagic.io address, authenticated as photomagic.io
- **Audience** Photomagic's own Mailchimp audience. An unsubscribe here must not
  suppress a Ticket Magic contact.

### Subject lines

Each version carries two, listed at the top of its file. Four versions split
two ways is **eight cells out of one list**, and a launch list is usually the
smallest a product ever has. At that size eight cells is not a test, it is eight
anecdotes.

**At launch size, pick one subject per version** and keep the spare for the
resend. If you do run the subject test, run it on all four or you are comparing
a two-cell average against single cells.

**If the list is too small for four cells**, hold D back and send it as the
follow-up to whichever of A, B or C wins. That is a sequence, not a test, and its
numbers are not comparable to the other three. Decide which you are doing before
you send, because the report will not tell you afterwards.

## Before this can send

Images are pinned to **`79584fd`**, the head of this branch and the first commit
that carries every asset the three files reference, `logo-photomagic.png`
included. Searching any of the three files for `{{` now returns **one
line**: the postal address.

| | Status |
|---|---|
| `{{ASSET_SHA}}` ×7 | **Resolved.** Pinned to `79584fd`. |
| `{{POSTAL_ADDRESS}}` | **Outstanding.** photomagic.io publishes a phone number and an email address and no postal address. One is legally required in bulk commercial email. It cannot be invented or borrowed from Ticket Magic's office. |

**The pins cannot resolve until the branch is pushed.** Until `79584fd` is on
origin, jsDelivr has no commit to serve and every image is a broken box. After
pushing:

```bash
grep -oh 'https://cdn.jsdelivr.net[^"]*' 01-launch-va-moments.html | sort -u |   while read u; do curl -s -o /dev/null -w "%{http_code} %{content_type} $u
" "$u"; done
```

All seven must return `200` with an image content type. Then run a **real seed
send** (the `*|UNSUB|*` tag looks broken in preview and only resolves on send).

**Merge with a real merge commit, not a squash.** A squash replays the asset
bytes under a new commit and leaves these pins dangling at a SHA that no longer
exists. jsDelivr serves from cache for a while and then stops: it passes every
check today and fails silently later.

## Register it

Add a row to [`docs/campaign-register.csv`](../../../docs/campaign-register.csv)
with campaign ID `PM-2026-10-LAUNCH`. The `PM-` prefix is Photomagic; `DTM-` is
Ticket Magic and must not be reused here.

## Reading the result

Judge by **click rate**, not open rate. Apple Mail Privacy Protection inflates
opens enough that a promise can win the open and lose the send.

Version C is the one to watch most carefully: curiosity opens it, and the click
is the only signal the curiosity survived contact with the claim. Version B is
the riskiest to support, because a speed promise invites the reader to test it.

**Version D is the one to watch on forwards rather than clicks.** It is the only
letter that answers the question an agency's or a school's own compliance person
asks first, so a forward means somebody needed it while a click only means
somebody liked it. Expect it to be the most polarising of the four rather than
the weakest on average: either the reader has lost control of a set of
photographs before, or they have not.
