# Speedy Travels: brief and research handoff

Updated 4 October 2026, end of chat 1. Use this file to start chat 2 with full context.

## 1. Start here

Do these three things before chat 2:

1. **Turn on network access.** In chat 1 the sandbox blocked every website except search and Mobbin, so Claude could not open or screenshot the sites in section 4. Open the cloud environment menu in the session title bar, click Edit, then change Network access. A broader access level is the simplest fix. If you pick Custom, keep the default package managers and add the domains in section 7. Steps: https://code.claude.com/docs/en/cloud-environments#network-access
2. **Add the workbook.** The brief builds on the Speedy Travels UK Travel Intelligence Database, and this repo does not have it yet. Put it in `data/` or attach it in chat 2.
3. **Paste this as your first message:**

```text
Read docs/speedy-travels-brief-and-research.md in full before you do anything. Section 3 is my brief and it is the source of truth. Network access is now on.

Work in this order and wait for my OK after each step:
1. Open and screenshot every site in section 4. Write a one-page design direction for Speedy: colours, type, imagery and motion rules, plus what we take from each site.
2. Propose the MVP architecture and data model (brief sections 31, 32 and 36). Start from the stack in section 5.2 and only change it with a reason.
3. Plan the import of the workbook in data/ (brief section 2). Keep the legacy Speedy IDs.
4. Build phase 0, then phase 1, from section 5.3.

Keep answers short. No em dashes. Only ask me when the decision is mine.
```

Claude Code reads `CLAUDE.md` in the repo root on its own, and that file points here. In a normal claude.ai chat, upload this file with the prompt.

## 2. Where things stand

| Item | Status |
|---|---|
| Repo | `kna1nshh/speedy-travels`, branch `claude/serene-gates-0x09qb`. No code yet. |
| Brief | Studied. Full text in section 3. |
| Research | Google, Mobbin and Awwwards done (section 4). Sites checked through search only. |
| Design direction | Not started |
| Architecture and data model | Not started |
| Workbook | Not in the repo yet |

**What you asked for in chat 1**

1. Read and study the brief.
2. Find products like Speedy on Google and Mobbin and study them.
3. Find Awwwards-level animated travel websites like Speedy and send the links.
4. Keep replies short: no paragraphs, no em dashes.
5. Save the brief and the research in one md file for the next chat (this file).

## 3. Your brief (full text)

Your words, unchanged. I added Markdown headings and bullets and swapped your long dashes for colons.

**SPEEDY TRAVELS: UK DMC, TRAVEL DESIGN & BOOKING PLATFORM**

### PROJECT OBJECTIVE

Build a production-ready customer website and internal DMC operations platform for Speedy Travels.

Speedy Travels is initially a UK Destination Management Company (DMC).

The business should combine:

- Destination discovery
- Expert UK travel information
- Intelligent trip recommendations
- Tailor-made itinerary creation
- Hotels and unique stays
- Activities and attractions
- Road trips
- Scenic rail journeys
- Transfers
- Car hire
- Tours and excursions
- Cruises/boat experiences
- Package holidays
- Online enquiries
- Quotations
- Customer payments
- Booking management
- Supplier management
- DMC operations

The platform must NOT behave like a generic OTA displaying hundreds of undifferentiated options.

Its core proposition is:

“Tell us who is travelling and what you want to experience. Speedy Travels will design the right UK trip for you.”

The system should recommend a small number of highly relevant choices and clearly explain WHY they were recommended.

### 1. CORE PRODUCT PHILOSOPHY

Speedy Travels is:

Destination Intelligence + Human Travel Designers + Booking + Local DMC Operations

The customer journey should be:

DISCOVER → PERSONALISE → RECOMMEND → DESIGN → CUSTOMISE → PRICE → BOOK → TRAVEL → SUPPORT

Do not design the platform around hotel search.

Design it around the trip.

Hotels, activities, transfers, trains, car hire and other products are components of the trip.

### 2. SOURCE DATABASE

Use the existing Speedy Travels UK Travel Intelligence Database as the seed dataset.

Preserve existing IDs wherever possible.

Import and normalise:

- Destinations
- National Parks
- Regions
- Bases/towns
- Experiences
- Attractions
- Activities
- Road trips
- Route days
- Route stops
- Hotels/stay strategies
- Unique stays
- Scenic rail journeys
- Family suitability
- Walking difficulty
- Adventure suitability
- Accessibility
- Halal infrastructure
- Rainy-day suitability
- Seasonality
- Practical travel information
- Supplier information
- Recommendation scores
- Trip templates
- Sources
- Verification dates

Every travel-content record must support:

- source URL
- source type
- last verified date
- verification status
- editor notes
- public notes
- internal notes
- active/inactive status

Separate relatively static destination intelligence from dynamic commercial data.

Never treat static database information as proof of current:

- price
- availability
- opening hours
- departure time
- room availability
- activity slot
- road closure
- weather
- tide
- ferry status
- EV charger status

Dynamic information must be obtained from a live supplier/API/manual verification layer.

### 3. CUSTOMER WEBSITE

Create a premium, modern, mobile-first UK travel website.

The homepage should NOT begin with a conventional hotel-search box.

Lead with:

“What would you like to experience in the UK?”

Provide experience discovery such as:

