# FAUnance: Business Strategy, Valuation & Accounting Engine
## Master Specification: FAU Business Strategy Foundations, DSR Architecture, and Literature Defense

> **Lead Author & System Architect:** Shikhar Thakur  
> **Course Alignment:** Designing Technology (57074) — WiSe 2026/27  
> **Theoretical Grounding:** FAU Business Strategy (Prof. Dr. Harald Hungenberg, Chair of Strategic Management) & Chair Wi1 (Prof. Dr. Kathrin Möslein)  
> **Target Artifact:** Case B — **FAUnance** (Intelligent Financial Monitoring)  
> **File Location:** `DT/05_Project_Case_B/Shikhar_Business_Strategy_Formulas_FAUnance.md`  
> **Local Reference Source:** `DT/06_Business_Strategy/Business Strategy_Handout_Winter_term_2425_SV.pdf`

---

## ⚡ Executive Brief for Teammates (Read This First)

> [!NOTE] **What is this document?**  
> This file is the **formal mathematical and technical specification** for FAUnance's backend engine. It serves as our theoretical foundation for the Midterm presentation, our conceptual data model, and the upcoming 20–30 page DSR seminar paper. You do not need to memorize every equation—use this as our shared accounting, valuation, and governance reference manual.

### The Analogy: Avionics Blueprint vs. Cockpit Dashboard
* **The Dashboard UI:** What the project manager sees (progress bars, S-curves, status lights).
* **This Specification:** **The flight physics engine running inside the avionics computer.**  
  It defines the exact mathematical laws (Earned Value, EBITDA, Cash Conversion Cycle) that continuously calculate whether a project has enough financial runway before an alert ever blinks on the screen.

### The 3-Bullet Summary
1. **The Deterministic Math Core (Zero Hallucination):**  
   We do not allow probabilistic AI/LLMs to guess financial numbers. Project budgets, progress, and margins are calculated strictly via deterministic accounting math:  
   $$\text{Cost Budget} = \text{Planned Revenue} - \text{Target EBITDA}$$  
   $$\text{Actual EBITDA} = \text{Earned Value (EV)} - \text{Actual Cost (AC)}$$
2. **The Two-Speed Gearbox (Fast Daily vs. Slow Monthly):**  
   * **Speed 1 (Daily Edge Telemetry):** Field teams log delivery receipts & worker hours on mobile $\rightarrow$ instant estimated burn rate ($AC_{\text{est}}$) to kill the 30-day ERP blind spot.  
   * **Speed 2 (Month-End ERP Re-Engineering):** Official vendor invoices arrive in SAP $\rightarrow$ system auto-reconciles the delta ($\Delta$) against preliminary edge logs.
