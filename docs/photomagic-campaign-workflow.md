# Photomagic Campaign Workflow

**This is a separate pipeline from the Ticket Magic Event Management System.**
It shares this repository, the jsDelivr CDN, and the weight budgets in the root
[`README.md`](../README.md). It shares nothing else.

The Ticket Magic side is documented in
[`docs/marketing-campaign-os.md`](marketing-campaign-os.md) (the full operating
system) and [`docs/express-campaign-sop.md`](express-campaign-sop.md) (the
same-day lane). Do not read those two as if they cover Photomagic. They assume a
UAE attractions and event-organizer audience, a Ticket Magic sender identity, and
the `DTM-` campaign register. All three of those are wrong here.

---

## 1. Why this is separate, and what "separate" actually means

Photomagic and Ticket Magic are two products sold to two markets by one company.
The temptation is to run one pipeline with a product column. Resist it, because
four things genuinely cannot be shared:

| | Ticket Magic | Photomagic |
|---|---|---|
| Product | Event Management System | Instant event photo delivery |
| Buyer | Event organizers, venues, operators | Photographers, studios, event teams |
| Domain | ticketmagic.me | photomagic.io |
| Reply-to | support@ticketmagic.me | inquiry@photomagic.io |
| WhatsApp | +971 52 706 4878 / +971 52 952 1204 | +971 58 259 1702 |
| Template | `email/templates/email-corporate.html` | `email/templates/email-photomagic.html` |
| Palette | Navy, teal, yellow CTA | Indigo, white CTA |
| Assets | `assets/icons/`, `assets/summer_is_here_campaign/` | `assets/photomagic/` |
| Campaign ID | `DTM-` | `PM-` |
| Audience | Ticket Magic list | **Its own Mailchimp audience** |

**The audience separation is the one that will bite you.** If Photomagic sends
from a Ticket Magic audience, a photographer who unsubscribes from photo-delivery
mail silently suppresses a contact the EMS side may have been working for months.
No report tells you it happened, because from Mailchimp's point of view nothing
went wrong. Two products, two audiences, two opt-outs.

**The sending domain matters too.** Photomagic mail should authenticate as
photomagic.io. Sending Photomagic copy from a ticketmagic.me domain, or the
reverse, spends one product's sender reputation on the other's list, and a
recipient who checks the headers sees a mismatch between the brand in the letter
and the domain that sent it.

---

## 2. What already exists

```
assets/photomagic/                                  brand assets, committed once
  photomagic-logo-indigo-682x162.png                for the white header bar
  photomagic-logo-white-682x162.png                 for the dark footer
  photomagic-feature-instant-sharing-580x580.jpg    same-day delivery
  photomagic-feature-selfie-search-580x580.jpg      AI face search
  photomagic-feature-photo-selection-580x580.jpg    client proofing
  photomagic-feature-secure-gallery-580x580.jpg     private galleries
  photomagic-band-photographer-1100x550.jpg         one human photograph

email/templates/email-photomagic.html               the template. Never edit.
docs/photomagic-campaign-workflow.md                this file.
```

All seven assets were taken from photomagic.io on 2026-09-01 and processed for
email. Provenance, processing, and the reason each one exists is documented in
the comment header of the template. Read it before you touch any of them.

---

## 3. Folder convention for a Photomagic campaign

Mirror the outreach structure the EMS side uses, under its own root so the two
never interleave:

```
email/photomagic/
  01-photographers-studios/
    01-photographers-va-{module}.html
    01-photographers-vb-{module}.html
    01-photographers-vc-{module}.html
  02-event-planners-teams/
  03-venues-hospitality/
  04-schools-education/          (EduMagic)
  05-wedding-planners/
```

For a seasonal or promotional campaign rather than cold outreach, use the
`campaigns/` convention from the root README instead:

```
campaigns/2026/10-photomagic-launch/{email,social,web}/
```

**Segment numbering is Photomagic's own and starts at 01.** It does not continue
from the EMS's nine segments. `01` here is photographers; `01` there is events
services. They are different lists and the number means nothing across products.

---

## 4. The nine-step build

### Step 1. Pick the segment and the feature under test

Photomagic has four sellable features, one per card image. A version leads on
exactly one:

| Feature | Card image | Sell it to |
|---|---|---|
| Same-day delivery | `instant-sharing` | Everyone. The core promise. |
| AI selfie search | `selfie-search` | Large-guest-count events |
| Client photo selection | `photo-selection` | Wedding and portrait studios |
| Secure galleries and leads | `secure-gallery` | Studios who want repeat bookings |

As on the EMS side, run A/B/C within a segment where all three letters are
structurally identical and only the leading feature changes. That is the only way
a difference in reply rate means anything.

### Step 2. Copy the template, never edit the original

```bash
cp email/templates/email-photomagic.html \
   email/photomagic/01-photographers-studios/01-photographers-va-instant-delivery.html
```

### Step 3. Delete the optional blocks you do not need

Blocks run `BLOCK n` to `/BLOCK n`. Delete whole blocks only. A half-deleted
table breaks the layout in Outlook. Blocks 1, 2, 3 and 13 are required; the rest
are optional.

For a cold outreach letter, the usual set is 1, 2, 3, 4, 5, 6, 7, 12, 13. Drop
the pricing strip: a price in a first-touch email invites a comparison before the
value is established.

### Step 4. Resolve every token

Personalisation tokens resolve to fixed wording, not to merge tags. Mailchimp has
no inline fallback syntax, so a merge tag means trusting an Audience default or
shipping a blank mid-sentence. `Hi there,` costs nothing and cannot break.

