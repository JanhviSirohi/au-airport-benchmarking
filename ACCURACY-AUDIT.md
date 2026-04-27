# Accuracy Audit & Source Trace
**File:** ACCURACY-AUDIT.md
**Date:** 2026-04-27
**Purpose:** Catalogue every methodological caveat in this benchmarking, map every headline figure to its primary source, and document derivation logic for every computed metric. This file is the rigour layer — read it before quoting any number.

The interactive companion to this document is [audit.html](audit.html), which presents the same content as filterable cards with cross-references between claims (C001–C022), sources (S1–S17), and risks (F1–F16).

---

## Part 1 — Methodological caveats (F1–F16)

### F1 · PDF extraction completeness · medium impact
For audited financial reports, the cash-flow statement line "Payments for property, plant and equipment, intangible assets and investment properties" is the authoritative CAPEX figure — distinct from "capital commitments" disclosed in the notes (forward-looking, not actual outlay). For every primary-source PDF, the cash-flow statement and revenue note are read in full and reconciled against summary tables in the directors' report. **Residual:** QAL group annual reports may contain aero/non-aero split and CAPEX detail in notes not in scope of this pass.

### F2 · Source-document size considerations · medium impact
Large primary PDFs (>10 MB) — including the HBA Master Plan 2022 and the ADG Aviation Green Paper submission of November 2023 — require local extraction tooling rather than browser-style fetch. AAL Integrated Review FY22 (16 MB) was extracted in full. The HBA Master Plan 2022 is not yet extracted; the HBA program-total figure (C005) is sourced from per-project pages and ministerial press releases. Full master plan extraction would refine this figure and unlock a 10-year CAPEX schedule.

### F3 · Pax denominator scope · high impact
Different airports use different passenger denominators in their per-pax ratios.

| Airport | Denominator used | FY24 figure | Notes |
|---|---|---|---|
| PER | ACCC pax (incl FIFO charter) | 16.14 m | BITRE RPT-only is 12.79 m |
| SYD/MEL/BNE | ACCC pax (matches financial scope) | varies | ACCC and BITRE differ marginally |
| ADL | BITRE RPT pax | 8.25 m | AAL itself reports 8.54 m incl transit/transfer |
| QAL group | Group pax (4 airports consolidated) | 8.34 m | Gold Coast standalone is 6.32 m (BITRE) |

**Implication:** Cross-airport per-pax ratios reflect different denominator scopes. PER's A$23 OPEX/pax vs ADL's A$13 includes a denominator effect distinct from real cost difference.

### F4 · EBITDA definition · high impact
"EBITDA" is a scope-distinct measure across the cohort:
- **ACCC-4 (SYD/MEL/BNE/PER):** "operating profit excluding landfill" from the ACCC supplementary database — pre-D&A operating result on regulated-account scope
- **ADL:** "underlying EBITDA" from AAL P&L — strips fair-value gain on investment properties (A$41.6 m FY24, A$67.6 m FY25); statutory AAL EBITDA is materially higher
- **QAL group:** group EBITDA from QAL annual report — includes property/development gains; consolidates four airports

**Implication:** EBITDA-margin comparisons across the cohort require this scope context. EBITDA/pax (less scope-sensitive than margin) is the recommended cross-airport comparator.

### F5 · Revenue scope · medium impact
ACCC monitoring captures revenue from regulated services (aeronautical + commercial activities on the regulated airport site). AAL/QAL/private-airport corporate accounts capture entity-wide revenue, which may include non-airport property (Capital Property Group at CBR explicitly mixes airport and adjacent property; QAL group consolidates four airports plus various JVs). Revenue-denominator ratios (CAPEX/rev, OPEX/rev, EBITDA margin) are not strictly comparable across regulated and unregulated airports.

### F6 · Nominal vs real terms · medium impact
All figures are AUD nominal. ABS CPI cumulative growth: FY20–FY24 ~18%, FY20–FY25 ~22%, FY22–FY25 ~12%. ADL's "5.4× CAPEX ramp FY22→FY25" includes ~12% CPI; the real-terms ramp is approximately 4.8×. Multi-year averages crossing the pandemic conflate cyclical recovery with inflation. For multi-year comparisons, restatement to common-base year using ABS CPI is recommended.

