# Superstore Sales Analysis

A Python analysis of four years of Superstore orders (2015 to 2018). It looks at customer purchase volume, monthly seasonality, category and regional revenue, and how discounts affect profit, then pulls the results into six business findings.

Everything lives in one notebook: `superstore_analysis.ipynb`.

## What's in the notebook

1. **Data cleaning** – removes non-order rows, parses dates, drops duplicates, extracts Year and Year-Month.
2. **Headline numbers** – total sales, profit, margin, orders, customers, plus a year-by-year table.
3. **Category, region and segment** – sales and profit for each, a category-by-region margin heatmap, and a sub-category profit breakdown.
4. **Monthly sales and seasonality** – sales over time with a 3-month average, and each calendar month's share of annual sales.
5. **Customer purchase volume** – orders per customer and how concentrated sales are among top customers.
6. **Discount sensitivity** – discount vs profit scatter, margin by discount band, and the regions and products that discount the most.
7. **Findings** – six takeaways, each with evidence and a recommended action.

## Running it

**Google Colab (recommended)**

1. Upload `superstore_analysis.ipynb` to Colab.
2. Run all cells.
3. When the file picker appears in the setup cell, select `superstore_sales.csv`.

**Locally**

Put `superstore_sales.csv` in the same folder as the notebook, then:

```bash
pip install pandas numpy matplotlib seaborn jupyter
jupyter notebook superstore_analysis.ipynb
```

## Notes on the data

The raw CSV has 10,800 rows, but only the first 9,994 are orders. Below them, the file contains two small lookup tables (regional managers and returned order IDs) that were pasted into the same sheet. They show up as rows that are almost entirely empty, so they are removed rather than treated as missing data. One exact duplicate order line is also dropped.

The only null values left are 11 `Postal Code` entries for Burlington, Vermont. Postal code isn't used anywhere in the analysis.

After cleaning, 9,993 order lines remain.

## Findings in brief

| Area | Result |
| --- | --- |
| Discounts | Margin is 29.5% with no discount and turns negative above 20%. 72% of loss-making lines carry a discount over 20%. |
| Categories | Furniture earns a 2.5% margin against about 17% for Technology and Office Supplies. Tables, Bookcases and Supplies lose money. |
| Seasonality | September to December brings in 51.6% of annual sales. January and February bring in 6.7%. |
| Customers | The top 20% of customers account for 48% of sales. 98.5% of customers ordered more than once. |
| Regions | Central has a 7.9% margin vs 14.9% in the West, and an average discount of 24% vs 11%. |
| Growth | Sales grew 20% in 2018 while margin slipped from 13.4% to 12.7%. |

The full write-up, with charts and recommendations, is at the end of the notebook.

## Limitations

- The discount and profit link is a correlation. Some deep discounts may be clearance on products that were already unprofitable.
- The dataset has no cost, return or cancellation fields, so margin is calculated as `Profit / Sales` using the values as given.

## Tools

Python, Pandas, NumPy, Matplotlib, Seaborn, Jupyter / Google Colab
