# MavenTech — B2B Sales Pipeline Analysis

A Google Sheets project that turns an opportunity-level CRM export into a sales-pipeline analysis and performance dashboard.

## Project overview

This project analyses the `sales_pipeline.csv` extract from Maven Analytics' **CRM Sales Opportunities** dataset. The dataset describes a fictional B2B company that sells computer hardware. This workbook focuses on opportunity stages, closed-deal outcomes, won revenue, sales-agent performance, product performance, and monthly revenue patterns.

The workbook is designed as a practical reporting tool for reviewing pipeline health and comparing sales performance. It is descriptive analysis, not a predictive model or causal study.

## Business questions

1. How are opportunities distributed across Prospecting, Engaging, Won, and Lost?
2. What percentage of closed opportunities are won?
3. Which sales agents and products contribute the most won revenue?
4. How does won revenue change by closing month?

## Workbook contents

| Sheet | Purpose |
|---|---|
| `01_Project_Guide` | Project summary, KPI definitions, findings, data-quality notes, and workbook navigation |
| `02_Raw_Data` | Original opportunity-level source extract retained for reference |
| `03_Cleaned_Data` | Prepared opportunity data and derived fields such as `Won_Revenue`, `Close_Month`, and `Sales_Cycle_Days` |
| `04_Pivot_Analysis` | Pivot tables and summary calculations used for the analysis |
| `05_Dashboard` | Charts and dashboard controls for reviewing pipeline and revenue performance |

## Tools and techniques

- Google Sheets
- Data inspection and cleaning
- Spreadsheet formulas and calculated fields
- Pivot tables
- Charts and dashboard layout
- Dropdown-based dashboard controls

## KPI definitions

- **Total Opportunities:** count of unique `opportunity_id` values.
- **Closed Opportunities:** Won + Lost opportunities.
- **Closed-Deal Win Rate:** Won ÷ (Won + Lost) × 100. Open opportunities are excluded from the denominator.
- **Won Revenue:** sum of `close_value` for Won opportunities only.
- **Open Opportunities:** Prospecting + Engaging opportunities.
- **Sales Cycle Days:** `close_date` minus `engage_date`, where both dates are available.

## Key findings

The analysed extract contains **8,800 opportunities**:

- **4,238 Won** opportunities
- **2,473 Lost** opportunities
- **2,089 Open** opportunities (1,589 Engaging and 500 Prospecting)
- **6,711 Closed** opportunities
- **63.15% closed-deal win rate**
- **10,005,534** total Won Revenue, expressed in dataset units (no currency symbol is assumed)

Additional observations:

- `GTXPro` has the highest product-level Won Revenue: **3,510,578**.
- `Darcel Schlecht` has the highest sales-agent Won Revenue: **1,153,214**.
- **June 2017** has the highest monthly Won Revenue: **1,338,466**.

These are descriptive findings from this extract; they do not establish why the differences occurred.

## Data quality and limitations

- The 8,800 `opportunity_id` values are unique; no duplicate IDs were identified.
- `account` is blank in 1,425 records.
- `engage_date` is blank in 500 records; these correspond to Prospecting opportunities.
- `close_date` and `close_value` are blank in 2,089 records; these correspond to open opportunities and should not automatically be treated as errors.
- This workbook analyses only the `sales_pipeline.csv` opportunity extract, not the other tables in the full Maven dataset.
- There is no lead-source, marketing-channel, or campaign field in this extract, so channel attribution cannot be analysed.
- The workbook does not establish a currency unit for `close_value`; revenue is therefore reported in dataset units.
- The records are historical (2016–2017) and describe a fictional company.
- Dashboard dropdown controls should be tested in the live Google Sheets version before describing their behaviour as fully interactive.

## Data source and attribution

**Maven Analytics — CRM Sales Opportunities**  
https://mavenanalytics.io/data-playground/crm-sales-opportunities

Maven Analytics describes the dataset as B2B sales-pipeline data for a fictitious computer-hardware company. Its current Data Playground listing shows 8,800 records and 18 fields across multiple tables. This project uses the `sales_pipeline.csv` opportunity extract only.

The workbook retains the source extract in `02_Raw_Data`. Before publishing a public copy, review the usage terms associated with the exact downloaded file/version. Keep the Maven Analytics source attribution with any shared version.

## How to explore

1. Start with `01_Project_Guide` for context and KPI definitions.
2. Review `02_Raw_Data` to understand the source fields.
3. Explore the derived columns in `03_Cleaned_Data`.
4. Review the summaries in `04_Pivot_Analysis`.
5. Use `05_Dashboard` for a high-level visual overview.

---

*Created as a portfolio project to demonstrate spreadsheet-based data preparation, analysis, reporting, and dashboard design.*