### Step 5. Commit the assets FIRST, then pin

**This is the step that gets skipped and the failure is silent.** A jsDelivr URL
addresses a commit, not a working tree. Editing an image on disk changes nothing
a recipient sees. The email looks correct in the repo and wrong in the inbox.

```bash
# only if you added or changed an image
git add assets/photomagic
git commit -m "Add Photomagic campaign assets"
git rev-parse HEAD          # this is the SHA you pin
git push
```

Then replace every `ASSET_SHA` placeholder in the campaign file with that SHA.
The template deliberately writes it in the double-curly-brace form so the
pre-send check for that character pair **catches an unresolved SHA**. An unpinned
image is a shipping error and it should trip the same wire as a missing headline.

Never `@main`: jsDelivr caches it up to 7 days, so a swapped image shows one
version to one subscriber and a different version to the next.

**Merge with a real merge commit, not a squash.** A squash replays the bytes
under a new commit and leaves the pin dangling at a SHA that no longer exists on
any branch. jsDelivr serves it from cache for a while and then stops: it passes
every check today and fails silently later.

### Step 6. Fill in the postal address

`POSTAL_ADDRESS` is a token because **photomagic.io publishes a phone number and
an email address and no postal address.** A physical mailing address is legally
required in bulk commercial email in most jurisdictions this list will touch.

It cannot be invented, guessed, or borrowed from Ticket Magic's Saheel Tower
office unless Photomagic genuinely operates from there. Find out what the
registered address is. If the answer is that it *is* the Saheel Tower address,
write it out anyway so the file records what shipped.

**This is a blocker, not a nice-to-have. Do not send without it.**

### Step 7. Verify before you send

```bash
# 1. zero unresolved tokens, including the asset SHA
grep -c '{{' email/photomagic/**/your-file.html          # must be 0

# 2. every image resolves on the CDN, not just on disk
grep -oh 'https://cdn.jsdelivr.net[^"]*' your-file.html | sort -u | \
  while read u; do curl -s -o /dev/null -w "%{http_code} %{content_type} $u\n" "$u"; done
# every line must read 200 image/...

# 3. no em dashes, no smart quotes (house rule)
grep -P '[\x{2014}\x{2013}\x{2018}\x{2019}\x{201C}\x{201D}]' your-file.html   # must be empty

# 4. no Ticket Magic leakage into a Photomagic letter
grep -in 'ticketmagic\|saheel\|971527064878\|971529521204\|0B3D5C\|FFC24B' your-file.html

# 5. under the Gmail clipping threshold
wc -c your-file.html                                      # must be < 102000
```

Then a **real seed send**, not a preview. `*|UNSUB|*` and `*|UPDATE_PROFILE|*`
resolve on send and will look broken in preview. They sit inside `href`
attributes, so an unresolved tag leaves the footer looking correct while the
unsubscribe link is dead. That is a legal problem, not a cosmetic one.

### Step 8. Send from the Photomagic audience

Not a Ticket Magic segment. See section 1.

### Step 9. Register it

Add a row to [`docs/campaign-register.csv`](campaign-register.csv) with a `PM-`
campaign ID, for example `PM-2026-10-LAUNCH`. The `DTM-` prefix is Dubai Ticket
Magic and must not be reused. UTM `utm_campaign` values should carry the product
too: `photomagic_launch_2026`, never a bare `launch_2026` that collides with an
EMS campaign in the same analytics property.

---

## 5. Copy rules specific to this product

**Lead with the delay, not the technology.** The buyer's pain is that photos
arrive days late and the moment has passed. AI face recognition is *how*, and it
only lands after the *why*.

**"No app needed" is a real objection killer.** Guests will not install anything
at an event. Say so.

**Do not promise what the site does not.** In particular the site makes no claim
about where face data is stored, how long it is kept, or which privacy regime it
complies with. A studio's client will ask all three. Have the answer ready for
the call; do not put it in the email.

**Prices go stale and a sent email is frozen.** The live tiers as of 2026-09-01
are Free $0, Pro $55/mo, Corporate $150, Enterprise custom. Check every figure
against the live pricing page on the day you send, or leave prices out and lead
on the free trial. A wrong price in an inbox is a refund conversation later.

**Testimonials must be attributed.** The site carries three real named reviews
(Santhiyagu Pasindu, Sylvester Cardoz, Steevan Vas). Use one verbatim, or one a
client gave you in writing. An unattributed quote reads as invented, and this
buyer is one search away from checking.

**No em dashes.** House rule, same as everywhere else in this repo. Recast the
sentence with a period, colon, comma or brackets rather than swapping the
character for a hyphen.

**The partner logos on the site are not yours to use.** `Partners/01-08.png` are
eight third-party client marks. Using someone else's logo in a cold email is a
permission question, not a design question. Get written sign-off first.

---

## 6. What this workflow deliberately does not have

- **No lead-generation section.** The EMS side's Apollo recipe targets event
  organizers by industry. Photographers and studios are found differently
  (Instagram, wedding directories, the Photomagic community page itself). That
  research has not been done yet and inventing a filter recipe here would be
  worse than leaving the gap visible.
- **No express lane.** The EMS express SOP works because that pipeline has run
  enough times to know what is safe to skip. This one has run zero times. Build
  three campaigns the long way first, then write the shortcut from what actually
  turned out to be skippable.
- **No post-mortem template of its own.** Use
  [`docs/templates/campaign-post-mortem.md`](templates/campaign-post-mortem.md);
  it is product-agnostic.
