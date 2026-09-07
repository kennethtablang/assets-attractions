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

**Nine segments, 01 to 09.** Segments 01 to 05 were planned when this file was
written. Segments 06 to 09 were promoted out of the expansion table below on
2026-09-02, when the folders were created. Four expansion candidates were left
behind and the reasons are recorded there, because a rejected segment that gets
silently dropped comes back as somebody's good idea six months later.

### The version plan, and why every segment has one

Photomagic has exactly **four sellable features**, one per card image in the
templates:

| Feature | Card image | The pain it answers |
|---|---|---|
| Same-day delivery | `instant-sharing` | The photos arrive days after the moment |
| AI selfie search | `selfie-search` | Nobody scrolls two thousand frames to find themselves |
| Client photo selection | `photo-selection` | Proofing runs over email and never converges |
| Private galleries | `secure-gallery` | The photos end up on a public link that travels |

**Every segment runs three versions, A/B/C, each leading on one of those four.**
All three show all four features; only the lead promise changes, so a difference
in reply rate is attributable to the promise and to nothing else. Which three,
and in which order, is the segment's own bet and it is written into each entry
below as **A/B/C**.

**A is always the control**, and it is always the feature this file predicts will
win for that segment. B and C are the challengers. If a challenger wins, this
file was wrong about that segment, which is a more useful finding than a feature
preference and is the reason to write the prediction down before sending rather
than after.

**No segment runs all four.** A fourth version splits an already small cold list
into a fourth cell for a feature the segment was never expected to want. The
feature left out of each A/B/C is a deliberate omission, not an oversight.

The whole plan on one screen. **A** is the control, **B** and **C** the
challengers, and a dash is the feature that segment does not lead on:

| # | Segment | Same-day | Selfie search | Selection | Private galleries | Folder |
|---|---|:---:|:---:|:---:|:---:|---|
| 01 | Photographers and studios | A | B | C | - | not built |
| 02 | Event planners and teams | **A** | **B** | - | **C** | **BUILT** |
| 03 | Venues and hospitality | B | A | - | C | not built |
| 04 | Schools and education | B | **never** | C | A | not built |
| 05 | Wedding planners and bridal | B | C | A | - | not built |
| 06 | Sports, races and academies | B | A | - | C | not built |
| 07 | Corporate HR and internal | B | **never** | C | A | not built |
| 08 | Nonprofits and community | A | C | - | B | not built |
| 09 | Real estate launches | A | C | - | B | not built |

Read the columns as well as the rows. **Same-day delivery leads four segments
and appears in all nine**, which is what it means for it to be the core promise.
**AI selfie search leads two and is banned from two**, and those two bans are the
only hard rules in this table: segments 04 and 07 must never receive a
face-search letter, for reasons written into their entries below. **Client photo
selection leads only segment 05** and is absent from five, which is the honest
read of a feature built for studios being sold to people who commission them.

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
- **A/B/C:** A same-day delivery · B AI selfie search · C client photo selection
  · *omits* private galleries. A studio already owns its client relationship and
  does not feel the public-link problem the way a corporate buyer does.
- **Folder:** `01-photographers-studios/` · **not built**
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
- **A/B/C:** A same-day delivery · B AI selfie search · C private galleries
  · *omits* client photo selection, which this file assigns to studios rather
  than to the agency that commissioned them.
- **Folder:** `02-event-planners-teams/` · **BUILT**, three letters on the dark
  card layout. See that folder's README.

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
- **A/B/C:** A AI selfie search · B same-day delivery · C private galleries
  · *omits* client photo selection. A venue hosts the event, it does not proof
  the shoot.
- **Folder:** `03-venues-hospitality/` · **not built**
- **Watch for:** the buyer usually sits in marketing, not operations, and the two
  read a letter differently. A banquet manager wants the gate to move; a
  marketing manager wants the content. The A/B/C split above leans marketing, so
  check which titles the Apollo list actually returned before reading the result.

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
- **A/B/C:** A private galleries · B same-day delivery · C client photo selection
  · **omits AI selfie search, and that omission is a rule, not a preference.**
- **Folder:** `04-schools-education/` · **not built**
- **Watch for:** **children's images carry consent obligations the other
  segments do not.** Do not send this segment copy that implies open or public
  galleries. Lead on access control, or do not send to this segment at all.

  **THERE IS NO VERSION C ON SELFIE SEARCH FOR THIS SEGMENT.** Every other
  segment gets a face-search letter and this one does not. Running face
  recognition against photographs of children is the single claim in this
  product most likely to end a conversation with a school, and a cold email is
  the worst possible place to raise it. The capability still appears in the
  feature showcase, because the showcase is held identical across a segment's
  three versions and describes the product rather than the pitch. Nothing leads
  on it, no subject line mentions it, and the letter never asks a school to
  picture it. If somebody later decides schools should get a selfie-search
  version, that is a product and legal conversation first and a copy decision
  second.

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
- **A/B/C:** A client photo selection · B same-day delivery · C AI selfie search
  · *omits* private galleries, which a couple hears as a feature for somebody
  else's compliance department.
