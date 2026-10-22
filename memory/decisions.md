# Decisions

<!-- ## DEC-YYYYMMDD-n — title
Context · Options · Decision · Reason · Linked ACT/EXP ids -->

## DEC-20261022-1 — Adopt Empire OS
**Context:** Starting a Shopify import business with an agent team from day 0.
**Decision:** All agents start at L0–L1 (`state/autonomy.yaml`). Owner approves every R1–R3 action via Linear for at least 30 days.
**Reason:** Approvals are the training data for autonomy; we need a measured track record before any hands-off step.

## DEC-20261022-2 — Sell abroad in USD; Owner inputs for day 0
**Context:** Owner answered the day-0 setup questions.
**Options:** Israel/ILS (original default) · US/USD · EU/EUR.
**Decision:** Do not sell in Israel. Provisional market US, currency USD; scout compares US vs EU per product. Guardrail money caps converted from ILS to USD (~3.7, rounded). Target price 50–300 USD, AOV floor 40 USD. Monthly ad envelope 0 until the Owner sets one (needed before V7). Approvals: Linear team SHOP. Notifications: Slack #shopify-os. Business name TBD until a brand is chosen.
**Reason:** Owner wants a bigger market and very high margins. No capital budget yet, so research and cost estimates can proceed but no spend is allowed.

## DEC-20261022-3 — V1 product shortlist (proposal)
**Status:** PROPOSAL from scout (L1, R0 research). **The go/kill decision is R3 for the Owner.** Nothing has been ordered, no supplier contacted, no account created.
**Context:** Stage validate, task V1. Brief: sell abroad (US provisional, EU alternative), gross margin >= 65%, price 50-300 USD, net >= 40 USD, benefit visible in a 15-second video, no capital budget (low MOQ / dropship / POD), avoid electrical, children's, cosmetics, food/supplements, medical, batteries. Scored with `playbook/product-scoring.yaml` (max weighted score 95; shortlist line 70% = 66.5).
**Research limits:** Only WebSearch worked. WebFetch and curl were refused by the network proxy for every host tried (Amazon, Alibaba, AliExpress, 1688, CJ Dropshipping, Etsy, Google Trends, Meta Ad Library, TikTok Creative Center, Reddit, Printify, CBP, USTR, USITC HTS, ustariffrates.com, tariffstool.com). So prices come from search-result snippets, not from opening the pages. Ad runtimes (30+ days) could not be checked in the Meta Ad Library. Any number marked (est.) is a scout estimate that has not been checked.

