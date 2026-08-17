# Richemont — data as a program-planning instrument

Prep for Lillian's second interview. The frame: **profile the most complex
transaction first, work backwards, and stand up a dynamically updating model
that substantiates every million-dollar deployment with actual business data.**

---

## The one-line frame

Richemont is ~20 Maisons on ~120 SAP instances, under a Bluefield S/4HANA
programme called **New Foundations** with an internal template called **Gemini**.
The data problem is not "clean the fields." It is: reconcile twenty acquired
Maisons onto one template without breaking a serialized High Jewellery piece,
a Kimberley certificate, or a Swiss Made BOM cost-split.

The way to lead that conversation is not to inventory the estate. It is to
**pick the most complex transaction, profile it against real data, and let
every other volume drop out as a subset.**

## The operating principle

**Model the most complex transaction first. Every other transaction is a
subset of that model.**

Why this is now practical:

- **Guess-then-test replaces analyse-then-guess.** AI can propose the shape of
  the most complex transaction from the data lake as it sits today, then test
  the guess against real record populations. Weeks, not workshop months.
- **"More than perfect" is the standard for program planning.** For decisions
  where every million dollars spent is graded against a hard business return, a
  directionally right, dynamically updating model beats a perfect static model
  that is stale on delivery.
- **Every deployment becomes an input signal.** When a release does not return
  what was expected, the gap between modelled and actual tells you where to
  look and how to correct — the model updates dynamically as deployments land.
- **The deployment-packaging constraint.** Package deployments small enough
  that returns land inside the model's refresh window. Otherwise the feedback
  loop is open and the program runs behind its investment cycle.

## Why after-sales is the anchor

Warranty & after-sales is the most complex transaction on the Richemont estate.
It carries every field every other flow needs, plus fields nothing else has.
Fix it first and everything else fits inside its shape.

**Complexity it carries:**

- **Serialized equipment master** — one physical object, one lifetime record.
- **Multi-decade lifecycle** — Cartier serials engraved since 1970; 8-year
  extended warranty on Cartier Care; 6-year service cadence.
- **Cross-border routing** — 10 Group repair workshops (Europe, Fort Worth,
  Mississauga, Sydney, Beijing, Shanghai, London) service any Maison for any
  client from any country. Each cross-border movement is a data-transfer event.
- **Cross-system reconciliation** — SAP CS (equipment + repair order) ↔
  Salesforce Service Cloud (Client 360 View) ↔ Cegid Y2 (boutique
  interaction). Client-facing Cartier Care and My IWC portals are the
  Service Cloud presentation of an SAP CS equipment record.
- **Regulatory retention** — LkSG / CS3D 5-year retention on due diligence;
  GDPR / PIPL / CCPA deletion trigger authority across 45 markets; CITES on
  exotic-leather strap components; hallmarking attributes per precious-metal
  batch.

**Subsets that fall out of the after-sales object:**

- **Retail sale** — the after-sales record at t=0, no service history yet.
- **Clienteling touch** — the client half of the record, no product half.
- **Marketing journey** — the client half, filtered to consent-permitted channels.
- **Loyalty accrual** — the transaction half, filtered to eligible references.
- **CPO resale** — the after-sales record replayed, with new owner attached and
  the servicing chain carried forward (Vacheron's blockchain digital passport
  via Watchfinder is exactly this pattern already made public).

Model the anchor once. Instrument its return. Every subset inherits the
instrumentation.

## The estate — what the anchor sits on top of

**SAP landscape.** ~120 SAP instances migrated to AWS by end-2022. **Gemini**
covers Finance, Controlling, Sales, Retail, Supply Chain, Procurement, EWM,
MDG. Around it sit **SuccessFactors + Concur**, **BW/4HANA + Datasphere + SAC**,
**SAP Commerce Cloud (Hybris)**, and **Fashion Management** (Chloé, Alaïa,
Peter Millar).

**Non-SAP satellites at the seam.** Salesforce **ELEVATE** — 11+ brands, 25+
countries, 7,000+ users growing to 10,000, Service Cloud + Marketing Cloud, 25
data sources into one golden client record. **Cegid Y2** at boutique POS.
**Workday HCM** live 2026 in parallel with SuccessFactors. **Google Cloud +
Vertex AI + BigQuery** as the client-AI backbone, connected via the Google x
Salesforce Connector.

