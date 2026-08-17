# Richemont — What "data" actually means

A briefing for Lillian ahead of the Richemont second interview. Every claim below has
a source in one of the five detail files in this repo.

## The one-line frame

Richemont is not one company with one ERP. It is roughly **twenty Maisons** sitting on
top of **~120 SAP instances** ([Businesswire](https://www.businesswire.com/news/home/20211122005617/en/Richemont-Selects-AWS-as-Its-Preferred-Cloud-Provider-to-Drive-Product-Innovation)),
each Maison carrying its own manufacturing model, its own uniqueness pattern, its own
regulatory surface, and — because the Group grew by acquisition since 1979 — its own
ERP heritage that has been folded in one Maison at a time. The transformation is called
**"New Foundations"** and it is a **Bluefield S/4HANA** conversion built on an internal
template known as **"Gemini"** (successor to an earlier "SAP Tiger" template)
([Undisturbed](https://undisturbed.blog/articles/richemont)). Anyone who says "data
transformation" at Richemont is really saying: reconcile twenty Maisons onto one
template without breaking a serialized High Jewellery piece, a Kimberley certificate, or
a Swiss-Made bill-of-materials cost split.

## SAP landscape — the count and what runs on it

- **~120 SAP instances** were migrated to AWS by end-2022 as the platform for the
  transformation ([Businesswire](https://www.businesswire.com/news/home/20211122005617/en/Richemont-Selects-AWS-as-Its-Preferred-Cloud-Provider-to-Drive-Product-Innovation)).
- The **Gemini** template covers Finance, Controlling, Sales, Retail, Supply Chain,
  Procurement, EWM, and Master Data Governance, and is the target state for every
  Maison. Buccellati was explicitly still being migrated onto Gemini as of a 2025 job
  posting, which tells you the rollout is not finished.
- Around Gemini sits **SuccessFactors + Concur** (HR/travel), **BW/4HANA + Datasphere +
  SAP Analytics Cloud** (the data platform), **SAP Commerce Cloud (Hybris)** (Maison
  e-commerce fronts), and a **Fashion Management** stack that is the successor to
  IS-AFS for the fashion/leather Maisons (Chloé, Alaïa, Peter Millar).
- Non-SAP satellites that Lillian will inevitably meet: **ELEVATE** — the Salesforce +
  Google Cloud clienteling platform, ~10,000 users, 45 markets, 11+ brands
  ([Salesforce](https://www.salesforce.com/eu/blog/richemont-maisons-delight-customers/)) —
  **Workday HCM** going live 2026 in parallel with SuccessFactors, and **Cegid Y2** as
  the POS layer in most boutiques. Salesforce is where the client-master lives;
  Cegid is where the transaction happens; SAP is where the finance and inventory land.
  Three systems, one client, one sale — and that seam is where most of the "data"
  problems actually sit.

Full detail: [`sap-landscape.md`](./sap-landscape.md).

## Acquisition heritage — why one template is hard

The Maisons did not arrive at Richemont as a set. They arrived over 46 years, each
with its own ERP:

- **1979** Cartier Monde; **1988** Piaget and Baume & Mercier; **1993** Vendôme
  (Montblanc, Chloé, Dunhill, Lancel); **1996** Vacheron Constantin; **1999–2003**
  Van Cleef & Arpels; **2000** LMH (IWC, Jaeger-LeCoultre, A. Lange & Söhne);
  **2012** Peter Millar; **2018** Watchfinder; **2019** Buccellati; **2021** Delvaux;
  **2023–24** Gianvito Rossi; **September 2024** Vhernier for €94m
  ([Richemont press releases, chronologically archived on richemont.com/news-media](https://www.richemont.com/news-media/press-releases-news/)).
- Divestitures matter as much as acquisitions. **YNAP was sold to Mytheresa in April
  2025** with a 33% retained stake in LuxExperience ([Richemont](https://www.richemont.com/news-media/press-releases-news/myt-netherlands-parent-bv-mytheresa-and-richemont-sign-agreement-for-mytheresa-to-acquire-yoox-net-a-porter-ynap/)),
  which was never on Gemini core — it ran IBM WebSphere/OMS, Centric PLM, and RELEX
  demand-planning. **Baume & Mercier was sold to Damiani, closing 1 July 2026**
  ([Richemont](https://www.richemont.com/news-media/press-releases-news/richemont-and-the-damiani-group-announce-the-completion-of-the-acquisition-of-baume-mercier-by-the-damiani-group/)),
  with Richemont providing transition services — a live carve-out of that Maison's
  vendor master, ValFleurier movement-supply agreements, and Business Network
  connections.
- Two Maisons are worth naming for the interview because they are visibly *not* on
  Gemini yet: **Buccellati** (still migrating, per the 2025 ad) and **Vhernier** (still
  has its own IT Director post-acquisition, September 2024).

Lillian's line if asked "how hard is the data": *twenty Maisons acquired over
forty-six years is twenty different legacy article-masters, twenty different
vendor-masters, twenty different chart-of-accounts translations — Bluefield preserves
history, so all of that has to be reconciled at the record level, not just at the
report level.*

Full detail: [`acquisition-erp-heritage.md`](./acquisition-erp-heritage.md).

## The article-master — what a SKU actually is at Richemont

This is where a claim about *data* has to survive its first follow-up question. The
Maisons do not run one SKU pattern. They run three in parallel, and Bluefield has to
carry all three:

1. **Collection / grid production** — Love bracelets, Alhambra pendants, Panthère
   watches. Style × metal × size × gem variants. This is conventional retail SKU
   logic, and it maps cleanly to SAP Variant Configuration (LO-VC): one super-BOM,
   one configuration profile, avoid one material master per combination
   ([SAP Help](https://help.sap.com/docs/SAP_ERP/61155ee7ed304ae8b66b7526555a6a07/1a40b953495bb44ce10000000a174cb4.html)).
2. **Serialized small series** — every mechanical watch, every limited edition.
   Individually numbered, matched to a certificate. Panerai's special-edition tier
   runs ~2–2,000 pieces per reference ([Watchlounge](https://panerai.watchlounge.com/introduction/)).
   Cartier has engraved serial numbers on every genuine piece since 1970 ([Hautane](https://hautane.com/en/guides/authentification/authentifier-bijoux-cartier)).
3. **One-of-a-kind** — most Cartier and VCA High Jewellery. The 2026 VCA "Fascinating
   Egypt" collection is one-of-a-kind bracelets ([Town & Country](https://www.townandcountrymag.com/style/jewelry-and-watches/a71424528/van-cleef-arpels-egyptian-high-jewelry-collection-2026/)).
   One material number equals one physical object, and there is no repeat production.

Order-of-magnitude counts Lillian can quote:

- **Cartier**: ~1,400+ current catalog *models* on the storefront (254 watch models +
  1,137–1,287 jewellery models depending on locale) ([Cartier.com watches](https://www.cartier.com/en-fr/watches/collections),
  [Cartier.com jewellery IT](https://www.cartier.com/en-it/jewellery/collections)),
  unpacking to **3,000–10,000+ distinct material numbers** once size/metal/gem
  variants each get their own article. The vintage/heritage archive adds thousands more:
  Sotheby's 2026 "Shapes of Cartier" sale alone catalogued 300+ vintage watch
  references from a single 25-year collection ([Bloomberg](https://www.bloomberg.com/news/articles/2026-04-08/largest-vintage-cartier-watch-collection-to-be-sold-by-sotheby-s)).
- **IWC** ~215 active references, **Piaget** ~400–441, **A. Lange & Söhne** ~92,
  **Jaeger-LeCoultre** 1,200+ calibres historically ([Coveted](https://www.coveted.com/discover/a-lange-sohne-watches),
  [WatchBase](https://watchbase.com/blog/tag/iwc), [Quill & Pad](https://quillandpad.com/2022/03/27/dandy-watches-of-piaget-reprise-2/)).
- **Van Cleef & Arpels** publishes no reference count — High Jewellery is
  "produced in limited quantities or as one-of-a-kind creations" ([Sotheby's](https://www.sothebys.com/en/articles/a-look-into-the-world-of-van-cleef-arpels-high-jewelry)).
- **YNAP** was hundreds of thousands of SKUs pre-sale — a benchmark of what Richemont
  chose to divest rather than absorb ([Centric Software](https://www.centricsoftware.com/success-stories/yoox-net-a-porter/)).

Then there is the depth *behind* each SKU. A standard mechanical movement carries
~130 components in three sub-assemblies; grand complications go past 250; Patek's
Grandmaster Chime is 1,366 parts; Vacheron's Reference 57260 is 2,800+ components and
242 jewels — a single unique piece ([Vacheron Constantin](https://www.vacheron-constantin.com/us/en/watches/exceptional-timepieces/reference-57260.html),
[Patek Philippe](https://www.patek.com/en/collection/grand-complications/6300gr-001)).
Multi-level BOMs are not a Richemont eccentricity, they are the entire discipline
([Edana](https://edana.ch/en/2025/12/12/watchmaking-erp-managing-complexity-and-industrializing-swiss-excellence/)).

Full detail: [`sku-and-article-master.md`](./sku-and-article-master.md).

## Manufacturing — where a "supplier" is a Group asset

Ask Richemont "how integrated is your supply chain?" and the honest answer is *it
depends which Maison*. The spectrum:

- **Full Manufacture** (own movement design + production + assembly): **Jaeger-LeCoultre**
  (82 workshops, 1,200+ in-house calibre variants under one Vallée de Joux roof —
  [JLC](https://www.jaeger-lecoultre.com/us-en/our-maison/manufacture-since-1833)),
  **Vacheron Constantin** (hairspring in-house at Le Brassus, cases and most dials
  outsourced — [WatchesBySJX](https://watchesbysjx.com/2024/07/vacheron-constantin-manufacture-visit.html)),
  **A. Lange & Söhne** (70+ in-house calibres, hand-assembled twice on site —
  [A. Lange & Söhne](https://www.alange-soehne.com/us-en/manufacture/art-of-watchmaking/manufacture-movements)),
  **Roger Dubuis** (~100% Poinçon de Genève certified —
  [Roger Dubuis](https://www.rogerdubuis.com/our-maison/craftsmanship/poincon-de-geneve)),
  **Piaget** (in-house movement design plus Group refinery supplying 100% of its
  fine gold — [Swisswatches Magazine](https://swisswatches-magazine.com/piaget-manufacture-visit-a-true-maison/)).
- **Partial Manufacture**: **IWC** — in-house from 1868, quartz-crisis outsourcing,
  in-house design rebuilt from calibre 5000 in 2000 and the first in-house chronograph
  (89360) in 2007; entry lines still use externally sourced ETA
  ([IWC](https://www.iwc.com/ch-en/journal/mechanical-marvels-part1)).
  **Cartier** — La Chaux-de-Fonds manufacture (33,000 m², completed 2000) makes on
  average one-third of components in-house; the rest is outsourced, with two-thirds of
  hands coming from Universo and Aiguilla
  ([WatchProZine](https://www.watchprozine.com/cartier/live-from-la-chaux-de-fonds-the-cartier-manufacture/3838926/886/)).
- **Outsourced base movements**: **Montblanc and Panerai** run on Group-supplied
  ValFleurier calibres; **Baume & Mercier** ran ETA 2824-2 / Sellita SW200-1-based
  calibres before the Damiani sale ([CaliberCorner](https://calibercorner.com/baume-mercier-caliber-bm-112824/),
  [Grail Watch Wiki](https://wiki.grail-watch.com/index.php/ValFleurier)).

The distinctive Richemont move is that the Group **buys** parts of the subcontractor
base rather than only contracting with it:

- **Manufacture Horlogère ValFleurier** — Group movement house, 5–6 new calibres a
  year, 20,000+ movements produced/finished, supplies Montblanc, Panerai, historically
  Baume & Mercier ([Europa Star](https://www.europastar.com/magazine/highlights/1002198110-val-fleurier-responds-to-richemont-s-movement.html)).
- **Donzé-Baume** — cases and bracelets, ~300 employees, acquired November 2007
  ([Richemont](https://www.richemont.com/news-media/press-releases-news/richemont-acquires-watch-component-manufacturer-done-baume-sa/)).
- **Varinor / VVSA** — precious-metals refining, RJC Chain-of-Custody certified for
  gold and platinum, acquired October 2012
  ([Richemont](https://www.richemont.com/news-media/press-releases-news/richemont-acquires-varin-etampage-and-varinor-vvsa/)).
- **Roger Dubuis component-manufacturing arm** — acquired September 2007, a year
  before Richemont took the 60% equity stake in the Maison itself
  ([Richemont, 2007](https://www.richemont.com/news-media/press-releases-news/richemont-acquires-component-manufacturing-operations-of-manufacturer-roger-dubuis-sa/)).

**Why Lillian cares**: this changes the SAP model. Group-owned but legally separate
component makers are candidates for **subcontracting scenarios** (SAP outsource
manufacturing / scenario 30) with consigned components, **not** arm's-length vendor
POs — and possibly for **intercompany billing/STO** logic rather than standard vendor
invoicing. The SAP case study confirms "outsource manufacturing" was one of the four
level-one processes piloted in the first six Maisons
([SAP news](https://news.sap.com/africa/2023/05/richemont-harmonizing-supply-chain-processes-between-group-business-and-suppliers/)).

The supplier network is quantifiable too. Richemont has ~700 direct suppliers, of
which **~460 are on the SAP Business Network**, and **only 17 have their own-ERP
integration back to Richemont** ([SAP case study](https://www.sap.com/asset/dynamic/2023/04/de62229b-6e7e-0010-bca6-c68f7e60039b.html)).
The captive Group makers (ValFleurier, Donzé-Baume, Varinor) are the plausible
priorities for that 17; the long tail of independent dial/strap/case houses sits in
portal-only, non-integrated tier.

Distribution: **1,392–1,393 internal boutiques + 1,071 franchised = ~2,463 total**
([Richemont FY25 results](https://www.richemont.com/media/nptj0zrk/richemont-fy25-annual-results-presentation-en.pdf)),
plus **Watchfinder** as the pre-owned lane buying/servicing/reselling 60+ brands
([Richemont](https://www.richemont.com/our-maisons/watchfinder-co/)). Owned vs.
franchised changes inventory ownership, which changes where consignment logic
belongs — this is a data question, not just a store question.

Full detail: [`manufacturing-and-supply-chain.md`](./manufacturing-and-supply-chain.md).

## The regulatory data surface

Every regulation below is a set of *fields that must live on a material master or a
batch record* — not a compliance memo. This is the layer that turns "data" into a
concrete cost.

- **Kimberley Process** on rough diamonds: certificate number, country of origin,
  carat weight, USD value, HS code, exporter/importer IDs; ≥3 years for the
  certificate, 5 years for trader records ([KP Core Document](https://www.worlddiamondcouncil.org/wp-content/uploads/2021/12/KP-Core-Document_20131122_amended.pdf)).
  Batch-managed material with the certificate travelling as batch attributes.
- **EU ESPR / Digital Product Passport**: textiles/apparel confirmed for a 2027
  delegated act ([European Commission ESPR FAQ](https://environment.ec.europa.eu/document/download/5f7ff5e2-ebe9-4bd4-a139-db881bd6398f_en?filename=FAQ-UPDATE-4th-Iteration_clean.pdf));
  jewellery/watches not yet in the plan but under review — the material master will
  need composition, substances-of-concern, recycled content, and repairability fields
  the moment they land. From **19 July 2026**, large enterprises face a **ban on
  destroying unsold apparel** with disclosure obligations
  ([Green Forum, European Commission](https://green-forum.ec.europa.eu/implementing-ecodesign-sustainable-products-regulation_en)) —
  a direct hit on the fashion-Maison side of the estate.
- **Swiss Made "60% rule"** (in force 1 January 2017): at least **60% of manufacturing
  cost of the complete watch** must be Swiss-generated, and for the movement at least
  **60% of movement manufacturing cost** with **≥50% of component value** Swiss-made,
  R&D in Switzerland ([Swiss Federal Institute of Intellectual Property](https://www.ige.ch/en/law-and-policy/national-ip-law/indications-of-source/swiss-indications-of-source/industry-ordinances/revision-of-the-ordinance-on-the-use-of-swiss-for-watches)).
  This is a **BOM cost-split**: every component on every watch reference has to carry
  its origin and unit cost in the material master, and the roll-up has to be auditable
  per reference. This is not a report — it is a data model requirement.
- **Hallmarking** — UK Assay Offices, French *poinçon de maître* with *livre de
  police* transaction ledger held by the *bureau de garantie*, Swiss *Bureau central du
  contrôle des métaux précieux* ([UK gov.uk](https://www.gov.uk/government/publications/hallmarking-guidance-notes/hallmarking-is-the-law-guidance-summary),
  [Douanes françaises](http://www.douane.gouv.fr/demarche/marquer-vos-ouvrages-dun-poincon-de-maitre-ou-de-responsabilite)).
  Sponsor's mark + fineness + assay-office code as material or batch attributes.
- **German LkSG** (≥1,000 employees since 2024) and **EU CS3D** (Directive
  2024/1760, phasing in 2027–2029) — human-rights/environmental due diligence over
  the entire chain of activities, with **≥5 years' retention** of due-diligence
  documentation ([EUR-Lex](https://eur-lex.europa.eu/eli/dir/2024/1760/oj/eng)). All
  700+ direct suppliers become governed business partners in MDG-BP with risk-score
  attributes.
- **CITES** for exotic leathers (alligator, python) and coral — Appendix II permits,
  species name, issuing country, permit position number, and Scientific Authority
  non-detriment finding, on every strap and every skin lot ([CITES](https://cites.org/eng/disc/text.php)).
  Natural home is **SAP GTS** (Global Trade Services) for legal-control determination
  at order/shipment creation.
- **GDPR / PIPL / CCPA** across ELEVATE's **45 markets and ~10,000 users** — consent
  flag, legal basis, Transfer Impact Assessment or SCC reference, PIPL security
  assessment status, retention/deletion trigger — on every client record touched by
  Salesforce, Cegid, and SAP simultaneously.

Full detail: [`regulatory-data-rules.md`](./regulatory-data-rules.md).

## The five questions that go a layer or two below "data"

For the interview itself, these are the questions that show Lillian has actually
walked past the word and looked at what's under it:

1. **Article-master pattern**: Does Richemont's Bluefield template model High Jewellery
   one-of-a-kind pieces as unique lots (one material master = one serialized object),
   or force them into Variant Configuration? And how far are Cartier and VCA — the two
   Maisons where this most matters — from that target state today?
2. **Swiss Made cost-split**: For the watch Maisons, is the 60% rule computed by rolling
   up cost/origin fields on every component in the material master, or maintained as a
   compliance overlay in EHS/Product Compliance? Bluefield preserves history — is the
   pre-conversion cost-split trustworthy across all seven watch Maisons, or does it get
   rebuilt at cutover?
3. **Group-owned suppliers as subcontractors, not vendors**: Are ValFleurier,
   Donzé-Baume, Varinor, and the Roger Dubuis component arm being modelled as
   subcontracting POs with consigned precious-metal components and intercompany
   billing, or are they still on standard third-party vendor flows? This is where a
   quarter-billion of intra-Group volume can silently misclassify.
4. **Divestiture data carve-outs**: With Baume & Mercier closed 1 July 2026 and YNAP
   sold in April 2025, how much of the current landscape is *transition-service*
   plumbing versus steady-state, and which of the ~120 SAP instances are still on the
   books solely to keep those carve-outs running?
5. **Client-master across three systems**: Salesforce (ELEVATE) owns the 360° view,
   Cegid Y2 owns the transaction, SAP owns the finance. Where is the source-of-truth
   for consent, transfer mechanism, and deletion — and how is that reconciled across
   45 markets governed by GDPR, PIPL, and CCPA simultaneously?

## What Lillian can safely name in the room

- **~120 SAP instances**, migrated to AWS end-2022, target state **S/4HANA Bluefield**
  under the **New Foundations** programme, template known internally as **Gemini**.
- **~20 Maisons**, largest is **Cartier**, acquired since **1979**; **YNAP** sold to
  Mytheresa **April 2025**; **Baume & Mercier** sold to Damiani, closing **1 July 2026**;
  **Buccellati** and **Vhernier** not yet on Gemini.
- **Cartier ~1,400+ catalog models** unpacking to **3,000–10,000+ SAP materials**; watch
  BOMs from **~130 components** to **2,800+** at the top end.
- **~700 direct suppliers**, **~460 on SAP Business Network**, only **17** with own-ERP
  integration.
- **1,392 internal + 1,071 franchised = ~2,463 boutiques**; **ELEVATE** = Salesforce +
  GCP, **~10,000 users, 45 markets, 11+ brands**; **Cegid Y2** POS; **Workday HCM**
  live 2026.
- **Regulatory surface**: Kimberley, ESPR/DPP (textiles first, 2027), Swiss Made 60%,
  UK/French/Swiss hallmarking, LkSG + CS3D (5-year retention), CITES on exotic
  leathers, GDPR/PIPL/CCPA across 45 markets.

That is the layer or two below the word *data* Lillian needs to hold. Everything above
is source-tagged so it can be re-checked. The detail files are in the same repo.

*Pour le bien-être du peuple.*
