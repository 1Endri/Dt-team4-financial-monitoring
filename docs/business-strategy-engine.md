# FAUnance: Business Strategy & Deterministic Accounting Engine
## Technical Specification: Operational Boundaries, EVM-to-EBITDA Fusion, and Two-Speed Reconciliation

> **Lead Author & System Architect:** Shikhar Thakur (`shikharthakur2404`)  
> **Course Alignment:** Designing Technology (57074) — WiSe 2026/27 (Chair Wi1, FAU)  
> **Theoretical Grounding:** FAU Strategic Management (Prof. Dr. Harald Hungenberg) & DSR Methodology (Prof. Dr. Kathrin Möslein)  
> **Target Artifact:** Case B — **FAUnance** (Intelligent Financial Monitoring)  
> **Repository Location:** `docs/business-strategy-engine.md`  
> **Companion Document:** `docs/tool-design-architecture.md` (Hossein Hosseinpour)

---

## ⚡ Executive Brief for Teammates (Read This First)

> [!NOTE] **What is this document?**  
> This file specifies the **deterministic accounting and financial mechanics** running inside FAUnance's backend engine. It defines how we link project-level work packages to corporate EBITDA targets, how we compute cost and schedule variances without AI hallucinations, and how our two-speed reconciliation connects daily site logs to official ERP invoices.

### The Analogy: Avionics Blueprint vs. Cockpit Dashboard
* **The Dashboard UI:** What the project manager sees (progress bars, S-curves, status lights).
* **This Specification:** **The flight physics engine running inside the avionics computer.**  
  It defines the exact mathematical laws (Earned Value, EBITDA, Cash Conversion Cycle) that continuously calculate whether a project has enough financial runway before an alert ever blinks on the screen.

### The 3-Bullet Summary
1. **The Deterministic Math Core (Zero Hallucination):**  
   We do not allow probabilistic AI/LLMs to guess financial figures. Project budgets, progress, and margins are calculated strictly via deterministic accounting math:  
   $$\text{Cost Budget (BAC)} = \text{Planned Revenue} \times \left(1 - \frac{\text{Target EBITDA \%}}{100}\right)$$  
   $$\text{Actual EBITDA}_t = \text{Earned Value (EV)}_t - \text{Actual Cost (AC)}_t$$
2. **The Two-Speed Gearbox (Fast Daily vs. Slow Monthly):**  
   * **Speed 1 (Daily Edge Telemetry):** Field teams log delivery slips & worker hours on mobile $\rightarrow$ instant estimated burn rate ($AC_{\text{est}}$) to eliminate the 30-day ERP blind spot.  
   * **Speed 2 (Month-End ERP Re-Engineering):** Official vendor invoices arrive in SAP $\rightarrow$ system auto-reconciles the delta ($\Delta$) against preliminary edge logs.
