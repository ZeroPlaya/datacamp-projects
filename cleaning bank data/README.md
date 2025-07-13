# Cleaning Bank Marketing Campaign Data

This project uses Python to clean and reformat a dataset containing information from a personal loan marketing campaign run by a bank. The cleaned data is split into structured CSV files for storage in a PostgreSQL database, enabling easy future campaign integration.

## Project Description

Personal loans generate substantial revenue for banks. In this project, we are given raw campaign data in `bank_marketing.csv`, which we've cleaned and transformed into three separate tables:

- `client.csv` — demographic and financial background
- `campaign.csv` — marketing efforts and results
- `economics.csv` — economic indicators

The cleaned files are saved as CSVs and structured to match specific schema and data type requirements.

---

## Dataset Schemas and Cleaning Details

### `client.csv`

| Column          | Description                                         | Data Type | Cleaning Performed                                    |
|------------------|-----------------------------------------------------|-----------|--------------------------------------------------------|
| `client_id`     | Unique identifier for the client                    | INTEGER   | No cleaning                                            |
| `age`           | Age of the client                                   | INTEGER   | No cleaning                                            |
| `job`           | Type of job                                         | OBJECT    | Replaced `.` with `_`                                 |
| `marital`       | Marital status                                      | OBJECT    | No cleaning                                            |
| `education`     | Level of education                                  | OBJECT    | Replaced `.` with `_` and `"unknown"` → `NaN`         |
| `credit_default`| Credit in default (`yes` / `no`)                    | BOOLEAN   | Converted `"yes"` → `True`, otherwise `False`         |
| `mortgage`      | Has mortgage (`yes` / `no`)                         | BOOLEAN   | Converted `"yes"` → `True`, otherwise `False`         |

---

### `campaign.csv`

| Column                      | Description                                                  | Data Type | Cleaning Performed                                    |
|-----------------------------|--------------------------------------------------------------|-----------|--------------------------------------------------------|
| `client_id`                 | Unique identifier for the client                            | INTEGER   | No cleaning                                            |
| `number_contacts`           | Contact attempts in current campaign                        | INTEGER   | No cleaning                                            |
| `contact_duration`          | Duration of last contact (in seconds)                       | INTEGER   | No cleaning                                            |
| `previous_campaign_contacts`| Contact attempts in previous campaign                       | INTEGER   | No cleaning                                            |
| `previous_outcome`          | Outcome of previous campaign (`success` / other)            | BOOLEAN   | Converted `"success"` → `True`, otherwise `False`     |
| `campaign_outcome`          | Outcome of current campaign (`yes` / `no`)                  | BOOLEAN   | Converted `"yes"` → `True`, otherwise `False`         |
| `last_contact_date`         | Date of last contact in `"YYYY-MM-DD"` format               | DATETIME  | Constructed from `day`, `month`, and fixed year `2022`|

---

### `economics.csv`

| Column               | Description                                     | Data Type | Cleaning Performed |
|----------------------|-------------------------------------------------|-----------|---------------------|
| `client_id`          | Unique identifier for the client               | INTEGER   | No cleaning         |
| `cons_price_idx`     | Consumer price index (monthly)                 | FLOAT     | No cleaning         |
| `euribor_three_months`| Euro Interbank Offered Rate (3-month daily)   | FLOAT     | No cleaning         |

---

## Key Transformations

Example of creating a boolean column from text values:

```python
df['credit_default'] = df['credit_default'].map(lambda x: 1 if x == 'yes' else 0).astype(bool)
```

## Links

- **DataCamp Project:** [Cleaning Bank Marketing Campaign Data](https://app.datacamp.com/learn/projects/1613)  
- **Learning Track:** [Data Engineer in Python](https://www.datacamp.com/completed/statement-of-accomplishment/track/1239f48432b3a47db932bfad99b900933000b204)
