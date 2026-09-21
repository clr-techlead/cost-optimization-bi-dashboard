# Dashboard Specification

## Purpose

The dashboard is designed for finance and business leaders who need to identify cost drivers, understand budget deviations, and prioritize savings actions.

## Implementation status (as built)

The live Power BI report ("Cost Optimization Executive Overview", published in Power BI Service) consolidated the original 3-page plan into 2 pages for a tighter narrative flow. What shipped:

- **Executive Summary** page — combines the planned Page 1 (Executive Overview) KPIs and charts with narrative-driven titles and a headline banner stating the key insight (e.g. "Spend is 5.7% over budget, led by CloudCore").
- **Transaction Detail** page — a full transaction table with native Power BI conditional formatting on the Status column (red = Over Budget, green = Within Budget), plus Department and Cost Type filters.
- Corporate blue/gray visual style applied across both pages (navy header row, clean white cards).
- Not yet implemented: icons on KPI cards, the decomposition tree and opportunity-ranking visuals from the original Page 2/Page 3 plans, and the semantic color system (blue/purple/amber/green) described below — these remain candidates for a future iteration.

## Page 1 — Executive Overview

### Primary questions

- Are we spending above or below budget?
- Which departments and suppliers are driving the variance?
- How large is the addressable savings opportunity?

### Recommended visuals

- KPI cards: Total Spend, Total Budget, Budget Variance, Savings Opportunity
- Monthly spend versus budget line and column chart
- Department variance bar chart
- Spend composition by Cost Type
- Top suppliers by variance
- Date, Department, Category, Supplier, Cost Type, and Status slicers

## Page 2 — Cost Driver Analysis

### Primary questions

- Which categories and suppliers require investigation?
- Is the variance concentrated in recurring or variable costs?
- Which transactions have the largest impact?

### Recommended visuals

- Decomposition tree from Budget Variance to Department, Category, and Supplier
- Category and supplier spend and variance table
- Scatter plot comparing Actual Cost and Budget
- Conditional formatting for high-risk transactions

## Page 3 — Savings Opportunity

### Primary questions

- Where can cost reduction actions create the greatest impact?
- Which opportunities should be prioritized first?
- Who should own the next action?

### Recommended visuals

- Opportunity ranking by department and supplier
- Savings opportunity by cost type
- Opportunity versus implementation effort matrix
- Action tracker with owner, status, target date, and estimated benefit

## Interaction design

- All pages should respond to shared slicers.
- Clicking a department should cross-filter categories, suppliers, and transactions.
- Tooltips should show Budget, Actual Cost, Variance, and Savings Rate.
- Users should be able to drill through from a summary visual to transaction detail.
- Use a consistent semantic color system: blue for budget, purple for actual spend, amber for risk, and green for savings.

## Decision rules

- Highlight positive variance when Actual Cost exceeds Budget.
- Prioritize opportunities by estimated value, controllability, and recurrence.
- Do not present synthetic results as confirmed financial savings.
- Show the data freshness date and source status on every executive page.

## Acceptance criteria

- A business user can identify the largest cost driver in under 30 seconds.
- Every KPI can be traced back to the source transaction table.
- Filters and drill-through interactions work consistently across pages.
- The report clearly distinguishes budget, actual spend, variance, and savings opportunity.
- The dashboard includes a visible synthetic-data disclaimer until production sources are connected.
