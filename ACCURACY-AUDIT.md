# Accuracy Audit & Source Trace
**File:** ACCURACY-AUDIT.md
**Generated:** 2026-04-27
**Purpose:** Catalogue every known accuracy risk in this benchmarking, map every headline figure to its primary source, and document derivation logic for every computed metric. This file is the rigour layer — read it before quoting any number.

---

## Part 1 — Failure modes that affect accuracy

Beyond the **URL-discovery failure** already discussed (agent gave up at 404/403 on guessed AAL URLs instead of crawling the corporate annual-reports landing page), the following risks remain and SHOULD be considered when quoting any figure from this report.

### F1 · Incomplete in-PDF extraction (high impact)
**What happened:** When the data-collector agent retrieved the AAL FY24 annual financial report, it pulled the directors' summary and noted "A$74m capex commitments" from a notes section, but never drilled to the cash-flow statement (p.17 of that PDF) where the actual A$106.83m FY24 CAPEX line lives. The figure was sitting in a PDF already on the agent's disk.
**Mitigation:** Re-extracted in 2026-04-27 enrichment pass. Now corrected.
**Residual risk:** Other PDFs may have similar unread sections — particularly the QAL annual reports, where aero/non-aero split and CAPEX line are likely present but not extracted. **Recommend:** systematic re-read of every retrieved PDF's cash-flow statement and revenue note before publishing.

### F2 · WebFetch 10MB size limit treated as "data not available" (high impact)
**What happened:** Hobart Master Plan 2022 (>10MB), ADG White Paper submission (>10MB), AAL Integrated Review FY22 (16.1MB) all flagged as "could not access." The same agent successfully used `curl` + local `pypdf` parsing for Productivity Commission submissions but didn't apply that workaround to oversized corporate PDFs.
**Mitigation:** AAL FY22 Integrated Review unblocked when user supplied the file. Others remain not retrieved.
**Residual risk:** HBA Master Plan probably contains 10–20-year CAPEX schedule and traffic forecasts that would refine the "~A$350m disclosed program" figure.

### F3 · Pax denominator inconsistency across cohort (high impact)
**Issue:** Different airports use different passenger denominators across the report:
- **PER:** ACCC pax (incl FIFO charter) — FY24: 16.14m
- **SYD/MEL/BNE:** ACCC pax — corresponds to ACCC financial scope
- **ADL:** BITRE RPT pax (8.25m FY24) used in ratios; AAL Integrated Report cites 8.54m FY24 (incl transit/transfer/GA) — 3.5% gap
- **QAL group:** group-level pax (8.34m FY24, 4 airports consolidated) used against group financials
- **OOL standalone:** BITRE 6.32m FY24 — not used in any ratio
**Implication:** Cross-airport ratios are NOT strictly comparable. If you compare PER's A$23 OPEX/pax to ADL's A$13, part of the gap is denominator (FIFO inclusion at PER, transit exclusion at ADL).
**Recommend:** For any future comparison, restate every airport on a single denominator (e.g., BITRE RPT only) and show both views side-by-side.

### F4 · EBITDA definition drift (high impact)
**Issue:** "EBITDA" means three different things across cohort:
- **ACCC-4 (SYD/MEL/BNE/PER):** "operating profit excluding landfill" from ACCC supplementary database — pre-D&A operating result on regulated-account scope
- **ADL:** "underlying EBITDA" from AAL P&L — strips fair-value gain on investment properties (A$41.6m FY24, A$67.6m FY25); statutory AAL EBITDA line is materially higher
- **QAL group:** group EBITDA from QAL annual report — includes property/development gains and consolidates 4 airports
**Implication:** The league-table EBITDA-margin column mixes scopes. ADL's 60.9% FY24 and QAL's 67.6% are not directly comparable to SYD's 57.1%, despite all being labelled "EBITDA margin."
**Mitigation:** This is now flagged in the league-table footnote. Best practice: report EBITDA/pax (less scope-sensitive than margin) for cross-airport comparisons.