- **Folder:** `05-wedding-planners/` · **not built**
- **Watch for:** the sharpest seasonality in the file. UAE wedding season runs
  roughly October to April and this segment is close to unreachable in July. A
  flat result in August means the month, not the message.

### 06. Sports, races and academies

Mass participation and competitive sport: road races, tournaments, leagues,
academies. Promoted from the expansion table on 2026-09-02.

**This is the strongest selfie-search case the product has**, and it is worth
being precise about why. A marathon photographer shoots five thousand runners.
The incumbent solution is bib-number search, which fails whenever the bib is
obscured by an arm, a jacket, a water station or another runner, and that is a
large fraction of frames. A selfie does not depend on the bib being visible at
all. This is the one segment where the feature is not a convenience but a
straight replacement for a tool they already run and already complain about.

- **Apollo industries:** `sports`, `health, wellness and fitness`,
  `recreational facilities and services`, `events services`
- **Company keywords:** marathon, half marathon, triathlon, sportive, cycling
  club, running club, race organiser, race organizer, race timing, chip timing,
  padel, tennis academy, football academy, sports academy, sports club,
  tournament, league, obstacle race, endurance, CrossFit, fitness competition,
  school sport, sports event management
- **Titles:** Race Director, Event Director, Founder, Owner, Operations Manager,
  Marketing Manager, Head of Marketing, Community Manager, Academy Director,
  Club Manager, General Manager, Head of Events
- **Employee count:** 1 to 100
- **Lead with:** AI selfie search, and lead hard. Nothing else in the product
  matters to a race director by comparison.
- **A/B/C:** A AI selfie search · B same-day delivery · C private galleries
  · *omits* client photo selection. Nobody proofs a race.
- **Folder:** `06-sports-races-academies/` · **not built**
- **Watch for:** two things. **Season:** UAE outdoor sport runs roughly October
  to April and the race calendar is nearly empty in summer, so send in season or
  do not send. **Minors:** an academy is a school in everything but name, so
  apply segment 04's posture to any list that returns youth academies. Split
  them out rather than sending them the selfie-search letter.

### 07. Corporate HR, internal comms and employer brand

Staff parties, annual days, town halls, long-service awards, family days,
offsites, CSR days. Promoted from the expansion table on 2026-09-02.

**This segment is found by title, not by industry.** The company can be a bank,
a contractor, a logistics firm or a software house; what makes it a prospect is
that somebody inside it owns the employee-experience budget and runs four
photographed events a year on it. Filtering by industry here produces noise.
Filter by title and employee count, and let the industry fall where it falls.

- **Apollo industries:** any. If a bias is needed for a first list, the UAE
  headcount sits in `oil & energy`, `banking`, `construction`,
  `logistics and supply chain`, `retail`, `information technology and services`,
  `real estate`, `hospitality`.
- **Company keywords:** not the primary filter. Leave the keyword field empty and
  let title plus headcount do the work.
- **Titles:** Head of Internal Communications, Internal Communications Manager,
  Employer Brand Manager, Employee Engagement Manager, People and Culture
  Manager, Head of People, Culture Manager, HR Manager, HR Director, Head of HR,
  CSR Manager, Sustainability Manager, Office Manager, Executive Assistant
- **Employee count:** 200 to 2,000
- **Lead with:** private galleries. Staff photographs are internal by default and
  the first question this buyer asks is who else can see them.
- **A/B/C:** A private galleries · B same-day delivery · C client photo selection
  · *omits* AI selfie search. Face recognition applied to a company's own
  employees is a works-council and data-protection conversation, not a cold
  email opener, and the reasoning is the same one that governs segment 04 even
  though the subjects are adults.
- **Folder:** `07-corporate-hr-internal/` · **not built**
- **Watch for:** **this is the one segment that deliberately breaks the size
  exclusion in section 8.** The usual rule caps the list at 1,000 employees
  because the buying cycle costs more than the contract. Here the headcount is
  the qualifier rather than the disqualifier: a 1,500 person company has an
  engagement manager, a discretionary budget and an annual day, and the photos
  never leave the building, so no procurement is triggered. That reasoning holds
  only while the buyer really can spend on a card. **Verify that on the first
  fifty contacts before scaling the list**, because if it turns out these
  purchases route through procurement, this segment is not a fit at this price
  and should be dropped rather than nurtured.

  Section 8 also excludes HR roles by default. This segment is the exception the
  exclusion already names. Do not apply both.

### 08. Nonprofits, charity galas and community events