3. **The Defensive Armor (Academic & Corporate Grounding):**  
   Ties project tasks directly to corporate shareholder value (EVA, DCF, WACC from FAU Strategic Management) and anchors our governance rules in peer-reviewed literature (Bouwens 2019, Rozenbaum 2019, Jensen & Meckling 1976).

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
│    • EBITDA / EBIT / NOPAT operational boundary control                │
│    • EVA (Economic Value Added) & Value Driver Tree (Slide 136)        │
│    • DCF (Discounted Cash Flow) & MVA Shareholder Value (Slide 137–138)│
│    • Two-Speed Real-Time Site Burn vs. Month-End Re-Engineering Audit  │
└────────────────────────────────────────────────────────────────────────┘
```

---

## 2. Literature Defense: Shikhar's 3 Assigned Anchor Papers

These three verified papers from the team brief provide the academic foundation for our business strategy and governance rules:

### Paper 1 (#9): The EBITDA Validity & Gaming Defense
- **Citation:** Bouwens, J., de Kok, T., & Verriest, A. (2019). The prevalence and validity of EBITDA as a performance measure. *Comptabilité Contrôle Audit*, 25(1), 55–105.
- **Key Finding:** EBITDA provides an excellent operational proxy by isolating core performance from financing distortions. However, viewed in isolation, it can mask capital intensity and liquidity strain.
- **FAUnance Application:** Directly justifies why FAUnance benchmarks project teams **up to EBITDA**, but pairs it with **Cash Flow and Working Capital** to prevent managers from hiding equipment wear-and-tear.

### Paper 2 (#10): Capital Allocation & Leverage Choices
- **Citation:** Rozenbaum, O. (2019). EBITDA and managers' investment and leverage choices. *Contemporary Accounting Research*, 36(1), 513–546.
- **Key Finding:** Managers evaluated solely on EBITDA tend to overinvest in debt-financed assets because interest and depreciation are excluded from their metrics.
- **FAUnance Application:** Validates our strict **income statement control boundary**: project teams manage operational EBITDA, while executive boards and treasury monitor corporate EBIT, debt service, and WACC.

### Paper 3 (#18): Agency Theory & Information Asymmetry
- **Citation:** Jensen, M. C., & Meckling, W. H. (1976). Theory of the firm: Managerial behavior, agency costs and ownership structure. *Journal of Financial Economics*, 3(4), 305–360.
- **Key Finding:** Information asymmetry between principals (executives) and agents (site managers) leads to moral hazard—site managers conceal cost overruns and delay reporting.
- **FAUnance Application:** Resolves agency loss by replacing manual monthly reporting with **daily, tamper-evident site telemetry backed by mandatory supervisor sign-offs**.

---

## 3. Mathematical Foundations: FAU Business Strategy Integration

*(Directly mapped from Prof. Hungenberg's Business Strategy Handout, Winter Term 24/25)*

```
                       FAU BUSINESS STRATEGY VALUE ENGINE
                                       │
         ┌─────────────────────────────┼─────────────────────────────┐
         ▼                             ▼                             ▼
  OPERATIONAL MARGIN           CAPITAL EFFICIENCY            LIQUIDITY & TIMING
  (EBITDA, EBIT, NOPAT)         (EVA, MVA, ROIC)             (DCF, CCC, NWC)
  [Handout pp. 14-20]          [Handout pp. 135-137]         [Handout pp. 68, 138]