**The three-system client seam.** Salesforce owns the client. Cegid owns the
transaction. SAP owns the finance and the equipment record. Every "data" project
at Richemont ultimately lands on that seam — after-sales is where it lands
hardest, which is why it is the right first target.

## Acquisition heritage — why one template is hard

Twenty Maisons arriving over 46 years, each with its own ERP: Cartier 1979 ·
Piaget / B&M 1988 · Vendôme (Montblanc, Chloé, Dunhill, Lancel) 1993 · VC 1996
· VCA 1999–2003 · LMH (IWC, JLC, Lange) 2000 · Peter Millar 2012 · Watchfinder
2018 · Buccellati 2019 · Delvaux 2021 · Gianvito Rossi 2023–24 · Vhernier
September 2024. Live divestitures: **YNAP → Mytheresa April 2025** (33%
retained in LuxExperience), **Baume & Mercier → Damiani closing 1 July 2026**
(transition services in flight). Not yet on Gemini: **Buccellati** (still
migrating) and **Vhernier** (still has its own IT Director post-acquisition).

Bluefield preserves history — twenty legacy article-masters, vendor-masters,
and chart-of-accounts translations reconcile at the record level, not the
report level.

## Article-master — what a SKU actually is

Three patterns run in parallel, and Bluefield carries all three:

1. **Collection / grid** — Love, Alhambra, Panthère. Style × metal × size × gem.
   Fits SAP Variant Configuration (LO-VC).
2. **Serialized small series** — every mechanical watch, every limited edition.
   Individually numbered, matched to a certificate. Panerai limited runs
   ~2–2,000 pieces. Cartier engraves serials on every piece since 1970.
3. **One-of-a-kind** — most Cartier and VCA High Jewellery. One material = one
   physical object.

**Order-of-magnitude counts.** Cartier ~1,400+ catalog models → 3,000–10,000+
SAP materials once variants expand. Vintage archive adds thousands more. IWC
~215 · Piaget ~400–441 · Lange ~92 · JLC 1,200+ calibres historically. VCA
publishes no reference count — "limited quantities or one-of-a-kind." YNAP was
hundreds of thousands pre-sale — what Richemont chose to divest.

**BOM depth.** Standard mechanical ~130 components, grand complications 250+,
Patek Grandmaster Chime 1,366 parts, Vacheron Ref. 57260 = 2,800+ components,
one unique piece. Multi-level BOMs are the discipline.

## Manufacturing — where a supplier is a Group asset

- **Full Manufacture:** JLC (82 workshops, 1,200+ calibres), VC, Lange (70+
  calibres, hand-assembled twice), Roger Dubuis (~100% Poinçon de Genève),
  Piaget.
- **Partial:** IWC, Cartier (La Chaux-de-Fonds — ~1/3 in-house, hands from
  Universo/Aiguilla).
- **Outsourced base movements:** Montblanc and Panerai on Group-supplied
  ValFleurier; Baume & Mercier ran ETA/Sellita.

**Group-owned suppliers (the twist).** ValFleurier (Group movement house, 5–6
new calibres/yr, 20,000+ movements). Donzé-Baume (cases and bracelets, ~300
employees, 2007). Varinor / VVSA (precious-metals refining, RJC certified,
2012). Roger Dubuis component arm (2007). SAP model: subcontracting scenarios
(scenario 30) with consigned components + intercompany billing/STO, **not**
arm's-length vendor POs.

**Supplier network.** ~700 direct suppliers · ~460 on SAP Business Network ·
**only 17 with own-ERP integration**. **Distribution:** 1,392 internal + 1,071
franchised = ~2,463 boutiques. **Watchfinder** as the pre-owned lane, 60+
brands, manufacturer-certified service centre.

## The regulatory surface

Every item below = fields on a material master or a batch record. Not a
compliance memo.

- **Kimberley Process** — cert number, origin, carat, USD value, HS code,
  exporter/importer IDs. 3-yr cert, 5-yr trader records.
