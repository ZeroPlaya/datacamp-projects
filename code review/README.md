# Performing a Code Review on Smartphone Data Analysis

This project focuses on reviewing and improving a data analysis workflow involving smartphone specifications and prices. The original notebook, written by a Junior Data Scientist, was evaluated and revised for better readability, adherence to Python best practices, and overall code quality.

## Project Description

In professional data teams, code quality and clarity are essential—especially when the code is used in production. As a Senior Data Scientist, your task was to perform a code review for a teammate, ensuring that their script for analyzing smartphone data is clean, consistent, and maintainable.

The original code involved data cleaning, visualization, and testing. Your improvements addressed:
- Adherence to [PEP-8](https://peps.python.org/pep-0008/) standards
- Removal of duplicated logic (DRY principle)
- Proper documentation and docstrings
- Clearer, reusable functions and test coverage

---

## Summary of Improvements

| Area                      | Description                                                                 |
|---------------------------|-----------------------------------------------------------------------------|
| **Function Documentation**| `prepare_smartphone_data()` updated with detailed docstrings and comments. |
| **Style (PEP-8)**         | Code was refactored for consistent spacing, naming conventions, and layout. |
| **DRY Principle**         | Extracted reusable code into `column_to_label()` to avoid redundancy.       |
| **Testing**               | Wrote and corrected a test to validate absence of missing values.           |

---

## 🔧 Main Functions

### `prepare_smartphone_data(file_path)`
- Cleans the raw CSV dataset.
- Drops missing values in key columns.
- Converts prices from cents to dollars.

### `column_to_label(column_name)`
- Helper function that converts `snake_case` strings into `Title Case` for use in visualizations.

### `visualize_versus_price(df, feature)`
- Creates a scatterplot comparing a specified feature against price, colored by OS.

---

## Unit Testing

The following test was implemented to ensure clean data:

```python
def test_nan_values(clean_data):
    assert clean_data["battery_capacity"].isnull().sum() == 0
    assert clean_data["os"].isnull().sum() == 0