```

---

### Layer 1: Operating Profitability & Cost Control

#### 1. EBITDA (Operational Control Boundary)
$$\text{EBITDA} = \text{Operating Revenue} - \text{Direct Labor} - \text{Direct Materials} - \text{Site Overhead}$$
- **Strategic Role:** Measures operational cash generation before capital structure and depreciation policies.
- **Software Rule:** Every Work Breakdown Structure (WBS) package has an assigned Target EBITDA margin.

#### 2. EBIT & Operating Margin
$$\text{EBIT} = \text{EBITDA} - \text{Depreciation} - \text{Amortization}$$
$$\text{Operating Margin (\%)} = \frac{\text{EBITDA}}{\text{Operating Revenue}} \times 100$$
- **Alert Gate:** Any work package where $\text{Actual Margin} < \text{Target Margin} - 2.0\%$ triggers an immediate priority exception alert.

#### 3. NOPAT (Net Operating Profit After Taxes)
$$\text{NOPAT} = \text{EBIT} \times (1 - \text{Effective Tax Rate})$$
- **Strategic Role:** Normalizes returns across multi-national projects under different tax jurisdictions.

---

### Layer 2: Capital Efficiency & Economic Profit (FAU Strategy Slide 136–137)

#### 4. EVA (Economic Value Added) & The Value Driver Tree
*(Handout Slide 136: EVA and Value Drivers)*
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

- **Application to FAUnance:** Proves whether a project is creating or destroying shareholder value. If $\text{ROIC} < \text{WACC}$, accelerating project delivery destroys capital.

#### 5. MVA (Market Value Added) & Firm Value
*(Handout Slide 137: Economic Value Added and Shareholder Value)*
$$\text{MVA} = \sum_{t=1}^{n} \frac{\text{EVA}_t}{(1 + \text{WACC})^t}$$
$$\text{Total Project / Enterprise Value} = \text{Invested Capital} + \text{MVA}$$

---

### Layer 3: Valuation, Timing & The "DCF Trap" (FAU Strategy Slide 68 & 138)

#### 6. Discounted Cash Flow (DCF) Valuation
*(Handout Slide 138: Calculation of Company & Equity Value)*
$$\text{DCF Value} = \sum_{t=1}^{n} \frac{\text{Free Cash Flow}_t}{(1 + \text{WACC})^t} + \frac{\text{Continuing Value}_n}{(1 + \text{WACC})^n}$$
$$\text{Equity Value} = \text{DCF Enterprise Value} - \text{Net Debt}$$

#### 7. Avoiding the "DCF Trap" (Christensen, 2008 / Handout Slide 68)
- **The Core Flaw in Traditional Finance:** Financial models typically compare an investment against an *assumed flat cash stream resulting from doing nothing*.
- **The Reality:** Doing nothing causes rapid margin decay.
- **Strategic Justification for FAUnance:** Implementing FAUnance prevents margin erosion. The value created is the delta between the degrading baseline and the protected margin.

#### 8. Net Working Capital & Cash Conversion Cycle (CCC)
$$\text{NWC} = (\text{Work in Progress} + \text{Accounts Receivable}) - \text{Accounts Payable}$$
$$\text{CCC} = \text{DIO} + \text{DSO} - \text{DPO}$$
- **Strategic Rule:** Detects liquidity crunches. If $\text{DSO} - \text{DPO} > 45\text{ days}$, FAUnance warns management that supplier payables will drain cash reserves before client milestone revenue arrives.

---

### Layer 4: EVM-to-EBITDA Operational Variance Engine

#### 9. Target Cost Allocation
$$\text{Planned Cost (BAC)} = \text{Planned Revenue} - \text{Target EBITDA}$$
- Example: $€1,000,000$ Revenue, $15\%$ Target Margin $\rightarrow \text{Cost Budget} = €850,000$.

#### 10. Dynamic Real-Time EBITDA Variance
$$\text{Actual EBITDA}_t = \text{Earned Value (EV)}_t - \text{Actual Cost (AC)}_t$$
$$\text{EBITDA Variance} = \text{Actual EBITDA}_t - \text{Target EBITDA}_t$$

#### 11. Multi-Factor Estimate at Completion (EAC)
$$\text{CPI} = \frac{\text{EV}}{\text{AC}}, \quad \text{SPI} = \frac{\text{EV}}{\text{PV}}$$
$$\text{EAC} = \frac{\text{BAC}}{\text{CPI} \times \text{SPI}}$$

---

### Layer 5: Organizational Learning & Sensitivity Control

#### 12. The Experience Curve Law (BCG / Handout Slide 41)
$$C_n = C_1 \times n^{-b}$$
- Unit cost drops by $20\%–30\%$ with every doubling of cumulative volume.
- **Application:** Captures the empirical finding from our 45-project PLOS ONE case study: as site engineers log data repeatedly over 11 months, logging accuracy rises and variance declines.

#### 13. Sensitivity Analysis for Risk Control (Handout Slide 135)
- Evaluates deviations across:
  - Product / Material Cost ($\pm 3\%, \pm 8\%$)
  - Labor Productivity
  - Client Payment Delays
- Directly powers FAUnance's **Calibrated Confidence Score** (Best-Case, Base-Case, Worst-Case EBITDA trajectories).

---

## 4. Competitive Differentiation: Outperforming Team 3

| Feature | Team 3 (Likely Pitfall) | FAUnance (Our Winning Design) |
| :--- | :--- | :--- |
| **Prediction Logic** | Black-box LLM / naive ML regression | **Deterministic FAU Strategy formulas + Two-Speed Reconciliation** |
| **Data Integrity** | Unverified user inputs | **Mandatory frontline supervisor approval gates (PLOS ONE)** |
| **Auditability** | Cannot explain where numbers came from | **Full source lineage back to ERP POs & timesheets** |
| **Cash-Flow View** | Ignores working capital timing | **Integrated DCF, DSO/DPO, and milestone liquidity tracking** |
| **EU AI Act Fit** | High regulatory risk (black-box decisions) | **100% compliant: transparent XAI with calibrated confidence** |

---

## 5. The Two-Speed Dynamic Reconciliation Architecture

```
┌────────────────────────────────────────────────────────────────────────┐
│ SPEED 1: REAL-TIME EDGE TELEMETRY (Daily / On-Site)                    │
│ • Subcontractor timesheets logged on mobile devices.                   │
│ • On-the-spot material delivery receipts & equipment hours logged.     │
│ • System calculates: AC_estimated = Hours × Standard Rate + Receipts.  │
│ • Daily supervisor signs off on task completion (EV).                  │
│ • Status: Labelled "Estimated / Preliminary".                          │
└───────────────────────────────────┬────────────────────────────────────┘
                                    │ Automated Variance Match
