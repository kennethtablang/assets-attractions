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

## The three versions

| File | Leads on | Headline |
|---|---|---|
| `01-launch-va-moments.html` | **The memory** (control) | Capture the Best **Moments** of Your Life |
| `01-launch-vb-same-day.html` | **The speed** | Deliver Event Photos **the Same Day** |
| `01-launch-vc-selfie-search.html` | **The capability** | One Selfie, Every **Photo** of You |

Version A is the message the design was drawn around, which is why it is the
control. B and C are challengers.

## What is under test

**Only the lead promise.** Exactly seven lines differ between the three files:

1. `<title>` 2. preheader 3. headline 4. hero subhead
5. card title 6. card intro 7. CTA lead line

**Held byte-identical:** the header bar, the four feature shots and captions,
both benefit columns and all eight bullets, the three How It Works steps, the
band photograph, the testimonial, the pricing strip, the button text, the button
URL, the closing band, the footer, and every measurement in the layout.

That is what makes this a test rather than three different emails. Verify before
you send:

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

If that prints anything but `IDENTICAL` three times, someone improved one file
and not the others, and the result will not mean what the report says.

## Sending

Split the list into **even random thirds**, all at the same time of day.
Sending C a week later to non-openers is a follow-up, not a test, and it puts
the same person in front of three launch emails.

- **Reply-To** `inquiry@photomagic.io`, never a Ticket Magic inbox
- **From** a photomagic.io address, authenticated as photomagic.io
- **Audience** Photomagic's own Mailchimp audience. An unsubscribe here must not
  suppress a Ticket Magic contact.

### Subject lines

Each version carries two, listed at the top of its file. Three versions split
two ways is **six cells out of one list**, and a launch list is usually the
smallest a product ever has.

**At launch size, pick one subject per version** and keep the spare for the
resend. If you do run the subject test, run it on all three or you are comparing
a two-cell average against single cells.

## Before this can send

Images are pinned to **`b0c928e`**, the commit that added `assets/photomagic/`
and nothing else. Searching any of the three files for `{{` now returns **one
line**: the postal address.

| | Status |
|---|---|
| `{{ASSET_SHA}}` ×7 | **Resolved.** Pinned to `b0c928e`. |
| `{{POSTAL_ADDRESS}}` | **Outstanding.** photomagic.io publishes a phone number and an email address and no postal address. One is legally required in bulk commercial email. It cannot be invented or borrowed from Ticket Magic's office. |

**The pins cannot resolve until the branch is pushed.** Until `b0c928e` is on
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
