# Audible Dataset – Data Cleaning in Python

This repository contains my work from a DataCamp Live Training focused on cleaning real-world audiobook data from [audible.in](https://www.audible.in/).

---

## Data Cleaning Workflow

The notebook demonstrates a complete data cleaning pipeline:

- Loaded and inspected raw audiobook data (`audible_raw.csv`)
- Cleaned text fields (`author`, `narrator`, `language`) for consistency
- Extracted and separated star ratings and number of reviews into numeric columns
- Standardized `price` values and converted currency from INR to USD
- Parsed and converted date fields (`releasedate`) to proper datetime objects
- Converted audiobook durations into total minutes (`time_mins`)
- Identified and removed duplicate records based on key attributes
- Performed summary statistics and visual checks using histograms
- Exported the cleaned dataset to `audible_clean.csv`

---

## Files

- `notebook.ipynb` – Final version of the cleaned data workflow  
- `notebook-solution.ipynb` – Instructor-provided reference solution  
- `data/audible_raw.csv` – Raw dataset  
- `data/audible_clean.csv` – Cleaned dataset output  

---

## Source

- 📦 [Kaggle: Audible Dataset](https://www.kaggle.com/datasets/snehangsude/audible-dataset)  
- 🎓 DataCamp Live Training – *Cleaning Data in Python*

## Links

- **DataCamp Project:** [Cleaning Data in Python](https://www.datacamp.com/code-along/cleaning-data-in-python)  
- **Learning Track:** [Data Engineer in Python](https://www.datacamp.com/completed/statement-of-accomplishment/track/1239f48432b3a47db932bfad99b900933000b204)
