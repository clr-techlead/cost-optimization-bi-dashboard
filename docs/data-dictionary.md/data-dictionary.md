# Data Dictionary

Source file: [expenses.csv](../data/expenses.csv)

This document defines the fields, grain, and business rules used by the Cost Optimization & Business Intelligence Dashboard.

## Dataset grain

One row represents one expense transaction recorded for a department, category, supplier, and date.

## Columns

| Column | Type | Definition |
| --- | --- | --- |
| TransactionID | Text | Unique identifier for the expense transaction. |
| Date | Date | Date on which the transaction was recorded. |
| Department | Text | Business area responsible for the expense. |
| Category | Text | Expense classification such as Software, Travel, or Hardware. |
| Supplier | Text | Vendor associated with the transaction. |
| Budget | Decimal | Approved budget amount for the transaction. |
| ActualCost | Decimal | Final recorded cost of the transaction. |
| CostType | Text | Recurring, Project, or Variable expense classification. |
| Status | Text | Budget status: Within Budget or Over Budget. |

## Business rules

- **Budget Variance** = ActualCost - Budget
- **Savings Opportunity** = positive Budget Variance for transactions flagged as Over Budget
- **Savings Rate** = Savings Opportunity / ActualCost
- A positive variance indicates an overspend.
- A negative variance indicates spending below budget.
- Currency values are intentionally represented as generic units because the dataset is synthetic.

## Data quality checks

- TransactionID must be unique and non-empty.
- Date must be a valid date.
- Budget and ActualCost must be numeric and non-negative.
- Department, Category, Supplier, CostType, and Status must be populated.
- Status should agree with the comparison between ActualCost and Budget.

## Power BI modeling notes

The transaction table will act as the central fact table. Future dimension tables may include Date, Department, Category, Supplier, and Cost Type to support a star-schema model.
