# Richemont — the layer below "data"

Prep for Lillian's second interview. Sources at the bottom of each section.

---

## The frame

- ~20 Maisons on ~120 SAP instances.
- Programme: **New Foundations** — a **Bluefield** S/4HANA conversion.
- Template: **Gemini** (successor to "SAP Tiger").
- The "data" problem = reconciling twenty Maisons onto one template without breaking a serialized High Jewellery piece, a Kimberley cert, or a Swiss-Made BOM cost-split.

## SAP landscape

- ~120 SAP instances migrated to AWS by end-2022.
- Gemini covers Finance, Controlling, Sales, Retail, Supply Chain, Procurement, EWM, MDG.
- Around it: **SuccessFactors + Concur**, **BW/4HANA + Datasphere + SAC**, **SAP Commerce Cloud (Hybris)**, **Fashion Management** (Chloé, Alaïa, Peter Millar).
- Non-SAP satellites Lillian will meet:
  - **ELEVATE** — Salesforce + GCP clienteling, ~10,000 users, 45 markets, 11+ brands.
  - **Workday HCM** — going live 2026 in parallel with SuccessFactors.
  - **Cegid Y2** — POS in most boutiques.
- The seam: Salesforce owns the client, Cegid owns the transaction, SAP owns the finance. Three systems, one client, one sale. Most "data" problems sit here.

## Acquisition heritage

- 46 years of acquisitions, each Maison arriving with its own ERP.
- Highlights: Cartier 1979 · Piaget / Baume & Mercier 1988 · Vendôme (Montblanc, Chloé, Dunhill, Lancel) 1993 · VC 1996 · VCA 1999–2003 · LMH (IWC, JLC, Lange) 2000 · Peter Millar 2012 · Watchfinder 2018 · Buccellati 2019 · Delvaux 2021 · Gianvito Rossi 2023–24 · **Vhernier September 2024**.
- Divestitures also live in the data:
  - **YNAP → Mytheresa, April 2025** (33% retained in LuxExperience). Never on Gemini; IBM WebSphere/OMS, Centric PLM, RELEX.
  - **Baume & Mercier → Damiani, closing 1 July 2026.** Transition services in flight = live carve-out of vendor master and ValFleurier movement-supply.
- Not yet on Gemini: **Buccellati** (still migrating per 2025 posting), **Vhernier** (still has its own IT Director).

**One-liner if asked how hard the data is:** 20 Maisons over 46 years = 20 legacy article-masters, 20 vendor-masters, 20 chart-of-accounts translations. Bluefield preserves history, so this reconciles at the record level, not the report level.

## Article-master — what a SKU actually is

Three SKU patterns run in parallel, and Bluefield carries all three:

1. **Collection / grid** — Love, Alhambra, Panthère. Style × metal × size × gem. Fits SAP Variant Configuration (LO-VC).
2. **Serialized small series** — every mechanical watch, every limited edition. Individually numbered, matched to a certificate. Panerai limited runs ~2–2,000 pieces. Cartier engraves serials on every piece since 1970.
3. **One-of-a-kind** — most Cartier and VCA High Jewellery. One material = one physical object.

**Order-of-magnitude counts Lillian can quote:**

- **Cartier** ~1,400+ catalog models → 3,000–10,000+ SAP materials once variants expand. Vintage archive adds thousands more.
- **IWC** ~215 · **Piaget** ~400–441 · **Lange** ~92 · **JLC** 1,200+ calibres historically.
- **VCA** publishes no reference count — "limited quantities or one-of-a-kind."
- **YNAP** was hundreds of thousands of SKUs pre-sale — what Richemont chose to divest.

**BOM depth:** standard mechanical ~130 components, grand complications 250+, Patek Grandmaster Chime 1,366 parts, Vacheron Ref. 57260 = 2,800+ components (single unique piece). Multi-level BOMs are the discipline, not the exception.

## Manufacturing — the spectrum

