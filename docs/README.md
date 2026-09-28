# Power BI Artifact Catalog

## Overview

This Power BI Project supports sales and store-performance analysis for Northwind Retail Group. Its Import semantic model brings together sales order lines, products, customers, stores, and calendar attributes; the Sales report uses the model for sales trends, brand and category comparisons, customer activity, and KPI summaries.

## Artifacts

| Artifact | Type | Source | Connected artifact(s) | Purpose | Documentation |
|---|---|---|---|---|---|
| Sales | Semantic model | `sales.SemanticModel/definition` | Used by the Sales report | Shared sales, product, customer, store, and calendar measures and dimensions. | [Open](sales.semantic-model.md) |
| Sales | Report | `sales.Report` | Sales semantic model (`sales.SemanticModel`) | Two-page report for sales analysis and a category-by-year KPI table. | [Open](sales.report.md) |

## Project Entry Point

Open [`sales.pbip`](../sales.pbip) in Power BI Desktop. The report's local model binding points to `../sales.SemanticModel`.

## Documentation Notes

- The semantic model document is based on Power BI Modeling MCP metadata and the repository's Northwind Retail Group context.
- The report's PBIR metadata was inspected with the Power BI report-authoring CLI. Screenshots are not included because approval to retain report images under the project was unavailable; see the capture limitation in the [report documentation](sales.report.md).
- The model metadata currently reports an unprocessed database and partitions without data. Report visuals are therefore documented from their definitions, not from observed rendered values.
