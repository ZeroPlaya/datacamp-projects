# 📦 Walmart E-commerce Holiday Sales Pipeline

This project focuses on building a data pipeline to analyze Walmart’s grocery sales around U.S. public holidays. It integrates and transforms multiple data sources to generate insights into how holidays impact sales.

By 2022, e-commerce made up over $80 billion of Walmart’s revenue—about 13% of its total. Understanding holiday-related demand patterns helps improve inventory, staffing, and promotions planning.

---

## 🧠 Project Objectives

- Combine sales and external data (weather, CPI, unemployment, markdowns)
- Clean and filter the merged dataset
- Extract features for analysis (e.g., month)
- Aggregate average weekly sales by month
- Store results as CSVs for downstream processing

---

## 🗃️ Data Sources

### `grocery_sales.csv` (PostgreSQL table)
| Column        | Description                       |
|---------------|-----------------------------------|
| `index`       | Unique row ID                     |
| `Store_ID`    | Store number                      |
| `Date`        | Week of sales (datetime)          |
| `Weekly_Sales`| Weekly sales in USD               |

### `extra_data.parquet`
| Column        | Description                                      |
|---------------|--------------------------------------------------|
| `IsHoliday`   | 1 if the week contains a public holiday          |
| `Temperature` | Temperature at the store                        |
| `Fuel_Price`  | Fuel cost in the region                         |
| `CPI`         | Consumer Price Index                            |
| `Unemployment`| Regional unemployment rate                      |
| `MarkDown1–5` | Promotional markdown amounts                    |
| `Dept`        | Department number                               |
| `Size`        | Size of the store                               |
| `Type`        | Type of store (based on size)                   |

---

## 🔧 Pipeline Steps

### 1. **Extract**

Merged the CSV and Parquet files on the `index` column using the `extract()` function.

### 2. **Transform**

Performed the following in `transform()`:
- Imputed missing values (mean or forward fill)
- Extracted month from `Date`
- Filtered out records with `Weekly_Sales <= 10,000`
- Dropped unnecessary columns
- Output: `clean_data`

**Columns retained in `clean_data`:**
| Column        | Description                             |
|---------------|-----------------------------------------|
| `Store_ID`    | Store number                            |
| `Month`       | Month extracted from `Date`             |
| `Dept`        | Department number                       |
| `IsHoliday`   | Holiday week flag                       |
| `Weekly_Sales`| Weekly sales (filtered)                 |
| `CPI`         | Consumer Price Index                    |
| `Unemployment`| Unemployment rate                       |

### 3. **Aggregate**

Calculated average weekly sales per month using `avg_weekly_sales_per_month()`:

| Month | Avg_Sales      |
|--------|----------------|
| 1.0    | 33174.18       |
| 2.0    | 34333.33       |
| ...    | ...            |

Output: `agg_sales_data`

---

## 💾 Load and Validate

Used the `load()` function to export both datasets as CSVs:
- `clean_data.csv`
- `agg_data.csv`

Confirmed successful saving using the `validation()` function.

---

## 🛠️ Technologies Used

- Python (pandas, os)
- PostgreSQL (original data source)
- Parquet file handling
- CSV file export
- Data wrangling and transformation

---

## 📁 Output Files

- `clean_data.csv` – cleaned, transformed dataset for analysis
- `agg_data.csv` – monthly average weekly sales for Walmart

## Links

- **DataCamp Project:** [Building a Retail Data Pipeline](https://app.datacamp.com/learn/projects/1833)  
- **Learning Track:** [Data Engineer in Python](https://www.datacamp.com/completed/statement-of-accomplishment/track/1239f48432b3a47db932bfad99b900933000b204)