### F5 · Revenue scope difference (medium impact)
**Issue:** ACCC monitoring captures revenue from **regulated services** (aeronautical + commercial activities on the regulated airport site). AAL/QAL/private-airport corporate accounts capture **all entity revenue**, which may include non-airport property businesses (Capital Property Group at CBR explicitly mixes airport + adjacent property; QAL group consolidates four airports + various JVs).
**Implication:** Revenue-denominator ratios (CAPEX/rev, OPEX/rev, EBITDA margin) are not strictly comparable across regulated and unregulated airports.
**No clean mitigation** without segment reporting that most private airports don't publish.

### F6 · Nominal vs real terms (medium impact)
**Issue:** All figures are AUD nominal. ABS CPI cumulative growth was approximately:
- FY20–FY24: ~18%
- FY20–FY25: ~22%
- FY22–FY25: ~12%
**Implication:** ADL's "5.4× CAPEX ramp FY22→FY25" includes ~12% CPI; real-terms ramp is approximately 4.8×. Multi-year averages crossing the pandemic conflate cyclical recovery with inflation.
**Recommend:** For multi-year analysis, restate to common-base year using ABS CPI.

### F7 · 5-year averages — computation method not always specified (medium impact)
**Issue:** "5-year cumulative average" appears multiple places (e.g., 5y CAPEX/pax). Not always clear whether this is:
- Sum of 5 years' CAPEX ÷ sum of 5 years' pax (cumulative-weighted) — what the analyst actually used
- Arithmetic mean of 5 annual ratios (simple average) — different result
**Implication:** The two methods can differ by ~10–20% for COVID-distorted series.
**Verified for ADL FY22–FY25:** Used cumulative-weighted (sum of CAPEX / sum of pax across 4 years) where stated as "cumulative."

### F8 · Outlier-flag medians not always recomputed when cohort changed (medium impact)
**Issue:** Original league table median CAPEX/pax was A$13.5 (ACCC-4 only, n=4). When ADL was added, median should drop to A$11.5 (n=5). The HTML league-table footnote was updated but earlier-section narrative (e.g., §1 Executive view: "MEL CAPEX/pax 1.70× median") still references the old median ratios.
**Recommend:** Treat all "× median" claims as approximations; recompute against current cohort-of-disclosure before quoting.

### F9 · Soft / aspirational narrative figures treated as hard (medium impact)
**Issue:** Several headline figures are program-totals or aspirational targets, not committed/audited spend:
- HBA "~A$350m+ disclosed program" — sum of named projects, some still in planning
- ADL "A$1bn 10-year program" — Integrated Review FY22 wording: *"ambitious infrastructure program for the next decade with an indicative value of approximately $1 billion"* — explicitly indicative, not committed
- CBR "A$3bn+ since 1998" — Capital Property Group corporate marketing claim, includes adjacent commercial property not strictly airport CAPEX
- CNS "A$1bn redevelopment" — Land Use Plan vision, not committed CAPEX
**Mitigation:** These are flagged in REPORT §3.1 as "program totals" but the executive summary doesn't always carry the caveat.

### F10 · Year-boundary ambiguity (low impact, real)
**Issue:** "FY24" in this report = year ended 30 Jun 2024 (Australian convention). ACCC labels the same period as "2023-24." BITRE annual file uses FY labels. Calendar-year sources (some news articles, NAIF press releases) sometimes refer to "2024" meaning calendar 2024. Where ratios use calendar-year pax against fiscal-year financials, error of up to ~5% can creep in.
**Verified clean for:** ACCC + BITRE FY-aligned figures throughout the report.

### F11 · Discrepancy reconciliation incomplete (medium impact)
**Issue:** Where multiple sources publish the same figure, discrepancies were flagged in the data-collector summary but not always reflected per-cell in the raw-data tables:
- **Perth FY24 pax:** ACCC 16.14m vs BITRE 12.79m (26% gap, FIFO inclusion). PER ratios use ACCC; gap not footnoted on every cell.
- **Sydney FY24 pax:** ACCC vs BITRE differ by ~0.1% (rounding).
- **Adelaide FY24 pax:** AAL 8.54m vs BITRE 8.25m (3.5% gap). ADL ratios use BITRE.
- **Brisbane FY24 ATMs:** ACCC 222.5k vs BITRE RPT 188k. ACCC scope used for OPEX/movement.
**Mitigation:** Documented in §7 Methodology, but not annotated cell-by-cell.

