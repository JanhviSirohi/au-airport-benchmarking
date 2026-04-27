# Australian airport benchmarking — derived metrics
**Version:** 1.0 · **Date:** 2026-04-27 · **Author:** Janhvi Sirohi (out-read.com) · **Prepared for:** KPMG

Generated: 2026-04-27
Raw data: raw-data-2026-04-27.md
Sources: sources.md
Currency: AUD nominal. No CPI adjustment. Australian fiscal year ends 30 June.

All figures derived by division of raw-data inputs as recorded on 2026-04-27. Where an input is missing, the cell is `n/a` with the missing-input flag in the completeness map (Section 0). Cumulative-period averages use only years for which both numerator and denominator are present (no imputation).

Denominator-choice key (per Section 7 methodology):
- SYD/MEL/BNE — ACCC pax for financial ratios; ACCC ATM for movement-based ratios.
- PER — ACCC pax (incl. FIFO charter) for financial ratios because the financials are ACCC regulatory-account series; ACCC ATM for movement ratios. BITRE retained for cross-checks but not used as denominator here.
- ADL — AAL integrated-report pax for total-pax denominators where available, BITRE pax otherwise; ATM denominator = BITRE RPT.
- OOL/QAL — QAL **group** financials over QAL **group** passengers (and QAL group ATM where available). Gold-Coast-only ratios mixing QAL group financials with GCA-only pax are explicitly excluded as non-comparable.
- HBA/CBR/DRW/CNS — BITRE pax + BITRE ATM for operational ratios. Financial ratios not computable.

Sydney FY24 EBITDA = ACCC "Total airport operating profit (excluding landfill)" = 1,083.83 m. The statutory FY24 negative-profit line driven by the A$9.6 bn one-off non-cash unitholder distribution is **not** used for any ratio in this file.

---

## 0. Completeness map

Cell legend: `Y` = computable from raw data current engagement scope; `n` = input missing (raw data flagged n/a or unavailable); `*` = computable but with denominator caveat (see notes below).

### 0.1 Financial inputs

| Airport | Total revenue | Aero revenue | Non-aero revenue | OPEX total | CAPEX total | EBITDA / op. profit | Total assets | FTE total |
|---|---|---|---|---|---|---|---|---|
| SYD | FY20–FY24 Y | FY20–FY24 Y | FY20–FY24 Y | FY20–FY24 Y | FY20–FY24 Y | FY20–FY24 Y (ACCC operating profit) | FY20–FY24 Y | FY20–FY24 Y |
| MEL | FY20–FY24 Y | FY20–FY24 Y | FY20–FY24 Y | FY20–FY24 Y | FY20–FY24 Y | FY20–FY24 Y | FY20–FY24 Y | FY20–FY24 Y |
| BNE | FY20–FY24 Y | FY20–FY24 Y | FY20–FY24 Y | FY20–FY24 Y | FY20–FY24 Y | FY20–FY24 Y | FY20–FY24 Y | FY20–FY24 Y |
| PER | FY20–FY24 Y | FY20–FY24 Y | FY20–FY24 Y | FY20–FY24 Y | FY20–FY24 Y | FY20–FY24 Y | FY20–FY24 Y | FY20–FY24 Y |
| ADL | FY23–FY24 Y; FY20–FY22 n | FY23–FY24 Y; FY20–FY22 n | FY23–FY24 Y; FY20–FY22 n | FY23–FY24 Y; FY20–FY22 n | n (CAPEX cash-flow line not extracted) | FY23–FY24 Y | FY23–FY24 Y; FY20–FY22 n | n |
| OOL/QAL | FY20–FY24 Y (group) | n (not split in QAL reports) | n (not split) | FY20–FY24 Y (group OPEX) | n (capex not in extracted lines) | FY20–FY24 Y (group EBITDA) | n (not extracted) | n |
| CBR | n | n | n | n | n | n | n | n |
| HBA | n | n | n | n | n | n | n | n |
| DRW | n | n | n | n | n | n | n | n |
| CNS | n | n | n | n | n | n | n | n |

### 0.2 Operational inputs