- Family Adventures
- Scenic Britain
- Road Trips
- Castles & Heritage
- National Parks
- Trains & Rail Journeys
- Coastal Escapes
- Wildlife
- Adventure
- Food
- Luxury
- Romantic Escapes
- Accessible Travel
- Easy Sightseeing
- Unique Stays

Primary navigation:

- Destinations
- Things To Do
- Road Trips
- National Parks
- Family Holidays
- Scenic Journeys
- Hotels & Unique Stays
- Tours & Experiences
- UK Packages
- Build My Trip

Also provide:

- About Speedy Travels
- UK DMC / Travel Trade
- Contact a Travel Designer
- My Trip

### 4. SMART TRIP FINDER

Create a conversational trip-planning questionnaire.

Ask:

- Where are you travelling from?
- Travel dates or approximate month?
- Number of nights?
- Adults?
- Children?
- Ages of children?
- Budget?
- Total budget or per-night budget?
- Main interests?
- Secondary interests?
- Preferred destinations, if any?
- First visit to UK?
- Walking tolerance?
- Maximum daily driving?
- Will they have a car?
- Would they like Speedy to arrange a car?
- Rail preference?
- Accommodation preference?
- Hotel standard?
- Unique stays?
- Accessibility requirements?
- Dietary requirements?
- Halal requirement?
- Occasion?
- Anniversary?
- Honeymoon?
- Birthday?
- Things they definitely want to see?
- Things they want to avoid?

Trip pace:

- Relaxed
- Balanced
- Fast

### 5. RECOMMENDATION ENGINE

Implement a recommendation engine using the Speedy suitability data.

Use three stages.

**Stage 1: Hard Filters**

Remove destinations/products incompatible with:

- dates
- number of nights
- child ages
- mobility/accessibility
- maximum driving
- transport requirement
- hard budget limits
- critical activity restrictions
- required availability

**Stage 2: Weighted Scoring**

Score destinations against:

- Family
- Scenery
- Adventure
- Heritage
- Coast
- Rail
- Wildlife
- Food
- City
- Luxury
- Value
- Low Walking
- Car-Free
- Halal Infrastructure
- Accessibility
- Rainy-Day Depth
- Compactness
- Seasonality
- Length-of-stay fit

Allow administrators to change scoring weights without changing code.

**Stage 3: Recommendation Diversity**

Do not simply return the three mathematically closest destinations.

Provide meaningful alternatives.

Example:

- BEST MATCH: Lake District
- ALTERNATIVE: North York Moors
- MORE ADVENTUROUS: Eryri

Every recommendation must be explainable.

Show:

Why Speedy recommends this

and, where relevant:

Things to consider

Example:

“Excellent for trains and family activities, but a car gives considerably more flexibility.”

Never expose raw scoring mathematics to customers.

Store the score and reasoning internally.

### 6. DESTINATION PAGES

Every destination page should be generated from structured database content.

Include:

- Destination overview
- Why visit
- Best for
- Best time to visit
- Recommended number of nights
- Best bases/towns
- Getting there
- Getting around
- Interactive map
- Top attractions
- Family activities
- Easy/low-walking sightseeing
- Adventure
- Scenic experiences
- Railways
- Boat trips
- Wildlife
- Castles and heritage
- Rainy-day activities
- Restaurants/food areas
- Halal information where verified
- Accessibility information
- Hotels and stays
- Unique stays
- Road-trip connections
- Suggested packages
- Practical travel advice
- Speedy Insider Tips
- Tour Designer Warnings

Show provenance and freshness internally.

Do not display unattractive technical database information to customers.

### 7. EXPERIENCE PAGES

Each attraction/activity should support:

- Name
- Destination
- Location
- Coordinates
- Category
- Description
- Images
- Typical duration
- Best time of day
- Best season
- Family suitability
- Minimum age
- Height restrictions
- Weight restrictions
- Walking effort
- Accessibility
- Indoor/outdoor
- Rain suitability
- Parking
- Public transport
- Toilets
- Food nearby
- Advance booking recommendation
- Typical price band
- Live price if available
- Supplier
- Cancellation policy
- Speedy recommendation score
- Speedy Insider Tip
- Tour Designer Warning
- Source
- Last verified

Restrictions and prices that can change must be marked dynamic.

### 8. MAP EXPERIENCE

Create an interactive map throughout the website.

Allow customers to view:

- Attractions
- Hotels
- Viewpoints
- Castles
- Railways
- Boat trips
- Family attractions
- Restaurants
- Road-trip stops
- National parks

When building a trip, display the itinerary geographically.

Show:

- Day 1
- Day 2
- Day 3 etc.

Avoid creating itineraries that look attractive on paper but require unreasonable backtracking.

### 9. PACKAGE BUILDER: CUSTOMER

Allow customers to:

- Add destination
- Add hotel
- Add activity
- Add transfer
- Add car hire
- Add train
- Add tour
- Add road trip
- Remove components
- Change dates
- Change hotel category
- Upgrade/downgrade
- Save trip
- Share trip
- Request quote

Display:

- Trip overview
- Day-by-day itinerary
- Map
- Accommodation
- Experiences
- Transport
- What’s included
- What’s excluded
- Important information
- Estimated/current price
- Booking status

Use terminology:

Add to My Trip

rather than conventional ecommerce terminology where appropriate.

### 10. THREE-CHOICE HOTEL SYSTEM

Do not overwhelm customers with 200 hotels.