### F7 · 5-year average — computation method · medium impact
"5-year cumulative average" can mean either (a) sum of 5 years' CAPEX ÷ sum of 5 years' pax (cumulative-weighted), or (b) arithmetic mean of 5 annual ratios. The two methods can differ ~10–20% on COVID-distorted series. This report uses cumulative-weighted throughout where stated as "cumulative."

### F8 · Cohort median sensitivity · medium impact
Cohort median CAPEX/pax = A$13.5 on the ACCC-4 cohort (n=4); inclusion of ADL FY24 (A$13) lowers the median to A$11.5 (n=5). Both views are valid; "× median" comparisons should specify which cohort the median is computed on. The league table presents both medians; narrative references the n=4 ACCC-monitored median where comparing to ACCC-monitored airports specifically.

### F9 · Indicative program totals vs audited annual CAPEX · medium impact
Several headline figures are multi-year program-totals or indicative disclosures, not audited annual cash-flow CAPEX, and are presented as such (D6 derivation):
- HBA "~A$350 m+" = sum of four named projects in mixed lifecycle stages
- ADL "A$1 bn 10-year program" — explicit "indicative" wording per AAL FY22 Integrated Review p.8
- CBR "A$3 bn since 1998" = 28-year cumulative figure including adjacent commercial property
- CNS "A$1 bn redevelopment" = Land Use Plan vision approved March 2025

### F10 · Year-boundary convention · low impact
"FY24" in this report = year ended 30 June 2024 (Australian convention). ACCC labels the same period as "2023-24." BITRE annual file uses FY labels. Calendar-year sources occasionally refer to "2024" meaning Jan–Dec. All ACCC and BITRE primary sources used in this report are FY-aligned to 30 June.

### F11 · Source discrepancy reconciliation · medium impact
Where multiple sources publish the same figure, discrepancies are documented in the methodology section but not always in per-cell footnotes:
- PER FY24 pax: ACCC 16.14 m vs BITRE 12.79 m (26% gap, FIFO inclusion)
- ADL FY24 pax: AAL 8.54 m vs BITRE 8.25 m (3.5% gap, transit/transfer/GA inclusion)
- BNE FY24 ATMs: ACCC 222.5 k vs BITRE RPT 188 k (definitional, military/GA inclusion)
- SYD FY24 pax: ACCC vs BITRE differ ~0.1% (rounding)

### F12 · Tertiary sources · low impact
Some capacity figures (runway counts, terminal floor area) are sourced from Wikipedia (S16). These are flagged `(tertiary; please verify)` in the raw-data file. For external publication of any quoted runway-count or terminal-m² figure, cross-check against the airport's own Master Plan.

### F13 · PDF text-extraction integrity · medium impact
PDF text extraction can introduce table-formatting errors (column alignment, en-dash vs minus, parenthesised negatives). Highest-impact figures (CAPEX, revenue, EBITDA, total assets) have been spot-checked against the PDF source. Spot checks performed include:
- SYD FY24 EBITDA (ACCC operating profit excl landfill): A$1,083.83 m — matches
- ADL FY24 CAPEX (cash flow line): A$106.829 m — matches PDF p.17 text "(106,829)"
- ADL FY24 revenue (Note 5 sum): A$284.610 m — matches each component

Residual: ~2–3 of 200+ data points may have extraction-related rounding errors at the 0.1% level.

### F14 · Non-recurring item normalisation · medium impact
Several years contain unusual items that distort comparisons:
- FY21 (all airports): JobKeeper subsidy receipts inflated underlying results
- FY21 ADL: Recovery of Virgin Australia debt provisions (~A$3.5 m)
- FY21 ADL: JobKeeper receipts (~A$3.8 m)
- SYD FY24: A$9.6 bn one-off non-cash unitholder distribution (statutory line; report uses ACCC operating profit)
- ADL FY22, FY24, FY25: A$48.5 m / A$41.6 m / A$67.6 m fair-value gains on investment properties (report uses underlying EBITDA throughout)

Major items are normalised. Smaller items (JobKeeper, debt-recovery) are not normalised at the cohort level.

### F15 · Source-document authenticity verification · low impact
For external publication, source PDFs should be re-fetched from the issuer's corporate website at point of citation to confirm authenticity. Auditor signatures within each PDF should be cross-checked against the issuer's announced auditor for the relevant fiscal year. AAL FY24 and FY25 reports were re-verified against `corporate.adelaideairport.com.au` URLs (S3, S4 entries).