3. **Strict Operational Boundary Control:**  
   Project managers control **operational EBITDA and local cash conversion**. Corporate-level capital structure metrics (WACC, EVA, DCF) are kept at the executive level and documented as future strategic extensions (see [Appendix](#appendix-corporate-level-valuation--future-strategic-extensions)).

---

## 1. System Philosophy: The Deterministic-Perceptual Hybrid Architecture

In corporate finance and mega-project engineering, **probabilistic AI (LLMs) cannot be allowed to hallucinate accounting figures**. No CFO, project controller, or auditing board will accept a balance sheet or P&L derived from an opaque neural network.

FAUnance enforces an uncompromising architectural boundary based on a **two-tier neuro-symbolic architecture**:

```
┌────────────────────────────────────────────────────────────────────────┐
│ 2. PERCEPTUAL INTELLIGENCE LAYER (Front-End & Decision Support)        │
│    • Natural Language Exception Narratives (LLM synthesis)             │
│    • Automated early-warning alert routing with supervisor sign-off    │
│    • Calibrated confidence scores (Best vs. Worst case scenarios)      │
│    • Sensitivity analysis visualization (FAU Strategy Slide 135)       │
├────────────────────────────────────────────────────────────────────────┤
│ 1. DETERMINISTIC ACCOUNTING ENGINE (Back-End Core Ground Truth)        │
│    • 100% exact mathematical formulas from FAU Corporate Strategy      │
│    • EBITDA operational boundary control & Target Cost Allocation      │
│    • EVM-to-EBITDA variance fusion & Composite EAC Forecasting         │
│    • Working Capital & Cash Conversion Cycle (CCC) tracking            │
│    • Two-Speed Real-Time Site Burn vs. Month-End Re-Engineering Audit  │
└────────────────────────────────────────────────────────────────────────┘
```

---

## 2. Literature Foundations: EVM Core & Strategic Controls

### 2.1 Primary Assigned Papers (Papers #1–#3)

#### Paper #1: EVM Costs vs. Benefits
* **Citation:** Christensen, D. S. (1998). The costs and benefits of the earned value management process. *Acquisition Review Quarterly*, 5, 373–386.
* **Key Finding:** EVM implementation and maintenance overhead is estimated at **1% to 2%** of total contract value (p. 379). The "20% rule" demonstrates that cumulative CPI does not change by more than **0.10** from its value at the 20% completion point to contract completion across US Department of Defense acquisition contracts (pp. 377–381). *(Note: Later research notes limitations in generalizing defense contract stability to commercial environments).*
* **FAUnance Application:** Forms our primary empirical business case: software monitoring overhead is modest relative to catching budget deviations before cost performance stabilizes past the 20% completion threshold.

#### Paper #2: Mathematical Foundation of EVM
* **Citation:** Anbari, F. T. (2003). Earned value project management method and extensions. *Project Management Journal*, 34(4), 12–23.
* **Key Finding:** Traditional accounting cannot detect whether low expenditure reflects genuine cost efficiency or severe schedule delay; tracking Earned Value ($EV$) against Planned Value ($PV$) is mandatory to evaluate true performance.
* **FAUnance Application:** Provides the formal mathematical equations for $PV, EV, AC, CV, SV, CPI, SPI$, and composite $EAC$, which we fuse with EBITDA targets.

#### Paper #3: Implementation & Adoption Drivers
* **Citation:** Kim, E., Wells, W. G., & Duffey, M. R. (2003). A model for effective implementation of Earned Value Management methodology. *International Journal of Project Management*, 21(5), 375–382.
* **Key Finding:** EVM implementations struggle when data collection imposes excessive administrative burden on field teams, when the Work Breakdown Structure (WBS) is misaligned with daily site tasks, and when leadership fails to foster organizational buy-in.
* **FAUnance Application:** Motivates keeping edge data collection lightweight, ensuring WBS work packages mirror operational site activities, and designing intuitive decision support rather than cumbersome administrative hurdles.

---

### 2.2 Cross-Referenced Literature & Boundary Controls

* **Paper #9 (Bouwens, de Kok & Verriest, 2019 — Assigned to Endri):**  
  *Critique of EBITDA:* Bouwens et al. (pp. 55–57, 62–64) demonstrate that EBITDA is not GAAP/IFRS defined, ignores capital intensity and working capital, and frequently paints an overly favorable ("rosy") picture compared to standard operating profit (EBIT).  
  *FAUnance Boundary:* We do **not** treat EBITDA as an unadjusted measure of overall corporate health. We use it strictly as an internal project-level operational control metric with a fixed, unadjusted definition, displayed alongside Cash Conversion Cycle and working capital.
* **Paper #10 (Rozenbaum, 2019 — Assigned to Rhydham):**  
  *Leverage & Overinvestment Risk:* Managers fixated solely on EBITDA tend to overinvest in debt-financed assets because interest and depreciation are excluded from their evaluations.  
  *FAUnance Boundary:* Enforces our **income statement control boundary**: project managers manage operational EBITDA, while corporate treasury oversees debt service, WACC, and capital allocation.
* **Paper #18 (Jensen & Meckling, 1976 — Agency Theory):**  
  *Information Asymmetry & Moral Hazard:* Field agents possess private operational information and are incentivized to conceal cost overruns and defer bad news from corporate principals.  
  *FAUnance Boundary:* Mitigates agency loss by replacing subjective monthly progress self-reporting with daily, auditable edge logs and supervisor sign-offs.

---

## 3. Mathematical Foundations: Operational Accounting Engine

```
                        FAUnance OPERATIONAL CONTROL ENGINE
                                        │
          ┌─────────────────────────────┴─────────────────────────────┐
          ▼                                                           ▼
   OPERATIONAL MARGIN                                         LIQUIDITY & TIMING
 (Target Cost, EBITDA, EBIT)                                    (CCC, NWC, DPO/DSO)
   [Handout pp. 14–20]                                        [Handout pp. 68, 138]
```

### 3.1 Operating Profitability & Margins

#### 1. EBITDA (Operational Control Boundary)
$$\text{EBITDA} = \text{Operating Revenue} - \text{Direct Labor} - \text{Direct Materials} - \text{Site Overhead}$$
* **Strategic Role:** Measures operational cash generation before capital structure, tax, and depreciation policies.
* **Software Rule:** Every Work Breakdown Structure (WBS) package has an assigned Target EBITDA margin.

#### 2. Operating Profit (EBIT) & Margin Definitions
$$\text{EBIT} = \text{EBITDA} - \text{Depreciation} - \text{Amortization}$$
$$\text{EBITDA Margin (\%)} = \frac{\text{EBITDA}}{\text{Operating Revenue}} \times 100$$
$$\text{Operating Margin (\%)} = \frac{\text{EBIT}}{\text{Operating Revenue}} \times 100$$
* **Alert Threshold:** Any work package where $\text{Actual EBITDA Margin} < \text{Target EBITDA Margin} - 2\text{ percentage points}$ triggers an immediate priority exception alert.

#### 3. NOPAT (Net Operating Profit After Taxes)
$$\text{NOPAT} = \text{EBIT} \times (1 - \text{Effective Tax Rate})$$
* **Strategic Role:** Normalizes operational performance across multi-national projects operating under differing tax jurisdictions.

---

### 3.2 Liquidity & Net Working Capital (FAU Strategy Slide 68 & 138)

#### 4. Net Working Capital & Cash Conversion Cycle (CCC)
$$\text{NWC} = (\text{Work in Progress} + \text{Accounts Receivable}) - \text{Accounts Payable}$$
$$\text{CCC} = \text{DIO} + \text{DSO} - \text{DPO}$$
* $\text{DIO}$ = Days Inventory Outstanding (materials & WIP tied up on site).
* $\text{DSO}$ = Days Sales Outstanding (client payment latency).
* $\text{DPO}$ = Days Payables Outstanding (vendor invoice terms).
* **Cash Shortage Guardrail (*Görög 2009*):** Even if a project is technically profitable on paper, if $\text{DSO} - \text{DPO} > 45\text{ days}$, FAUnance alerts management to a projected liquidity deficit before subcontractor payments drain working capital.

---

### 3.3 EVM-to-EBITDA Operational Variance Engine

#### 5. Target Cost Allocation
$$\text{Planned Cost (BAC)} = \text{Planned Revenue} \times \left(1 - \frac{\text{Target EBITDA \%}}{100}\right)$$
* *Example:* Work package with $€1,000,000$ Planned Revenue and $15\%$ Target EBITDA $\rightarrow \text{BAC} = €850,000$.

#### 6. Dynamic Real-Time EBITDA Variance
$$\text{Actual EBITDA}_t = \text{Earned Value (EV)}_t - \text{Actual Cost (AC)}_t$$
$$\text{EBITDA Variance}_t = \text{Actual EBITDA}_t - \text{Target EBITDA}_t$$

#### 7. Estimate at Completion (EAC) Forecasting
* **Standard Cost-Efficiency Forecast:**
  $$\text{EAC}_{\text{cost}} = \frac{\text{BAC}}{\text{CPI}} = \text{AC} + \frac{\text{BAC} - \text{EV}}{\text{CPI}}$$
* **Composite Cost & Schedule Forecast (Anbari 2003):**
  $$\text{EAC}_{\text{composite}} = \text{AC} + \frac{\text{BAC} - \text{EV}}{\text{CPI} \times \text{SPI}}$$
  Where $\text{CPI} = \frac{\text{EV}}{\text{AC}}$ and $\text{SPI} = \frac{\text{EV}}{\text{PV}}$.

---

### 3.4 Production Learning & Risk Control

#### 8. Experience Curve Law (BCG / Handout Slide 41)
$$C_n = C_1 \times n^{-b}$$
* Unit costs decline predictably by 20%–30% with each doubling of cumulative output in repetitive fabrication (e.g., serial ship hull blocks or standardized piping assemblies).

#### 9. Sensitivity Analysis for Risk Control (Handout Slide 135)
* Evaluates financial impact under parameter shifts:
  * Material Price Surge ($\pm 3\%, \pm 8\%$)
  * Labor Rate / Overtime Variance ($\pm 5\%, \pm 12\%$)
  * Milestone Certification Delay ($+15, +30\text{ days}$)
* Directly feeds the **Calibrated Confidence Score** (Best-Case, Base-Case, Worst-Case EBITDA trajectories).

---

## 4. Architectural Differentiation: Deterministic Modeling vs. Black-Box AI

| Dimension | Black-Box ML / Generic Approaches | FAUnance Deterministic Architecture |
| :--- | :--- | :--- |
| **Calculation Logic** | Statistical regression / LLM extrapolation | **Deterministic EVM & accounting math** (100% reproducible) |
| **Data Provenance** | Unverified self-reported spreadsheets | **Traceable link to ERP POs & daily site receipts** |
| **Cash-Flow View** | Ignores payment schedules and working capital | **Integrated Working Capital (CCC) and milestone liquidity tracking** |
| **Governance & Trust** | Automated black-box budget adjustments | **Human-in-the-Loop:** Supervisor sign-off required for changes |
| **Regulatory Alignment** | Unchecked AI automation risk | **Designed with EU AI Act High-Risk oversight principles in mind** |

---

## 5. The Two-Speed Dynamic Reconciliation Architecture

```
┌────────────────────────────────────────────────────────────────────────┐
│ SPEED 1: REAL-TIME EDGE TELEMETRY (Daily / On-Site)                    │
│ • Subcontractor timesheets logged on mobile devices.                   │
│ • On-the-spot material delivery receipts & equipment hours logged.     │
│ • System calculates: AC_estimated = Hours × Standard Rate + Receipts.  │
│ • Daily supervisor signs off on task completion (EV).                  │
│ • Status: Labelled "ESTIMATED".                                        │
└───────────────────────────────────┬────────────────────────────────────┘
                                    │ Automated Variance Match
┌───────────────────────────────────▼────────────────────────────────────┐
│ SPEED 2: MONTH-END INVOICE RE-ENGINEERING (Official ERP Ingestion)      │
│ • Ingests official vendor invoices, bank debits, and payroll runs.     │
│ • Re-engineers delta: Δ = Invoiced Actuals − Estimated Edge Receipts.  │
│ • Flags discrepancies (e.g. unbilled subcontractor surcharges).        │
│ • Confirms final EBITDA numbers and updates future EAC projections.    │
│ • Status: Labelled "CONFIRMED".                                        │
└────────────────────────────────────────────────────────────────────────┘
```

---

## 6. Database Schema & Telemetry Specification

```sql
-- Work Breakdown Structure & EBITDA Target
CREATE TABLE WorkPackage (
    wp_id VARCHAR(50) PRIMARY KEY,
    project_id VARCHAR(50) NOT NULL,
    planned_revenue DECIMAL(15, 2) NOT NULL,
    target_ebitda_pct DECIMAL(5, 2) NOT NULL,  -- e.g. 15.00%
    cost_budget DECIMAL(15, 2) NOT NULL,       -- planned_revenue * (1 - target_ebitda_pct / 100.0)
    planned_value DECIMAL(15, 2) NOT NULL
);

-- Real-Time Site Transactions (Speed 1: Edge Telemetry)
CREATE TABLE SiteTelemetry (
    telemetry_id VARCHAR(50) PRIMARY KEY,
    wp_id VARCHAR(50) REFERENCES WorkPackage(wp_id),
    worker_hours DECIMAL(6, 2) NOT NULL,
    hourly_rate DECIMAL(8, 2) NOT NULL,
    material_receipt_cost DECIMAL(12, 2) DEFAULT 0.00,
    earned_progress_pct DECIMAL(5, 2) NOT NULL,
    supervisor_id VARCHAR(50),                 -- Nullable at initial edge capture
    supervisor_signed_at TIMESTAMP,            -- Populated upon supervisor approval gate
    status VARCHAR(20) DEFAULT 'ESTIMATED'
);

-- Official Invoiced ERP Records (Speed 2: Batch Reconciliation)
CREATE TABLE ERPRecord (
    invoice_id VARCHAR(50) PRIMARY KEY,
    wp_id VARCHAR(50) REFERENCES WorkPackage(wp_id),
    booked_amount DECIMAL(15, 2) NOT NULL,
    payment_terms_days INT NOT NULL,           -- DPO calculation
    reconciled_delta DECIMAL(12, 2),           -- Nullable until matched with edge slip
    reconciled_at TIMESTAMP,                   -- Nullable until batch reconciliation
    status VARCHAR(20) DEFAULT 'CONFIRMED'
);
```

---

## Appendix: Corporate-Level Valuation & Future Strategic Extensions

> [!NOTE] **Scope Demarcation**  
> Operational project teams manage performance up to **EBITDA, EVM, and Working Capital**. The valuation metrics below operate at the corporate treasury/executive board level and represent strategic future extensions.

### A.1 Capital Efficiency: EVA & Value Driver Tree (FAU Strategy Slide 136)
$$\text{EVA} = \text{NOPAT} - (\text{Capital Employed} \times \text{WACC})$$

```
                            EVA (Economic Value Added)
                                       │
                  ┌────────────────────┴────────────────────┐
                  ▼                                         ▼
                NOPAT                               Cost of Capital
                  │                                         │
        ┌─────────┴─────────┐                     ┌─────────┴─────────┐
        ▼                   ▼                     ▼                   ▼
     Revenue              Costs                Capital             WACC
   (Price, Vol)      (Efficiency)             Employed           (Financing)
```
* **Application:** Evaluates enterprise wealth creation. If project return on capital ($\text{ROIC}$) does not exceed the corporate hurdle rate ($\text{WACC}$), running the project destroys shareholder value.

### A.2 Valuation & The "DCF Trap"
* **Discounted Cash Flow (DCF) Formula (Slide 138):**
  $$\text{DCF Value} = \sum_{t=1}^{n} \frac{\text{Free Cash Flow}_t}{(1 + \text{WACC})^t} + \frac{\text{Continuing Value}_n}{(1 + \text{WACC})^n}$$
* **The "DCF Trap" (Clayton M. Christensen et al., 2008):**
  * *Citation:* Christensen, C. M., Kaufman, S. P., & Shih, W. C. (2008). Innovation killers: How financial tools destroy your capacity to innovate. *Harvard Business Review*, 86(1), 98–105. *(Note: Authored by Clayton M. Christensen, distinct from David S. Christensen #1).*
  * *Core Concept:* Standard DCF appraisals typically compare an investment against an *assumed static baseline of doing nothing*. In competitive markets, doing nothing leads to rapid margin erosion. FAUnance protects against the deteriorating baseline.