| Airport | Passengers FY20–FY24 | Aircraft movements FY20–FY24 | Int'l freight FY20–FY24 |
|---|---|---|---|
| SYD | Y (ACCC + BITRE) | Y (ACCC + BITRE) | Y |
| MEL | Y (ACCC + BITRE) | Y (ACCC + BITRE) | Y |
| BNE | Y (ACCC + BITRE) | Y (ACCC + BITRE) | Y |
| PER | Y (ACCC + BITRE; large gap — see methodology) | Y (ACCC + BITRE; large gap — FIFO) | Y |
| ADL | Y (AAL FY23/FY24 + BITRE all) | Y (BITRE) | Y |
| OOL (GCA only) | Y (BITRE; QAL FY21 GCA n) | Y (BITRE) | Y |
| QAL group | FY20, FY22–FY24 Y; FY21 derived from FY22 report comparator | FY23–FY24 Y; FY20–FY22 n | n/a (group pax includes regional airports without int'l freight) |
| CBR | Y (BITRE) | Y (BITRE) | Y |
| HBA | Y (BITRE) | Y (BITRE) | Y |
| DRW | Y (BITRE) | Y (BITRE) | Y |
| CNS | Y (Cairns own + BITRE) | Y (BITRE) | Y |

### 0.3 Computable derived metrics by airport

| Airport | CAPEX/pax | CAPEX/rev % | CAPEX/assets % | CAPEX/ATM | OPEX/pax | OPEX/rev % | OPEX/ATM | OPEX/FTE | Aero rev/pax | Non-aero rev/pax | Aero share % | Rev/ATM | CAPEX/OPEX | EBITDA margin | EBITDA/pax | Asset turnover |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| SYD | Y | Y | Y | Y | Y | Y | Y | Y | Y | Y | Y | Y | Y | Y | Y | Y |
| MEL | Y | Y | Y | Y | Y | Y | Y | Y | Y | Y | Y | Y | Y | Y | Y | Y |
| BNE | Y | Y | Y | Y | Y | Y | Y | Y | Y | Y | Y | Y | Y | Y | Y | Y |
| PER | Y | Y | Y | Y | Y | Y | Y | Y | Y | Y | Y | Y | Y | Y | Y | Y |
| ADL | n (capex) | n (capex) | n (capex) | n (capex) | FY23–FY24 | FY23–FY24 | FY23–FY24 | n | FY23–FY24 | FY23–FY24 | FY23–FY24 | FY23–FY24 | n | FY23–FY24 | FY23–FY24 | FY23–FY24 |
| QAL group | n | n | n | n | Y (FY20–FY24) | Y | FY23–FY24 only | n | n | n | n | FY23–FY24 only | n | Y | Y | n |
| CBR | n | n | n | n | n | n | n | n | n | n | n | n | n | n | n | n |
| HBA | n | n | n | n | n | n | n | n | n | n | n | n | n | n | n | n |
| DRW | n | n | n | n | n | n | n | n | n | n | n | n | n | n | n | n |
| CNS | n | n | n | n | n | n | n | n | n | n | n | n | n | n | n | n |

CBR/HBA/DRW/CNS are **operational only** at current engagement scope (pax × ATM ratios in Section 2.3 footnote where computable from BITRE-only inputs, but no AUD ratios).

---

## 1. CAPEX intensity

### 1.1 CAPEX per passenger (AUD)
Divisor: ACCC pax (millions) for SYD/MEL/BNE/PER. ADL and QAL/OOL: not computable (CAPEX line not extracted).

| Airport | FY20 | FY21 | FY22 | FY23 | FY24 | 5y cumulative (sum CAPEX / sum pax) |
|---|---|---|---|---|---|---|
| SYD | 8 | 48 | 11 | 4 | 7 | 9 |
| MEL | 23 | 51 | 18 | 17 | 23 | 23 |
| BNE | 26 | 9 | 4 | 12 | 10 | 13 |
| PER | 9 | 19 | 16 | 10 | 17 | 14 |
| ADL | n/a | n/a | n/a | n/a | n/a | n/a |
| OOL/QAL | n/a | n/a | n/a | n/a | n/a | n/a |
| CBR | n/a | n/a | n/a | n/a | n/a | n/a |
| HBA | n/a | n/a | n/a | n/a | n/a | n/a |
| DRW | n/a | n/a | n/a | n/a | n/a | n/a |
| CNS | n/a | n/a | n/a | n/a | n/a | n/a |

Footnote: 5y cumulative = sum(CAPEX FY20–FY24, AUD m) / sum(pax FY20–FY24, m). SYD 1,202.83/130.00=9.25; MEL 2,512.37/112.31=22.37; BNE 1,066.11/79.19=13.46; PER 766.53/55.30=13.86.

### 1.2 CAPEX as % of total revenue

| Airport | FY20 | FY21 | FY22 | FY23 | FY24 | 5y avg (sum CAPEX / sum revenue) |
|---|---|---|---|---|---|---|
| SYD | 16.6% | 41.2% | 17.2% | 9.1% | 14.6% | 17.7% |
| MEL | 64.4% | 83.4% | 41.1% | 49.1% | 68.2% | 60.5% |
| BNE | 54.7% | 13.7% | 7.2% | 27.6% | 24.3% | 28.4% |
| PER | 23.7% | 37.1% | 25.3% | 22.3% | 42.2% | 29.7% |
| ADL | n/a | n/a | n/a | n/a | n/a | n/a |
| OOL/QAL | n/a | n/a | n/a | n/a | n/a | n/a |

### 1.3 CAPEX as % of total tangible non-current assets

| Airport | FY20 | FY21 | FY22 | FY23 | FY24 |
|---|---|---|---|---|---|
| SYD | 1.5% | 2.2% | 0.9% | 0.9% | 1.9% |
| MEL | 9.2% | 4.6% | 3.5% | 8.0% | 11.7% |
| BNE | 7.3% | 1.1% | 0.6% | 4.1% | 4.2% |
| PER | 3.1% | 3.5% | 3.6% | 4.4% | 8.9% |
| ADL | n/a | n/a | n/a | n/a | n/a |

### 1.4 CAPEX per aircraft movement (AUD)
Divisor: ACCC ATM ('000) for SYD/MEL/BNE/PER.

| Airport | FY20 | FY21 | FY22 | FY23 | FY24 |
|---|---|---|---|---|---|
| SYD | 1,002 | 2,799 | 1,072 | 478 | 947 |
| MEL | 3,330 | 3,945 | 1,881 | 2,361 | 3,336 |
| BNE | 2,760 | 613 | 284 | 1,190 | 1,070 |
| PER | 914 | 1,148 | 1,114 | 1,030 | 1,793 |

---

## 2. OPEX intensity

### 2.1 OPEX per passenger (AUD)
Divisors: ACCC pax for SYD/MEL/BNE/PER; AAL pax for ADL FY23–FY24; QAL group pax for QAL group OPEX.

| Airport | FY20 | FY21 | FY22 | FY23 | FY24 | 5y avg (sum OPEX / sum pax) |
|---|---|---|---|---|---|---|
| SYD | 27 | 95 | 56 | 23 | 20 | 31 |
| MEL | 21 | 81 | 41 | 19 | 17 | 26 |
| BNE | 27 | 59 | 37 | 22 | 18 | 28 |
| PER | 26 | 46 | 38 | 23 | 23 | 29 |
| ADL | n/a | n/a | n/a | 12 | 13 | 13 (FY23+FY24) |
| QAL group | 7 | 6 | 9 | 6 | 8 | 7 |

Footnote: SYD 3,998.01/130.00=30.75; MEL 2,798.58/112.31=24.92; BNE 2,194.44/79.19=27.71; PER 1,556.71/55.30=28.15. ADL FY23 90.4/7.78=11.62; FY24 111.2/8.54=13.02. QAL FY20 43.25/6.27=6.90; FY21 27.66/4.39=6.30; FY22 38.73/4.39=8.82; FY23 51.70/7.98=6.48; FY24 64.29/8.34=7.71. **Caveat:** QAL group OPEX divided by QAL group pax — not directly comparable with single-airport OPEX/pax because QAL group pax includes the lower-margin regional airports (Townsville, Mt Isa, Longreach).

### 2.2 OPEX as % of total revenue

| Airport | FY20 | FY21 | FY22 | FY23 | FY24 |
|---|---|---|---|---|---|
| SYD | 54.1% | 81.0% | 89.0% | 55.9% | 42.9% |
| MEL | 59.3% | 132.6% | 90.5% | 56.2% | 50.4% |
| BNE | 56.3% | 89.2% | 68.3% | 51.4% | 42.2% |
| PER | 67.3% | 89.7% | 58.3% | 49.6% | 56.8% |
| ADL | n/a | n/a | n/a | 36.0% | 39.1% |
| QAL group | 38.7% | 39.5% | 41.3% | 30.6% | 32.4% |

### 2.3 OPEX per aircraft movement (AUD)
Divisor: ACCC ATM ('000) for SYD/MEL/BNE/PER. QAL group: FY23/FY24 only (group ATM available; FY20–FY22 not in QAL reports extracted).

| Airport | FY20 | FY21 | FY22 | FY23 | FY24 |
|---|---|---|---|---|---|
| SYD | 3,261 | 5,506 | 5,557 | 2,928 | 2,773 |
| MEL | 3,069 | 6,269 | 4,142 | 2,704 | 2,464 |
| BNE | 2,843 | 4,003 | 2,696 | 2,218 | 1,855 |
| PER | 2,600 | 2,774 | 2,567 | 2,290 | 2,414 |
| QAL group | n/a | n/a | n/a | 779 | 932 |

### 2.4 OPEX per FTE (AUD)
Divisor: ACCC FTE total. ADL/QAL not disclosed.

| Airport | FY20 | FY21 | FY22 | FY23 | FY24 |
|---|---|---|---|---|---|
| SYD | 1,720,794 | 1,599,893 | 1,656,215 | 1,586,083 | 1,485,055 |
| MEL | 1,573,952 | 1,647,738 | 1,628,727 | 1,710,288 | 1,520,025 |
| BNE | 1,232,170 | 1,395,766 | 1,158,207 | 1,135,681 | 1,061,003 |
| PER | 1,103,262 | 1,098,543 | 1,005,704 | 1,033,000 | 1,075,994 |

Footnote: dollar values, not millions. SYD FY20 867.28m/504=1.7208m → 1,720,794.

---

## 3. Revenue mix and yield

### 3.1 Aeronautical revenue per passenger (AUD)
Divisor: ACCC pax. (Replicates ACCC's own published per-pax row; minor differences from raw-data row "Aero rev / pax" are rounding.)

| Airport | FY20 | FY21 | FY22 | FY23 | FY24 |
|---|---|---|---|---|---|
| SYD | 26 | 40 | 32 | 24 | 29 |
| MEL | 18 | 24 | 21 | 17 | 18 |
| BNE | 23 | 21 | 22 | 20 | 21 |
| PER | 19 | 18 | 22 | 20 | 19 |
| ADL | n/a | n/a | n/a | 16 | 16 |

Footnote: ADL FY23 121.4/7.78=15.60; FY24 137.0/8.54=16.04.

### 3.2 Non-aeronautical revenue per passenger (AUD)

| Airport | FY20 | FY21 | FY22 | FY23 | FY24 |
|---|---|---|---|---|---|
| SYD | 23 | 77 | 31 | 16 | 17 |
| MEL | 18 | 37 | 24 | 17 | 16 |
| BNE | 26 | 45 | 32 | 22 | 22 |
| PER | 20 | 33 | 43 | 25 | 23 |
| ADL | n/a | n/a | n/a | 17 | 17 |

### 3.3 Aeronautical share of total revenue (%)

| Airport | FY20 | FY21 | FY22 | FY23 | FY24 |
|---|---|---|---|---|---|
| SYD | 52.7% | 34.3% | 50.8% | 60.4% | 62.7% |
| MEL | 49.1% | 39.1% | 46.0% | 50.1% | 52.7% |
| BNE | 46.5% | 31.6% | 40.5% | 47.9% | 49.5% |
| PER | 48.7% | 35.9% | 33.7% | 44.7% | 45.0% |
| ADL | n/a | n/a | n/a | 48.4% | 48.1% |

### 3.4 Total revenue per aircraft movement (AUD)
Divisor: ACCC ATM ('000). ADL/QAL not computable for ATM ratios except QAL FY23–FY24 (group ATM available).

| Airport | FY20 | FY21 | FY22 | FY23 | FY24 |
|---|---|---|---|---|---|
| SYD | 6,026 | 6,799 | 6,245 | 5,236 | 6,465 |
| MEL | 5,172 | 4,728 | 4,578 | 4,808 | 4,894 |
| BNE | 5,049 | 4,486 | 3,950 | 4,317 | 4,400 |
| PER | 3,864 | 3,094 | 4,404 | 4,613 | 4,247 |
| QAL group | n/a | n/a | n/a | 2,544 | 2,881 |

---

## 4. Cross-cuts

### 4.1 CAPEX-to-OPEX ratio

| Airport | FY20 | FY21 | FY22 | FY23 | FY24 |
|---|---|---|---|---|---|
| SYD | 0.31 | 0.51 | 0.19 | 0.16 | 0.34 |
| MEL | 1.08 | 0.63 | 0.45 | 0.87 | 1.35 |
| BNE | 0.97 | 0.15 | 0.11 | 0.54 | 0.58 |
| PER | 0.35 | 0.41 | 0.43 | 0.45 | 0.74 |

### 4.2 EBITDA margin (EBITDA / total revenue, %)
SYD EBITDA = ACCC operating-profit-excluding-landfill (NOT statutory FY24). QAL EBITDA = group line.

| Airport | FY20 | FY21 | FY22 | FY23 | FY24 |
|---|---|---|---|---|---|
| SYD | 45.9% | 19.0% | 11.0% | 44.1% | 57.1% |
| MEL | 40.7% | -32.6% | 9.5% | 43.8% | 49.6% |
| BNE | 43.7% | 10.8% | 31.7% | 48.6% | 57.8% |
| PER | 32.7% | 10.3% | 41.7% | 50.4% | 43.2% |
| ADL | n/a | n/a | n/a | 64.0% | 75.5% |
| QAL group | 61.2% | 60.4% | 58.7% | 69.4% | 67.6% |

Footnote: ADL FY23 160.6/251.0=64.0%; FY24 215.0/284.6=75.5%. ADL margin appears very high vs ACCC peers because ADL reports EBITDA as an explicit P&L line that already strips D&A and interest, whereas ACCC "operating profit excluding landfill" is the operating-profit-before-D&A line; these are conceptually similar but the ADL figure is likely closer to a "consolidated" group-level EBITDA including non-airport income — flagged.

### 4.3 EBITDA per passenger (AUD)

| Airport | FY20 | FY21 | FY22 | FY23 | FY24 | 5y avg |
|---|---|---|---|---|---|---|
| SYD | 23 | 22 | 7 | 18 | 27 | 21 |
| MEL | 15 | -20 | 4 | 15 | 17 | 11 |
| BNE | 21 | 7 | 17 | 21 | 25 | 19 |
| PER | 13 | 5 | 27 | 23 | 18 | 17 |
| ADL | n/a | n/a | n/a | 21 | 25 | 23 (FY23+FY24) |
| QAL group | 11 | 10 | 13 | 15 | 16 | 13 |

Footnote: SYD 2,721.49/130.00=20.93; MEL 1,381.39/112.31=12.30; BNE 1,601.16/79.19=20.22; PER 992.65/55.30=17.95.

### 4.4 Asset turnover (total revenue / total tangible non-current assets, ×)

| Airport | FY20 | FY21 | FY22 | FY23 | FY24 |
|---|---|---|---|---|---|
| SYD | 0.09 | 0.05 | 0.05 | 0.09 | 0.13 |
| MEL | 0.14 | 0.05 | 0.09 | 0.16 | 0.17 |
| BNE | 0.13 | 0.08 | 0.09 | 0.15 | 0.17 |
| PER | 0.13 | 0.09 | 0.14 | 0.20 | 0.21 |
| ADL | n/a | n/a | n/a | 0.15 | 0.14 |

---

## 5. Most-recent-fiscal-year league table

All airports use FY24 (FY24 financial inputs available for SYD, MEL, BNE, PER, ADL, QAL). Tier-2 airports without financials (CBR, HBA, DRW, CNS) are excluded. ADL row uses AAL FY24 P&L; CAPEX-derived columns are blank where AAL CAPEX line was not extracted.

| Airport | FY used | CAPEX/pax (AUD) | OPEX/pax (AUD) | Aero rev/pax (AUD) | EBITDA margin | EBITDA/pax (AUD) | CAPEX/rev % |
|---|---|---|---|---|---|---|---|
| SYD | FY24 | 7 | 20 | 29 | 57.1% | 27 | 14.6% |
| MEL | FY24 | 23 | 17 | 18 | 49.6% | 17 | 68.2% |
| BNE | FY24 | 10 | 18 | 21 | 57.8% | 25 | 24.3% |
| PER | FY24 | 17 | 23 | 19 | 43.2% | 18 | 42.2% |
| ADL | FY24 | n/a | 13 | 16 | 75.5% | 25 | n/a |
| QAL group | FY24 | n/a | 8 | n/a | 67.6% | 16 | n/a |

Distribution stats across the airports with each metric (n included is the count of computable cells):

- CAPEX/pax (n=4): median = 13.5; min=7 (SYD); max=23 (MEL); >1.5× median = MEL (23 / 13.5 = 1.70×); <0.5× median = none.
- OPEX/pax (n=6): median = 17.5; min=8 (QAL group); max=23 (PER); >1.5× median = PER (1.31× — not flagged), QAL group (8/17.5 = 0.46× — flagged below median); <0.5× median = QAL group (0.46×).
- Aero rev/pax (n=5): median = 19; min=16 (ADL); max=29 (SYD); SYD = 1.53× median (flagged above).
- EBITDA margin (n=6): median = 57.4%; min=43.2% (PER); max=75.5% (ADL); ADL = 1.31× median (not flagged at 1.5× threshold), PER = 0.75× median (not flagged below 0.5×).
- EBITDA/pax (n=6): median = 21.5; min=16 (QAL group); max=27 (SYD); none beyond 1.5× / 0.5× thresholds.
- CAPEX/rev % (n=4): median = 33.3%; min=14.6% (SYD); max=68.2% (MEL); MEL = 2.05× median (flagged above), SYD = 0.44× median (flagged below).

Outliers vs FY24 league-table medians (>1.5× or <0.5× median):
- MEL — CAPEX/pax 23 vs median 13.5 (1.70×); CAPEX/rev 68.2% vs median 33.3% (2.05×). Build-out phase: ACCC notes Mar-2024 third-runway approval and large terminal works.
- SYD — Aero rev/pax 29 vs median 19 (1.53×); CAPEX/rev 14.6% vs median 33.3% (0.44×). Slot-constrained gateway with high yield; FY24 was a low-CAPEX year vs recent history.
- QAL group — OPEX/pax 8 vs median 17.5 (0.46×). Driven by group reporting that includes regional airports with much lower per-pax cost structures alongside Gold Coast.

---

## 6. Outlier flags and structural notes

These flag any cell across all years whose ratio sits at >1.5× or <0.5× the median computed across the airports with that metric in that year (medians computed only over the 4 ACCC-monitored airports unless otherwise noted; ADL and QAL retained where comparable).

COVID-distorted years (FY20, FY21, FY22) are flagged explicitly; the absolute ratio outliers in these years should not be read as structural.

- **SYD FY21 CAPEX/pax = 48** vs ACCC-4 FY21 median ~33.5 → 1.43× (not flagged at 1.5×, but extreme absolute level reflects COVID pax collapse to 7.85m while CAPEX (379m) ran ahead of revenue).
- **SYD FY21 OPEX/pax = 95** vs ACCC-4 FY21 median ~70 → 1.36× — COVID-distorted (denominator collapse).
- **SYD FY24 Aero rev/pax = 29** vs ACCC-4 FY24 median ~20 → 1.45×. Slot-constrained Sydney with international-mix premium; consistent year on year.
- **SYD FY24 CAPEX/rev = 14.6%** vs ACCC-4 median 33.3% → 0.44× (FY24 league flag). FY24 was below-trend vs SYD's own 5y avg of 17.7%; reflects post-take-private capital-allocation discipline.
- **MEL FY20 CAPEX/rev = 64.4%** vs ACCC-4 FY20 median ~39% → 1.65×. Pre-COVID build phase (terminal expansion).
- **MEL FY21 OPEX/rev = 132.6%** vs ACCC-4 FY21 median ~89% → 1.49× — COVID-distorted (revenue collapsed to 379m while OPEX held).
- **MEL FY21 EBITDA margin = -32.6%** — only ACCC-4 airport with negative EBITDA in FY21; reflects MEL's higher fixed-cost base relative to revenue collapse.
- **MEL FY22–FY24 CAPEX/pax = 18 / 17 / 23** vs ACCC-4 FY24 median ~13.5; persistently elevated CAPEX intensity through the build-out cycle including the Mar-2024-approved third runway.
- **MEL FY24 CAPEX/rev = 68.2%** → 2.05× FY24 median (flagged); MEL is in active expansion.
- **BNE FY20 CAPEX/rev = 54.7%** vs ACCC-4 FY20 median ~39% → 1.40× (not flagged) — completion of new parallel runway 01L/19R commissioned 2020.
- **BNE FY21–FY22 CAPEX collapse to 71m / 40m** — post-runway-completion CAPEX slowdown; not an outlier vs reduced denominators but a structural narrative point.
- **PER FY24 CAPEX/rev = 42.2%** vs ACCC-4 FY24 median 33.3% → 1.27×; CAPEX surge to 281m (2× the FY20–FY23 average).
- **PER FY22 EBITDA/pax = 27** vs ACCC-4 FY22 median ~9 → 3.0×. PER FY22 reflects FIFO-charter resilience through COVID — Perth's pax base did not collapse the way SYD/MEL international did.
- **PER OPEX/ATM consistently below ACCC-4 median** every year (FY20: 2,600 vs median ~2,950; FY24: 2,414 vs ~2,440) — structural: high FIFO ATM share with relatively low OPEX per movement.
- **QAL group OPEX/pax 6–9 across all years** — well below 0.5× ACCC-4 median in every year. Reflects (a) group includes regional airports with smaller cost per pax, (b) QAL group financials may not include all OPEX captured in ACCC regulatory-account scope (e.g., security recovery treatment); flagged but not adjusted.
- **QAL group EBITDA margin 58.7%–69.4%** — consistently above ACCC-4 median; reflects different cost-allocation conventions in the QAL annual report vs ACCC regulatory accounts (notably treatment of intercompany / property revenue) — flagged.
- **ADL FY24 EBITDA margin 75.5%** — highest of any ratio in the file. Reflects AAL P&L convention which strips D&A (61.6m FY24 implied) and includes property revenue at gross margin. Not directly comparable with ACCC operating-profit basis without reconciliation; flagged.

Tier-2 airports (CBR/HBA/DRW/CNS):
- **No financial outlier flags possible** — only operational ratios computable.
- Operational note (passengers per ATM, BITRE basis FY24): CBR 71.6, HBA 127.6, DRW 69.9, CNS 104.8, OOL 157.3. CBR and DRW have the lowest pax-per-ATM among the tier-2 airports, consistent with smaller average aircraft size and higher GA / regional-RPT mix.

Arithmetic consistency checks (raw-data spot checks):
- SYD FY24: aero 1,190.19 + non-aero 707.45 = 1,897.64 ✓
- MEL FY24: aero 628.34 + non-aero 564.01 = 1,192.35 vs total 1,192.36 (rounding, ✓)
- BNE FY24: aero 484.97 + non-aero 494.17 = 979.14 ✓
- PER FY24: aero 299.66 + non-aero 366.67 = 666.33 ✓
- ACCC-published Aero rev/pax row vs derived (aero ÷ ACCC pax) for FY24: SYD 29.36 vs 29.36 (1,190.19/40.53) ✓; MEL 17.88 vs 17.88 ✓; BNE 21.33 vs 21.33 ✓; PER 18.57 vs 18.57 ✓. Internally consistent.
- SYD FY24 EBITDA used here (1,083.83 m) is the ACCC operating-profit-before-D&A line; the statutory net-profit line in the audited statements is separately distorted by the A$9.6 bn one-off non-cash unitholder distribution — see Section 7.
- MEL OPEX/rev FY21 = 132.6% (OPEX > revenue) is consistent with the negative operating-profit line for FY21 (-123.56 m); not a data error.

---

## 7. Methodological notes

- **Fiscal year basis:** 30 Jun (Australian). FY24 = year ending 30 Jun 2024. No CY data substituted.
- **Currency:** AUD nominal as reported. **No inflation adjustment applied** — multi-year comparisons (especially 5y cumulative averages crossing FY20–FY24) include 2020–2024 cumulative ABS CPI of roughly 18%; readers should adjust where year-on-year real-terms comparisons matter.
- **Passenger denominator choice for Perth: ACCC** (incl. FIFO charter), not BITRE RPT-only. Reason: PER financials in this file are the ACCC regulatory-account series, and the ACCC pax denominator is the matching scope. Using BITRE RPT (~70–80% of ACCC) would inflate per-pax ratios for an airport that earns aero revenue from FIFO charter movements not in the BITRE denominator. The gap is large (FY24: ACCC 16.14 m vs BITRE 12.79 m, 26% difference). Per-pax ratios in this file for PER are therefore lower than they would be on a BITRE basis; do not compare PER per-pax figures with tier-2 BITRE-based per-pax figures without adjustment.
- **Passenger denominator for SYD/MEL/BNE: ACCC.** Difference vs BITRE is <1.5% in every year so the choice is immaterial.
- **Passenger denominator for ADL: AAL integrated-report pax** (FY23 7.78 m, FY24 8.54 m) for ratios using AAL P&L data. AAL reports run ~3.5% above BITRE (transit/transfer + GA inclusion).
- **QAL group treatment:** Gold Coast Airport standalone financials are NOT separately disclosed by QAL. Therefore:
  - All QAL ratios in this file use **QAL group financials over QAL group passengers** (4-airport consolidation: Gold Coast + Townsville + Mt Isa + Longreach).
  - Mixing QAL group financials with Gold-Coast-only pax (BITRE 6.32 m FY24) is **explicitly excluded** as it would inflate every per-pax ratio by ~30% (group pax 8.34 m FY24 vs GCA 6.32 m).
  - QAL ratios in this file are therefore **not directly comparable** with single-airport ratios for SYD/MEL/BNE/PER/ADL.
  - QAL group ATM only available FY23–FY24 from the QAL annual reports extracted; ATM ratios for QAL FY20–FY22 are blank.
- **Sydney FY24 underlying vs statutory:** Sydney's audited FY24 statutory profit-and-loss shows a large negative due to a A$9.6 bn one-off non-cash unitholder distribution recognised post the 2022 take-private. This file uses the **ACCC operating-profit (excluding landfill)** line of 1,083.83 m as EBITDA, which is the operating-cash-earnings basis. The statutory line is **not** used for any ratio.
- **EBITDA definitional note:** SYD/MEL/BNE/PER use ACCC "Total airport operating profit (excluding landfill)" — operating profit before D&A on regulatory-account scope. ADL uses the explicit "EBITDA" P&L line in the AAL Annual Financial Report 30 June 2024. QAL uses the explicit "EBITDA" line in the QAL annual reports. These three definitions are conceptually similar (all strip D&A and below-the-line items) but allocations differ; cross-airport EBITDA-margin comparisons should be treated with a ±5pp uncertainty band.
- **Per-FTE only computable for ACCC-monitored airports.** ADL/QAL/CBR/HBA/DRW/CNS FTE not in extracted scope.
- **5y cumulative figures** use only the years for which **both** numerator and denominator are present. ADL 5y figures use FY23+FY24 only (n=2) and are flagged as such. No imputation of missing years.
- **Outlier thresholding** is mechanical (1.5× / 0.5× the cohort median for that metric in that year, with COVID years FY20–FY22 flagged separately). Structural reasons cited come **only** from disclosed facts in the raw-data file (build-out phase, regulatory-account convention, FIFO mix at Perth, group reporting at QAL, take-private recognition at SYD). Where the raw data does not support a structural reason, the flag is recorded without explanation.
- **Excluded ratios (not computable on current engagement scope):**
  - ADL: all CAPEX-based ratios (CAPEX/pax, CAPEX/rev, CAPEX/assets, CAPEX/ATM, CAPEX-OPEX); FY20–FY22 financials missing.
  - QAL/OOL: all aero / non-aero per-pax and aero-share ratios (no aero/non-aero split in QAL annual reports extracted); CAPEX-based ratios (CAPEX line not extracted); asset turnover (total assets not extracted).
  - CBR / HBA / DRW / CNS: every AUD-denominated derived ratio.
- **Provenance:** every numerator and denominator traces back to the rows in raw-data-2026-04-27.md whose `Source` column points to the ACCC supplementary database (SYD/MEL/BNE/PER), AAL annual financial reports (ADL), QAL annual reports (QAL group), Cairns Airport own PDF (CNS pax), and BITRE FY 2024-25 file (operational data for all airports). No new fetches were performed for this benchmarking pass.
