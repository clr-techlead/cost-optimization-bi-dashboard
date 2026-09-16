# Power BI Data Model

## Model approach

The dashboard uses a star-schema design. Expenses is the central fact table, while dimensions provide filtering and analysis context.

## Fact table

### Expenses

- Grain: one row per expense transaction
- Measures: Budget, ActualCost, Budget Variance, Savings Opportunity
- Keys: TransactionID, Date, Department, Category, Supplier, CostType

## Dimensions

### Date

- Date
- Year
- Quarter
- Month Number
- Month Name

### Department

- Department
- Department Group

### Category

- Category
- Cost Family

### Supplier

- Supplier
- Supplier Tier

### Cost Type

- CostType

## Relationships

- Date[Date] 1 → * Expenses[Date]
- Department[Department] 1 → * Expenses[Department]
- Category[Category] 1 → * Expenses[Category]
- Supplier[Supplier] 1 → * Expenses[Supplier]
- Cost Type[CostType] 1 → * Expenses[CostType]

Single-direction filtering should flow from dimensions to the fact table.

## Data types

- Date: Date
- Budget: Decimal number
- ActualCost: Decimal number
- TransactionID: Text
- Department, Category, Supplier, CostType, Status: Text

## Design principles

- Keep business logic in measures where possible.
- Use an explicit date dimension for time intelligence.
- Avoid bi-directional relationships unless there is a documented requirement.
- Keep the model simple, auditable, and easy to extend.