### F16 · Source granularity for ministerial communications · low impact
A subset of federal ministerial press releases (`minister.infrastructure.gov.au`, `defence.gov.au`) were captured via Google search-result excerpts rather than full HTML retrieval. Headline figures (project values, federal funding amounts) are captured but conditional phrasing or qualifying detail may not be. Snippet-sourced figures are tagged "(via search excerpt)" in `sources.md`.

---

## Part 2 — Source & derivation index for headline figures

### Source codes

| Code | Source | Type |
|---|---|---|
| **S1** | ACCC Airport Monitoring Report 2023-24 supplementary database (XLSX) — sheets `SYD/MEL/BNE/PER total and aero` | Primary, audited regulatory accounts |
| **S2** | BITRE annual airport activity FY1985-86 to FY2024-25 (XLSX) | Primary, government statistics |
| **S3** | AAL Annual Financial Report 30 Jun 2024 (PDF, 58 pp) | Primary, audited (AASB Tier 2) |
| **S4** | AAL Annual Financial Report 30 Jun 2025 (PDF, 57 pp) | Primary, audited (AASB Tier 2) |
| **S5** | AAL Annual Financial Report 30 Jun 2023 (PDF, 57 pp) | Primary, audited (AASB Tier 2) |
| **S6** | AAL Integrated Review 2022 (PDF, 89 pp) | Primary narrative + summary financials |
| **S7** | QAL Annual Reports FY20–FY24 (group-level) | Primary, audited (group not standalone) |
| **S8** | NAIF North Queensland Airports project page (naif.gov.au) | Primary government disclosure |
| **S9** | Hobart Airport project pages (projects.hobartairport.com.au) | Primary corporate |
| **S10** | Capital Property Group corporate "About Us" (capitalpropertygroup.com.au) | Primary corporate disclosure |
| **S11** | Productivity Commission inquiry submissions (assets.pc.gov.au) — sub031 HBA, sub008 NTA, sub049 NQA, sub056 CBR | Primary submission |
| **S12** | DIA 2023 Master Plan Preliminary Draft Sep 2023 (PDF) | Primary corporate |
| **S13** | Department of Defence press release 13 Aug 2023 | Primary, snippet-sourced (F16) |
| **S14** | Palisade Investment Partners press release | Primary corporate (DIA shareholder) |
| **S15** | Australian Aviation / Tasmanian Times news coverage | Secondary news |
| **S16** | Wikipedia (capacity facts only) | Tertiary |
| **S17** | Minister Catherine King / Madeleine King press releases | Primary government, snippet-sourced (F16) |

### Derivation codes

| Code | Meaning |
|---|---|
| **D1** | Direct read from primary source (no computation) |
| **D2** | Ratio: numerator ÷ denominator (both from primary; no estimation) |
| **D3** | Sum of components (e.g., total OPEX = sum of P&L expense lines) |
| **D4** | Year-over-year derivation (e.g., FY21 revenue derived from FY22 narrative) |
| **D5** | Cohort statistic (median, range, % of median) |
| **D6** | Indicative / aspirational corporate disclosure (NOT audited) |

### Per-figure trace — League Table FY24