### F12 · Tertiary sources embedded (low impact)
**Issue:** Some capacity figures (runway counts, terminal floor area) come from Wikipedia. Marked `(tertiary; please verify)` in raw-data file, but the figures still propagate into the report.
**Recommend:** For any quoted runway-count or terminal-m² figure, cross-check against the airport's own Master Plan before publishing externally.

### F13 · PDF text-extraction errors not QA'd (low-medium impact)
**Issue:** `pypdf` extraction can misread tables — column alignment errors, en-dash misread as minus sign, parentheses around negative numbers stripped. Each of the four AAL PDFs was extracted via pypdf without a second-eye QA against the original PDF.
**Sample verification done:** SYD FY24 EBITDA spot-checked at A$1,083.83m (ACCC operating-profit-excl-landfill) — matches; ADL FY24 CAPEX spot-checked at A$106.829m — matches PDF p.17 text "Payments for property, plant and equipment, intangible assets and investment properties (106,829)".
**Residual risk:** ~2–3 figures across 200+ data points may have extraction errors. **Highest-impact figures (CAPEX, revenue, EBITDA, total assets) have been spot-checked.**

### F14 · One-off items not consistently normalised (medium impact)
**Issue:** Several years had unusual items that distort comparisons:
- **FY21 (all airports):** JobKeeper subsidy receipts inflated underlying results
- **FY21 ADL:** Recovery of Virgin Australia debt provisions (~A$3.5m)
- **FY21 ADL:** JobKeeper receipts (~A$3.8m)
- **SYD FY24:** A$9.6bn one-off non-cash unitholder distribution (statutory line; report uses ACCC operating profit instead)
- **ADL FY22, FY24, FY25:** A$48.5m / A$41.6m / A$67.6m fair-value gains on investment properties (report uses underlying EBITDA excl these)
**Mitigation:** Major items flagged. Smaller items (JobKeeper, debt-recovery) not normalised in cohort-level ratios.

### F15 · Source-document chain of custody not verified (low impact for research, high for legal use)
**Issue:** AAL PDFs supplied via user's local Desktop. Filenames suggest agency/print-shop origin (NJ01710, NJ01810). Auditor signatures (KPMG / EY / etc.) within the PDFs were noted in passing but not formally verified against AAL's announced auditor for each year.
**Recommend:** For any external publication, re-fetch the same PDFs from `corporate.adelaideairport.com.au` directly to confirm authenticity.

### F16 · Snippet-based extraction (low impact, flagged)
**Issue:** Several minister.infrastructure.gov.au press releases timed out on direct WebFetch and were captured via WebSearch result snippets instead. Snippets show the headline figures (e.g., "A$130m runway", "A$60m Cwlth funding") but cannot be cross-referenced for context (date qualifier, conditional phrasing).
**Mitigation:** Each snippet-sourced figure is flagged `(via search snippet)` in sources.md.

---

## Part 2 — Source & derivation index for headline figures

Every figure cited in REPORT-2026-04-27.md or report.html should trace to one of the source codes below. **Where a figure is computed from inputs, the derivation is explicit.**

### Source codes