- **Full Manufacture:** JLC (82 workshops, 1,200+ calibres), VC, A. Lange & Söhne (70+ calibres, hand-assembled twice), Roger Dubuis (~100% Poinçon de Genève), Piaget.
- **Partial:** IWC (in-house from cal. 5000, entry lines on ETA), Cartier (La Chaux-de-Fonds — ~1/3 in-house, hands from Universo/Aiguilla).
- **Outsourced base movements:** Montblanc and Panerai run on Group-supplied **ValFleurier**; Baume & Mercier ran ETA/Sellita.

**Group-owned suppliers (this is the twist):**

- **ValFleurier** — Group movement house, 5–6 new calibres/yr, 20,000+ movements. Supplies Montblanc, Panerai, historically B&M.
- **Donzé-Baume** — cases and bracelets, ~300 employees, acquired Nov 2007.
- **Varinor / VVSA** — precious-metals refining, RJC certified, acquired Oct 2012.
- **Roger Dubuis component arm** — acquired Sept 2007, a year before the Maison itself.

**Why it matters for SAP:** Group-owned but legally separate = subcontracting scenarios (scenario 30) with consigned components + intercompany billing/STO, **not** arm's-length vendor POs. SAP case study confirms "outsource manufacturing" was one of four level-one processes piloted in the first six Maisons.

**Supplier network:** ~700 direct suppliers · ~460 on SAP Business Network · **only 17 with own-ERP integration**. The captive Group makers are the plausible core of that 17.

**Distribution:** 1,392 internal + 1,071 franchised = ~2,463 boutiques. **Watchfinder** as the pre-owned lane, 60+ brands. Owned vs. franchised = who owns the inventory = where consignment logic sits.

## The regulatory surface

Every item below = fields on a material master or a batch record. Not a compliance memo.

- **Kimberley Process** — cert number, origin country, carat, USD value, HS code, exporter/importer IDs. 3-yr cert, 5-yr trader records. Batch-managed material.
- **EU ESPR / DPP** — textiles/apparel confirmed for 2027 delegated act. Jewellery/watches under review. Composition, substances-of-concern, recycled content, repairability fields the moment they land. From **19 July 2026**, large enterprises face **ban on destroying unsold apparel**.
- **Swiss Made 60% rule** (in force 1 Jan 2017) — 60% of manufacturing cost of the watch and of the movement must be Swiss; ≥50% component value Swiss; R&D in CH. This is a **BOM cost-split**, not a report. Every component carries origin + unit cost, audit per reference.
- **Hallmarking** — UK Assay Offices; French *poinçon de maître* with *livre de police* ledger at the *bureau de garantie*; Swiss Bureau central. Sponsor's mark + fineness + assay-office code as material/batch attributes.
- **German LkSG + EU CS3D** (Directive 2024/1760, phasing 2027–29) — HR/environmental due diligence over the full chain; **≥5-yr retention**. All ~700 suppliers become governed business partners in MDG-BP with risk-score attributes.
- **CITES** — exotic leathers (alligator, python), coral. Appendix II permits, species, issuing country, permit number, Scientific Authority non-detriment finding — on every strap and every skin lot. Natural home: **SAP GTS**.
- **GDPR / PIPL / CCPA** across ELEVATE's 45 markets — consent flag, legal basis, TIA/SCC ref, PIPL security assessment, retention/deletion trigger. On every client record touched by Salesforce, Cegid, and SAP simultaneously.

## Five questions that go a layer below "data"

1. **High Jewellery article-master.** Bluefield template — unique lots (one material = one serialized object) or forced into Variant Configuration? How far are Cartier and VCA from target state?
2. **Swiss Made cost-split.** Rolled up from component-level origin/cost fields, or maintained as an EHS/Product Compliance overlay? Is the pre-conversion split trustworthy across all seven watch Maisons, or rebuilt at cutover?
3. **Group-owned suppliers.** ValFleurier / Donzé-Baume / Varinor / RD components — modelled as subcontracting POs with consigned precious metals and intercompany billing, or still on standard third-party vendor flows? Quarter-billion of intra-Group volume can silently misclassify.
4. **Divestiture carve-outs.** With B&M closed 1 July 2026 and YNAP sold April 2025, how much of the landscape is transition-service plumbing vs. steady-state? How many of the ~120 instances exist only to keep carve-outs running?
5. **Client-master across three systems.** Where is the source-of-truth for consent, transfer mechanism, and deletion — Salesforce, Cegid, or SAP — and how is it reconciled across GDPR, PIPL, CCPA simultaneously?

