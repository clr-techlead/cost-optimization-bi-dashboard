# DAX Measures

These measures are designed for the Cost Optimization & Business Intelligence Dashboard. The source table is named Expenses.

## Core financial measures

### Total Spend

    DAX
    Total Spend = SUM(Expenses[ActualCost])

### Total Budget

    DAX
    Total Budget = SUM(Expenses[Budget])

### Budget Variance

    DAX
    Budget Variance = [Total Spend] - [Total Budget]

A positive value indicates that actual spending is above budget.

## Optimization measures

### Savings Opportunity

    DAX
    Savings Opportunity =
    SUMX(Expenses, MAX(Expenses[ActualCost] - Expenses[Budget], 0))

This estimates the amount of overspending that should be investigated or reduced.

### Savings Rate

    DAX
    Savings Rate = DIVIDE([Savings Opportunity], [Total Spend], 0)

Format as a percentage.

### Budget Compliance Rate

    DAX
    Budget Compliance Rate =
    DIVIDE(COUNTROWS(FILTER(Expenses, Expenses[Status] = "Within Budget")), COUNTROWS(Expenses), 0)

## Operational measures

### Transaction Count

    DAX
    Transaction Count = COUNTROWS(Expenses)

### Average Transaction Cost

    DAX
    Average Transaction Cost = AVERAGE(Expenses[ActualCost])

### Over Budget Transactions

    DAX
    Over Budget Transactions = CALCULATE([Transaction Count], Expenses[Status] = "Over Budget")

## Recommended visuals

- KPI cards: Total Spend, Budget Variance, Savings Opportunity, Savings Rate.
- Bar chart: Savings Opportunity by Department.
- Matrix: Category and Supplier with Actual Cost and Variance.
- Line chart: Total Spend and Total Budget by Month.
- Decomposition tree: Savings Opportunity by Department, Category, and Supplier.