### Tariff and import baseline (checked by search on 2026-10-22; confirm with a customs broker before V4)
- **US, China-origin goods:** MFN duty + original Section 301 (List 1-3 25%, List 4A 7.5%) + new Section 301 "forced-labor" duty of 12.5% for China. The 12.5% replaced the Section 122 surcharge when it expired on 2026-07-24. IEEPA tariffs were struck down on 2026-02-20 and are being refunded. Sources: [STR](https://www.strtrade.com/trade-news-resources/str-trade-report/trade-report/october/section-301-tariffs-on-imports-from-china-officially-continued), [KPMG](https://kpmg.com/us/en/taxnewsflash/news/2026/10/ustr-china-section-301-actions-product-exclusion.html), [Argents](https://argents.com/section-301-tariffs-2026-guide/), [Portless](https://www.portless.com/blogs/section-301-tariffs-china).
- **US de minimis:** the $800 duty-free exemption no longer applies to Chinese goods (suspended 2025; statutory end 2027-07-01). Every parcel pays duty, and carriers or brokers may add fees. Source: [SmartAsset](https://smartasset.com/taxes/de-minimis-trump), [HQTExp](https://www.hqtexp.com/en/knowledge/us-tariff-system-2026/).
- **EU:** since 2026-07-01, a flat EUR 3 duty applies per tariff line in each parcel under EUR 150 (temporary to 2028), plus import VAT through IOSS. A further EUR 2 handling fee is proposed but not confirmed. Sources: [Politis](https://en.politis.com.cy/globe/globe-europe/974185/eu-imposes-eur3-duty-on-small-parcels-under-eur150-ending-duty-free-imports), [Air Cargo Week/Rhenus](https://aircargoweek.com/the-rhenus-group-urges-exporters-to-prepare-for-julys-eu-low-value-parcel-customs-changes/). The EU General Product Safety Regulation (GPSR) requires an EU responsible person for any consumer product.

### All candidates — hard filters, then weighted score
Score order: problem x3, demand x3, margin_room x3, repeat x2, differentiation x2, competition x2, supply x2, content x1, seasonality x1.

| # | Candidate (target price) | margin >=65% | net >=40 | IP | ship <2kg | regulated | ad policy | Weighted score | Result |
|---|---|---|---|---|---|---|---|---|---|
| 1 | Lab-created moissanite in 925 silver: studs hero 129 USD, 3mm tennis bracelet 249 USD | PASS (72-73%) | PASS | PASS (C&C patents expired; avoid "Forever One" and any "diamond" naming) | PASS (<100 g) | PASS (adult jewelry; FTC Jewelry Guides apply) | PASS | **76/95 (80%)** [4,4,5,4,3,2,5,5,4] | **SHORTLIST** |
| 2 | Custom pet portrait canvas, US print-on-demand: 16x20 at 99 USD, 12x16 at 79 USD | PASS (68-74%) | PASS | PASS (own templates; no franchise themes) | PASS (~1.3 kg packed, est.) | PASS | PASS | **69/95 (72.6%)** [4,4,3,4,3,2,5,5,3] | **SHORTLIST** |
| 3 | Mulberry silk pillowcase 22 momme, 79 USD single | PASS, thin (65.6%); a 89 USD set with eye mask comes in at 63.9% = FAIL | PASS | PASS | PASS | PASS (textile; hair/skin claims count as unverifiable claims) | PASS | 61/95 (64%) [3,4,3,3,3,2,4,3,4] | Below line, runner-up |
| 4 | Carbon-fiber pickleball paddle, 109 USD | PASS (67.6%) | PASS | PASS, needs check (core/edge patents) | PASS | PASS (USA Pickleball approval per model for tournament play) | PASS | 58/95 (61%) [3,5,3,2,2,1,4,3,4] | Below line |
| 5 | Packable puffy camping blanket, 99 USD | PASS (69.7%) | PASS | PASS | PASS (~1 kg, est.) | PASS | PASS | 53/95 (56%) [3,3,3,2,3,2,3,4,2] | Below line |
| 6 | Cashmere travel wrap, 169 USD | Borderline: 63.9% at a competitive 149 USD = FAIL; 68.2% at 169 USD | PASS | PASS | PASS | PASS (Wool Products Labeling Act) | PASS | 49/95 (52%) [3,3,2,3,2,2,3,3,2] | Below line |
| 7 | Pilates bar kit + bands | PASS | **FAIL**: market anchor 20-45 USD (Walmart 29.99, eBay 19.95-42.54) | PASS | PASS | PASS | PASS | not scored | Killed |
| 8 | Personalized name necklace (POD) | PASS | **FAIL**: retail 25-40 USD (Teelaunch benchmark) | PASS | PASS | PASS | PASS | not scored | Killed |
| 9 | Golf swing trainer | PASS | **FAIL**: top sellers 17.99 USD, top-10 average ~28 USD (ASINsight) | Risk on premium "whip" designs | PASS | PASS | PASS | not scored | Killed |
| 10 | Dog back-seat extender (hard base) | PASS | PASS (54-81 USD) | PASS | **FAIL**: rigid base, bulky, likely >2 kg packed (est.) | PASS | PASS | not scored | Killed |
| 11 | Portable cold-plunge / ice-bath tub | PASS | PASS | PASS | **FAIL**: 2-3.6 kg empty (Bubplay 3.6 kg, Titan 3 kg) | Recovery/health claims | Risk | not scored | Killed |
| 12 | Waterproof changing robe (Dryrobe-type) | PASS (est.) | PASS (GBP 90-175) | Avoid "dryrobe" (trademark) | **FAIL**: 1.3-2.35 kg adult sizes, packed >2 kg likely | PASS | PASS | not scored | Killed |
| 13 | Minimalist aluminum card wallet | PASS | PASS | **FAIL (block)**: Ridge patent litigation against look-alikes (Ridge v. Mosaic, C.D.Cal. 2:23-cv-09673; Ridge v. 2985 LLC, D.Colo.) | PASS | PASS | PASS | not scored | Killed |
| 14 | Posture corrector | PASS | PASS | PASS | PASS | **needs_owner_approval**: medical device / medical claims (excluded category) | Risk | not scored | Parked (excluded by brief) |

Evidence by candidate (not shortlisted):
- **Silk:** retail anchors Slip 85-120 USD, Blissy 79-100+, Fishers Finery 71, Mulberry Park 67-77 ([HGTV](https://www.hgtv.com/shopping/news-and-trends/best-silk-pillowcases), [Mulberry Park](https://mulberryparksilks.com/collections/22-momme-silk-pillowcases)). Blissy complaints: zipper detachment, tearing ([Kimola](https://kimola.com/reports/unlock-insights-blissy-silk-pillowcase-customer-feedback-report-amazon-en-us-145178)). Demand: "blissy" 27.1K searches +1533%, silk sleep mask 33-40K ([Exploding Topics](https://explodingtopics.com/topic/blissy?period=180)). Supply: 22 momme at 15-18 USD MOQ 100, 16.85 USD MOQ 100, 25-30 day lead time ([Global Sources](https://www.globalsources.com/Pillowcase/Silk-Pillowcases-1225640121p.htm), [Made-in-China](https://shaoxingxinlan.en.made-in-china.com/product/tZVGEvUyYnWH/China-Wholesale-Mulberry-22-25-Momme-Silk-Pillowcase.html)). US tariff est. 24.3% (HTS 6302.39.0020: MFN 4.3% + 7.5% + 12.5%; [Wove](https://tariffs.wove.com/us/tariff/6302.39.00.20)). Revisit if a 25-momme quality angle lifts price to 89+ USD.
- **Pickleball:** budget carbon paddles cluster at 99-110 USD (Vatic V-SOL Pro 109.99, often 99 or 84.99 on promo; Friday Fever 99; [MyPickleballConnect](https://mypickleballconnect.com/reviews/best-pickleball-paddles-under-150-2026/), [Slickdeals](https://slickdeals.net/f/19681164-vatic-pro-via-amazon-v-sol-pro-v7-16mm-pickleball-paddle-foam-core-includes-paddle-cover-v7-84-99)). Top 5 brands hold 52% ([GMI](https://www.gminsights.com/industry-analysis/north-america-pickleball-equipment-market)). OEM 9.90-22.90 USD MOQ 200; some MOQ 2 ([SourceReady](https://www.sourceready.com/report/detail/pickleball-racket-manufacturers-report)).
- **Puffy blanket:** Rumpl 68-135 USD, Kelty 35-55, Glorsign 34 ([CleverHiker](https://www.cleverhiker.com/camping/best-camping-blankets/), [OutdoorGearLab](https://www.outdoorgearlab.com/topics/camping-and-hiking/best-camping-blanket/ratings)). Custom US vendor 16.15-33.98 USD at MOQ 50 ([UCHANGE](https://uchangepromo.com/products/waterproof-outdoor-1-person-camping-blanket)). Factory FOB not verified.
- **Cashmere:** 34-39.60 USD at MOQ 3-50 ([Global Sources guide](https://www.globalsources.com/STM/knowledge/article/buyers-guide-sourcing-cashmere-scarves/), [Pietra](https://www.pietrastudio.com/sourcing/products/inner-mongolia-cashmere-stole-pure-mongolian)). Winter-seasonal.
- **Kills:** pilates ([ASINsight](https://www.asinsight.com/report/US/pilates-bar-kit), [Walmart](https://www.walmart.com/ip/1104410832)); necklace ([Teelaunch](https://blog.teelaunch.com/2022/11/personalized-name-necklaces)); golf ([ASINsight](https://www.asinsight.com/report/US/swing-trainer-golf)); dog extender ([Walmart Kohree](https://www.walmart.com/ip/Kohree-Dog-Car-Seat-Cover-for-Back-Seat-Bottom-Holds-400lbs-Waterproof-Dog-Hammock-for-Car-SUV-Truck/14855816430)); ice bath ([Titan](https://titanplunge.com/pages/compare-titan-model), [LIT](https://www.litmethod.com/blogs/lit-blog/how-much-does-a-cold-plunge-cost-2026-pricing-guide)); robe ([220 Triathlon](https://www.220triathlon.com/gear/swim/swim-clothing/dryrobe-alternatives), [Live for the Outdoors](https://www.livefortheoutdoors.com/camping/accessories/best-changing-robes/)); wallet ([Stanford NPE](https://npe.law.stanford.edu/node/288103), [AllTheWallets](https://www.allthewallets.com/ridge-wallet-has-patents/)).

### Shortlist (2 products; no third product reached 70%)

#### S1 — Lab-created moissanite jewelry in 925 sterling silver (score 76/95, 80%)
- **Range:** hero = 2 ct total (2 x 1 ct, 6.5 mm) D/VVS1 studs with GRA card at **129 USD**; upsell = 3 mm tennis bracelet at **249 USD**; later = solitaire pendant and tennis necklace.
- **Demand:** "moissanite earrings" 27.1K monthly searches, +92% to +317% growth ([Exploding Topics](https://explodingtopics.com/topic/moissanite-earrings?period=24)). Adamans ran Instagram tennis-chain ads from June 2025 ([Particl](https://www.particl.com/adamans/take-a-closer-look-at-this-tennis-chain-1884431-66414117)). Runtime not checked; Meta Ad Library blocked. Lab-grown share of engagement purchases rising (Knot 2026, via Alibaba, unverified).
- **Competitor stores / prices:**
  1. Adamans (Shopify, adamans.com): 925 studs 89-149.99 USD; 3 mm silver tennis chain from 349.99 USD, shown against "compare at" 555.99 ([Adamans](https://adamans.com/products/3mm-moissanite-tennis-chain-14k-white-gold-d-colour-vvs1)).
  2. Vianne Jewellery (Shopify, velvetrose.it.com): silver moissanite tennis bracelet GBP 139 ([listing](https://velvetrose.it.com/products/moissanite-bracelet-in-sterling-silver.oembed)).
  3. Charles & Colvard: 2.18 ctw silver tennis necklace 299.25 USD (Walmart); Mimi & Max 12.5 ct silver tennis necklace 293 USD ([Walmart](https://www.walmart.com/ip/Charles-Colvard-Sterling-Silver-1-6mm-Round-Moissanite-Tennis-Necklace-2-18cttw-DEW/5301599389), [Aureus](https://www.aureusboutique.com/products/ss005-43279-mimi-max-12-1-2ct-dew-created-moissanite-tennis-necklace-in-sterling-silver)).
- **Suppliers (asking prices from search snippets; not quotes):**
  - Wuzhou Goldleaf ("Golfleaf"), Alibaba: D VVS1 925 tennis bracelet ~49.26 USD, MOQ 1 ([Alibaba](https://www.alibaba.com/product-detail/Golfleaf-925-Sterling-Silver-Moissanite-Bracelets_1601212476916.html)).
  - Wuzhou Zuanfu, Alibaba: 3/4/5 mm tennis bracelet ~40.99 USD, MOQ 1 chain ([Alibaba](https://www.alibaba.com/product-detail/Fashion-Jewelry-tennis-bracelet-D-VVS_1600963623467.html)).
  - Saidiwei Jewelry, Alibaba: 2/3 mm D VVS1 GRA bracelet ~53 USD, MOQ 1 ([Alibaba](https://www.alibaba.com/product-detail/Valentines-Gift-Moissanite-Tennis-925-Silver_1601356309111.html)).
  - Studs: GRA D VVS1 925 studs retail from Chinese sellers at 28.11 USD (Holycome) and 41.92 USD (2 ct halo) ([eBay](https://www.ebay.de/itm/396631534090)). A factory price of 15-25 USD per pair is a scout estimate; no Alibaba stud listing was readable.
  - Lead time: not verified. Est. 3-7 days production + 7-12 days to the US by a DDP line.
- **MOQ cash needed:** ~0 inventory (MOQ 1, dropship through a sourcing agent). Samples from 2 suppliers x 2 SKUs about 150-250 USD (est.), R3 for ops/Owner.
- **US import / regulatory:** HTS 7113.11.5000 (silver jewelry). MFN 5% + List 4A 7.5% (CBP ruling cites 9903.88.15) + 12.5% = **~25% (est.)**; aggregators show 15-22.5% ([Wove](https://tariffs.wove.com/us/tariff/7113.11.50.00)). Rules that apply:
  - FTC Jewelry Guides (16 CFR 23): always say "lab-created moissanite". Never "diamond" without an immediately preceding qualifier, no #diamond, and do not use the "passes diamond tester" claim ([FTC](https://www.ftc.gov/business-guidance/resources/loupe-advertising-diamond-gemstones-pearls)).
  - National Gold and Silver Stamping Act: a "925" mark must be accurate and carry a registered trademark of the marker.
  - California Prop 65 (lead/cadmium): request supplier test reports.
  - Adult positioning only; children's jewelry is an excluded category.
- **EU:** HTS 7113 duty ~2.5% (est.) + EUR 3 per tariff line + VAT 19-25% in the price. REACH nickel release limits (stricter for piercing posts), cadmium and lead limits. Compulsory hallmarking in several states (e.g. IE, NL; not verified). GPSR responsible person needed.
- **Market:** **US first.** Moissanite awareness is highest and competitors are proven in USD (Adamans, C&C). English only. Margin holds after the 25% tariff. **EU alternative: Germany** (largest EU e-commerce market; not on the scout's list of compulsory-hallmark states, to verify). Needs a German store, VAT/IOSS, a GPSR representative and nickel test reports.
- **IP check:** Charles & Colvard moissanite patents expired (2015, from memory, est.). Avoid C&C trademarks ("Forever One") and Adamans product photos. Use our own photography. No conflict found.
- **Recommended retail:** studs 129 USD; tennis bracelet 249 USD. Use only real compare-at prices (guardrail).
- **Creative angle hypothesis:** "Real sparkle you can afford to wear every day." The 15-second demo: a 6.5 mm stud under window light and a phone flashlight throwing rainbow fire. Then a close-up of the GRA card. Then an on-screen "Lab-created moissanite, 925 silver, 129 USD". Audiences: women 25-45 buying for themselves, plus partners buying gifts (Q4 and Valentine's). Hooks to test: "The earrings everyone asks about", "Same sparkle, no mined-diamond guilt" (needs a substantiation check), and a gift-box unboxing. No tester-beep videos and no diamond-equivalence claims.
- **Open questions:**
  1. Real FOB price and lead time for studs; whether GRA cards can be checked against the GRA lab database.
  2. Nickel content under the rhodium plating; Prop 65 / REACH test reports.
  3. Can an agent quality-check stones and send DDP to the US at the estimated 6.5 USD?
  4. Confirm HTS line and List 4A status with a broker.
  5. Return rate for jewelry (assumed 5-8%, est.).

#### S2 — Custom pet portrait on canvas, US print-on-demand (score 69/95, 72.6%)
- **Range:** customer uploads a pet photo, we render a portrait in one of our own style templates (AI generation + human QC), customer approves a preview, a US POD partner prints and ships. **12x16 at 79 USD; 16x20 at 99 USD (hero); two pets 16x20 at 129 USD.**
- **Demand:** tracked custom-pet-art retailers made ~30M USD online in 2025, up 20-50% YoY. The same tracker forecasts -20 to -50% for 2026, and revenue drops 86% from Nov to Apr ([Grips](https://gripsintelligence.com/insights/industries/animals-pet-supplies/custom-pet-art-and-merchandise)). ~40% of POD revenue comes in Q4 ([Merchize](https://merchize.com/print-on-demand-seasonal-products/)), and the Q4 window is now. Ad runtimes not checked (Meta Ad Library blocked).
- **Competitor stores / prices:**
  1. West & Willow (Shopify): one pet 77 USD (from 105), two pets 121 USD (from 160) ([one pet](https://westandwillow.com/products/custom-one-pet-portrait), [two pets](https://westandwillow.com/products/custom-two-pet-portrait)).
  2. Crown & Paw: costume portraits from 49.95 USD on sale (59.95) ([Apartment Therapy](https://www.apartmenttherapy.com/crown-and-paw-pet-portraits-36805381), [Dogster](https://www.dogster.com/lifestyle/crown-paw-pet-portraits-review/)).
  3. My Pet Canvas / Pet Customs (Shopify DTC, [parse.gl](https://parse.gl/brands/mypetcanvas-com)), prices not readable; category range 40-200 USD ([Hepper](https://www.hepper.com/best-pet-portraits/)).
- **Suppliers (all US production, MOQ 1, no inventory):**
  - Printify canvas: from 10.87-12.05 USD (smallest size, Premium plan); 16x20 production 15-22 USD per Merch Titans ([Printify](https://printify.com/custom-canvas-prints), [PodVector](https://podvector.ai/articles/print-on-demand/costs-and-suppliers/canvas-on-demand-canvas-print-quality-and-pricing)).
  - MyDesigns / District Photo: 16x20 gallery wrap 20.40-22.10 USD, ~3-day production ([MyDesigns](https://mydesigns.io/product-catalog/canvas/product/canvas-gallery-wrap-16-20)).
  - Gelato: local production in US and EU (for the EU option). Canvas price not readable.
  - Lead time: 2-5 days production + 3-5 days US shipping (est.).
- **MOQ cash needed:** 0 inventory. 2-3 sample canvases about 100 USD (est.). AI image tool subscription about 20-40 USD per month (est.).
- **US import / regulatory:** printed and shipped inside the US, so **no import tariff** and no de minimis exposure. No product-category regulation. FTC rules on shipping times apply: Q4 cut-off dates must be real (guardrail: no fake urgency).
- **EU:** Gelato prints locally, so no customs and no EUR 3 duty. VAT OSS registration needed. Personalised goods are exempt from the 14-day withdrawal right (Consumer Rights Directive art. 16(c), from memory, verify). GPSR responsible person needed (est.: Gelato may cover it, unverified).
- **Market:** **US first.** Q4 gift season is now, US POD needs no import, and English only. **EU alternative: Germany or the Netherlands** through Gelato local print, as a second market in 2027.
- **IP check:**
  - Use only our own style templates. No franchise themes (some competitors sell Star Wars / Harry Potter / Peaky Blinders pets; that is copyright and trademark risk).
  - Do not copy Crown & Paw costume artwork.
  - Customer photos: customer warrants rights in the upload terms. Refuse photos showing people (guardrail on images of real people).
  - Check that the AI tool's licence allows commercial use.
- **Recommended retail:** 99 USD (16x20) hero; 79 USD (12x16); 129 USD (two pets).
- **Creative angle hypothesis:** "Your dog, as royalty." In 3 seconds: the phone photo of a scruffy dog morphs into the finished canvas, then real gift-reveal reactions (our own customers only, with consent). Offer: "See your preview before you pay" removes the main risk. A Christmas cut-off date that is real and shown honestly. Audiences: pet parents 25-55 and gift-buyers for them; also a memorial angle (handle with care in copy).
- **Open questions / risks:**
  1. Ops load: every order needs an art step and a customer proof. Can a preview-before-checkout app automate this within the Owner's 7 h/week?
  2. Remake rate for unhappy customers (est. 5-10%).
  3. Canvas damage in transit.
  4. Strong Q4 skew: Jan-Apr revenue may fall 80%+.
  5. The Grips 2026 decline forecast.
  6. Exact Printify 16x20 and shipping price; confirm in the catalog once an account exists (R3, Owner).

### Cost inputs for finance (V4) — ALL VALUES ARE ESTIMATES, unverified with suppliers or a broker
| Product / SKU | Supplier unit cost | Est. freight per unit to customer | Est. duty/tariff | Est. packaging | Other per unit | Est. landed COGS | Recommended price | Est. gross margin |
|---|---|---|---|---|---|---|---|---|
| S1 moissanite studs 2 ctw (US) | 20.00 USD (range 15-28) | 6.50 USD (DDP line, <100 g) | ~25% of FOB = 5.00 USD (HTS 7113.11.5000) | 2.50 USD (box, pouch, GRA card) | 1.00 USD brokerage/handling | **35.00 USD** | **129 USD** | **72.9%** |
| S1 moissanite tennis bracelet 3 mm (US) | 47.00 USD (range 40.99-53) | 6.50 USD | ~25% = 11.75 USD | 2.50 USD | 1.00 USD | **68.75 USD** | **249 USD** | **72.4%** |
| S2 pet portrait 16x20 canvas (US) | 20.00 USD print (range 15-22.10) | 9.00 USD US POD shipping | 0% (US-made) | 0 (included by POD) | 2.00 USD art generation + QC | **31.00 USD** | **99 USD** | **68.7%** |
| S2 pet portrait 12x16 canvas (US) | 15.00 USD | 8.00 USD | 0% | 0 | 2.00 USD | **25.00 USD** | **79 USD** | **68.4%** |
| S2 two-pet 16x20 canvas (US) | 22.00 USD | 9.00 USD | 0% | 0 | 3.00 USD | **34.00 USD** | **129 USD** | **73.6%** |
Margins are before payment fees, returns and ads (gross_margin per `playbook/unit-economics.md`). Finance should stress-test moissanite at a 42.5% tariff (if List 3 at 25% applies instead of 4A), which gives ~72 USD landed for the bracelet (~71%) and ~38.50 USD for the studs (~70%). EU versions: deduct VAT from the price and add EUR 3 duty per line (moissanite).

**Decision requested (R3, Owner):** go / kill / iterate on S1 and S2 so ops can request quotes and samples (V3, R3) and finance can build V4. Scout's recommendation:
- **S1 moissanite** first: highest score, widest margin room, no-inventory dropship.
- **S2 pet portraits** as the Q4 quick test: zero import risk, but heavy on operations.
**Linked:** none yet (no ACT/EXP opened).
