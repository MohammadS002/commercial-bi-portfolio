# Commercial Excellence and Profitability

> **DEMO · SYNTHETIC DATA** — All figures, data labels, and example findings shown here are fictional and do not represent actual company results.

## Business question

Find the products and customers that contribute profit and the combinations that need a margin review.

## My contribution

Commercial Excellence (ComEx) is a management review that brings sales, profitability, inventory, retail visibility, and marketing together to decide what the commercial team should act on. I developed executive reporting and analyzed net sales, cost of goods sold, gross profit, and margin by product and customer.

## Decision supported

Use the product and customer margin breakdowns to identify a follow-up, then assign an owner to validate the drivers.

## Full-page walkthrough

These visuals adapt the layout of the interactive Q3 ComEx report for a profitability case study. The overview summarizes the quarter and the detail shows where to investigate pricing, discounts, product mix, and costs.

### Q3 executive profitability overview

![Synthetic Q3 ComEx executive overview with net sales, COGS, gross profit and margin](../../images/comex-q3-profitability.png)

### Product and customer profitability

![Synthetic product and customer profitability rankings and margin review](../../images/comex-product-customer.png)

### Commercial priorities

The commercial review connects sales recovery, stock cover, shelf presence, and marketing spend. In this demo, Product C earns a 35% gross margin and has 1.5 months of cover. Review incoming supply before expanding distribution.

![Full commercial priorities page showing target achievement, stock cover, shelf presence, and marketing budget](../../images/comex-commercial-priorities.png)

### Recommended Actions

![Full action review page linking commercial signals to recommended actions and suggested owners](../../images/comex-action-review.png)

I turned ComEx findings into recommended actions for the commercial review. Each recommendation states what the data shows, what the team should check or change, and who could follow up.

| Demo finding | Recommended action | Suggested owner |
| --- | --- | --- |
| Product A with Customer A contributes 25% of sales at an 18% gross margin, versus 28% overall. | Review realized prices, discounts, and unit costs before changing commercial terms. | Sales and Finance |
| Product C earns a 35% margin and contributes $21K gross profit. | Check incoming supply before expanding distribution. | Brand and Supply |
| Customer B has shelf presence in 2 of 6 branches. | Validate demand and space at the remaining branches. | Trade Marketing |
| Brand A is short of its sales target and has used 120% of its marketing budget. | Review campaign spend and sales response before committing additional budget. | Marketing and Sales |

## Technical walkthrough

This example uses synthetic sales data to illustrate how the profitability view can be built and checked.

```mermaid
flowchart LR
    Product["Product dimension"] --> Sales["Sales fact"]
    Customer["Customer dimension"] --> Sales
    Date["Date dimension"] --> Sales
    Sales --> KPI["Net sales, COGS, gross profit, and margin"]
```

With a sales fact at invoice-line grain, product, customer, and period selections filter both net sales and cost. Calculate margin as a ratio of totals so the result remains valid when rolling up across customers and products.

```dax
Gross Profit = [Net Sales] - [COGS]

Gross Margin % = DIVIDE ( [Gross Profit], [Net Sales] )
```

**Validation example.** Suppose one product has $1,000 in net sales and $700 in cost, while another has $200 in sales and $180 in cost. The total gross profit is $320 and the total margin is 26.67% ($320 / $1,200). Averaging the individual margins of 30% and 10% would incorrectly return 20%. A zero-sales slice returns a blank margin.

[Back to all projects](../../README.md)
