# Data definitions & interpretation / 口径说明

| Metric | Definition / data scope |
|---|---|
| Delivered orders (96,478) | Orders whose final status is `delivered`. |
| Item sales (R$13,221,498.11) | Sum of `order_items.price` on delivered orders; excludes freight, cost, discount attribution, tax and returns adjustments. |
| Average item amount per order (R$137.04) | Delivered-order item sales ÷ delivered order count. |
| Monthly growth (Nov 2017) | Measured by purchase month; November 2017 vs October 2017. |
| Category growth contribution (32.87%) | Top three named categories' increase in item sales divided by the platform's *net* increase in item sales, Oct→Nov 2017. |
| 90-day cohort repeat (2.01%) | 1,514 repeated / 75,320 eligible first-time delivered-purchase customers with a full 90-day observation horizon. |
| Valid delivery records (96,470) | Delivered orders with valid actual-delivery dates; excludes 8 delivered orders without actual delivery dates. |
| On-time rate (93.23%) | Delivered by estimated date, among 96,470 valid delivery records. |
| Average delivery days (12.56) | Calendar-day interval from order purchase to actual customer delivery. |
| Delayed orders (6,534) | Actually delivered after estimated delivery date among 96,470 valid delivery records. |
| Delayed low-score rate (62.42%) | 3,983 low scores (1–2 stars) / 6,381 reviewed delayed orders. |
| On-time low-score rate (9.27%) | 8,289 low scores / 89,443 reviewed on-time orders. |
| Regional metrics | State grouped by customer shipping state (`customer_state`); counts and lateness rate have different denominators from reviews. |
| Review-based 90-day repeat | First-order reviewed customers with a complete 90-day window after review; not the same cohort as overall 2.01% first-purchase repeat indicator. |
| Review association p≈0.033 | Chi-square test; associated proportions but a small 0.28 percentage-point observed high vs low group gap. |

**Important:** Aggregated CSV values ending in `_pct` are already percentage-scale numbers (e.g., `62.42` means `62.42%`, **not** `0.6242`).
