# T-Shirt Pricing & Catalog Intelligence Dashboard

**A Power BI dashboard that shows whether big discounts on men's t-shirts are meaningful, and which brands and price tiers actually earn money.**

| | |
|---|---|
| **Data** | 1,428 men's t-shirts from 143 brands, listed on an Indian e-commerce platform |
| **Tools** | Power BI, DAX, Power Query, Excel |
| **Report** | 3 dashboard pages, 6 calculated columns, 12 DAX measures |
| **Full project document** | [Read the PDF](https://github.com/Tahseenahhamza/T-Shirt-Pricing-Catalog-Intelligence-Dashboard/blob/main/Tshirt%20pricing%20analysis%20documentation.pdf) |
| **All DAX formulas** | [Open dax_measures.md](https://github.com/Tahseenahhamza/T-Shirt-Pricing-Catalog-Intelligence-Dashboard/blob/main/dax_measures.md) |

---

## Summary

Online shops often advertise very large discounts. A discount only has value if the original price (MRP) is realistic and the product still earns a profit at the selling price.

This project studies a catalog of 1,428 men's t-shirts. It shows that the average discount is **57.1%**, but most of the catalog earns very little profit per product. A small group of Premium, Luxury and international products earns most of the profit.

**Who this is for:** category managers, buying teams, pricing teams and anyone who decides which products and brands to stock and how to price them.

---

## Business Questions

1. How far is the MRP above the real selling price?
2. Which price tiers earn good profit, and which depend on heavy discounts?
3. How many products have a discount of 70% or more?
4. Which brands sell the most products, and do they also earn the most?
5. Do international brands perform differently from domestic brands?

---

## Key Results

| Measure | Result |
|---|---|
| Average discount | **57.1%** |
| MRP compared with selling price | **2.32 times** higher |
| Products with a discount of 70% or more | **26.5%** (about 1 in 4) |
| Average selling price | **₹1,034** |
| Estimated average profit margin | **26.3%** |
| Average profit per product | **₹243** |

### What the data shows

| Finding | Detail |
|---|---|
| **Most products earn little** | The Budget tier has 560 products (39% of the catalog) but earns only ₹99 profit per product. The Luxury tier has 58 products and earns ₹1,586 per product. |
| **The Economy tier relies on discounts** | It has the highest average discount (73.1%) and earns only ₹96 profit per product. |
| **International brands earn more** | They are 16.5% of products but earn ₹575 per product. Domestic brands earn ₹141. That is about 4 times more. |
| **The biggest brand is not the top earner** | The Indian Garage Co has the most products (184) but earns only ₹77 per product. |

---

## Dashboard Pages

### Page 1: Catalog Overview
Catalog size, average price, discount level, brand pricing and results by tier.

![Catalog Overview](https://raw.githubusercontent.com/Tahseenahhamza/T-Shirt-Pricing-Catalog-Intelligence-Dashboard/main/Overview.jpg)

### Page 2: Discount & Profitability
How deep the discounts are and whether products still earn a profit.

![Discount and Profitability](https://raw.githubusercontent.com/Tahseenahhamza/T-Shirt-Pricing-Catalog-Intelligence-Dashboard/main/Discount%20%26%20Profitability.jpg)

### Page 3: Brand Intelligence
Brand comparison on price, profit and discount, including domestic vs international brands.

![Brand Intelligence](https://raw.githubusercontent.com/Tahseenahhamza/T-Shirt-Pricing-Catalog-Intelligence-Dashboard/main/Brand%20Intelligence.jpg)

**How to use it:** use the filters (Tier, Price Band, Type, Brand) to focus on one group. Click any chart to filter the rest of the page.

---

## Recommendations

| # | Action | Reason |
|---|---|---|
| 1 | Judge brands by selling price and profit, not by discount % | The average discount is 57.1% mainly because MRPs are high (2.32 times the selling price). |
| 2 | Grow Premium and international brands | They earn ₹400 and ₹575 per product, compared with ₹99 for Budget. |
| 3 | Review the Economy tier | Average discount of 73.1% and only ₹96 profit per product. |
| 4 | Remove low-profit products before adding new ones | 560 Budget products earn ₹99 each. The biggest brand earns ₹77 per product. |
| 5 | Check the MRP of products with a discount of 70% or more | 26.5% of the catalog is in this group. |

---

## How It Was Built

1. **Data model:** two tables joined on Brand (star schema).
   - `T-Shirt Products` (1,428 rows): Brand, Title, Sale Price, MRP, Cost Price
   - `Brand Tier Reference` (143 rows): Brand, Tier, Origin, Type (Domestic / International)
2. **Calculated columns (6):** Profit Per Unit, Profit Margin %, Discount Amount, Discount %, Price Band, Discount Flag.
3. **DAX measures (12):** grouped in 4 folders: Core Metrics, Discount Analysis, Profitability, Brand Intelligence.
4. **Quality check:** the measures were tested with DAX queries and compared with the charts. This found one error in the Domestic vs International chart (it showed MRP instead of selling price). It was fixed.

**Skills shown:** data modelling, DAX, Power BI dashboard design, data validation, and turning data into business recommendations.

---

## Files in This Repository

| File | Description |
|---|---|
| [T-Shirt Products Data.CSV](https://github.com/Tahseenahhamza/T-Shirt-Pricing-Catalog-Intelligence-Dashboard/blob/main/T-Shirt%20Products%20Data.CSV) | Product data |
| [Brand_tier_reference.xlsx](https://github.com/Tahseenahhamza/T-Shirt-Pricing-Catalog-Intelligence-Dashboard/blob/main/Brand_tier_reference.xlsx) | Brand tier and origin data |
| [dax_measures.md](https://github.com/Tahseenahhamza/T-Shirt-Pricing-Catalog-Intelligence-Dashboard/blob/main/dax_measures.md) | All DAX formulas |
| [Project document (PDF)](https://github.com/Tahseenahhamza/T-Shirt-Pricing-Catalog-Intelligence-Dashboard/blob/main/Tshirt%20pricing%20analysis%20documentation.pdf) | Full project documentation |
| Overview.jpg, Discount & Profitability.jpg, Brand Intelligence.jpg | Dashboard screenshots |

---

## Limitations

- **Snapshot only:** the data is from June 2026. It shows prices at one point in time, not how they change over weeks or months.
- **Estimated profit:** profit figures depend on the Cost Price column, so they are estimates.
- **MRP gap:** a large gap between MRP and selling price suggests the MRP may be set high. It does not prove the MRP was never charged.
- **Scope:** the data comes from one platform and does not include sales volumes.

---

## Author

**Tahseenah Hamza**, Data Analyst and Power BI Developer
[LinkedIn](https://linkedin.com/in/tahseenah-hamza) · [Portfolio](https://datascienceportfol.io/tahseenahhamza) · tahseenahhhamza@gmail.com