| Cell | Value | Source | Derivation | Notes |
|---|---|---|---|---|
| SYD CAPEX/pax FY24 | 7 | S1 | D2: 277.83 / 40.53 = 6.85 → 7 | CAPEX from ACCC supp DB; pax = ACCC scope incl ~16% int'l |
| SYD OPEX/pax FY24 | 20 | S1 | D2: ~813 / 40.53 = 20.1 → 20 | OPEX = ACCC "total airport operating expenses" |
| SYD aero rev/pax FY24 | 29 | S1 | D2 (also D1: A$29.36 published in supp DB) | Exactly matches derived |
| SYD EBITDA margin FY24 | 57.1% | S1 | D2: 1,083.83 / 1,898 = 57.1% | EBITDA = ACCC "operating profit excl landfill"; not statutory (F14) |
| SYD CAPEX/rev FY24 | 14.6% | S1 | D2: 277.83 / 1,898 = 14.6% | |
| MEL CAPEX/pax FY24 | 23 | S1 | D2: 812.88 / 35.14 = 23.13 → 23 | |
| MEL CAPEX/rev FY24 | 68.2% | S1 | D2: 812.88 / 1,192 = 68.2% | |
| MEL EBITDA margin FY24 | 49.6% | S1 | D2 | |
| BNE CAPEX/pax FY24 | 10 | S1 | D2: 237.92 / 24.08 = 9.88 → 10 | |
| BNE OPEX/movement FY24 | 1,855 | S1 | D2: ~412.6 m / 222.5 k movements | ACCC ATM scope (incl military/GA), not BITRE RPT (F11) |
| BNE EBITDA margin FY24 | 57.8% | S1 | D2: 566.42 / 979.14 = 57.85% | |
| PER CAPEX/pax FY24 | 17 | S1 | D2: 281 / 16.14 = 17.4 → 17 | Pax = ACCC incl FIFO; BITRE RPT-only would give A$22 (F3) |
| PER OPEX/pax FY24 | 23 | S1 | D2: 378 / 16.14 = 23.4 → 23 | Same denominator caveat |
| PER EBITDA margin FY24 | 43.2% | S1 | D2 | |
| ADL CAPEX/pax FY24 | 13 | S3 | D2: 106.829 / 8.25 = 12.95 → 13 | CAPEX from AAL FY24 cash flow statement p.17; pax from BITRE (F3) |
| ADL CAPEX/rev FY24 | 37.5% | S3 | D2: 106.829 / 284.610 = 37.5% | |
| ADL OPEX/pax FY24 | 13 | S3 | D2: 111.241 / 8.25 = 13.5 → 13 | OPEX = sum of 7 P&L expense lines (D3) |
| ADL aero rev/pax FY24 | 17 | S3 | D2: 136.972 / 8.25 = 16.6 → 17 | |
| ADL EBITDA margin FY24 | 60.9% | S3 | D2: 173.4 / 284.610 = 60.9% | EBITDA = underlying (excl A$41.6 m FV gain); statutory = 75.5% (F4) |
| ADL CAPEX/pax FY25 | 24 | S4 | D2: 208.718 / ~8.6 | Audited CAPEX A$208.718 m verified; FY25 BITRE pax denominator pending |
| ADL CAPEX/rev FY25 | 65.6% | S4 | D2: 208.718 / 318.206 = 65.59% | Both audited |
| QAL OPEX/pax FY24 | 8 | S7 | D2: ~64 / 8.34 (group pax) | Group-vs-pax-denominator scope (F3, F4, F5) |
| QAL EBITDA margin FY24 | 67.6% | S7 | D2 | Group-level (4 airports), includes property gains (F4) |
| Median CAPEX/pax FY24 (n=4) | 13.5 | derived | D5 | ACCC-monitored cohort |
| Median CAPEX/pax FY24 (n=5) | 11.5 | derived | D5 | Inclusive of ADL (F8) |
| Median CAPEX/rev FY24 (n=4) | 33.3% | derived | D5 | ACCC-monitored cohort |

### Per-figure trace — ADL P&L breakdown

ADL OPEX FY24 = A$111.241 m derived as **D3** sum from S3 p.14:
- Employee benefits expense: 24,464
- Services & utilities: 61,690
- Consultants & advisors: 2,886
- General administration: 11,178
- Increase of expected credit loss: 1,929
- Leasing & maintenance: 8,967
- (Loss)/Gain on disposal of PP&E: 127 (loss)
- **Sum: A$111,241 k = A$111.2 m**

ADL Revenue FY24 = A$284.610 m direct read (S3 p.14, Note 5):
- Aeronautical: 136,972
- Commercial trading: 32,338
- Property: 68,989
- Car parking: 37,462
- Other: 8,849

