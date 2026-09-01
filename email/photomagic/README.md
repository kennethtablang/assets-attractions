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
01-photographers-studios/
  01-photographers-va-instant-delivery.html
  01-photographers-vb-selfie-search.html
  01-photographers-vc-photo-selection.html
02-event-planners-teams/
03-venues-hospitality/
04-schools-education/          EduMagic
05-wedding-planners/
```

**Segment numbers are Photomagic's own and start at 01.** They do not continue
from the EMS's nine segments. `01` here is photographers; `01` in `../outreach/`
is events services. The number means nothing across the two products.

Within a segment, versions A, B and C are structurally identical and differ only
in the feature they lead on, so a difference in reply rate is attributable to the
copy and nothing else. If you edit the layout of one, edit all of them.

## Before sending

Run the five checks in section 4, step 7 of the workflow doc. The two that catch
the most:

- `grep -c '{{' yourfile.html` must return **0**. The asset commit SHA is a token
  on purpose, so an unpinned image trips this check.
- The postal address token is a **legal blocker**, not a placeholder to tidy up
  later. photomagic.io publishes no postal address; find the registered one.