- **EU ESPR / DPP** — textiles/apparel confirmed for 2027 delegated act.
  Jewellery/watches under review. From 19 July 2026, ban on destroying unsold
  apparel for large enterprises.
- **Swiss Made 60% rule** (in force 1 Jan 2017) — 60% of manufacturing cost
  Swiss, movement ≥60% + ≥50% component value Swiss, R&D in CH. A BOM
  cost-split per reference, auditable at record level.
- **Hallmarking** — UK Assay Offices; French *poinçon de maître* with *livre
  de police*; Swiss Bureau central. Sponsor's mark + fineness + assay-office
  code as material/batch attributes.
- **LkSG + CS3D** (Directive 2024/1760, phasing 2027–29) — HR/environmental
  due diligence over the full chain; ≥5-yr retention. All ~700 suppliers
  become governed business partners in MDG-BP.
- **CITES** — exotic leathers, coral. Appendix II permits, species, issuing
  country, permit number, non-detriment finding. Natural home: SAP GTS.
- **GDPR / PIPL / CCPA** — consent flag, legal basis, TIA/SCC ref, PIPL
  security assessment, retention/deletion trigger — on every client record
  touched by Salesforce, Cegid, and SAP simultaneously.

## Five questions that go a layer below "data"

1. **After-sales as the anchor object.** Is Richemont profiling the after-sales
   transaction as the most complex object and deriving all other client
   objects as subsets — or modelling client, sale, and service in parallel and
   reconciling later?
2. **High Jewellery article-master.** Bluefield template — unique lots (one
   material = one serialized object) or forced into Variant Configuration? How
   far are Cartier and VCA from target state?
3. **Swiss Made cost-split.** Rolled up from component-level origin/cost
   fields, or maintained as an EHS/Product Compliance overlay? Is the
   pre-conversion split trustworthy across all seven watch Maisons, or rebuilt
   at cutover?
4. **Group-owned suppliers.** ValFleurier / Donzé-Baume / Varinor / RD
   components — subcontracting POs with consigned precious metals and
   intercompany billing, or standard third-party vendor flows?
5. **Client-master across three systems.** Where is the source-of-truth for
   consent, transfer mechanism, and deletion — Salesforce, Cegid, or SAP —
   and how is it reconciled across GDPR, PIPL, CCPA simultaneously?

## Facts safe to name in the room

- ~120 SAP instances on AWS since end-2022, target S/4HANA Bluefield,
  programme **New Foundations**, template **Gemini**.
- ~20 Maisons, oldest acquisition 1979. YNAP sold Apr 2025. B&M sold 1 Jul
  2026. Buccellati and Vhernier not on Gemini.
- Cartier ~1,400+ models → 3,000–10,000+ SAP materials. BOMs 130 → 2,800+.
- ~700 direct suppliers · ~460 on SAP Business Network · only 17 own-ERP
  integrated.
- 1,392 internal + 1,071 franchised = ~2,463 boutiques.
- ELEVATE (Salesforce Service Cloud + Marketing Cloud + Google Cloud) — 11+
  brands, 25+ countries, 7,000+ users, 25 data sources into one golden record.
- 10 Group repair workshops behind Cartier Care, My IWC, and Vacheron
  Constantin CPO (blockchain digital passport via Watchfinder).
- Regulatory: Kimberley, ESPR/DPP (textiles 2027), Swiss Made 60%, UK/FR/CH
  hallmarking, LkSG + CS3D (5-yr retention), CITES, GDPR/PIPL/CCPA.

## The engagement posture — our number, their check

The assessment does not begin with "tell us what you have." It begins with
**our tools running against their data**, producing a number they can then
validate against their own enterprise systems and reporting.

What this changes:

- **We arrive with an answer, not a questionnaire.** The AI-assisted profile of
  the anchor transaction runs first. The interview validates the guess.
- **The client's data is the check on our number, not the source we depend
  on.** They compare our number to what SAP, Salesforce, and Cegid say, and
  the delta is the finding.
- **For estimate purposes, our number stands on its own.** If a stakeholder
  wants to know whether the estimate is right, they look at our number and
  reason about it. They don't need to run a parallel study to validate it.