Fundraising galas, awards nights, community iftars, volunteer days, member
events. Promoted from the expansion table on 2026-09-02.

**The pitch is the news cycle, not the photography.** A fundraiser's thank-you
email goes out within forty-eight hours or it does not go out at all, and the
photographs are what makes it worth opening. A gallery that arrives the following
week arrives after the moment the whole event was staged to create.

- **Apollo industries:** `nonprofit organization management`,
  `civic & social organization`, `philanthropy`, `fund-raising`,
  `religious institutions`, `international affairs`
- **Company keywords:** charity, foundation, nonprofit, non-profit, NGO,
  fundraising, fundraiser, gala dinner, awards night, volunteer, community
  centre, community center, humanitarian, endowment, social impact, CSR,
  donor relations, member events
- **Titles:** Executive Director, Development Manager, Head of Fundraising,
  Fundraising Manager, Communications Manager, Head of Communications, Marketing
  Manager, Events Manager, Programme Manager, Program Manager, Community
  Manager, Founder
- **Employee count:** 2 to 200
- **Lead with:** same-day delivery, then private galleries for donor events.
- **A/B/C:** A same-day delivery · B private galleries · C AI selfie search
  · *omits* client photo selection. There is no client to proof for.
- **Folder:** `08-nonprofits-community/` · **not built**
- **Watch for:** **price sensitivity is real here and the letters must respect
  it.** Lead on the free tier and let the pricing strip do the rest. Do not open
  a nonprofit letter on Corporate at 150 dollars a month. Separately, a
  meaningful share of UAE charities are government linked or royal foundations,
  which reintroduces exactly the procurement cycle this ICP is built to avoid.
  Expect to split the list into independents and government linked, and expect
  the independents to be the ones that reply.

### 09. Real estate launches and handovers

Off-plan launches, sales gallery openings, broker roadshows, handover ceremonies,
master community events. Promoted from the expansion table on 2026-09-02.

**This is the most UAE-specific segment in the file**, which is both why it is
here and why it is last. Developers run a dense photographed event calendar,
brokers are commission funded and buy their own tools without asking anyone, and
launch photography has a publication deadline measured in days because the
listing goes live either way.

- **Apollo industries:** `real estate`, `commercial real estate`,
  `architecture & planning`, `construction`
- **Company keywords:** property developer, real estate developer, off plan,
  off-plan, sales gallery, show apartment, property brokerage, real estate
  brokerage, real estate agency, master community, handover, property launch,
  broker event, investor event, property management, owners association,
  property exhibition
- **Titles:** Marketing Manager, Head of Marketing, Brand Manager, Events
  Manager, Head of Events, Head of Sales, Sales Director, Broker Relations
  Manager, Community Manager, Managing Director, Founder
- **Employee count:** 5 to 500
- **Lead with:** same-day delivery for launches, then private galleries for
  broker and investor events.
- **A/B/C:** A same-day delivery · B private galleries · C AI selfie search
  · *omits* client photo selection.
- **Folder:** `09-real-estate-launches/` · **not built**
- **Watch for:** **this is the segment most likely to collide with Ticket
  Magic.** EMS outreach segment 03 is real estate and is being sold an Event
  Management System to the same job titles at the same companies. Rule 2 in
  section 1 applies at full force: a company can be in both lists, but it holds
  two sender identities and two independent opt-outs, and the two letters must
  not arrive in the same week. **Diff this Apollo list against the EMS segment 03
  list before importing either.** Nothing in either tool will warn you.

### Expansion segments, still not in the folder plan

Real fit, no copy written, and **not promoted on 2026-09-02 for the reasons
given**. Do not search these until a letter exists for them, and read the reason
before reviving one.

