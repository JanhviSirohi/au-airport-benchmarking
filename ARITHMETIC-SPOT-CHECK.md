# Arithmetic Spot-Check — Headline Numbers

**Date performed:** 2026-04-27
**Scope:** Top 10 headline numbers in the report verified directly against primary-source data (ACCC AMR 2024-25 supplementary database; AAL FY24/FY25 audited financial reports; QAL 2025 Annual Report).
**Method:** Each ratio recomputed from raw numerator and denominator extracted from the source XLSX/PDF; verified to 2 decimal places (rounding tolerance applied where the report rounds to nearest integer or 0.1%).

---

| # | Claim | Source | Computation | Result |
|---|---|---|---|---|
| 1 | MEL FY25 CAPEX/rev = 86.9% | ACCC supp DB MEL R42 / R18 | A$1,197.812m / A$1,377.801m = 86.9365% | ✓ MATCH |
| 2 | SYD FY25 CAPEX/rev = 18.7% | ACCC supp DB SYD R52 / R18 | A$375.278m / A$2,011.324m = 18.6583% | ✓ MATCH |
| 3 | BNE FY25 CAPEX +96% YoY | ACCC supp DB BNE R42 FY24 vs FY25 | A$342.647m → A$670.768m = +95.76% | ✓ MATCH |
| 4 | SYD FY25 aero rev/pax = A$29.43 | ACCC supp DB SYD R14 (published) and R17 ÷ R2 (derived) | A$1,229.383m / 41.775m = A$29.4290 | ✓ MATCH (published and derived agree to 4dp) |
| 5 | ADL CAPEX 5.4× ramp FY22→FY25 | AAL FY23 audited PDF p.16 + FY25 audited PDF p.17 | A$208.718m / A$38.650m = 5.4002× | ✓ MATCH |
| 6 | ADL FY25 CAPEX/rev = 65.6% | AAL FY25 audited PDF p.17 (CAPEX) + p.14 Note 5 (revenue) | A$208.718m / A$318.206m = 65.5921% | ✓ MATCH |
| 7 | ADL FY24 underlying EBITDA = A$173.4m | AAL FY24 audited PDF p.14 P&L EBITDA line + Note 9 FV gain | A$215.004m − A$41.576m = A$173.428m | ✓ MATCH |
| 8 | Cohort median FY25 CAPEX/rev = 61.5% | derived from claims 1, 2 + BNE/PER/ADL CAPEX/rev | sorted: [18.66, 37.49, 61.45, 65.59, 86.94] → median 61.4540% | ✓ MATCH |
| 9 | QAL FY25 NPAT = A$41.8m, -13.6% YoY | QAL 2025 AR p.12 | A$48.376m → A$41.795m = -13.6039% | ✓ MATCH |
| 10 | PER FY25 CAPEX/pax = A$17 | ACCC supp DB PER R42 / R2 | A$290.813m / 17.501m = A$16.6172/pax | ✓ MATCH (rounded to nearest A$ — boundary case; underlying value is A$16.62) |

**Result:** **10 of 10 headline numbers verified against primary source data.** No discrepancies between report figures and source data.

**Note on claim 10:** PER CAPEX/pax of A$16.62 rounds to A$17 under the report's rounding convention (nearest A$). Some readers may prefer to see this as A$17 (rounded) or A$16.62 (unrounded); both are correct.

**Spot-check coverage:** This verification covers the top 10 headline numbers but is not exhaustive. The report contains ~200+ data points; F13 in the audit notes residual extraction-error risk on the order of ~2–3 of 200+ data points. Lower-priority figures (e.g., capacity floor area, FY20–FY22 historical FTE counts) have not been independently re-verified at this level of rigour and remain subject to F13.