Default to three:

- **SPEEDY CHOICE:** Best overall fit.
- **BETTER VALUE:** Lower cost while preserving itinerary quality.
- **UPGRADE:** Meaningful premium upgrade.

Allow “Show More Hotels” for customers who want additional choice.

Hotel selection should consider:

- location
- trip routing
- parking
- family rooms
- connecting rooms
- occupancy
- breakfast
- restaurant
- pool
- spa
- EV charging
- accessibility
- public transport
- room configuration
- cancellation conditions
- guest rating
- Speedy suitability
- price
- supplier margin

Show:

Why Speedy selected this hotel

### 11. TAILOR-MADE REQUEST

Provide a prominent:

Build My Trip

option.

Customers should be able to submit an incomplete request.

Example:

“We have six days in Scotland with children aged 6 and 10. We want scenery, Harry Potter train experiences and castles but don’t want long hikes.”

The enquiry should automatically create a CRM lead and run the recommendation engine.

### 12. SPEEDY DMC STAFF PORTAL

Build a secure internal portal separate from the public interface.

Roles:

- Administrator
- Sales
- Travel Designer
- Product/Contracting
- Reservations
- Operations
- Finance
- Management
- Read Only

Use role-based permissions.

### 13. INTERNAL DASHBOARD

Dashboard should display:

- New enquiries
- Quotes being prepared
- Quotes sent
- Quotes viewed
- Quotes awaiting response
- Bookings awaiting payment
- Bookings awaiting supplier confirmation
- Confirmed bookings
- Arrivals this week
- Customers currently travelling
- Departures
- Supplier payments due
- Customer balances due
- Bookings with operational warnings
- Data requiring verification
- High-value enquiries
- Lost enquiries
- Conversion rate
- Revenue
- Gross margin

### 14. UNIVERSAL SPEEDY SEARCH

Staff must have one powerful search box.

Example searches:

- “Family activities Lake District”
- “Hotels Keswick family parking”
- “Easy waterfalls Wales”
- “Scenic railway Scotland”
- “Things for 5-year-old Cornwall”
- “Halal Manchester”
- “Luxury anniversary Cotswolds”
- “Wheelchair accessible York”
- “Rainy day Cairngorms”

Search across the structured travel database.

Provide filters.

### 15. INTERNAL PACKAGE BUILDER

This is a critical module.

Travel designers should be able to create a package visually.

Select customer.

Select destination.

Select dates.

Then create:

- DAY 1
- DAY 2
- DAY 3 etc.

Drag components into each day.

Components:

- Hotel
- Transfer
- Attraction
- Activity
- Restaurant recommendation
- Train
- Boat
- Car hire
- Guide
- Free time
- Scenic stop
- Road-trip stop
- Flight

Show travel time between components.

Warn when:

- daily driving exceeds customer preference
- activity conflicts with child age
- activity conflicts with mobility requirement
- venue is closed or requires verification
- travel time makes itinerary unrealistic
- hotel is geographically inefficient
- booking is unconfirmed
- supplier price has expired

### 16. SPEEDY INSIDER INTELLIGENCE

Create two important internal fields:

**SPEEDY INSIDER TIP**

Examples:

- “Arrive before 09:30 during school holidays.”
- “Better from Keswick than Windermere.”
- “Children usually prefer the railway to another castle.”

**TOUR DESIGNER WARNING**

Examples:

- “Google driving time is unrealistic in summer.”
- “Return walk is considerably steeper than the outward route.”
- “Limited parking after 10am.”
- “Not suitable for large vehicles.”

These fields should influence recommendations.

This intelligence is one of Speedy Travels’ key competitive advantages.

### 17. QUOTATION ENGINE

Each package component must support:

- Supplier
- Supplier reference
- Currency
- Net cost
- Tax/VAT treatment
- Markup
- Commission
- Selling price
- Gross margin
- Margin percentage
- Cancellation deadline
- Cancellation cost
- Payment deadline
- Booking status

Package screen should show:

- TOTAL NET COST
- TOTAL SELLING PRICE
- GROSS PROFIT
- GROSS MARGIN %

Allow margin to be hidden from customer-facing output.

Support:

- fixed markup
- percentage markup
- supplier commission
- package-level adjustment
- promotional discount
- manual override with approval

Keep full pricing audit history.

### 18. QUOTE VERSIONING

A customer may change their trip repeatedly.

Support:

- Quote V1
- Quote V2
- Quote V3

Never overwrite historical quotes.

Record:

- who changed it
- when
- what changed
- price change
- margin change

Allow staff to compare versions.

### 19. CUSTOMER PROPOSAL

Generate a beautiful mobile-friendly web proposal.

Also support PDF output.

Include:

- customer name
- trip title
- dates
- travellers
- map
- day-by-day itinerary
- hotels
- images
- activities
- transport
- what’s included
- what’s excluded
- price
- deposit
- balance deadline
- cancellation terms
- important information

Actions:

- Accept Proposal
- Request Changes
- Talk to Travel Designer
- Pay Deposit

### 20. CUSTOMER ACCOUNT

Create “My Trip”.

Customers can access:

- Proposal
- Confirmed itinerary
- Payment schedule
- Vouchers
- Hotel details
- Activity tickets
- Transfers
- Driver details
- Emergency contact
- Travel documents
- Messages
- Changes
- Important alerts

