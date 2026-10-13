# Power BI Dashboard Build Guide / 看板复现指南

This project uses **two Power BI pages** based on **10 pre-aggregated CSV files** in `powerbi_data/`.

## Page 1: Sales Performance & Customer Retention

Four KPI cards:
- `01_总体经营KPI`: `total_item_amount_brl`, `delivered_orders`, `avg_item_amount_per_order_brl`
- `05_90天复购总体KPI`: `repeat_rate_90d_pct`

Main visuals:
- Monthly bar+line: `02_月度销售趋势` (`order_month`, `total_sales`, `order_count`)
- Top 10 category growth: `03_2017年11月品类增长Top10` (`category`, `sales_increase`; `contribution_pct` in tooltip)
- Cohort repeat line: `04_90天复购Cohort` (`cohort_month`, `repeat_rate_90d_pct`)

## Page 2: Delivery Performance & Customer Experience

Four KPI cards:
- `06_配送履约KPI`: `on_time_rate_pct`, `avg_delivery_days`, `late_orders`
- `07_准时与延迟订单评价`: `low_score_pct` **with `delivery_status = late` visual filter**

Main visuals:
- On-time versus late low-score rate: `07_准时与延迟订单评价`
- Delay-day groups and low-score rate: `08_延迟天数与低评分`; order groups from on time through 15+ days
- Regional combo chart: `09_各州配送问题Top10`; columns `late_orders`, line `late_rate_pct`, dual Y-axis; filter Top 6 **by late order count** (not by rate)
- Rating and 90-day repeat: `10_评分与评价后90天复购`

## Numeric display tips / 数值显示提示

- Display percentage-scale values with custom DAX `FORMAT(MAX(Table[column]), "0.00") & "%"`, when using KPI cards. Do **not** multiply source `_pct` fields by 100.
- Use numeric `late_orders` for charts. To prevent abbreviated KPI labels, a text measure can be used: `FORMAT(MAX(Table[late_orders]), "#,##0", "en-US")`.
- In a combo chart, use separate primary and secondary axes for order counts and percentage-scale rates; **do not use logarithmic scale**.
- A custom sort key may be required for text-based delay groups. Derive the sort key from the original `delay_group` code rather than the displayed Chinese label to avoid circular dependencies.
- Treat all causal statements conservatively; this is observational data.
