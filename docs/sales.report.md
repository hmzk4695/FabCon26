# Sales Report

## Overview

The Sales report supports Northwind Retail Group's sales and store analysis. It starts with a Sales analysis page for net sales by product and month, customer activity, and a store scatter analysis, followed by a KPI page that compares sales, margin, and cost by category and year.

| Property | Value |
|---|---|
| Source | `sales.Report` |
| Semantic model | [Sales](sales.semantic-model.md), bound by local path to `../sales.SemanticModel` |
| Pages | 2 |
| Landing page | Sales |

Report metadata shows no report-level filters. The Sales page has four categorical page filters and the KPI page has none. The report uses the Fluent2 base theme and a registered CopilotDefault custom theme.

## Report Flow

The Sales page is the landing page and provides a calendar date slicer, summary measures, product comparisons, and monthly sales trends. Users can then open the KPI page for a category-by-year table of Sales Amount, Margin, and Cost. The Sales page is also configured as a drillthrough destination requiring Calendar Year.

Cross-visual filtering is enabled in the visual definitions. No custom page-navigation buttons or bookmarks were found; report page navigation is through the standard page tabs.

## Pages

### Sales

**Screenshot limitation:** A screenshot was not captured. The preview CLI reported Desktop available, but approval to retain report imagery in this project was unavailable. Visual descriptions below are based on report page and visual metadata; exact rendered appearance and values were not verified.

The landing page is titled “Northwind Retail Group - Sales Analysis.” It brings the core commercial measures together, then supports comparisons by product, customer gender, store, and month.

#### Main Metrics

- **Sales Amount**: Net sales revenue, built from quantity multiplied by net unit price.
- **Sales Amount Avg per Day**: Average net sales over dates with a nonblank sales result in the current date context.
- **# Customers (w/ Sales)**: Distinct customers appearing in filtered sales rows.
- **Margin**: Gross margin dollars, not a margin percentage.
- **Sales Amount (LY)**: Comparable prior-year net sales, subject to the measure's current-period-positive condition.
- **Moving average**: A visual calculation, `MOVINGAVERAGE([Sales Amount], 12)`, over the area chart's monthly categories; it is defined in the report visual rather than as a reusable model measure.

#### Analysis Breakdowns

- A clustered bar chart compares Sales Amount by Product Category, with Subcategory and Product available as lower levels in the category hierarchy.
- A bar chart compares Sales Amount by Product Brand and Customer Gender; the product hierarchy includes Product as a lower level.
- A scatter chart plots monthly Sales Amount by Store, sizes points by distinct purchasing customers, and uses Calendar Month Name on the horizontal axis.
- An area chart plots Sales Amount and Sales Amount (LY) by Calendar Year-Month, alongside the 12-period visual moving average.
- A date slicer uses Calendar Date.

#### Available Filters

| Scope | Filter or slicer | Behavior / default |
|---|---|---|
| Page | `Calendar[Year]` | Categorical filter configured for single selection; no selected year is recorded in the page definition. |
| Page | `Product[Category]` | Categorical page filter; no selected value is recorded. |
| Page | `Product[Subcategory]` | Categorical page filter; no selected value is recorded. |
| Page | `Store[Store]` | Categorical page filter; no selected store is recorded. |
| Visual | `Calendar[Year]` on the Brand/Gender bar chart | Categorical visual filter; no selected year is recorded. |
| Visual | `Calendar[Date]` slicer | Date field sorted ascending; no selected date range is recorded. |

#### Interactions and Navigation

The page has a Year-based drillthrough binding. The report visuals enable cross-filtering/drill filtering according to their definitions. No custom navigation controls or bookmarks were found.

### KPI

**Screenshot limitation:** A screenshot was not captured. The preview CLI reported Desktop available, but approval to retain report imagery in this project was unavailable. Visual descriptions below are based on report page and visual metadata; exact rendered appearance and values were not verified.

The page is titled “Northwind Retail Group - KPI” and contains a table-style summary, titled “KPI table.” It presents a compact category and year comparison rather than a separate set of KPI cards.

#### Main Metrics

- **Sales Amount**: Net sales revenue.
- **Margin**: Gross margin dollars.
- **Cost**: Quantity multiplied by unit cost.

#### Analysis Breakdowns

- Product Category appears on rows.
- Calendar Year appears in columns.
- Sales Amount, Margin, and Cost appear as values.

#### Available Filters

| Scope | Filter or slicer | Behavior / default |
|---|---|---|
| Page | None found | No page-level filter configuration is present. |

#### Interactions and Navigation

The pivot table has standard visual interactions enabled in its definition. No page-specific drillthrough binding, custom navigation controls, or bookmarks were found.

## Global Filters and Navigation

There are no report-level filters in the report metadata. The Sales page's `Calendar[Year]`, `Product[Category]`, `Product[Subcategory]`, and `Store[Store]` filters are page-scoped; its visual-level year filter applies only to the Brand/Gender chart. The report opens on Sales and contains Sales and KPI pages in that order.