| Code | Source | Type |
|---|---|---|
| **S1** | ACCC Airport Monitoring Report 2023-24 supplementary database (XLSX) — sheets `SYD/MEL/BNE/PER total and aero` | Primary, audited regulatory accounts |
| **S2** | BITRE annual airport activity FY1985-86 to FY2024-25 (XLSX) | Primary, government statistics |
| **S3** | AAL Annual Financial Report 30 Jun 2024 (PDF, 58pp) | Primary, audited |
| **S4** | AAL Annual Financial Report 30 Jun 2025 (PDF, 57pp) | Primary, audited |
| **S5** | AAL Annual Financial Report 30 Jun 2023 (PDF, 57pp; user-supplied 2026-04-27) | Primary, audited |
| **S6** | AAL Integrated Review 2022 (PDF, 89pp; user-supplied 2026-04-27) | Primary narrative + summary financials |
| **S7** | QAL Annual Reports FY20–FY24 (group-level) | Primary, audited (group not standalone) |
| **S8** | NAIF North Queensland Airports project page (naif.gov.au) | Primary government disclosure |
| **S9** | Hobart Airport project pages (projects.hobartairport.com.au) | Primary corporate |
| **S10** | Capital Property Group corporate "About Us" (capitalpropertygroup.com.au) | Primary corporate disclosure |
| **S11** | Productivity Commission inquiry submissions (assets.pc.gov.au) — sub031 HBA, sub008 NTA, sub049 NQA, sub056 CBR | Primary submission |
| **S12** | DIA 2023 Master Plan Preliminary Draft Sep 2023 (PDF) | Primary corporate |
| **S13** | Department of Defence press release 13 Aug 2023 | Primary, secondary fetch via search snippet |
| **S14** | Palisade Investment Partners press release | Primary corporate (DIA shareholder) |
| **S15** | Australian Aviation / Tasmanian Times news coverage | Secondary news |
| **S16** | Wikipedia (capacity facts only) | Tertiary |
| **S17** | Minister Catherine King / Madeleine King press releases | Primary government, captured via snippet |

### Derivation codes

| Code | Meaning |
|---|---|
| **D1** | Direct read from primary source (no computation) |
| **D2** | Ratio: Numerator ÷ Denominator (both from primary; no estimation) |
| **D3** | Sum of components (e.g., total OPEX = sum of P&L expense lines) |
| **D4** | Year-over-year derivation (e.g., FY21 revenue = FY22 revenue minus disclosed YoY change) |
| **D5** | Cohort statistic (median, range, % of median) |
| **D6** | Indicative / aspirational corporate disclosure (NOT audited) |

### Per-figure trace — League Table FY24 (REPORT §6, HTML §2)

| Cell | Value | Source | Derivation | Notes |
|---|---|---|---|---|
| SYD CAPEX/pax FY24 | 7 | S1 | D2: 277.83 / 40.53 = 6.85 → 7 | CAPEX from ACCC supp DB; pax = ACCC scope incl ~16% int'l |
| SYD OPEX/pax FY24 | 20 | S1 | D2: ~813 / 40.53 = 20.1 → 20 | OPEX = ACCC "total airport operating expenses" |
| SYD aero rev/pax FY24 | 29 | S1 | D2 OR D1: A$29.36 published directly in supp DB | Exactly matches derived |
| SYD EBITDA margin FY24 | 57.1% | S1 | D2: 1,083.83 / 1,898 = 57.1% | EBITDA = ACCC "operating profit excl landfill"; NOT statutory (statutory has A$9.6bn one-off) — see F14 |
| SYD CAPEX/rev FY24 | 14.6% | S1 | D2: 277.83 / 1,898 = 14.6% | |
| MEL CAPEX/pax FY24 | 23 | S1 | D2: 812.88 / 35.14 = 23.13 → 23 | |
| MEL CAPEX/rev FY24 | 68.2% | S1 | D2: 812.88 / 1,192 = 68.2% | |
| MEL EBITDA margin FY24 | 49.6% | S1 | D2 | |
| BNE CAPEX/pax FY24 | 10 | S1 | D2: 237.92 / 24.08 = 9.88 → 10 | |
| BNE OPEX/movement FY24 | 1,855 | S1 | D2: ~412.6m / 222.5k movements | ACCC ATM scope (incl military/GA), not BITRE RPT (188k) — see F11 |
| BNE EBITDA margin FY24 | 57.8% | S1 | D2: 566.42 / 979.14 = 57.85% | |
| PER CAPEX/pax FY24 | 17 | S1 | D2: 281 / 16.14 = 17.4 → 17 | Pax = ACCC incl FIFO; BITRE RPT-only is 12.79m (would give A$22) — see F3 |
| PER OPEX/pax FY24 | 23 | S1 | D2: 378 / 16.14 = 23.4 → 23 | Same denominator caveat |
| PER EBITDA margin FY24 | 43.2% | S1 | D2 | |
| **ADL CAPEX/pax FY24** | **13** | **S3** | **D2: 106.829 / 8.25 = 12.95 → 13** | CAPEX from AAL FY24 cash flow statement p.17; pax from BITRE — see F3 (mixed denominator vs ACCC-4) |
| **ADL CAPEX/rev FY24** | **37.5%** | **S3** | **D2: 106.829 / 284.610 = 37.5%** | |
| **ADL OPEX/pax FY24** | **13** | **S3** | **D2: 111.241 / 8.25 = 13.5 → 13** | OPEX = sum of 7 P&L expense lines (D3); see source map below |
| **ADL aero rev/pax FY24** | **17** | **S3** | **D2: 136.972 / 8.25 = 16.6 → 17** | |
| **ADL EBITDA margin FY24** | **60.9%** | **S3** | **D2: 173.4 / 284.610 = 60.9%** | EBITDA = underlying (excl A$41.6m FV gain); statutory would give 75.5% — see F4 |
| **ADL CAPEX/pax FY25** | **24** | **S4** | **D2: 208.718 / ~8.6** | **WARNING:** FY25 BITRE pax not yet retrieved; A$24 uses estimated pax denominator. Audited CAPEX figure A$208.718m is verified. **Recommend:** re-derive once BITRE FY25 published. |
| **ADL CAPEX/rev FY25** | **65.6%** | **S4** | **D2: 208.718 / 318.206 = 65.59%** | Both numerator and denominator audited |
| QAL OPEX/pax FY24 | 8 | S7 | D2: ~64 / 8.34 (group pax) | NOT comparable to ACCC-4 — see F3, F4, F5 |
| QAL EBITDA margin FY24 | 67.6% | S7 | D2 | Group-level (4 airports), includes property gains — see F4 |
| Median CAPEX/pax FY24 (n=4) | 13.5 | derived | D5 | Original 4-airport cohort; new 5-airport median (incl ADL) is 11.5 — see F8 |
| Median CAPEX/rev FY24 (n=4) | 33.3% | derived | D5 | Same caveat |