┌───────────────────────────────────▼────────────────────────────────────┐
│ SPEED 2: MONTH-END INVOICE RE-ENGINEERING (Official ERP Ingestion)      │
│ • Ingests official vendor invoices, bank debits, and payroll runs.     │
│ • Re-engineers delta: Δ = Invoiced Actuals − Estimated Edge Receipts.  │
│ • Flags discrepancies (e.g. unbilled subcontractor surcharges).        │
│ • Confirms final EBITDA numbers and updates future EAC projections.    │
│ • Status: Labelled "Confirmed / Audited".                              │
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
    cost_budget DECIMAL(15, 2) NOT NULL,       -- planned_revenue * (1 - target_ebitda_pct)
    planned_value DECIMAL(15, 2) NOT NULL,
    wacc DECIMAL(5, 2) DEFAULT 11.20           -- FAU Strategy Handout p. 138 benchmark
);

-- Real-Time Site Transactions (Speed 1)
CREATE TABLE SiteTelemetry (
    telemetry_id VARCHAR(50) PRIMARY KEY,
    wp_id VARCHAR(50) REFERENCES WorkPackage(wp_id),
    worker_hours DECIMAL(6, 2) NOT NULL,
    hourly_rate DECIMAL(8, 2) NOT NULL,
    material_receipt_cost DECIMAL(12, 2) DEFAULT 0.00,
    earned_progress_pct DECIMAL(5, 2) NOT NULL,
    supervisor_id VARCHAR(50) NOT NULL,
    supervisor_signed_at TIMESTAMP NOT NULL,   -- Mandatory HITL gate
    status VARCHAR(20) DEFAULT 'ESTIMATED'
);

-- Official Invoiced ERP Records (Speed 2)
CREATE TABLE ERPRecord (
    invoice_id VARCHAR(50) PRIMARY KEY,
    wp_id VARCHAR(50) REFERENCES WorkPackage(wp_id),
    booked_amount DECIMAL(15, 2) NOT NULL,
    payment_terms_days INT NOT NULL,           -- DPO calculation
    reconciled_delta DECIMAL(12, 2) NOT NULL,  -- Invoiced - Estimated
    reconciled_at TIMESTAMP NOT NULL,
    status VARCHAR(20) DEFAULT 'CONFIRMED'
);
```

---

## 7. Executive Defense Script (For Mid-Term Presentation & Seminar Paper)

When presenting or defending this architecture to Prof. Möslein and Joni:

> *"Our system does not rely on opaque AI guesses.  
> Following the theoretical foundations of FAU Business Strategy (Prof. Hungenberg), we ground our engine in **deterministic valuation and accounting mathematics**: EVA value-driver decomposition, EBITDA operational boundaries, and DCF liquidity timing.*  
> *We combine **real-time edge logging** from site workers with **month-end ERP invoice re-engineering**, creating a two-speed architecture that catches margin erosion weeks before traditional accounting close.*  
> *The AI layer operates strictly as an **explainable decision-support co-pilot**—flagging calibrated variance exceptions while requiring human supervisor authorization for any budget adjustments."*
