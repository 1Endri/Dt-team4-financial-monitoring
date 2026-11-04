# Case B: Intelligent Financial Monitoring

> **Course:** Designing Technology (57074) — WiSe 2026/27  
> **Institution:** Friedrich-Alexander-Universität Erlangen-Nürnberg (FAU)  
> **Chair:** Information Systems I, Innovation and Value Creation (Prof. Dr. Kathrin Möslein)  
> **Team:** Team 4 (Case B)  

---

## 1. Executive Summary & Case Overview

Project managers regularly monitor budgets, actual costs, committed expenses, forecasts, margins, and milestone invoicing across multiple concurrent initiatives. However, financial data is fragmented across siloed ERPs, local spreadsheets, and email exchanges, creating critical reporting latency and blinding decision-makers to cost deviations until after the damage is done.

**Mission:** Design a digital financial reporting artifact that consolidates approved multi-source project data into a single source of truth, automates exception detection (budget overruns, margin slippage, delayed billing), and provides interactive decision-support with human-in-the-loop (HITL) oversight.

---

## 2. Problem Space & Root Cause Analysis

### Identified Problem
> **Fragmented financial data across disconnected ERPs and email threads delays reporting, preventing project managers from detecting budget deviations and margin erosion before they become critical.**

### 5-Whys Root Cause Chain
1. *Why are overruns discovered too late?* $\to$ Review cycles occur only during retrospective monthly reporting.
2. *Why are reviews purely monthly?* $\to$ Compiling financial figures takes days of manual spreadsheet chasing.
3. *Why does compilation take so long?* $\to$ Budgets, POs, invoices, and actuals reside in disconnected systems.
4. *Why are sources disconnected?* $\to$ No unified integration pipeline continuously normalizes and reconciles transaction streams.
5. *Why is this fatal (Root Cause)?* $\to$ **Without automated exception detection and continuous reconciliation, financial intervention remains reactive rather than preventative.**

---

## 3. Research Framing (Design Science Research)

### Primary Research Question
> **"How can an intelligent financial monitoring tool be designed to consolidate multi-source project data and detect budget deviations in real time while maintaining transparency and human-in-the-loop oversight?"**

### Sub-Research Questions (SRQs)
* **SRQ 1 (Data Model & Ingestion):** *How can fragmented records (ERP budgets, committed purchase orders, actual expenses, and invoices) be conceptually unified into an auditable data model?*
* **SRQ 2 (Exception Detection Engine):** *What algorithmic rules reliably flag budget deviations, margin erosion, and cash flow bottlenecks before they become irreversible?*
* **SRQ 3 (Human-in-the-Loop Interaction):** *How should financial anomalies and forecasting trajectories be visualized in an interactive dashboard to enable fast, auditable human verification and corrective action?*

---

## 4. Required Project Deliverables

| Deliverable | Description |
|---|---|
| **1. Conceptual Data Model** | Unified schema integrating budgets, actuals, committed expenses, cash flow, and vendor invoices. |
| **2. Exception Engine Logic** | Automated rules/heuristics detecting margin erosion, cost overruns, and invoicing lag. |
| **3. Financial Dashboard Mockups** | UI displaying cash flow, margins, variance analysis, and audit trails. |
| **4. Scenario Walkthrough** | Step-by-step trace showing how an anomaly (e.g. 15% budget overrun) is flagged, presented, reviewed, and acted upon. |

---

## 5. Key Milestones & Deadlines

| Milestone | Date / Deadline | Deliverable | Weight |
|---|---|---|:---:|
| **Mid-Term Presentation** | **Wed 09.12.2026** *(10:00–13:00)* | Problem definition, conceptual architecture & early mockups | Gate |
| **Final Deck Submission** | **Tue 26.01.2027** *(23:55)* | Presentation slides & demo links | — |
| **Final Presentation** | **Wed 27.01.2027** *(10:30–14:45)* | Live prototype demonstration & defense | **50%** |
| **Seminar Paper** | **Mon 15.02.2027** *(23:55)* | Final academic DSR research paper | **50%** |

---

## 6. Core Design Principles

1. **Automate Repetitive Tasks:** Ingestion, parsing, and variance computation.
2. **Ensure Transparency:** Trace every KPI directly back to underlying ERP/PO source records.
3. **Handle Uncertainty:** Flag data inconsistencies and anomalies rather than making speculative assumptions.
4. **Enable Human Intervention (HITL):** Require interactive user review before reports or alerts are published.
5. **Maintain Accountability:** Clearly distinguish autonomous alerts from human-gated financial decisions.
