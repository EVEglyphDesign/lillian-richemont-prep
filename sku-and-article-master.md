# Luxury SKU / Article-Master Shape — Richemont Bluefield Prep

Purpose: give Lillian concrete, source-backed numbers on the article/material-master scale she'll meet inside Richemont's Maisons, one to two layers below "data," for an S/4HANA Bluefield conversion conversation.

## 1. Cartier — order of magnitude

Cartier's own sitemap is the cleanest public proxy for active SKUs. Its watch catalog page shows **254 watch models** ([Cartier.com](https://www.cartier.com/en-fr/watches/collections)), and jewellery catalog pages show **1,137–1,287 models** depending on locale ([Cartier.com IT](https://www.cartier.com/en-it/jewellery/collections), [Cartier.com TR](https://www.cartier.com/en-tr/jewellery/collections/)); the Panthère de Cartier line alone has **142 models** ([Cartier.com](https://www.cartier.com/en-us/jewelry/all-collections/panthere-de-cartier/)). Current-season references top **1,400+ models** on the storefront alone — an undercount, since each "model" bundles size/metal/gem variants that each get a distinct material number, consistent with the brief's **3,000–10,000+ active references** estimate. Vintage/heritage material multiplies this: Sotheby's 2026 "Shapes of Cartier" sale alone assembled **over 300 vintage watch references** from one 25-year private collection spanning Cartier's Paris, London, and New York workshops ([Bloomberg](https://www.bloomberg.com/news/articles/2026-04-08/largest-vintage-cartier-watch-collection-to-be-sold-by-sotheby-s)) — a fraction of Cartier's near-century-deep archive.

## 2. Van Cleef & Arpels — order of magnitude and uniqueness

VCA publishes no catalog reference count, but Sotheby's notes High Jewelry pieces are frequently **"produced in limited quantities or as one-of-a-kind creations"** — many exist as a single serialized unit, never restocked ([Sotheby's](https://www.sothebys.com/en/articles/a-look-into-the-world-of-van-cleef-arpels-high-jewelry)). The 2026 "Fascinating Egypt" collection is explicitly **one-of-a-kind bracelets** ([Town & Country](https://www.townandcountrymag.com/style/jewelry-and-watches/a71424528/van-cleef-arpels-egyptian-high-jewelry-collection-2026/)). VCA's classic lines (Snowflake, Palmyre, À Cheval, Olympia) behave more like conventional style/size/color grids ([Van Cleef & Arpels](https://www.vancleefarpels.com/us/en/collections/high-jewelry/classic-high-jewelry.html)).

## 3. Specialist Watchmakers — reference counts and BOM depth

| Maison | Approx. active references | Source |
|---|---|---|
| IWC Schaffhausen | ~215 active references across 5 core lines (Pilot's 79, Portugieser 58, Portofino 56, Ingenieur 12, Aquatimer 10) | [WatchBase](https://watchbase.com/blog/tag/iwc) |
| Piaget | ~400–441 references historically/currently listed | [Quill & Pad](https://quillandpad.com/2022/03/27/dandy-watches-of-piaget-reprise-2/), [Coveted](https://www.coveted.com/discover/piaget-watches) |
| A. Lange & Söhne | ~92 current models across 7 collections | [Coveted](https://www.coveted.com/discover/a-lange-sohne-watches) |
| Jaeger-LeCoultre | 1,200+ distinct movement calibres produced since 1833 (historical depth, not current SKU count) | [HROCK](https://hrockluxury.com/blogs/journal/jaeger-lecoultre-reverso-master-reference-guide) |
| Vacheron Constantin, Panerai, Roger Dubuis | Hundreds of active references each (public listings run into the hundreds per brand per essential-watches.com reference indexes); Panerai's in-house-movement current line runs to "well over 200 individual watch models" | [SX-Z Panerai guide](https://www.sx-z.com/the-complete-panerai-buying-guide-every-current-model-line-explained/) |

This confirms the brief's framing: watch brands sit in the **hundreds to low thousands of active references**. The component-depth multiplier is the real complexity driver. A standard mechanical movement holds **~130 components in three sub-assemblies** per the Swiss Federation of Watchmakers, rising to **250+ parts for grand complications** ([WatchesHome/FHS](https://watcheshome.com/where-mechanical-watch-parts-come-from/)). Patek Philippe's Grandmaster Chime carries **1,366 parts** ([Patek Philippe](https://www.patek.com/en/collection/grand-complications/6300gr-001)); Vacheron Constantin's Reference 57260 — a single unique piece — has **over 2,800 components and 242 jewels** ([Vacheron Constantin](https://www.vacheron-constantin.com/us/en/watches/exceptional-timepieces/reference-57260.html)). A Swiss watchmaking-ERP analysis states: **"A watch movement can comprise several hundred components, assembled according to multi-level BOM structures... each subassembly requires specific tracking and distinct configuration rules"** ([Edana](https://edana.ch/en/2025/12/12/watchmaking-erp-managing-complexity-and-industrializing-swiss-excellence/)) — matching the brief's 200–500-component-per-reference assumption.

## 4. Uniqueness: one-of-a-kind vs serial-numbered vs collection production

Every genuine Cartier piece since 1970 carries hallmarks plus a **unique serial number**, engraved (not stamped), cross-referenced against a certificate ([Alibaba luxury guide citing Cartier authentication standards](https://www.alibaba.com/product-insights/how-to-choose-cartier-jewelry-authenticity-value-guide-2026.html); [Hautane](https://hautane.com/en/guides/authentification/authentifier-bijoux-cartier)). Van Cleef & Arpels pieces likewise each carry **"their own serial number, usually a mix of letters and numbers,"** matched against production records at boutiques ([Romestation](https://romestation.ca/blogs/news/van-cleef-arpels-hallmarks-explained-stamps-fonts-and-authenticity-clues)). This creates three distinct article-master patterns Lillian should expect Richemont to run in parallel:
- **One-of-a-kind (unique lot):** most annual High Jewellery "collection" pieces at VCA and Cartier — one material number = one physical object, no repeat production.
- **Serial-numbered small series:** limited/special editions (Panerai's SE tier runs ~2–2,000 pieces per the Panerai reference-database taxonomy) ([Watchlounge](https://panerai.watchlounge.com/introduction/)) — a shared base reference with individually serialized units.
- **Collection/grid production:** standard jewellery lines (e.g., Love, LOVE bracelet, Alhambra) — true style/color/size variant grids, closer to conventional retail SKU logic.

## 5. YNAP as a pre-sale SKU benchmark

YNAP (Richemont-owned until the 2024–25 sale to Mytheresa) never published one "total SKU" figure, but disclosed proxies over time: Net-A-Porter carried products from **"more than 350 designers"** as of 2013 with **2M+ monthly visitors** ([Wikipedia/YNAP](https://en.wikipedia.org/wiki/YOOX_Net-a-Porter_Group)); YOOX shipped **"over 1.7 million products... to 53 countries"** that same year ([Wikipedia/YNAP](https://en.wikipedia.org/wiki/YOOX_Net-a-Porter_Group)). Post-merger, YNAP's boilerplate describes Net-A-Porter offering **"more than 200 specialist beauty brands"** plus fine watches, jewellery, apparel and accessories across four stores (Net-A-Porter, Mr Porter, The Outnet, YOOX) ([YNAP](https://www.ynap.com/what-we-do/multibrand-online-stores/net-a-porter/)). A Centric Software case study notes YNAP's own private-label operation alone manages **"over 4,000 SKUs per season across a number of different brands"** ([Centric Software](https://www.centricsoftware.com/success-stories/yoox-net-a-porter/)) — implying total marketplace SKU count, across "thousands of brands and suppliers" per YNAP's modern-slavery disclosure ([YNAP FY25 Statement](https://s206.q4cdn.com/479417833/files/doc_downloads/esg-ynap/YNAP-Modern-Slavery-Statement-FY25.pdf)), in the hundreds of thousands, driven by size/colour proliferation and heavy seasonality. Richemont sold its 100% YNAP stake to Mytheresa ([Richemont](https://www.richemont.com/news-media/press-releases-news/myt-netherlands-parent-bv-mytheresa-and-richemont-sign-agreement-for-mytheresa-to-acquire-yoox-net-a-porter-ynap/)) — useful as a *historical* benchmark, not a current Richemont system.

## SAP article-master implications

- **Serialisation:** Every watch and most High Jewellery pieces are individually serial-numbered at the point of manufacture, matched to certificates ([Romestation](https://romestation.ca/blogs/news/van-cleef-arpels-hallmarks-explained-stamps-fonts-and-authenticity-clues), [Hautane](https://hautane.com/en/guides/authentification/authentifier-bijoux-cartier)) — this is squarely SAP EWM/IM serial-number profile territory, with batch or handling-unit-level tracking needed even for "collection" grid items once individualized (engraving, sizing).
- **Movement BOM depth:** Multi-level BOMs from case/dial/hands down to movement sub-assemblies and individual jewels/components, confirmed at 130–2,800+ parts per reference depending on complication ([Edana](https://edana.ch/en/2025/12/12/watchmaking-erp-managing-complexity-and-industrializing-swiss-excellence/), [Patek Philippe](https://www.patek.com/en/collection/grand-complications/6300gr-001)).
- **Configurable products:** Metal type, gem type, size, and engraving map directly to SAP LO-VC (Variant Configuration): a "super BOM" and configuration profile per configurable material, avoiding one discrete material master per combination ([SAP Help](https://help.sap.com/docs/SAP_ERP/61155ee7ed304ae8b66b7526555a6a07/1a40b953495bb44ce10000000a174cb4.html)).
- **Certificates and chain-of-custody:** Hallmarks (French eagle head, Swiss sun/moon, UK crown), RJC responsible-sourcing documentation, and Cartier/VCA certificates of authenticity must attach at the material/batch level, not just the sales-order level, given resale, insurance, and regulatory dependence on this documentation ([Alibaba luxury guide](https://www.alibaba.com/product-insights/how-to-choose-cartier-jewelry-authenticity-value-guide-2026.html)).

## Comparative table: Maison × active references × uniqueness

| Maison | Approx. active references | Uniqueness profile |
|---|---|---|
| Cartier | ~1,400+ current catalog models (jewellery+watches); 3,000–10,000+ once variants unpacked; vintage archive adds hundreds/thousands more | Mixed: collection grid (Love, Panthère) + serialized watches + one-of-a-kind High Jewellery |
| Van Cleef & Arpels | Not publicly quantified; High Jewellery lines are annual (dozens of pieces/collection) | Predominantly one-of-a-kind or micro-series; classic lines are grid-based |
| IWC | ~215 | Collection/grid, individually serialized |
| Piaget | ~400–441 | Collection/grid, individually serialized |
| A. Lange & Söhne | ~92 | Collection/grid, individually serialized, low volume |
| Jaeger-LeCoultre | 1,200+ calibres historically; hundreds of current references | Collection/grid; grand complications near-unique |
| Vacheron Constantin / Panerai / Roger Dubuis | Hundreds each | Collection/grid + limited/special editions (serialized small series) |
| YNAP (historical benchmark) | Hundreds of thousands of SKUs (multi-brand, size/colour, seasonal) | Pure grid/variant retail model, no uniqueness |

## Questions Lillian should ask

1. Does Richemont plan to model one-of-a-kind High Jewellery pieces as unique "lots" (one material master = one serialized object) or force them into a variant-configuration model designed for repeatable production — and which Maisons already do which today?
2. What is the actual count of *distinct material numbers* (not "models") currently active across Cartier and VCA in legacy systems, including vintage/heritage/archive references still serviced or resold?
3. For watch movement BOMs, how many BOM levels deep does Richemont's target S/4HANA design go — case/dial/hands as one level, or full explosion to individual jewels and screws — and does that vary by Maison?
4. How are RJC chain-of-custody documents, hallmark certificates, and Cartier/VCA authenticity certificates currently attached to material records, and will Bluefield preserve that link at conversion, or does it need to be rebuilt?
5. Given YNAP's grid-based, high-SKU-count model differs fundamentally from the Maisons' serialized/unique-piece model, is a single S/4HANA article-master template meant to serve both patterns, or will Richemont run materially different configurations per business type?
