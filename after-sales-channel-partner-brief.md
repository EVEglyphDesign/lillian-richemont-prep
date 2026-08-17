# Warranty & After-Sales — the entry lane for a Salesforce channel partner

Prep for Lillian's second-interview thread and a downstream conversation with a
Salesforce channel partner. **Warranty & after-sales is where the client, the
product, and the record all meet.** Solve it and the rest of the client-master
work at Richemont becomes a simpler variant of the same pattern.

---

## Why this seam first

- **Highest data complexity.** Serial-number equipment master keyed to a caseback,
  8-year extended warranty, 6-year service cadence, multi-decade servicing history,
  cross-border repair routing.
- **All three systems have to line up.** SAP CS (repair order + equipment) ↔
  Salesforce Service Cloud (Client 360 View) ↔ Cegid Y2 (boutique interaction).
- **Regulated by default.** LkSG / CS3D require ≥5-year retention. GDPR / PIPL
  require deletion trigger authority. CITES lives on the strap/leather side.
- **Business-critical.** The lifetime servicing record is the asset that supports
  Certified Pre-Owned, insurance valuation, and the Cartier Care / My IWC promise.

Everything else — clienteling, marketing journeys, loyalty — is a simpler client
object with fewer retention and reconciliation constraints.

## The landscape today

**Two systems own after-sales at Richemont, not one:**

- **SAP CS on ECC** — Group template, "10 repair workshops" (Devif),
  Warranty Management + Equipment / Serial Number technical objects (Ghirardo).
  Runs the shared repair platform behind **Cartier**, **IWC**, **JLC**, **VCA**,
  **Montblanc**, **Panerai**, **Vacheron Constantin**, **Alfred Dunhill**.
- **Salesforce Service Cloud** — the 360° Client View, brought together from
  **25 different data sources** (Meyer). Named directly in a current JLC
  Client Data & Reporting Specialist posting alongside SAP and GCP.

**Where the seam is:** the client-facing warranty portal (Cartier Care, My IWC)
runs off Service Cloud, but the equipment record and the repair order live in
SAP CS. A client's "watch history" in Salesforce today is at best a reference to
a repair-order number that resolves in SAP.

## The Group-owned repair network

- **10 repair workshops** across Europe under one Group Technology platform,
  supporting 150+ boutiques (Devif, 2010–2017 scope).
- **North America:** Richemont Technical Center, Fort Worth, TX (Trinity Blvd 15100).
- **Canada:** Mississauga (Eastgate Parkway 4610).
- **APAC:** Sydney (Castlereagh 74), Beijing, Shanghai (Vacheron China per
  Europa Star).
- **Watchfinder** as the manufacturer-certified pre-owned service centre in
  London — same Group.

Every one of these workshops touches the same SAP CS equipment records. That is
the pipe a Salesforce partner would help re-plumb.

## Public tell-tales the interviewer will recognise