## Facts safe to name in the room

- ~120 SAP instances, on AWS since end-2022, target S/4HANA Bluefield, programme **New Foundations**, template **Gemini**.
- ~20 Maisons, biggest **Cartier**, oldest acquisition **1979**. YNAP sold Apr 2025. B&M sold 1 Jul 2026. Buccellati and Vhernier not on Gemini.
- Cartier ~1,400+ models → 3,000–10,000+ SAP materials. BOMs 130 → 2,800+ components.
- ~700 direct suppliers · ~460 on SAP Business Network · only 17 own-ERP integrated.
- 1,392 internal + 1,071 franchised = ~2,463 boutiques. ELEVATE 10,000 users / 45 markets / 11+ brands. Cegid Y2 POS. Workday HCM live 2026.
- Regulatory: Kimberley, ESPR/DPP (textiles 2027), Swiss Made 60%, UK/FR/CH hallmarking, LkSG + CS3D (5-yr retention), CITES exotic leathers, GDPR/PIPL/CCPA.

---

## Sources

**SAP landscape and cloud** — [Businesswire (Richemont + AWS)](https://www.businesswire.com/news/home/20211122005617/en/Richemont-Selects-AWS-as-Its-Preferred-Cloud-Provider-to-Drive-Product-Innovation) · [Undisturbed on New Foundations / Gemini](https://undisturbed.blog/articles/richemont) · [SAP News on Business Network](https://news.sap.com/africa/2023/05/richemont-harmonizing-supply-chain-processes-between-group-business-and-suppliers/) · [SAP case study PDF](https://www.sap.com/asset/dynamic/2023/04/de62229b-6e7e-0010-bca6-c68f7e60039b.html)

**Divestitures** — [Richemont on YNAP → Mytheresa](https://www.richemont.com/news-media/press-releases-news/myt-netherlands-parent-bv-mytheresa-and-richemont-sign-agreement-for-mytheresa-to-acquire-yoox-net-a-porter-ynap/) · [Richemont on B&M → Damiani](https://www.richemont.com/news-media/press-releases-news/richemont-and-the-damiani-group-announce-the-completion-of-the-acquisition-of-baume-mercier-by-the-damiani-group/) · [Richemont press-release archive](https://www.richemont.com/news-media/press-releases-news/)

**Article-master and BOM depth** — [Cartier watches](https://www.cartier.com/en-fr/watches/collections) · [Cartier jewellery IT](https://www.cartier.com/en-it/jewellery/collections) · [Hautane on Cartier serials since 1970](https://hautane.com/en/guides/authentification/authentifier-bijoux-cartier) · [Panerai limited editions](https://panerai.watchlounge.com/introduction/) · [VCA on High Jewellery via Sotheby's](https://www.sothebys.com/en/articles/a-look-into-the-world-of-van-cleef-arpels-high-jewelry) · [T&C on VCA "Fascinating Egypt"](https://www.townandcountrymag.com/style/jewelry-and-watches/a71424528/van-cleef-arpels-egyptian-high-jewelry-collection-2026/) · [Bloomberg on Sotheby's Shapes of Cartier](https://www.bloomberg.com/news/articles/2026-04-08/largest-vintage-cartier-watch-collection-to-be-sold-by-sotheby-s) · [Vacheron Ref. 57260](https://www.vacheron-constantin.com/us/en/watches/exceptional-timepieces/reference-57260.html) · [Patek Grandmaster Chime](https://www.patek.com/en/collection/grand-complications/6300gr-001) · [Edana on watchmaking ERP complexity](https://edana.ch/en/2025/12/12/watchmaking-erp-managing-complexity-and-industrializing-swiss-excellence/) · [SAP Help — Variant Configuration](https://help.sap.com/docs/SAP_ERP/61155ee7ed304ae8b66b7526555a6a07/1a40b953495bb44ce10000000a174cb4.html)

**Manufacturing** — [JLC on the Manufacture](https://www.jaeger-lecoultre.com/us-en/our-maison/manufacture-since-1833) · [WatchesBySJX on Vacheron](https://watchesbysjx.com/2024/07/vacheron-constantin-manufacture-visit.html) · [Lange manufacture movements](https://www.alange-soehne.com/us-en/manufacture/art-of-watchmaking/manufacture-movements) · [Roger Dubuis Poinçon de Genève](https://www.rogerdubuis.com/our-maison/craftsmanship/poincon-de-geneve) · [Swisswatches on Piaget](https://swisswatches-magazine.com/piaget-manufacture-visit-a-true-maison/) · [IWC Journal on movements](https://www.iwc.com/ch-en/journal/mechanical-marvels-part1) · [WatchProZine on Cartier La Chaux-de-Fonds](https://www.watchprozine.com/cartier/live-from-la-chaux-de-fonds-the-cartier-manufacture/3838926/886/) · [CaliberCorner on B&M calibres](https://calibercorner.com/baume-mercier-caliber-bm-112824/) · [Grail Watch Wiki on ValFleurier](https://wiki.grail-watch.com/index.php/ValFleurier) · [Europa Star on ValFleurier](https://www.europastar.com/magazine/highlights/1002198110-val-fleurier-responds-to-richemont-s-movement.html) · [Richemont acquires Donzé-Baume](https://www.richemont.com/news-media/press-releases-news/richemont-acquires-watch-component-manufacturer-done-baume-sa/) · [Richemont acquires Varinor / VVSA](https://www.richemont.com/news-media/press-releases-news/richemont-acquires-varin-etampage-and-varinor-vvsa/) · [Richemont acquires Roger Dubuis component arm](https://www.richemont.com/news-media/press-releases-news/richemont-acquires-component-manufacturing-operations-of-manufacturer-roger-dubuis-sa/) · [Richemont FY25 results (boutique counts)](https://www.richemont.com/media/nptj0zrk/richemont-fy25-annual-results-presentation-en.pdf) · [Watchfinder Maison page](https://www.richemont.com/our-maisons/watchfinder-co/)

**Regulation** — [Kimberley Core Document](https://www.worlddiamondcouncil.org/wp-content/uploads/2021/12/KP-Core-Document_20131122_amended.pdf) · [European Commission ESPR FAQ](https://environment.ec.europa.eu/document/download/5f7ff5e2-ebe9-4bd4-a139-db881bd6398f_en?filename=FAQ-UPDATE-4th-Iteration_clean.pdf) · [Green Forum on unsold-apparel ban](https://green-forum.ec.europa.eu/implementing-ecodesign-sustainable-products-regulation_en) · [Swiss IPI on Swiss Made watches](https://www.ige.ch/en/law-and-policy/national-ip-law/indications-of-source/swiss-indications-of-source/industry-ordinances/revision-of-the-ordinance-on-the-use-of-swiss-for-watches) · [UK gov.uk hallmarking](https://www.gov.uk/government/publications/hallmarking-guidance-notes/hallmarking-is-the-law-guidance-summary) · [Douanes françaises poinçon de maître](http://www.douane.gouv.fr/demarche/marquer-vos-ouvrages-dun-poincon-de-maitre-ou-de-responsabilite) · [EUR-Lex CS3D Directive 2024/1760](https://eur-lex.europa.eu/eli/dir/2024/1760/oj/eng) · [CITES text](https://cites.org/eng/disc/text.php)

**Non-SAP satellites** — [Salesforce on ELEVATE](https://www.salesforce.com/eu/blog/richemont-maisons-delight-customers/)

---

*Pour le bien-être du peuple.*