ADL EBITDA underlying FY24 = A$173.4 m direct read (S3 p.4 Directors' Report):
- AAL P&L statutory EBITDA line: 215,004 (S3 p.14)
- Less: changes in fair value of investment properties: 41,576 (S3 p.14, Note 9)
- = A$173,428 k underlying

ADL CAPEX FY24 = A$106.829 m direct read (S3 p.17):
- Cash flow statement line: "Payments for property, plant and equipment, intangible assets and investment properties (106,829)"
- Note: includes intangibles + investment property as well as PP&E — wider scope than ACCC's "asset additions" line (F5)

### Per-figure trace — ADL Build-Cycle ("5.4× ramp FY22→FY25")

| Year | CAPEX (A$m) | Source | Source detail |
|---|---|---|---|
| FY22 | 38.650 | S5 | Cash flow statement, comparative column in FY23 PDF p.16 |
| FY23 | 39.541 | S5 | Cash flow statement, FY23 PDF p.16 |
| FY24 | 106.829 | S3 | Cash flow statement, FY24 PDF p.17 |
| FY25 | 208.718 | S4 | Cash flow statement, FY25 PDF p.17 |

**Derivation: 5.4× = 208.718 / 38.650 = 5.40** (D2)

**Caveat (F6):** FY22→FY25 nominal; CPI growth FY22-FY25 ~12%, so real ramp ~4.8×.

**Caveat (F9):** "A$1 bn 10-year program" — quote from AAL Integrated Review FY22 p.8 reads *"ambitious infrastructure program for the next decade with an indicative value of approximately $1 billion"* (S6). The word "indicative" matters — this is a planning intent, not a Board-committed CAPEX commitment.

### Per-figure trace — Disclosed CAPEX programs (REPORT §3.1)

| Claim | Figure | Source | Type |
|---|---|---|---|
| HBA total program | ~A$350 m+ | S9 | D3 sum of 4 named projects (130 runway + 200 terminal + 20 carparks + 25 Cambridge MDP); D6 indicative — projects in different lifecycle stages |
| HBA runway | A$130 m | S9 + S15 + S17 | D1 from project page; corroborated by minister press release + Australian Aviation |
| HBA federal co-fund | A$60 m | S17 | D1 from minister press release; via search excerpt (F16) |
| HBA terminal | A$200 m | S9 | D1 from project page |
| CBR cumulative since 1998 | A$3 bn+ | S10 | D6 — corporate disclosure, includes adjacent commercial property; PC sub056 (S11) cited A$2 bn as of 2018 |
| CBR terminal 2014 | A$480 m | S11 | D1 — PC sub056 p.5; corporate disclosure cites A$550 m, possibly different scope |
| CBR FY07-13 CAPEX/rev | 1.24× | S11 | D1 — PC sub056 p.~6 verbatim |
| DRW runway | A$200 m | S13 | D1 — Defence press release; via search excerpt (F16) |
| DRW current cycle | ~A$300–400 m | derived | D3 sum of named items (200 runway + 30 hotel + 60 diesel + 11 terminal + 7.5 chiller + historical 75 + 100); D6 indicative — sums across decades and mixed funding sources |
| CNS T1 + EAP | ~A$115 m | S8 + cairnsairport.com.au | D3 sum (55 + 60) |
| CNS NAIF facility | A$155 m | S8 | D1 — concessional loan facility, max draw, shared with Mackay |
| CNS A$1 bn vision | A$1 bn | busyatwork.com.au | D6 — Land Use Plan vision approved Mar 2025; long-horizon, not committed CAPEX |

---

## Part 3 — Items not in the audited per-FY framework

The following are documented but not directly comparable per-FY audited figures:

1. **HBA / CBR / DRW / CNS audited annual CAPEX** — not publicly disclosed; only program totals available
2. **OOL standalone P&L** — only QAL group available
3. **ADL FY20** — pre-COVID year; AAL FY20 standalone Annual Financial Report not in scope of this pass
4. **ADL FY21** — derivable from FY22 Integrated Review narrative (revenue A$115.8 m, underlying EBITDA A$67.8 m); ADL FY21 standalone Annual Financial Report would be authoritative
5. **All FTE / headcount data** — not consistently disclosed across the cohort
6. **CAPEX-by-purpose split** — capacity / maintenance / commercial — not in any audited statement
7. **International peer figures** (Auckland, Singapore Changi) — not in scope of this pass

---

## Part 4 — Application

**Before quoting any figure externally:**

1. Look up the figure in Part 2 source/derivation index to confirm scope and derivation
2. Treat all "× cohort median" claims as cohort-specific (n=4 ACCC vs n=5 with ADL — F8)
3. Treat all program totals (HBA A$350 m, ADL A$1 bn, CBR A$3 bn) as indicative disclosures, not audited per-FY CAPEX (F9)
4. For real-terms comparisons across multiple years, restate using ABS CPI before quoting (F6)
5. For cross-airport ratios, footnote the denominator scope (ACCC pax / BITRE pax / corporate-reported pax — F3)

**Strongest series in this report:**
- ACCC supplementary database series for SYD/MEL/BNE/PER FY20–FY24 (audited regulatory accounts)
- AAL FY22–FY25 cash-flow CAPEX line (audited per AASB Tier 2)

All other series carry one or more of the F1–F16 caveats.