Make this mobile-first because most travellers will use it while travelling.

### 21. BOOKING WORKFLOW

Use statuses:

- Enquiry
- Qualified
- Designing
- Pricing
- Quote Sent
- Customer Reviewing
- Revision Requested
- Accepted
- Deposit Pending
- Deposit Paid
- Supplier Booking
- Partially Confirmed
- Confirmed
- Documents Issued
- Travelling
- Completed
- Cancelled

Each individual package item should have its own status.

A trip must never display “Confirmed” internally if critical components remain unconfirmed.

### 22. SUPPLIER DATABASE

Create supplier management for:

- Hotels
- Apartments
- Cottages
- Unique stays
- Attractions
- Activity operators
- Guides
- Transfer companies
- Coach companies
- Car hire
- Rail
- Boat/cruise operators
- Restaurants where commercially relevant

Store:

- supplier name
- contact details
- contract status
- contract dates
- net rates
- commission
- payment terms
- credit limit
- cancellation terms
- emergency number
- booking method
- API
- email
- portal
- currency
- insurance documentation
- risk information
- internal rating
- service issues
- last reviewed

### 23. CONTRACTED INVENTORY VS LIVE INVENTORY

Support three product types:

- DIRECT CONTRACT
- API / LIVE SUPPLIER
- MANUAL / ON REQUEST

Clearly identify the source of the rate.

Never present an old database price as live availability.

### 24. OPERATIONS MODULE

Once booked, convert the package into an operational file.

Show:

- arrival
- airport/train station
- transfer
- driver
- hotel check-in
- activities
- guides
- restaurant bookings
- rail tickets
- car hire
- special requests
- dietary requirements
- accessibility
- children
- emergency contacts
- supplier confirmations

Create supplier reconfirmation tasks.

Example:

- 7 days before arrival: reconfirm hotel.
- 72 hours: reconfirm transfer.
- 24 hours: reconfirm driver.
- Morning of activity: check disruption/weather where relevant.

### 25. INCIDENT MANAGEMENT

Allow staff to record:

- supplier no-show
- hotel problem
- transfer delay
- activity cancellation
- weather disruption
- road closure
- customer illness
- lost luggage
- complaint

Record:

- time
- staff member
- action taken
- supplier communication
- customer communication
- financial consequence
- resolution

### 26. CRM

Every enquiry should create a customer/lead record.

Store:

- contact details
- country
- source
- travelling party
- previous trips
- preferences
- budget
- interests
- dietary needs
- accessibility
- quotes
- bookings
- communications
- lost reason
- lifetime value

Avoid storing unnecessary sensitive data.

### 27. B2B DMC MODULE

Speedy should also sell UK ground arrangements to overseas:

- Travel agencies
- Tour operators
- Corporate travel companies
- Concierge companies
- Group organisers

Create a separate:

UK DMC / Travel Trade

website section.

Allow B2B agents to submit:

- FIT enquiry
- Group enquiry
- Series enquiry
- MICE enquiry
- Transport enquiry
- Hotel enquiry
- Tailor-made itinerary

Support B2B net pricing separately from B2C retail pricing.

### 28. CONTENT MANAGEMENT

Travel-product staff must be able to update destination content without developers.

Provide CMS editing for:

- destinations
- experiences
- hotels
- tips
- warnings
- images
- SEO
- trip templates
- FAQs
- seasonality
- verification

Every content change should record:

- editor
- date
- previous value
- new value

### 29. DATA FRESHNESS

Create verification queues.

Example:

- RED: expired/unverified
- AMBER: approaching review date
- GREEN: verified

Different information should have different review frequencies.

Dynamic information should be refreshed more frequently than destination descriptions.

Do not silently publish stale operational information.

### 30. ANALYTICS

Track:

- destination searches
- recommendation results
- packages viewed
- packages saved
- quote requests
- quote conversion
- booking conversion
- average booking value
- gross margin
- destination popularity
- activity popularity
- hotel conversion
- abandoned trips
- customer acquisition source
- repeat customer rate
- reason quotes are lost

The objective is to learn what customers actually want and improve recommendation weights.

### 31. TECHNICAL ARCHITECTURE

Use a modern, scalable web architecture.

Preferred principles:

- Type-safe modern web frontend
- Server-side rendering for SEO
- Relational SQL database
- Geospatial capability for coordinates/routes
- REST or typed API layer
- Secure authentication
- Role-based permissions
- Object storage for images/documents
- Background jobs for supplier synchronisation
- Audit logging
- Versioning
- API integration layer
- Responsive/mobile-first design
- Automated backups
- Staging and production environments

Do not use the spreadsheet as the production database.

Create a structured database and build an import process from the Speedy workbook.

Keep the workbook available for:

- data imports
- exports
- bulk editing
- QA
- management analysis

### 32. CORE DATA ENTITIES

Create relational models for:

- customers
- traveller_profiles
- enquiries
- destinations
- regions
- bases
- experiences
- attractions
- activities
- hotels
- room_types
- unique_stays
- restaurants
- suppliers
- supplier_contacts
- contracts
- rates
- availability_snapshots
- routes
- route_days
- route_stops
- transport
- car_hire
- rail_journeys
- boat_trips
- packages
- package_days
- package_items
- quotes
- quote_versions
- bookings
- booking_items
- payments
- refunds
- vouchers
- documents
- operations_tasks
- incidents
- recommendation_rules
- recommendation_scores
- sources
- verification_records
- media
- staff
- roles
- audit_logs

