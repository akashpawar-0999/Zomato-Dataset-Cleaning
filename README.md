# Zomato Dataset Cleaning

A beginner-friendly data cleaning project in Python. It takes a small, messy, **fictional** Zomato-style restaurant dataset and cleans it step by step using only `pandas` and `numpy`.

> The data is generated for practice. It is not real Zomato data.

## Problem

A food-delivery startup has a messy list of restaurants. Before anyone can analyse it, the data must be inspected, cleaned and saved as a clean file.

## Dataset

`zomato_raw_dataset.xlsx` has 250 rows and 8 columns:

| Column | Meaning |
|---|---|
| Name | Restaurant name |
| City | City of the restaurant |
| Cuisine | Type of food served |
| Cost For Two | Average cost for two people (rupees) |
| Rating | Customer rating (1 to 5) |
| Votes | Number of customers who rated |
| Online Order | Takes online orders? |
| Opening Date | Date the restaurant opened |

## Problems in the raw data

- Duplicate rows
- Column names with capitals and spaces
- Mixed case, extra spaces and city aliases in text
- Cost with symbols and text, plus `0` and `50000`
- Ratings that are `NEW` or above 5
- Negative votes
- Yes/No written many ways
- Dates that are `Unknown` or in the future
- Missing values in several columns

## Cleaning steps

1. Inspect the data: `shape`, `info`, `isna().sum()`, `duplicated()`
2. Clean column names (capitals and spaces)
3. Remove duplicate rows
4. Fix text columns (case, spaces, city aliases, missing cuisine)
5. Fix cost (symbols, text, wrong values, missing)
6. Fix rating (`NEW`, values above 5)
7. Fix votes (negative values, missing, convert to `int`)
8. Fix online order (many spellings to `True`/`False`)
9. Fix dates (`Unknown`, future dates, add `opening_year`)
10. Add new columns: `cost_level` and `rating_label`
11. Answer small questions with `groupby`, `value_counts` and `nlargest`
12. Save the result with `to_csv(index=False)`

## Result

| | Before | After |
|---|---|---|
| Rows | 250 | 240 |
| Columns | 8 | 12 |
| Duplicates | 10 | 0 |

Missing values left on purpose: `rating` (new restaurants), `opening_date` and `opening_year` (unknown or future dates).

## Project files

```
.
├── zomato_raw_dataset.xlsx
├── Data-Cleaning-of-Zomato-Data-Set.ipynb
├── zomato_dataset_cleaned.csv
└── README.md
```

## How to run

1. Clone or download this repository.
2. Install the requirements (`openpyxl` is needed for pandas to read `.xlsx`):

   ```bash
   pip install pandas numpy openpyxl jupyterlab
   ```

3. Open `Data-Cleaning-of-Zomato-Data-Set.ipynb` in Jupyter Lab and run the cells from top to bottom.

## What I learned

1. Inspect data before cleaning it
2. Standardise text with `strip` and `title`
3. `errors="coerce"` turns bad values into missing
4. Set impossible values to missing first
5. Choose the fill method per column
6. Add new columns and summarise with `groupby`
---
