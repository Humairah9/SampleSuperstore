# Superstore Sales and Profit Analysis

Using Python, I analysed a retail superstore dataset of 9,977 sales transactions to find out which categories, regions and products make money and which ones only look good on sales. I cleaned the data, built summary tables and charts with Pandas, Matplotlib and Seaborn, and measured how discounts relate to sales and profit. The main finding is that **high sales do not always mean high profit**.

## Table of Contents

- [Dashboard Preview](#dashboard-preview)
- [Introduction](#introduction)
- [Data Overview and Dataset Structure](#data-overview-and-dataset-structure)
- [Data Cleaning and Preparation](#data-cleaning-and-preparation)
- [Analysis and Findings](#analysis-and-findings)
- [Conclusion](#conclusion)
- [Recommendations](#recommendations)
- [Assumptions and Limitations](#assumptions-and-limitations)
- [Tools and Repository Structure](#tools-and-repository-structure)

## Dashboard Preview

![Profitability by Sub-Category](images/profit_by_subcategory.png)

*Tables rank 4th on sales but lose more money than any other sub-category.*

## Introduction

A retailer needs to know which products and regions drive revenue, and which of them actually drive profit. Without that view, big sellers that lose money go unnoticed, and weak regions keep receiving the same attention as strong ones.

This project analyses the SampleSuperstore dataset using Python to answer practical questions about sales and profit. The analysis aims to:

- Measure total sales, total profit and the overall profit margin.
- Compare sales and profit across categories, sub-categories, regions, segments and ship modes.
- Find which products sell well but earn little or lose money.
- Test how discounts, quantity, sales and profit relate to each other.

## Data Overview and Dataset Structure

The dataset holds one row per sales transaction. After removing duplicates it contains **9,977 transactions** and 13 columns, covering 3 categories, 17 sub-categories and 4 regions across the United States.

| Column | Description |
|---|---|
| Ship Mode | Shipping method: Standard, Second, First Class or Same Day |
| Segment | Customer segment: Consumer, Corporate or Home Office |
| Country | Country of the order |
| City | City of the order |
| State | State of the order |
| Postal Code | Postal code of the order |
| Region | West, East, Central or South |
| Category | Furniture, Office Supplies or Technology |
| Sub-Category | Product group within each category |
| Sales | Sales amount in dollars |
| Quantity | Number of units sold |
| Discount | Discount applied to the order |
| Profit | Profit (or loss) in dollars |

## Data Cleaning and Preparation

| Issue | Treatment |
|---|---|
| Missing values | None found in any column |
| 17 duplicate rows | Removed, reducing 9,994 rows to 9,977 transactions |
| Data types | Checked, with no changes needed |

All totals and charts below use the 9,977 de-duplicated transactions.

## Analysis and Findings

### 1. Headline KPIs

The store recorded **$2,296,195.59** in sales and **$286,241.42** in profit, an overall profit margin of **12.5%**.

![KPI card](images/kpi_card.png)

### 2. Sales and Profit by Category

| Category | Sales | Profit | Margin |
|---|---|---|---|
| Technology | $836,154 | $145,455 | 17.4% |
| Furniture | $741,306 | $18,422 | 2.5% |
| Office Supplies | $718,735 | $122,365 | 17.0% |

Technology leads on both sales and profit. Furniture is the clearest case of high sales with low profit: it ranks second on sales but earns only 6.4% of total profit, with a margin of just 2.5%. Office Supplies sells the least but earns 42.8% of profit.

![Sales by Category](images/sales_by_category.png)

![Profit by Category](images/profit_by_category.png)

### 3. Sales and Profit by Region

| Region | Share of sales | Share of profit | Margin |
|---|---|---|---|
| West | 31.6% | 37.8% | 14.9% |
| East | 29.5% | 32.0% | 13.5% |
| South | 17.1% | 16.3% | 11.9% |
| Central | 21.8% | 13.9% | 7.9% |

West is the strongest region on both measures. Central is the weakest: it makes 21.8% of sales but only 13.9% of profit, a margin of 7.9% that is about half of West's, which points to cost or pricing problems.

![Sales by Region](images/sales_by_region.png)

![Profit by Region](images/profit_by_region.png)

### 4. Sales and Profit by Sub-Category

Phones ($330,007) and Chairs ($327,778) lead on sales. Copiers earn the most profit ($55,618, a 37.2% margin), followed by Phones ($44,516) and Accessories ($41,937).

Three sub-categories lose money: **Tables (-$17,725)**, **Bookcases (-$3,473)** and **Supplies (-$1,189)**. Tables are the biggest warning sign, because they rank 4th on sales at $206,966 yet are the least profitable product. Chairs also sell almost as much as Phones but earn a margin of only 8.1%. Fasteners contribute the least sales ($3,024).

![Sales by Sub-Category](images/sales_by_subcategory.png)

![Profitability by Sub-Category](images/profit_by_subcategory.png)

### 5. Segment and Ship Mode

Consumers make up 50.5% of sales but have the lowest margin of the three segments (11.5%), against 13.0% for Corporate and 14.0% for Home Office. Standard Class carries 59.1% of sales and 57.3% of profit, so no ship mode stands out as a problem.

### 6. Correlations

![Correlation Heatmap](images/correlation_heatmap.png)

- **Sales and profit (0.48):** a moderate positive link, so higher sales generally lead to higher profit, but far from always.
- **Sales and discount (-0.03):** almost no link, so discounts do not boost sales.
- **Profit and discount (-0.22):** a negative link, so higher discounts tend to reduce profit.
- **Sales and quantity (0.20):** a weak link, so revenue depends more on order value than on the number of units.

## Conclusion

The store is profitable overall, with a 12.5% margin, but the profit is not spread evenly across the business:

- **Category:** Technology and Office Supplies earn about 17% margins, while Furniture earns just 2.5%.
- **Region:** West leads, while Central earns a 7.9% margin on 21.8% of sales.
- **Products:** Tables, Bookcases and Supplies lose money. Tables sell well but lose the most.
- **Discounts:** they do not lift sales, but they are linked to lower profit.

Overall, **high sales do not always mean high profit**.

## Recommendations

1. **Review Tables, Bookcases and Supplies.** Check their costs and discounts, and consider repricing, reducing discounts or dropping the weakest lines.
2. **Fix the Furniture margin.** Furniture sells $741,306 but keeps only 2.5% as profit, so look at supplier costs and pricing.
3. **Investigate the Central region.** Its margin is about half of West's, so find out whether costs, discounts or product mix explain it.
4. **Tighten discounts.** They do not raise sales but are linked to lower profit, so target them instead of applying them widely.
5. **Promote high-margin lines.** Copiers, Accessories and Phones earn strong profits and are worth pushing.

## Assumptions and Limitations

- The dataset is a sample retail dataset used for practice, not a real company's records.
- The data has no dates, so trends over time cannot be analysed.
- Profit is taken as given in the dataset. How it was calculated is not documented.
- Correlations show relationships, not causes, so a link between discounts and lower profit does not prove one causes the other.
- Category, region and product effects overlap, so a difference cannot be put down to a single factor.

## Tools and Repository Structure

**Tools:** Python, Pandas, Matplotlib, Seaborn, Google Colab.

```
.
├── README.md
├── SampleSuperstore.csv          # source dataset
├── superstore_analysis.ipynb     # analysis notebook
├── images/                       # chart images used in this README
└── HNG Task 0.pdf                # task brief
```

This report was developed as part of the HNG Internship, which equips participants with industry-ready data analysis and other tech skills. Learn more at [HNG Internship](https://hng.tech/internship) or explore opportunities to hire skilled professionals through [HNG Hire](https://hng.tech/hire).

## Author

Aisha Hamza | [LinkedIn](https://www.linkedin.com/in/aisha-hamza-a21188187/) | [Email](mailto:hamzaaisha798@gmail.com)
