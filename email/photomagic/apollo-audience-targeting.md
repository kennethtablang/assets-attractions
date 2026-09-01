# Photomagic: Apollo audience, keywords and industries

**Product** Photomagic (photomagic.io), instant event photo delivery
**Pipeline** Photomagic only. Not Ticket Magic. See
[`README.md`](README.md) and
[`docs/photomagic-campaign-workflow.md`](../../docs/photomagic-campaign-workflow.md).
**Status** Filter recipe, not a verified list. Nothing here has been run in
Apollo yet. See [Before you trust this file](#10-before-you-trust-this-file).

This is the lead-generation gap the workflow doc names in section 6. It exists so
the gap is filled with something reviewable rather than improvised inside the
Apollo UI at 11pm and lost when the tab closes.

---

## 1. Two rules that come before any filter

**1. Apollo contacts never enter Mailchimp.** They are cold, third-party sourced,
and have not opted in. Mailchimp's terms prohibit that list, and the penalty is
account suspension plus damage to the sending domain, which then poisons the warm
list. Apollo output goes to a cold outreach tool only. This is stated as an
account-termination risk in
[`docs/marketing-campaign-os.md`](../../docs/marketing-campaign-os.md) section 1,
and it applies to Photomagic exactly as it applies to Ticket Magic.

**2. Photomagic prospects are not Ticket Magic prospects.** A venue can be both.
If it is, it lives in two lists, gets two sender identities, and holds two
independent opt-outs. Merging them to save an import is the mistake the workflow
doc spends its first section warning about.

---

## 2. Who actually buys this

Photomagic sells to whoever is **responsible for the photos after the event
ends**. That is the entire ICP in one line, and it is more useful than any
industry code, because the job exists under a dozen different titles across
industries that otherwise have nothing in common.

The buyer has three properties:

| Property | Why it matters |
|---|---|
| Shoots or commissions photos at events with **many people in frame** | AI selfie search is worthless at a product shoot and decisive at a 400 guest gala |
| Has a **delivery problem**, not a shooting problem | The pain is the two week wait, the USB drive, the link that expired |
| Is **small enough to buy without procurement** | At $55 and $150 a month, the buyer and the decision maker have to be the same person |

That last property is the one most likely to be ignored, and it quietly wrecks
targeting. Pricing this low means an owner-operator or a department head with a
card, not an enterprise. **Filter hard on employee count.** A 5,000 person hotel
group is not a bad fit on paper, it is a bad fit on cycle time.

### The trigger worth searching for

Every good Photomagic prospect has recently run, or is about to run, an event
with a crowd in it. Recency beats fit. A wedding photographer in peak season is a
better prospect than a better-fitting studio that is dark until March.

---

## 3. Segments

Numbered to match the folder convention in [`README.md`](README.md). Build one
Apollo saved search per segment, never one combined search, because the copy
differs per segment and a merged list cannot be split back apart cleanly.

### 01. Photographers and studios

The core segment. They feel the delivery pain daily and they pay for tools
themselves.

- **Apollo industries:** `photography`, `media production`,
  `motion pictures and film`, `fine art`
- **Company keywords:** wedding photography, event photography, photo studio,
  photography studio, portrait studio, photo booth, 360 photo booth,
  photographer, videography, wedding films, corporate event photography,
  headshot studio, photo agency, creative studio
- **Titles:** Owner, Founder, Co-Founder, Managing Director, Photographer,
  Lead Photographer, Principal Photographer, Studio Manager, Studio Owner,
  Creative Director, Head of Production, Operations Manager
- **Employee count:** 1 to 20. Most will be 1 to 3.
- **Lead with:** client photo selection for wedding and portrait studios,
  same-day delivery for event shooters
- **Watch for:** this segment is heavily sole-trader, so Apollo coverage is
  thinner than the result count suggests. Expect a high share of generic `info@`
  addresses. Budget for that in the send plan rather than discovering it at
  bounce time.

### 02. Event planners and event management teams

They do not shoot, they commission. They buy Photomagic to look good to their own
client, which makes the same-day angle the whole pitch.

- **Apollo industries:** `events services`, `marketing and advertising`,
  `public relations and communications`, `management consulting`
- **Company keywords:** event management, event planning, event agency, event
  production, event organiser, event organizer, conference organiser, exhibition
  organiser, trade show, corporate events, brand activation, experiential
  marketing, roadshow, product launch, gala dinner, awards ceremony, MICE,
  destination management, DMC
- **Titles:** Event Manager, Senior Event Manager, Event Producer, Head of
  Events, Director of Events, Event Coordinator, Project Manager, Account
  Director, Brand Activation Manager, Experiential Manager, Managing Director,
  Founder
- **Employee count:** 2 to 200
- **Lead with:** same-day delivery, then AI selfie search for the large formats

### 03. Venues and hospitality

Hotels, ballrooms, clubs, attractions. The photos are a guest-experience asset
and a marketing asset at the same time, so the buyer often sits in marketing
rather than operations.

- **Apollo industries:** `hospitality`, `leisure, travel & tourism`,
  `restaurants`, `recreational facilities and services`, `entertainment`,
  `food & beverages`, `wine and spirits`, `gambling & casinos`
- **Company keywords:** hotel, resort, banquet, ballroom, wedding venue, event
  venue, conference centre, conference center, exhibition centre, beach club,
  nightclub, lounge, rooftop, theme park, water park, attraction, cruise, yacht
  charter, desert safari, catering
- **Titles:** Director of Sales and Marketing, Marketing Manager, Head of
  Marketing, Director of Events, Banquet Manager, Catering Sales Manager, Guest
  Experience Manager, Guest Relations Manager, Social Media Manager, Brand
  Manager, General Manager, Operations Manager
- **Employee count:** 10 to 500, with the decision maker check applied. A large
  chain needs a named marketing contact, not a head office switchboard.
- **Lead with:** AI selfie search. High guest counts are exactly where it wins.

### 04. Schools and education (EduMagic)

Graduations, sports days, recitals, school trips. Distinct enough in language and
in privacy posture that it carries its own product name in the folder plan.

- **Apollo industries:** `education management`, `primary/secondary education`,
  `higher education`, `e-learning`, `professional training & coaching`
- **Company keywords:** international school, private school, British curriculum,
  IB school, nursery, kindergarten, university, college, academy, campus life,
  student affairs, alumni relations, graduation
- **Titles:** Marketing Manager, Head of Marketing, Head of Admissions,
  Admissions Manager, Communications Manager, Head of Communications, Alumni
  Relations Manager, Student Life Coordinator, Principal, School Director,
  Events Coordinator
- **Employee count:** 20 to 500
- **Lead with:** secure private galleries, then same-day delivery
- **Watch for:** **children's images carry consent obligations the other four
  segments do not.** Do not send this segment copy that implies open or public
  galleries. Lead on access control, or do not send to this segment at all.

### 05. Wedding planners and bridal

Adjacent to 01 and 02 but a different vocabulary and a different season, so it
gets its own search rather than a keyword bolted onto photographers.

- **Apollo industries:** `events services`, `consumer services`,
  `individual & family services`, `apparel & fashion`
- **Company keywords:** wedding planner, wedding planning, wedding coordinator,
  bridal, destination wedding, wedding venue, wedding stylist, wedding
  decoration, engagement, nikah, mehndi, henna, walima, bridal boutique
- **Titles:** Wedding Planner, Owner, Founder, Creative Director, Lead Planner,
  Client Manager, Operations Manager
- **Employee count:** 1 to 30
- **Lead with:** client photo selection. Proofing and picking favourites is
  language this segment already uses with couples.

### Expansion segments, not yet in the folder plan

Real fit, no copy written. Do not search these until a letter exists for them.

| Segment | Apollo industries | Why it fits |
|---|---|---|
| Sports clubs, races, academies | `sports`, `health, wellness and fitness` | Marathons and tournaments are the strongest selfie-search case there is, thousands of finishers each wanting their own frame |
| Conferences and exhibitions | `events services`, `computer software`, `information technology and services` | Delegate photos are a sponsor deliverable with a deadline attached |
| Nonprofits and charity galas | `nonprofit organization management`, `civic & social organization`, `philanthropy`, `fund-raising` | Fundraiser photos have a short news cycle, so same-day matters |
| Government and civic events | `government administration`, `government relations` | The UAE public event calendar is dense and heavily photographed |
| Museums, galleries, performing arts | `museums and institutions`, `performing arts`, `music` | Opening nights and season launches |
| Corporate HR and internal comms | any industry, filtered on title | Staff parties, town halls, annual days, bought on the employer-brand budget |
| Real estate launches | `real estate`, `commercial real estate` | Launch events and handover ceremonies |
| Car shows and automotive events | `automotive` | Crowd events with strong enthusiast photo demand |

---

## 4. Master keyword bank

Paste into Apollo's company keyword field. Apollo treats comma-separated terms as
OR within one field, so **run these as separate blocks**, not as one wall of 120
terms. A single mega-query returns a list nobody can attribute a reply to.

**Block A, the act of shooting**

```
photography, photographer, photo studio, photography studio, portrait studio,
videography, videographer, photo booth, 360 photo booth, headshot, photo agency,
event photography, wedding photography, corporate photography, sports photography
```

**Block B, the act of organising**

```
event management, event planning, event agency, event production, event organiser,
event organizer, conference organiser, exhibition organiser, trade show,
corporate events, brand activation, experiential marketing, roadshow,
product launch, gala dinner, awards ceremony, MICE, destination management
```

**Block C, the place it happens**

```
hotel, resort, banquet, ballroom, wedding venue, event venue, conference centre,
exhibition centre, beach club, nightclub, rooftop, theme park, attraction,
catering, yacht charter, desert safari
```

**Block D, the occasion**

```
wedding, bridal, engagement, graduation, sports day, annual day, festival,
concert, marathon, tournament, expo, summit, conference, seminar, retreat,
family day, staff party, iftar, gala
```

**Block E, the pain. Highest intent, lowest volume.**

```
photo gallery, photo delivery, client gallery, online gallery, photo sharing,
image delivery, proofing, photo selection, digital album, event album,
face recognition, AI photo
```

Block E is the one worth running first. It returns the fewest companies and the
warmest ones, because a company that describes itself in delivery language has
already decided the problem is real.

---

## 5. Industry values

Apollo's industry filter is a **fixed dropdown**, not free text. A value that is
not in the dropdown silently matches nothing. The strings below are written as
Apollo renders them, but **pick them from the dropdown rather than typing them**,
and correct this file if any differ.

| Priority | Apollo industry | Segment |
|---|---|---|
| 1 | photography | 01 |
| 1 | events services | 02, 05 |
| 1 | hospitality | 03 |
| 2 | leisure, travel & tourism | 03 |
| 2 | entertainment | 03 |
| 2 | education management | 04 |
| 2 | primary/secondary education | 04 |
| 2 | higher education | 04 |
| 2 | marketing and advertising | 02 |
| 2 | media production | 01 |
| 3 | restaurants | 03 |
| 3 | recreational facilities and services | 03 |
| 3 | food & beverages | 03 |
| 3 | sports | expansion |
| 3 | motion pictures and film | 01 |
| 3 | public relations and communications | 02 |
| 3 | performing arts | expansion |
| 3 | museums and institutions | expansion |
| 3 | nonprofit organization management | expansion |
| 3 | consumer services | 05 |
| 3 | individual & family services | 05 |
| 4 | music | expansion |
| 4 | fine art | 01 |
| 4 | apparel & fashion | 05 |
| 4 | real estate | expansion |
| 4 | government administration | expansion |
| 4 | civic & social organization | expansion |
| 4 | religious institutions | expansion |
| 4 | automotive | expansion |
| 4 | wine and spirits | 03 |
| 4 | gambling & casinos | 03 |

Priority 1 and 2 are the first thousand contacts. Priority 3 and 4 wait until the
first three sends have said which message lands.

### NAICS and SIC, for the codes filter

Codes are stricter than keywords and much cleaner than the industry dropdown
wherever a code exists for exactly the thing you want.

| Code | Standard | Covers |
|---|---|---|
| 541921 | NAICS | Photography studios, portrait |
| 541922 | NAICS | Commercial photography |
| 561920 | NAICS | Convention and trade show organizers |
| 711310 | NAICS | Promoters of events with facilities |
| 711320 | NAICS | Promoters of events without facilities |
| 721110 | NAICS | Hotels and motels |
| 722320 | NAICS | Caterers |
| 611110 | NAICS | Elementary and secondary schools |
| 7221 | SIC | Photographic studios, portrait |
| 7335 | SIC | Commercial photography |
| 7999 | SIC | Amusement and recreation services |

---

## 6. Technology filter, the sharpest signal available

Apollo can filter on the technology a company's site runs. For this product that
is close to a buying-intent signal, because a company already paying for a
gallery tool has accepted the category and is now comparing on price, speed and
face search.

**Direct competitors and adjacent gallery tools:** Pixieset, Pic-Time,
ShootProof, SmugMug, Zenfolio, CloudSpot, PhotoShelter, Format

**Booking and studio management:** HoneyBook, Dubsado, 17hats, Sprout Studio,
Studio Ninja, Tave

**Event platforms, for segment 02:** Eventbrite, Cvent, Whova, Bizzabo, Splash

**Generic site stacks, weak on their own:** WordPress, Squarespace, Wix, Showit,
Shopify

Run the first group as its own search and treat it as the highest-priority list
in this entire file. Never run the fourth group alone. It matches half the
internet.

---

## 7. Geography

The product is UAE-based. The WhatsApp number in every letter is
+971 58 259 1702 and support runs on Gulf hours.

- **Core:** Dubai, Abu Dhabi, Sharjah, Ajman, Ras Al Khaimah, Fujairah,
  Umm Al Quwain
- **Ring 2, once the core is exhausted:** Saudi Arabia (Riyadh, Jeddah, Dammam,
  AlUla), Qatar (Doha), Kuwait, Bahrain, Oman (Muscat)
- **Ring 3, a decision and not an assumption:** anywhere else. The product is
  SaaS and travels fine, but the letters lean on a UAE number and Gulf-hours
  support. Decide whether a photographer in Manila or London is being sold to
  before putting them in a list, and if the answer is yes, the copy needs a
  version that does not lean on the local number.

Search on **company location**, not contact location. A Dubai hotel whose
regional marketing manager sits in Riyadh is still a Dubai prospect.

---

## 8. Exclusions

Negative filters are worth more than positive ones here, because `photography`
matches a large number of companies that will never buy this.

**Exclude by keyword:**

```
stock photo, stock photography, photo printing, printing press, camera rental,
camera store, drone survey, aerial survey, photogrammetry, real estate
photography, product photography, food photography, e-commerce photography,
medical imaging, passport photo, ID photo, photo frame, image licensing
```

The logic: no crowd in frame means no selfie search, no guest gallery and no
same-day pressure. A product photographer shooting 40 SKUs for a catalogue has
none of the three problems Photomagic solves. Passport and ID studios match
`photography` and are the single largest source of junk in this category.

**Exclude by industry:** printing, semiconductors, medical devices, computer
hardware, photography equipment retail.

**Exclude by size:** over 1,000 employees, unless a named marketing or events
contact was found. At this price point the buying cycle costs more than the
contract is worth.

**Exclude by role:** anything in IT, finance, legal, procurement or HR
operations, except where the segment is corporate internal comms and HR is the
buyer. Photomagic is bought by the person embarrassed by the delivery delay, and
that person sits in marketing, events, or the studio itself.

---

## 9. Saved search naming

One saved search per segment per geography, so a reply can be traced back to the
filter that produced it.

```
PM-<segment number>-<segment slug>-<geo>-<yyyymm>

PM-01-photographers-UAE-202610
PM-02-planners-UAE-202610
PM-03-venues-DXB-202610
```

Log every search in the campaign register with its result count on the day it was
run. Apollo counts drift, and a count with no date cannot be compared to anything
later.

---

## 10. Before you trust this file

Written 2026-09-01 from the product positioning, the pricing strip in the launch
letters, and the segment plan in [`README.md`](README.md). **No part of it has
been run in Apollo.** Three things need checking before it drives a real send:

1. **Every industry string, against the live dropdown.** Apollo's taxonomy
   changes, and a value that is not in the list fails silently by returning
   nothing rather than erroring. Verify, then correct this file in place.
2. **Real result counts per segment, in the UAE.** Segment 01 is the one at risk.
   Sole-trader photographers are under-covered in B2B databases, and if the UAE
   count comes back small, segment 01 needs a different source (Instagram,
   wedding directories, the Photomagic community page) rather than a wider Apollo
   filter. That is the same conclusion the workflow doc reached before this file
   existed, so treat it as likely until the count says otherwise.
3. **Deliverability on a 50 contact sample per segment**, before committing the
   full list. Apollo's own verification is not sufficient on its own, and this
   category runs heavy on `info@` catch-alls that verify clean and then bounce.

Then update this file with what the counts actually were. A targeting doc that
never absorbs its own results is a guess that grows more confident with age.