- **The comparison itself is a decision-intelligence artifact.** Where our
  number and theirs agree, the model is proven. Where they disagree, the
  disagreement points at the specific reconciliation gap the deployment needs
  to close — which is exactly the input the dynamic model wants.

## The closing frame

The pitch is not "help us do data governance." It is: **substantiate the
program plan with actual business data, structured so it updates dynamically,
and produces decision intelligence that proves the models work before the next
million is committed.**

The anchor is warranty & after-sales because it is the most complex
transaction on the estate. Once profiled, every other volume — retail,
clienteling, marketing, loyalty, CPO — loads into the same model as a subset.
Deployments are packaged small enough that returns land inside the model's
refresh window, so the feedback loop stays closed and the program does not run
behind its investment cycle. Our tools give a number Richemont's own systems
can check — that check is the estimate.

---

## Sources

**SAP landscape and cloud** — [Businesswire (Richemont + AWS)](https://www.businesswire.com/news/home/20211122005617/en/Richemont-Selects-AWS-as-Its-Preferred-Cloud-Provider-to-Drive-Product-Innovation) · [Undisturbed on New Foundations / Gemini](https://undisturbed.blog/articles/richemont) · [SAP News on Business Network](https://news.sap.com/africa/2023/05/richemont-harmonizing-supply-chain-processes-between-group-business-and-suppliers/) · [SAP case study PDF](https://www.sap.com/asset/dynamic/2023/04/de62229b-6e7e-0010-bca6-c68f7e60039b.html)

**ELEVATE and the client-AI backbone** — [Salesforce case study — Richemont's 20 Maisons](https://www.salesforce.com/eu/blog/richemont-maisons-delight-customers/) · [Google Cloud — AI suggestions at Richemont](https://cloud.google.com/blog/products/ai-machine-learning/ai-suggestions-serve-a-better-client-experience-at-richemont) · [Richemont JLC — Client Data & Reporting Specialist job](https://jobs.richemont.com/Jaeger-LeCoultre/job/Meyrin-Client-Data-&-Reporting-Specialist-GE/1194371101/) · [Klover.ai — Richemont AI strategy](https://www.klover.ai/richemont-ai-strategy-analysis-of-dominance-in-luxury/)

**After-sales (SAP CS on the shared repair platform)** — [Guillaume Devif — SAP Retail, CRM & CS](https://www.linkedin.com/in/guillaume-devif-3887521b) · [Andrea Ghirardo — SAP CS Senior Product Specialist](https://www.linkedin.com/in/andreaghirardo) · [Cartier Care registration](https://www.cartier.com/en-us/register-watch.html) · [My IWC FAQ](https://www.iwc.com/us-en/services/faq) · [Watchfinder Maison page](https://www.richemont.com/our-maisons/watchfinder-co/) · [Vacheron Constantin CPO (WristReview)](https://wristreview.com/vacheron-constantin-introduces-a-new-certified-pre-owned-programme/) · [Europa Star — Vacheron Constantin China customer service](https://www.europastar.com/magazine/highlights/1004086513-service-please-vacheron-constantin-s-customer.html)

**Divestitures** — [Richemont on YNAP → Mytheresa](https://www.richemont.com/news-media/press-releases-news/myt-netherlands-parent-bv-mytheresa-and-richemont-sign-agreement-for-mytheresa-to-acquire-yoox-net-a-porter-ynap/) · [Richemont on B&M → Damiani](https://www.richemont.com/news-media/press-releases-news/richemont-and-the-damiani-group-announce-the-completion-of-the-acquisition-of-baume-mercier-by-the-damiani-group/) · [Richemont press-release archive](https://www.richemont.com/news-media/press-releases-news/)

**Article-master and BOM depth** — [Cartier watches](https://www.cartier.com/en-fr/watches/collections) · [Cartier jewellery IT](https://www.cartier.com/en-it/jewellery/collections) · [Hautane on Cartier serials since 1970](https://hautane.com/en/guides/authentification/authentifier-bijoux-cartier) · [Panerai limited editions](https://panerai.watchlounge.com/introduction/) · [VCA on High Jewellery via Sotheby's](https://www.sothebys.com/en/articles/a-look-into-the-world-of-van-cleef-arpels-high-jewelry) · [Bloomberg on Sotheby's Shapes of Cartier](https://www.bloomberg.com/news/articles/2026-04-08/largest-vintage-cartier-watch-collection-to-be-sold-by-sotheby-s) · [Vacheron Ref. 57260](https://www.vacheron-constantin.com/us/en/watches/exceptional-timepieces/reference-57260.html) · [Patek Grandmaster Chime](https://www.patek.com/en/collection/grand-complications/6300gr-001) · [Edana on watchmaking ERP complexity](https://edana.ch/en/2025/12/12/watchmaking-erp-managing-complexity-and-industrializing-swiss-excellence/) · [SAP Help — Variant Configuration](https://help.sap.com/docs/SAP_ERP/61155ee7ed304ae8b66b7526555a6a07/1a40b953495bb44ce10000000a174cb4.html)

**Manufacturing** — [JLC on the Manufacture](https://www.jaeger-lecoultre.com/us-en/our-maison/manufacture-since-1833) · [WatchesBySJX on Vacheron](https://watchesbysjx.com/2024/07/vacheron-constantin-manufacture-visit.html) · [Lange manufacture movements](https://www.alange-soehne.com/us-en/manufacture/art-of-watchmaking/manufacture-movements) · [Roger Dubuis Poinçon de Genève](https://www.rogerdubuis.com/our-maison/craftsmanship/poincon-de-geneve) · [Swisswatches on Piaget](https://swisswatches-magazine.com/piaget-manufacture-visit-a-true-maison/) · [IWC Journal on movements](https://www.iwc.com/ch-en/journal/mechanical-marvels-part1) · [WatchProZine on Cartier La Chaux-de-Fonds](https://www.watchprozine.com/cartier/live-from-la-chaux-de-fonds-the-cartier-manufacture/3838926/886/) · [Grail Watch Wiki on ValFleurier](https://wiki.grail-watch.com/index.php/ValFleurier) · [Europa Star on ValFleurier](https://www.europastar.com/magazine/highlights/1002198110-val-fleurier-responds-to-richemont-s-movement.html) · [Richemont acquires Donzé-Baume](https://www.richemont.com/news-media/press-releases-news/richemont-acquires-watch-component-manufacturer-done-baume-sa/) · [Richemont acquires Varinor / VVSA](https://www.richemont.com/news-media/press-releases-news/richemont-acquires-varin-etampage-and-varinor-vvsa/) · [Richemont acquires Roger Dubuis component arm](https://www.richemont.com/news-media/press-releases-news/richemont-acquires-component-manufacturing-operations-of-manufacturer-roger-dubuis-sa/) · [Richemont FY25 results (boutique counts)](https://www.richemont.com/media/nptj0zrk/richemont-fy25-annual-results-presentation-en.pdf)

**Regulation** — [Kimberley Core Document](https://www.worlddiamondcouncil.org/wp-content/uploads/2021/12/KP-Core-Document_20131122_amended.pdf) · [European Commission ESPR FAQ](https://environment.ec.europa.eu/document/download/5f7ff5e2-ebe9-4bd4-a139-db881bd6398f_en?filename=FAQ-UPDATE-4th-Iteration_clean.pdf) · [Green Forum on unsold-apparel ban](https://green-forum.ec.europa.eu/implementing-ecodesign-sustainable-products-regulation_en) · [Swiss IPI on Swiss Made watches](https://www.ige.ch/en/law-and-policy/national-ip-law/indications-of-source/swiss-indications-of-source/industry-ordinances/revision-of-the-ordinance-on-the-use-of-swiss-for-watches) · [UK gov.uk hallmarking](https://www.gov.uk/government/publications/hallmarking-guidance-notes/hallmarking-is-the-law-guidance-summary) · [Douanes françaises poinçon de maître](http://www.douane.gouv.fr/demarche/marquer-vos-ouvrages-dun-poincon-de-maitre-ou-de-responsabilite) · [EUR-Lex CS3D Directive 2024/1760](https://eur-lex.europa.eu/eli/dir/2024/1760/oj/eng) · [CITES text](https://cites.org/eng/disc/text.php)

---

*Pour le bien-être du peuple.*