Use UUID/internal IDs while retaining legacy Speedy IDs for imported records.

### 33. SEARCH ENGINE OPTIMISATION

Destination intelligence should also generate organic search traffic.

Build indexable pages around genuine customer intent.

Examples:

- Things to do in the Lake District with kids
- Easy waterfalls in Wales
- Best scenic train journeys in Scotland
- UK road trips with children
- Things to do in Cornwall when it rains
- Accessible attractions in York
- Best UK holidays without a car
- Family road trips in Scotland
- Unique places to stay in Wales

Avoid low-quality automatically generated SEO pages.

Only publish pages with meaningful Speedy editorial value.

### 34. TRUST

Throughout the website explain:

Why Speedy recommends something.

Do not pretend every product is perfect.

Include genuine negatives.

Example:

**Why we like it**

Excellent family location and easy parking.

**Things to know**

The hotel is approximately 20 minutes outside the town centre, so it is better for customers travelling by car.

This transparency should differentiate Speedy from conventional booking sites.

### 35. DESIGN

The design should feel:

- Premium
- Warm
- British
- Exploratory
- Trustworthy
- Modern
- Family-friendly
- Not corporate
- Not cluttered

Use large destination imagery, maps and itinerary cards.

Avoid visually copying major OTAs.

Speedy should look like a knowledgeable travel designer rather than a price-comparison engine.

### 36. MVP

Do NOT attempt every integration on day one.

MVP should prioritise:

- UK destination discovery
- Smart Trip Finder
- Recommendation engine
- Destination pages
- Experience database
- Package templates
- Customer Build My Trip
- Enquiry capture
- Internal DMC portal
- CRM
- Package builder
- Cost/margin calculator
- Quote generation
- Customer proposal
- Manual/live-assisted supplier pricing
- Payment/deposit capability
- Booking management
- Operations dashboard

Build integrations behind an abstraction layer so supplier APIs can be added later without redesigning the product.

### 37. CRITICAL DEVELOPMENT PRINCIPLE

Speedy Travels’ intellectual property is not merely the list of attractions.

It is the combination of:

- TRAVELLER PROFILE
- DESTINATION INTELLIGENCE
- SUITABILITY RULES
- PRACTICAL LOCAL KNOWLEDGE
- NEGATIVE INTELLIGENCE
- ITINERARY LOGIC
- COMMERCIAL SUPPLIER DATA
- HUMAN DMC EXPERIENCE

This logic must remain structured and reusable so that, after proving the model in the UK, another destination country can be added without rebuilding the platform.

Design the system from day one as:

COUNTRY → REGION → DESTINATION → BASE → EXPERIENCE → PRODUCT → SUPPLIER

UK is Country 001.

Future countries should plug into exactly the same architecture.

### FINAL OBJECTIVE

A customer should be able to say:

“We are two adults with children aged 4 and 9. We have five nights in October, a £2,500 budget, don’t want difficult hikes, love trains and animals, need halal food and don’t want to drive more than two hours per day.”

Within seconds Speedy should be able to:

- recommend the best destinations,
- explain why,
- show an appropriate itinerary,
- recommend three accommodation choices,
- suggest appropriate activities,
- identify important warnings,
- allow customisation,
- obtain live pricing,
- produce a final package price,
- take payment,
- book the components,
- issue travel documents,
- and operate the trip.

The Speedy staff portal must allow a human travel designer to review, override and improve every automated recommendation before or after it reaches the customer.

The objective is not to eliminate the travel designer.

The objective is to give each Speedy travel designer the knowledge and productivity of an expert UK DMC.

## 4. Research from chat 1

### 4.1 The gap Speedy fills

| Type | Examples | Strong at | Missing (from what I found) |
|---|---|---|---|
| Tailor-made travel brands | Black Tomato, Audley, Jacada, Wilderness Scotland | Human designers, trust, premium content | Instant personalised recommendations, a self-serve trip builder |
| AI trip planners | Mindtrip, Layla, Tripadvisor Trips | Instant itineraries, maps, travel times | Local warnings (your "negative intelligence"), designer review, DMC operations |
| DMC software | Tourwriter, Wetu, Safari Portal, TripCreator, Vamoos | Quoting, margins, proposals, traveller apps | A customer recommendation engine, suitability rules (family, walking, halal, rain) |

I found no company that does all three. Your brief covers all three, and brief section 37 calls that combination Speedy's IP.

### 4.2 Awwwards-level motion sites

