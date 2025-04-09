# Calculation-Views-SQLScript-and-performance-tuning-tips

1) Calculation Views

Type: Graphical (Star Join)
Layers:
Base: VBAP, VBAK, KNA1
Join Type: Inner joins for master data, left outer for optional info
Filters: Input Parameter for date range
Aggregation: Sales value, quantity, by region and month
Key Features:
Input Parameters for dynamic filtering
Restricted measures
Currency conversion

cv-inventory-levels
Type: Cube with Star Join
Combines MARD, MARC, MAST, STPO
Input: Plant, Material Group
Aggregates current and historical stock
Exposes Table Function to calculate dynamic safety stock

2) Basic SQL script example
SELECT MATERIAL, SUM(QUANTITY)
FROM INVENTORY
WHERE PLANT = '3400'
GROUP BY MATERIAL;

✅ 3. Performance Tuning Tips
Use explicit projection lists (avoid SELECT *)
Avoid nested SELECT if possible; use joins instead
Use IN with caution (rewrite to JOIN where feasible)
Avoid functions like LEFT() or CAST() on indexed columns in WHERE clause
Prefer Table Variables over temporary tables