| Segment | Apollo industries | Why it fits | Why it was not promoted |
|---|---|---|---|
| Conferences and exhibitions | `events services`, `computer software`, `information technology and services` | Delegate photos are a sponsor deliverable with a deadline attached | **Overlaps segment 02 too heavily to be a clean list.** Segment 02 already searches `conference organiser`, `exhibition organiser` and `trade show`. The organizers that would be left over are the large recurring show operators, and those are exactly the enterprises the ICP rules out on cycle time. A separate list here would mostly re-find segment 02 and attribute its replies to the wrong letter. |
| Government and civic events | `government administration`, `government relations` | The UAE public event calendar is dense and heavily photographed | **Fails the third ICP property.** Government buying runs through procurement by design, and this product is priced for a person with a card. It is a real fit on need and a poor fit on how the money moves. Revisit if an enterprise tier and a tender-capable process ever exist. |
| Museums, galleries, performing arts | `museums and institutions`, `performing arts`, `music` | Opening nights and season launches | **Volume, not fit.** The UAE count for these industries is small enough that a segment would not fill a send, and most venues that qualify are already reachable through segment 03. Fold the good ones into 03 rather than running a ninth list. |
| Car shows and automotive events | `automotive` | Crowd events with strong enthusiast photo demand | **Too narrow to justify its own copy.** The buyers are event agencies and venues running automotive formats, which are segments 02 and 03 with a keyword attached. Add `car show`, `auto show` and `motor show` to Block D instead. |

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
family day, staff party, iftar, gala, car show, auto show, motor show,
town hall, awards night, volunteer day, property launch, handover
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
| 2 | sports | 06 |
| 2 | real estate | 09 |
| 3 | restaurants | 03 |
| 3 | recreational facilities and services | 03, 06 |
| 3 | food & beverages | 03 |
| 3 | motion pictures and film | 01 |
| 3 | public relations and communications | 02 |
| 3 | nonprofit organization management | 08 |
| 3 | health, wellness and fitness | 06 |
| 3 | commercial real estate | 09 |
| 3 | consumer services | 05 |
| 3 | individual & family services | 05 |
| 3 | fund-raising | 08 |
| 4 | fine art | 01 |
| 4 | apparel & fashion | 05 |
| 4 | philanthropy | 08 |
| 4 | civic & social organization | 08 |
| 4 | religious institutions | 08 |
| 4 | international affairs | 08 |
| 4 | architecture & planning | 09 |
| 4 | construction | 09, 07 |
| 4 | wine and spirits | 03 |
| 4 | gambling & casinos | 03 |
| 4 | performing arts | see expansion table |
| 4 | museums and institutions | see expansion table |
| 4 | music | see expansion table |
| 4 | government administration | see expansion table |
| 4 | automotive | see expansion table |

Priority 1 and 2 are the first thousand contacts. Priority 3 and 4 wait until the
first three sends have said which message lands.

**Segment 07 is missing from this table on purpose.** Corporate HR and internal
comms is found by job title across every industry, so an industry row for it
would be every row. Filter that segment on title and headcount and leave the
industry field alone. See its entry in section 3.

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
| 611620 | NAICS | Sports and recreation instruction, segment 06 |
| 713940 | NAICS | Fitness and recreational sports centers, segment 06 |
| 813211 | NAICS | Grantmaking foundations, segment 08 |
| 813410 | NAICS | Civic and social organizations, segment 08 |
| 531210 | NAICS | Offices of real estate agents and brokers, segment 09 |
| 237210 | NAICS | Land subdivision, the developer code, segment 09 |
| 7221 | SIC | Photographic studios, portrait |
| 7335 | SIC | Commercial photography |
| 7999 | SIC | Amusement and recreation services |
| 8641 | SIC | Civic and social associations, segment 08 |
| 6552 | SIC | Land subdividers and developers, segment 09 |

There is **no useful code for segment 07**, for the same reason it has no
industry row: the code describes the employer, not the job, and the job is the
qualifier.

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
PM-04-schools-UAE-202610
PM-05-weddings-UAE-202610
PM-06-sports-UAE-202610
PM-07-corphr-UAE-202610
PM-08-nonprofits-UAE-202610
PM-09-realestate-DXB-202610
```

The slug is the segment's short name, not its folder name. Folder names carry
more words for readability; a saved search name has to stay short enough to read
in Apollo's sidebar. The number is what ties the two together, which is the other
reason not to renumber a segment once it exists.

Log every search in the campaign register with its result count on the day it was
run. Apollo counts drift, and a count with no date cannot be compared to anything
later.

---

## 10. Before you trust this file

Written 2026-09-01 from the product positioning, the pricing strip in the launch
letters, and the segment plan in [`README.md`](README.md). Extended 2026-09-02
with segments 06 to 09 and an A/B/C plan per segment, written the same way: from
the product and the positioning, not from data. **No part of it has been run in
Apollo.** Three things need checking before it drives a real send:

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

Two more, added with segments 06 to 09:

4. **The segment 07 buying assumption**, which is the largest unverified claim in
   this file. It says an engagement or internal-comms manager at a company of
   200 to 2,000 people can put this on a card without procurement. If that is
   wrong, segment 07 is not a fit at this price and should be dropped rather
   than nurtured. Fifty contacts and a handful of replies will settle it.
5. **The segment 09 overlap with Ticket Magic.** EMS outreach segment 03 sells
   an Event Management System to the same job titles at the same UAE developers
   and brokerages. Diff the two lists before importing either, and keep the
   sends apart in time. Nothing in either tool will warn you.

Then update this file with what the counts actually were. A targeting doc that
never absorbs its own results is a guess that grows more confident with age.

**Nine of nine segments now have a plan. One of nine has letters.** Segment 02 is
built; 01 and 03 to 09 are folders with a README and nothing else. That gap is
the honest state of this pipeline and it is recorded in each folder rather than
tracked somewhere central, so a folder always says whether it can send.