- **[Cartier Care](https://www.cartier.com/en-us/register-watch.html)** — register
  by caseback serial, 8-year extended warranty on registration, 6-year service
  cadence, service-order tracking.
- **[My IWC](https://www.iwc.com/us-en/services/faq)** — register serial, 6-year
  extension on top of 24 months base, track by Service Order number or serial.
- **Vacheron Constantin CPO** — blockchain digital passport with ownership,
  technical, and full servicing history via Watchfinder — this is a customer-facing
  presentation of an equipment-master record.
- **Cartier Ref. 57260 / Grandmaster Chime class** — the extreme end of what has
  to sit on a single equipment record.

## The channel-partner opportunity, ranked

### 1. Bring SAP CS repair-order lifecycle into Service Cloud
The single unmet capability. Today a boutique associate sees "watch registered"
and "service order created" as a link out to SAP. The partner build:

- **Bidirectional SAP CS ↔ Service Cloud** on repair-order status, equipment
  master, warranty terms, service history events.
- **Salesforce object model** — Asset (or custom Timepiece) with lifetime
  history related list, tied to Person Account.
- **Integration pattern** — MuleSoft is already in the Richemont stack per the
  Magellan/Comforth partner claim; SAP Event Mesh + iFlows on the SAP side.
- **Deliverable** — the client walks into any boutique in any country and the
  associate sees the full watch lifetime in Service Cloud without switching to SAP.

Business framing for the partner: this is the capability Cartier Care and My IWC
already promise the *customer*. The internal reality is that the associate's
view of that record is still fragmented. Closing that gap is a defined,
value-quantifiable project.

### 2. Certified Pre-Owned as a Service Cloud pattern
Watchfinder is Richemont's CPO channel, and VC has already committed to a
blockchain digital passport. That passport is the presentation layer of a
Service Cloud object. Extending the Cartier and IWC CPO surfaces on the same
pattern is a natural follow-on — one Group model, several Maison skins.

### 3. Retention, deletion, and cross-border service routing under GDPR/PIPL
Cross-border repair routing (US watch serviced in Fort Worth vs. Geneva) is a
data-transfer event. Under PIPL for the mainland-China workshops (Beijing,
Shanghai), it needs a documented transfer mechanism per repair order. LkSG /
CS3D adds 5-year retention on the due-diligence side. Service Cloud is where
consent, transfer basis, and retention flag naturally sit — and today the JLC
posting suggests this is hand-managed across SAP + Service Cloud + GCP.

### 4. Boutique associate app for after-sales intake
Cartier already runs a bespoke boutique associate app (Occtoo case study). The
after-sales intake flow — client identifies watch, associate confirms warranty
status, initiates repair order — is a natural extension of that app, powered by
the same Client 360 View.

## Who is on the Salesforce side today

- **Incumbent partner:** Comforth Easyfront (Magellan Partners) — currently
  claims scope of "CRM, Marketing Cloud, Service Cloud, Data (Salesforce Data
  Cloud), AI (Agentforce)" for Richemont.
- **Internal Salesforce architecture:** Michal Danilczyk defined the Group
  Salesforce architecture 2020 (Versoix).
- **Group Client Marketing Director:** Philippe Meyer — the ELEVATE sponsor,
  public voice of the programme.

**Where a new partner competes:** the incumbent is deep in Marketing Cloud and
Data Cloud. **SAP CS ↔ Service Cloud integration for after-sales is not their
proven lane.** A partner with luxury-retail + SAP CS + Service Cloud references
would be complementary, not competitive, at the discovery stage.

## What Lillian says if this comes up in the interview

- **The frame:** "After-sales is the highest-fidelity client record you have.
  Every repair is a data point about the client and the object. Bringing that
  fully into the Client 360 is the highest-leverage seam."
- **The proof she has done the reading:** "The public Cartier Care and My IWC
  experience is a customer-facing view of an SAP CS equipment record. The
  associate's view of that record is where the seam sits."
- **The follow-on:** "Once that pattern is proven for one Maison, the same
  Salesforce Asset object and the same SAP CS integration serve every Maison on
  the shared repair platform. That is the multiplier that makes the business
  case work."

## Numbers safe to quote

- **10 repair workshops** under one Group Technology platform ([Devif](https://www.linkedin.com/in/guillaume-devif-3887521b)).
- **8-year** Cartier Care warranty on registration ([Cartier](https://www.cartier.com/en-us/faq/creations/watches/)).
- **6-year** IWC extension over 24 months base ([IWC](https://www.iwc.com/us-en/services/faq)).
- **25 data sources** consolidated into the Service Cloud golden record
  ([Salesforce case study](https://www.salesforce.com/eu/blog/richemont-maisons-delight-customers/)).
- **11 brands / 25+ countries** on the ELEVATE clienteling deployment
  ([Google Cloud](https://cloud.google.com/blog/products/ai-machine-learning/ai-suggestions-serve-a-better-client-experience-at-richemont)).
- **~2,463 total boutiques** as the eventual reach of any successful pattern
  ([Richemont FY25 results](https://www.richemont.com/media/nptj0zrk/richemont-fy25-annual-results-presentation-en.pdf)).

---

*Pour le bien-être du peuple.*
