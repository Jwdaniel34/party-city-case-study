# README – Party City (PRTY) Q4 2022 Comparable Sales Forecast & Store Closure Risk Analysis

## **1. Project Overview**

This project analyzes Party City’s (PRTY) historical and transaction-based sales data to forecast **Q4 2022 Brand Comparable Sales** and assess **store closure risk**.

Key objectives:

* Estimate Q4 2022 comparable sales using reported and transaction-level data
* Identify high-risk stores for potential closures based on service offerings and location characteristics
* Visualize trends and risks in an executive-friendly format

---

## **2. Data Sources**

| File                                                                  | Description                                                               |
| --------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| `system2_case_study_reported_numbers.xlsx`                            | Historical reported Brand Comparable Sales (%) by quarter                 |
| `system2_case_study_transaction_data_monthly_sales_by_locationid.csv` | Transaction-level monthly sales by location                               |
| `system2_case_study_transaction_data_location_info.csv`               | Store open/close dates by location                                        |
| `system2_case_study_webscrape_data_locations.csv`                     | Web-scraped Party City store information, including services and location |

**Note:** Transaction data represents a ~1% sample of the US population.

---

## **3. Analysis Steps**

1. **Data Cleaning & Preparation**

   * Convert reported YoY percentages to numeric values
   * Filter transaction data for Q4 2021 and Q4 2022
   * Merge store info for closure risk analysis

2. **Comparable Sales Forecast**

   * Calculate historical Q4 vs Q3 deltas
   * Estimate transaction-implied Q4 comps:

     ```python
     transaction_comp_q4_2022 = (sales_2022 / sales_2021 - 1) * 100
     ```
   * Combine historical trends and transaction data to generate final forecast

3. **Store Closure Risk Scoring**

   * Score stores based on:

     * `num_services <= 3` → low service coverage
     * `suburban_flag == True` → suburban location
   * High-risk stores: risk score = 2

4. **Visualization**

   * Historical comps line chart
   * Q4 transaction sales bar chart
   * Store closure risk distribution pie chart

---

## **4. How to Run**

1. Clone or download this repository
2. Ensure Python 3.x is installed with the following packages:

   ```bash
   pip install pandas matplotlib seaborn openpyxl
   ```
3. Open the notebook: `case_study_YoY_forecast.ipynb`
4. Run all cells to reproduce:

   * Cleaned and prepared datasets
   * Forecast calculations
   * Visualizations (PNG files are also saved)

**Optional:** Export cleaned notebook or Python script for review.

---


## **5. Key Observations**

* Q4-2022 Brand Comparable Sales forecast: **~–4.4% YoY**
* Transaction data suggests a sharper decline (~–11%)
* ~5.5% of stores are classified as high risk; the majority are not flagged
* Declines appear **system-wide**, not isolated to a few locations
* Closure-risk scoring helps prioritize which stores may need attention

---

## **6. Notes & Assumptions**

* Only stores open before Q4-2021 and not closed early are considered for comparable sales calculations
* High-risk scoring is a simple rule-based model: number of services + suburban location
* Transaction data is based on a ~1% sample; extrapolated for total sales trends
* Forecasts do not include external factors such as macroeconomic shocks or marketing initiatives

---