| Site | Award | What to take |
|---|---|---|
| [White Desert](https://white-desert.com/) · [Awwwards page](https://www.awwwards.com/sites/white-desert) | Site of the Day, 11 Sep 2026 | Full-screen cinematic storytelling for luxury expeditions |
| [Tengile MalaMala](https://tengilemalamala.com/) · [Awwwards page](https://www.awwwards.com/sites/tengile-malamala-collection) | Awwwards, Oct 2026 (DashDigital) | Film-style editorial pages. Closest match to "premium, warm" |
| [Jesko Jets](https://www.awwwards.com/sites/jesko-jets) | Site of the Day and Developer Award, Jan 2026. Webby winner for Best Homepage | Premium motion for a tailored service you request rather than book |
| [Explora Journeys](https://explorajourneys.com/) · [Awwwards page](https://www.awwwards.com/sites/explora-journeys) | Honorable Mention, Nov 2025 (Skywire) | Luxury booking funnel. Study it for the customer package builder (brief 9) |
| [Hedwig Curated Travel](https://hedwigtravel.com/) · [Awwwards page](https://www.awwwards.com/sites/hedwig-curated-travel) | Honorable Mention, 2026 | Editorial look for bespoke travel. Fits brief 35: "a knowledgeable travel designer" |
| [66°Nord](https://www.66nord.com/) · [Awwwards page](https://www.awwwards.com/sites/66degnord-the-polar-travel) | Site of the Day, Jan 2019 (Akaru) | Same model as Speedy: a tailor-made destination specialist |
| [Niarra Travel](https://www.awwwards.com/sites/niarra-travel) | Site of the Day and Developer Award, Jun 2021 | Hover mask slideshow |
| [When to Travel](https://www.awwwards.com/sites/when-to-travel) | Site of the Day | Events and weather by month. Model for "Best time to visit" (brief 6) |
| [Velaa Private Island](https://www.velaaprivateisland.com/) | Listed in the Awwwards hotel and photography categories (STRV) | Photography-led hospitality pages |

Also listed on Awwwards: [Travel Next Level](https://www.awwwards.com/sites/travel-next-level) (Site of the Day, Dec 2024) and [Travel Sensations](https://www.awwwards.com/sites/travel-sensations) (Honorable Mention, Sep 2025).

Browse more: [Awwwards travel](https://www.awwwards.com/websites/travel-tourism/) · [Awwwards hotels](https://www.awwwards.com/websites/hotel-restaurant/)

### 4.3 Closest real businesses

**Tailor-made travel (same promise as Speedy)**

| Company | Why it matters |
|---|---|
| [Black Tomato UK](https://www.blacktomato.com/destinations/united-kingdom-ireland/) | Builds every itinerary around who is travelling. Sells private compartments on the Jacobite steam train (the "Hogwarts Express"), close to your brief 11 example |
| [Audley Travel Scotland](https://www.audleytravel.com/us/united-kingdom/scotland) | Specialists who have explored or lived in the country design each trip |
| [Wilderness Scotland](https://www.wildernessscotland.com/) | UK company. A dedicated travel designer per trip. Family adventure holidays |
| [Jacada Travel](https://www.jacadatravel.com/) | Calls its staff "travel designers", the same role as Speedy |
| [Belmond Royal Scotsman](https://www.belmond.com/trains/europe/scotland/belmond-royal-scotsman/journeys) | Premium scenic rail pages. Tours of 2 to 7 nights from Edinburgh, April to October |

**AI trip planners (benchmark for the Smart Trip Finder, brief 4 and 5)**

| Product | What it does |
|---|---|
| [Mindtrip](https://mindtrip.ai/) | Chat plus map. Orders timed stops and shows travel time between each one |
| [Layla](https://layla.ai/) | AI agent that builds a day-by-day plan with live pricing |
| [Tripadvisor Trips](https://www.tripadvisor.com/Trips) | AI trip builder: asks questions, then returns an itinerary with places to stay |

**DMC software (benchmark for the staff portal, brief 12 to 25)**

| Product | What it does |
|---|---|
| [Tourwriter](https://www.tourwriter.com/product/) | Drag-and-drop itinerary builder. Margins, commission and tax update live. Mobile web itineraries instead of PDFs. From USD 99 per user per month (per search results) |
| [Safari Portal](https://www.safariportal.app/) | Digital itineraries, PDF or Word proposals, payments, sales pipeline, tasks and in-app messaging |
| [Wetu](https://wetu.com/operators) | Itinerary builder, map-based digital itineraries and a supplier content library. From USD 75 per month (per review sites) |
| [TripCreator](https://tripcreator.com/) | Itineraries, quotes, proposals, online sales and operations in one platform |
| [Vamoos](https://www.vamoos.com/) | Branded traveller app with itinerary, documents, messaging and offline access. Black Tomato and Scott Dunn use it. Model for My Trip (brief 20) |

### 4.4 Mobbin references mapped to your brief

**Customer side**

| Brief | Pattern | Link |
|---|---|---|
| 4 | "Who's coming with you?" tiles, dates, interest chips, "Building a trip just for you" loader | [Tripadvisor: Creating a trip (AI)](https://mobbin.com/flows/10ff32ab-8aa0-4892-9215-9cfd91269b75) |
| 4, 5 | Result page: "5 days for a family with children", map, places to stay | [Tripadvisor: Creating a trip (using AI)](https://mobbin.com/flows/6ebf5884-66b6-4877-b521-c8a8356c7036) |
| 11 | Interest chips plus an "Anything else?" free-text box. "Booked" badges on itinerary items | [Vrbo: Creating an itinerary with AI](https://mobbin.com/flows/577ac76e-8781-4e0a-8d83-9e847a2c145d) |
| 8, road trips | Route map, nights per stop, drive distance and time between stops, "Travel DNA" profile | [Polarsteps: Creating a trip (AI)](https://mobbin.com/flows/637c20ef-f458-482f-8649-bd960938ff51) |
| 8 | Day list with numbered map pins | [Wanderlog](https://mobbin.com/screens/6e26cab3-e74a-48cf-b4ee-93087c03a25f) |
| 7, 8 | Suggested visit length, opening hours, walking time between stops | [Trip.com](https://mobbin.com/screens/6829121a-b641-4e80-bd26-c4f5be973891) |
| 8, road trips | Day map with a timed drive block and total distance | [Mindtrip (iOS)](https://mobbin.com/screens/fd4c577b-fc6a-4784-9b4c-540a74e03c79) |
| 4 | Chat on the left, "For you" cards on the right, trip pills for where, when, travellers and budget | [Mindtrip (web)](https://mobbin.com/screens/346f2b69-d656-46ec-b465-3638dd007ff4) |
| 10, 34 | Hotel cards with a short "why" text and badges | [Tripadvisor hotels](https://mobbin.com/screens/f56e04e3-da38-46ba-9765-d57ff8d74bd5) |
| 20 | Booking card: voucher, add to calendar, message or call the supplier, important information | [GetYourGuide](https://mobbin.com/screens/1226bf9b-ae61-4238-9e5e-6525025c1422) |
| 20 | Hotel booking detail: reservation number, check-in and check-out, address, room | [Navan](https://mobbin.com/screens/1296a157-3a45-406f-ba1b-cf7658145d09) |
| 20 | Upcoming stay: call, add to calendar, directions | [Marriott Bonvoy](https://mobbin.com/screens/deb6b935-7b87-41f0-a9a8-97a10d3831ea) |

**Staff portal**

| Brief | Pattern | Link |
|---|---|---|
| 10, 15 | Staff pick "recommended hotels" that customers see when booking | [Navan](https://mobbin.com/screens/861d9426-db69-4c34-b213-344bbb60652f) |
| 21, 26 | Pipeline board with deal cards and values per stage | [Attio](https://mobbin.com/screens/e275641a-a3e8-440a-b53e-983bb9cec7c7) · [Pipedrive](https://mobbin.com/screens/2ff3c977-7902-48b5-8361-0c89710e5c2e) |
| 17 | Quote builder with "Client view" toggles that hide unit prices, plus a required deposit | [Jobber](https://mobbin.com/screens/4e746ccf-6d79-44b0-8208-c596b55d2259) |
| 17 | Totals block with subtotal, discount, tax and a manual adjustment line | [Zoho CRM](https://mobbin.com/screens/9e6648e1-0ca4-4e86-8df0-b1dfc4517c47) |
| 17 | Line items with sub-items, tax and service charge settings | [HoneyBook](https://mobbin.com/screens/105f5259-a5e3-475f-8a0e-a94d34d8a2bf) |
| 19 | Proposal with Accepted status, a payments panel and Download PDF | [Bonsai](https://mobbin.com/screens/6d59b802-265c-42b7-8418-7b60be6ae3db) |
| 19 | Quote wizard with e-signature and online payment steps | [HubSpot](https://mobbin.com/screens/496e0211-9d23-402b-a93e-d447ef4249f5) |

### 4.5 Copy, avoid, motion

**Copy**

- One question per screen with big tap targets (Tripadvisor).
- Free text for messy requests (Vrbo "Anything else?").
- Travel time between every stop (Trip.com, Polarsteps, Mindtrip).
- A "why" line on every recommendation (Tripadvisor hotels).
- Designer-picked options that customers see first (Navan).

**Avoid** (brief 3 and 35 rule these out)

- A search box as the hero: [Tripadvisor "Where to?"](https://mobbin.com/sites/sections/4c18737d-3f81-41c4-928b-649b8f2f94c9)
- Price-led hotel grids with discount badges: [Expedia](https://mobbin.com/screens/266f27bd-8e38-4d26-a452-e066e7e45e8a)

**Motion**

- Put cinematic video, scroll reveals and hover effects on marketing pages: home, destinations, rail journeys.
- Keep the Trip Finder, My Trip and the staff portal fast and plain. Travellers open My Trip on patchy signal in places like the Highlands.

## 5. Recommendations for chat 2 (not agreed yet)

### 5.1 Legal must-haves before you take customer money

| Rule | What it means for Speedy | Source |
|---|---|---|
| Package Travel Regulations 2018 | If Speedy sells packages (hotel plus car hire, tours or rail), Speedy is the organiser and needs insolvency protection that covers refunds and repatriation, for example a bond, insurance or a trust account | [legislation.gov.uk](https://www.legislation.gov.uk/ukdsi/2018/9780111168479/pdfs/ukdsi_9780111168479_en.pdf) · [gov.uk guidance](https://assets.publishing.service.gov.uk/media/62dea082e90e0766afece5ee/package-travel-regulations-2018-guidance.pdf) |
| ATOL | Needed only for packages that include flights. Brief 15 lists "Flight" as a component. Acting as an agent for an ATOL holder is one exemption | [CAA: Do I need an ATOL?](https://www.caa.co.uk/atol-protection/atol-requirements-for-the-travel-industry/do-i-need-an-atol/) |
| UK GDPR special category data | A halal requirement can reveal religion. Accessibility needs and illness are health data. You need an Article 9 condition such as explicit consent, and you should store the minimum (brief 26 already says this) | [ICO: special category data](https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/lawful-basis/special-category-data/what-is-special-category-data/) |
| Card payments | Take payments through Stripe Checkout or Payment Links so card numbers never touch Speedy's servers | Recommendation |

### 5.2 Suggested tech stack (maps to brief section 31)

| Need | Suggestion |
|---|---|
| Type-safe frontend with SSR for SEO | Next.js (App Router), TypeScript, Tailwind CSS |
| Motion | GSAP with ScrollTrigger and Lenis smooth scroll on marketing pages. Motion (Framer Motion) for UI transitions |
| Relational SQL with geospatial | PostgreSQL with PostGIS for points, routes and distance queries |
| Typed API | tRPC, or REST route handlers validated with Zod |
| ORM | Drizzle. It stays close to SQL, which makes PostGIS easier than with Prisma |
| CMS with edit history (brief 28) | Payload CMS. It runs inside Next.js on Postgres and has versions, drafts and field-level access control |
| Auth and the 9 staff roles (brief 12) | One auth provider for staff and customers. Roles and permissions live in the database |
| Maps and drive times (brief 8, 15) | Mapbox GL JS (or MapLibre, free) for maps. A routing API for drive times, adjusted by Speedy warnings such as "Google driving time is unrealistic in summer" |
| Payments (brief 19) | Stripe for deposits, balances, refunds and webhooks |
| Images and documents | S3-compatible storage such as Cloudflare R2 |
| Background jobs (brief 24, 29) | Inngest or Trigger.dev for reconfirmation tasks, verification queues and supplier sync |
| Staff search (brief 14) | Postgres full-text search with pg_trgm first. Add Meilisearch or Typesense if it gets slow |
| PDF proposals (brief 19) | Render the web proposal to PDF with Playwright |
| AI layer | Claude API to turn free-text requests into structured trip fields and to write "Why Speedy recommends this" from stored reasons. Rules and admin weights do the scoring (brief 5), so every result stays explainable |
| Hosting | Vercel for the app. Managed Postgres with PostGIS (Neon or Supabase). Separate staging and production, daily backups |

### 5.3 Build order (the brief 36 MVP split into phases)

| Phase | Scope | Brief sections |
|---|---|---|
| 0. Foundations | Design direction. Data model on Country → Region → Destination → Base → Experience → Product → Supplier. Auth and roles, audit log, workbook import with source and verification fields | 2, 12, 28, 31, 32, 37 |
| 1. Discovery | Homepage, destination pages, experience pages, map, CMS editing, SEO pages | 3, 6, 7, 8, 28, 33, 34 |
| 2. Trip Finder | Questionnaire, recommendation engine (filters, admin weights, diversity, explanations), Build My Trip, enquiry creates a CRM lead | 4, 5, 10, 11, 26 |
| 3. Staff portal | Dashboard, universal search, internal package builder with travel times and warnings, insider tips | 13, 14, 15, 16 |
| 4. Quotes | Costs and margins, markup rules, quote versions with audit history, web proposal and PDF, accept or request changes | 17, 18, 19 |
| 5. Booking | Stripe deposit and balance, a status on every booking item, supplier database, rate source labels | 21, 22, 23 |
| 6. Operations | Operational file, reconfirmation tasks, incidents, My Trip | 20, 24, 25 |
| Later | B2B trade portal, live supplier APIs, analytics loop, the next country | 27, 30, 37 |

### 5.4 Decisions for you

1. **Build or buy the back office.** My view: build it. The warnings in brief 15 need Speedy's own data, and Tourwriter or Safari Portal cannot read it. Book demos of both anyway and copy their workflow.
2. **Flights.** Selling flights inside packages needs an ATOL or an agency deal with an ATOL holder. Without one, treat "Flight" (brief 15) as customer-booked information used for transfer timing.
3. **Insolvency protection.** Choose a bond, insurance or a trust account before the first deposit. A travel lawyer, ABTA or ABTOT can advise.
4. **The workbook.** Decide who owns it and how bulk edits flow back after launch (brief 31 keeps it for imports and bulk editing).
5. **Photography.** Licensed stock or your own shoots. Brief 35 asks for large destination imagery, and image rights cost money.
6. **Launch scope.** Brief 36 lists 18 MVP items. Section 5.3 splits them into 7 phases. Agree which phase you launch on.

## 6. Research limits

- The sandbox network policy blocked direct visits to every site in section 4 (white-desert.com, awwwards.com, 66nord.com and others). I checked links through search results and Mobbin. Award names and dates come from search snippets.
- 66°Nord (2019) and Niarra (2021) won years ago. Their sites may look different now.
- Tengile MalaMala: one search result said Site of the Day on 3 Oct 2026, but the Awwwards page title said Honorable Mention. Check the page.
- Jesko Jets, Niarra Travel and When to Travel: I only have the Awwwards page. Use its Visit Site button.
- Tourwriter and Wetu prices come from review sites. Confirm them in a demo.

## 7. Domains to allow (Custom network access only)

Add each one with and without `www.`:

```text
awwwards.com
white-desert.com
tengilemalamala.com
explorajourneys.com
hedwigtravel.com
66nord.com
velaaprivateisland.com
blacktomato.com
audleytravel.com
wildernessscotland.com
jacadatravel.com
belmond.com
mindtrip.ai
layla.ai
tripadvisor.com
tourwriter.com
safariportal.app
wetu.com
tripcreator.com
vamoos.com
mobbin.com
```

The live sites also load fonts, CDNs and video hosts that this list does not cover. A broader access level avoids that problem.
