readme2 = """# Fund Reconciliation Case Study
### Daily NAV Reconciliation | ERISA 401(k) & Defined Benefit Pension Plans

---

## Business Problem

Fund administrators and investment operations analysts are responsible for determining the Net Asset Value (NAV) of mutual funds, separately managed accounts, and collective investment funds on a daily basis. This process requires reconciling holdings, cash positions, and income accruals between the fund's internal records and the custodian's records — and resolving any exceptions before NAV is finalized and reported to clients.

In practice, even small discrepancies — a stale custodian price, a missed dividend settlement, or an incorrect coupon rate — can materially impact reported NAV, create compliance risk, and erode client trust. Fund analysts must identify, investigate, and resolve these exceptions within tight daily and monthly deadlines.

This project simulates the complete daily reconciliation workflow for a portfolio of 6 ERISA-governed funds, mirroring real-world fund accounting operations.

---

## Scope

| Attribute | Detail |
|---|---|
| Funds Monitored | 6 (Mutual, Separately Managed, Collective, Commingled) |
| Plan Types | Defined Contribution (401k) & Defined Benefit (Pension) |
| Valuation Date | March 31, 2026 |
| Holdings Reconciled | 18 positions across 6 funds |
| Exceptions Identified | 4 |
| Resolution Rate | 100% |

---

## Tech Stack

| Tool | Purpose |
|---|---|
| Microsoft Excel | Reconciliation workbooks, exception logging, accruals audit |
| Microsoft PowerPoint | Supervisor-ready summary presentation |
| Python (openpyxl) | Automated Excel workbook generation |
| Python (python-pptx) | Automated PowerPoint generation |

---

## Deliverables

### 1. Excel Workbook — `Fund_Reconciliation_Case_Study.xlsx`

Five-tab structured workbook covering the full reconciliation workflow:

| Tab | Content |
|---|---|
| Summary | KPI dashboard — funds reconciled, exceptions flagged/resolved, exception rate, fund-level status |
| Holdings Reconciliation | 18-position comparison of custodian vs fund prices, variance $ and %, exception flagging at ±0.5% threshold |
| Cash Reconciliation | Custodian vs fund cash balances for all 6 funds, break identification |
| Accruals Audit | Dividend and coupon income postings vs expected amounts, discrepancy flagging |
| Exception Resolution Log | Root-cause documentation and resolution notes for all 4 exceptions |

### 2. PowerPoint Presentation — `Fund_Reconciliation_Summary.pptx`

Four-slide supervisor-ready summary:

| Slide | Content |
|---|---|
| 1 | Title — valuation date, plan type, analyst name |
| 2 | Reconciliation Overview — KPIs and fund-level status table |
| 3 | Exceptions Detail — each exception with root cause and resolution |
| 4 | Methodology & Key Takeaways — process steps and outcome metrics |

---

## Solution Walkthrough

### Step 1 — Holdings Reconciliation
Compared custodian-reported closing prices against fund-recorded prices for all 18 positions. Applied a ±0.5% variance threshold — the standard industry threshold for price exception flagging. Two exceptions were identified:

- **TLT (Beta Bond Fund):** Custodian price $92.10 vs fund price $93.85 — variance of 1.90%. Root cause: custodian used a stale T-1 price. Corrected via Bloomberg terminal verification.
- **IWM (Epsilon Small Cap Fund):** Custodian price $198.60 vs fund price $201.30 — variance of 1.36%. Root cause: price vendor feed lag. Corrected to fund administrator end-of-day NAV.

### Step 2 — Cash Reconciliation
Reconciled custodian cash balances against fund internal records for all 6 funds. One cash break was identified:

- **Gamma Balanced Fund:** Custodian cash $95,000 vs fund records $97,500 — difference of $2,500. Root cause: pending AAPL dividend settlement not yet reflected in custodian records. Confirmed and reconciled.

### Step 3 — Accruals & Income Audit
Verified dividend and coupon postings against expected amounts calculated from fund prospectus rates. One accrual error was identified:

- **Beta Bond Fund (TLT Coupon):** Posted amount $1,650 vs expected $1,875 — difference of $225. Root cause: incorrect coupon rate applied. Recalculated at 3.75% on $50,000 par value and reposted.

### Step 4 — Exception Resolution
All 4 exceptions were documented with full root-cause analysis, corrective action taken, and final resolution confirmation — mirroring the exception resolution workflow used in live fund accounting operations.

---

## Key Takeaways

| Metric | Result |
|---|---|
| Total positions reconciled | 18 |
| Cash accounts reconciled | 6 |
| Accruals audited | 10 |
| Exceptions identified | 4 |
| Exceptions resolved | 4 |
| Resolution rate | 100% |
| Exception rate | 11.1% |
| Total variance impact | $4,925 |

- Price feed reliability is the most common source of daily exceptions — custodian T-1 lag and vendor feed delays accounted for 50% of exceptions in this cycle
- Cash breaks frequently originate from timing differences in dividend settlements — not errors — and require confirmation rather than correction
- Accrual errors are highest-risk for NAV accuracy as they directly impact income positions and reported fund returns
- Structured exception logs with root-cause documentation are essential for audit trails and client reporting transparency

---

## Project Structure