### Per-figure trace — ADL P&L breakdown (the new data)

ADL OPEX FY24 = A$111.241m derived as **D3** sum:
- Employee benefits expense: 24,464 (S3 p.14)
- Services & utilities: 61,690
- Consultants & advisors: 2,886
- General administration: 11,178
- Increase of expected credit loss: 1,929
- Leasing & maintenance: 8,967
- (Loss)/Gain on disposal of PP&E: 127 (loss)
- **Sum: A$111,241k = A$111.2m**

ADL Revenue FY24 = A$284.610m direct read (S3 p.14, Note 5)
- Aeronautical: 136,972
- Commercial trading: 32,338
- Property: 68,989
- Car parking: 37,462
- Other: 8,849

ADL EBITDA underlying FY24 = A$173.4m direct read (S3 p.4 Directors' Report)
- AAL P&L statutory EBITDA line: 215,004 (S3 p.14)
- Less: changes in fair value of investment properties: 41,576 (S3 p.14, Note 9)
- = A$173,428k underlying

ADL CAPEX FY24 = A$106.829m direct read (S3 p.17)
- Cash flow statement line: "Payments for property, plant and equipment, intangible assets and investment properties (106,829)"
- Note: includes intangibles + investment property as well as PP&E — wider scope than ACCC's "asset additions" line; see F5

### Per-figure trace — ADL Build-Cycle headline ("5.4× ramp FY22→FY25")

| Year | CAPEX (A$m) | Source | Source detail |
|---|---|---|---|
| FY22 | 38.650 | S5 | Cash flow statement, comparative column in FY23 PDF p.16 |
| FY23 | 39.541 | S5 | Cash flow statement, FY23 PDF p.16 |
| FY24 | 106.829 | S3 | Cash flow statement, FY24 PDF p.17 |
| FY25 | 208.718 | S4 | Cash flow statement, FY25 PDF p.17 |

**Derivation: 5.4× = 208.718 / 38.650 = 5.40** (D2)

**Caveat (F6):** FY22→FY25 nominal; CPI growth FY22-FY25 ~12%, so real ramp ~4.8×.

**Caveat (F9):** "A$1bn 10-year program" — quote from AAL Integrated Review FY22 p.8 reads *"ambitious infrastructure program for the next decade with an indicative value of approximately $1 billion"* (S6). Word "indicative" matters — this is a planning intent, not a Board-committed CAPEX commitment.

### Per-figure trace — Disclosed CAPEX programs (REPORT §3.1, HTML §5)

| Claim | Figure | Source | Type |
|---|---|---|---|
| HBA total program | ~A$350m+ | S9 | D3 sum of 4 named projects (130 runway + 200 terminal + 20 carparks + 25 Cambridge MDP); D6 caveat — projects in different lifecycle stages |
| HBA runway | A$130m | S9 + S15 + S17 | D1 from project page; corroborated by min press release + Australian Aviation |
| HBA federal co-fund | A$60m | S17 | D1 from minister press release; via search snippet (F16) |
| HBA terminal | A$200m | S9 | D1 from project page |
| CBR cumulative since 1998 | A$3bn+ | S10 | D6 — corporate marketing claim, includes adjacent property; PC sub056 (S11) cited A$2bn as of 2018 |
| CBR terminal 2014 | A$480m | S11 | D1 — PC sub056 p.5; corporate disclosure cites A$550m, possibly different scope |
| CBR FY07-13 CAPEX/rev | 1.24× | S11 | D1 — PC sub056 p.~6 verbatim |
| DRW runway | A$200m | S13 | D1 — Defence press release; via search snippet (F16) |
| DRW current cycle | ~A$300–400m | derived | D3 sum of named items (200 runway + 30 hotel + 60 diesel + 11 terminal + 7.5 chiller + historical 75 + 100); D6 caveat — sums across decades, mixed funding sources |
| CNS T1 + EAP | ~A$115m | S8 + cairnsairport.com.au | D3 sum (55 + 60) |
| CNS NAIF facility | A$155m | S8 | D1 — concessional loan facility, max draw, shared with Mackay |
| CNS A$1bn vision | A$1bn | busyatwork.com.au | D6 — Land Use Plan vision approved Mar 2025; long-horizon, not committed CAPEX |

---

## Part 3 — What's NOT in the audited per-FY framework

Things treated as data points in the report but which are NOT directly comparable per-FY audited figures:

1. **HBA / CBR / DRW / CNS audited annual CAPEX** — not publicly disclosed; only program totals available
2. **OOL standalone P&L** — only QAL group available
3. **ADL FY20** — pre-COVID year; not in any of the four user-supplied PDFs; would require AAL FY20 standalone or FY21 standalone with comparatives
4. **ADL FY21** — only narrative-derived from FY22 Integrated Review (revenue A$115.8m, underlying EBITDA A$67.8m, net loss A$18.7m) — not audited; ADL FY21 standalone Annual Financial Report would be authoritative
5. **All FTE / headcount data** — not consistently disclosed
6. **CAPEX-by-purpose split** — capacity / maintenance / commercial — not in any audited statement
7. **International peer figures** (Auckland, Changi) — not in scope of this pass

---

## Part 4 — How to use this audit

- **Before quoting any figure externally**, look it up in Part 2 source/derivation index to know exactly what it represents and what its scope is.
- **Treat all "× cohort median" claims** as approximations; medians shifted when ADL was added.
- **Treat all program totals** (HBA A$350m, ADL A$1bn, CBR A$3bn) as **indicative** disclosures, not audited per-FY CAPEX.
- **For real-terms comparisons across multiple years**, restate using ABS CPI before quoting.
- **For cross-airport ratios**, footnote the denominator scope (ACCC pax / BITRE pax / corporate-reported pax).

The strongest figures in this report are the **ACCC supplementary database series for SYD/MEL/BNE/PER FY20–FY24** (audited regulatory accounts) and the **AAL FY22–FY25 cash-flow statement CAPEX line** (audited per AASB Tier 2). Everything else carries one or more of the caveats above.
