# Lab 4 — Reading and Writing Data Files

**Course:** Python for AI & Data  
**Unit:** 1 — Applying Python Fundamentals to Solve Data Problems  
**Lab Time:** 60 minutes

---

## The BeanScene Scenario

In Labs 1–3, BeanScene's data was hardcoded directly in your notebooks. That was fine for getting started, but Sarah needs something more practical: her menu data and performance thresholds should live in files that can be updated without touching any code.

This week Sarah has provided two files:
- **`beanscene_menu.csv`** — the full menu with prices and weekly units sold
- **`beanscene_config.json`** — performance thresholds and café settings

Your job: load these files, run the menu analysis from Lab 3 using the config values, and save the processed results back to disk. Sarah should be able to hand you a new CSV next week and your code will handle it without modification.

---

## Learning Objectives

By the end of this lab, you'll be able to:

- Read structured data from a CSV file using `csv.DictReader`
- Read configuration from a JSON file using `json.load`
- Convert string values to the correct numeric types after loading
- Use `pathlib.Path` to build portable, reliable file paths
- Write processed results to CSV and JSON output files
- Organise a project with separate `raw/` and `processed/` data folders

---

## Getting Started

### Step 1: Fork the Lab Repo

Go to the course GitHub organisation and find **lab-4-reading-and-writing-data-files**.  
Click **Fork** to create your personal copy.

### Step 2: Clone Your Fork

```bash
git clone git@github.com:YOUR-USERNAME/lab-4-reading-and-writing-data-files.git
cd lab-4-reading-and-writing-data-files
```

### Step 3: Activate Your Environment and Launch JupyterLab

```bash
source venv/bin/activate        # Mac/Linux
# source venv/Scripts/activate  # Windows
jupyter lab
```

Open `notebooks/lab4_starter.ipynb` from the file browser.

---

## Project Structure

```text
lab-4-reading-and-writing-data-files/
│
├── data/
│   ├── raw/                       ← provided files — do not modify
│   │   ├── beanscene_menu.csv
│   │   └── beanscene_config.json
│   └── processed/                 ← your code writes here
│
├── notebooks/
│   └── lab4_starter.ipynb
│
├── requirements.txt
│
└── README.md
```

> **Important:** Never modify files in `data/raw/`. If your analysis goes wrong, you should always be able to re-run the notebook from scratch using the original files.

---

## Lab Exercises

### Task 1 — Confirm Your Environment
Verify your working directory and confirm the data files can be found using `pathlib`.

### Task 2 — Load the Menu from CSV
Read `beanscene_menu.csv` into a list of dictionaries with correctly typed values (floats and ints, not strings).

### Task 3 — Load the Config from JSON
Read `beanscene_config.json` and use its values to drive the analysis — not hardcoded numbers.

### Task 4 — Analyse the Menu
Using the loaded data and config, calculate revenue and classify each item. Reuse your `classify_item` logic from Lab 3 (you can either copy the function or reimplement it here).

### Task 5 — Save Results to CSV
Write the analysis results (name, revenue, tier) to `data/processed/menu_results.csv`.

### Task 6 — Save a Summary to JSON
Build a summary dictionary and write it to `data/processed/weekly_summary.json`.

### Task 7 — Verify Your Outputs
Re-load both processed files and print their contents to confirm they were saved correctly.

---

## Optional Advanced Tasks

1. **Append to an existing file:** After completing Task 5, write a second CSV with only the "Low" performing items to `data/processed/low_performers.csv`. Then look up how to open a file in append mode (`"a"`) and add a footer row with the total count of low performers.

2. **Config-driven thresholds:** Modify your analysis so that the performance tiers (High/Medium/Low) are determined entirely by the values in `beanscene_config.json`. Then edit the JSON file to change the `high` threshold from `250` to `200` and re-run — verify the output changes without changing any Python code.

3. **Category summary:** Group the menu items by `category` (Hot Drinks, Cold Drinks, Specialty) and write a JSON file to `data/processed/category_summary.json` that shows the total revenue per category.

---

## Submitting Your Work

When you have completed the lab, make sure all cells show output, then:

```bash
git add .
git commit -m "Complete lab 4"
git push
```

Make sure:
- All notebook cells show output (run top to bottom before pushing)
- `data/processed/` contains at least `menu_results.csv` and `weekly_summary.json`
- No cells raise unhandled errors

---

## Tips for Success

- **Confirm your working directory first** — most path errors are just "wrong directory"
- **Always convert types after reading CSV** — numbers come in as strings
- **Raw data is read-only** — write all outputs to `data/processed/`
- **Verify your outputs** — re-load what you saved and print it to confirm correctness

---

## Resources

- **Python csv module:** https://docs.python.org/3.11/library/csv.html
- **Python json module:** https://docs.python.org/3.11/library/json.html
- **pathlib:** https://docs.python.org/3.11/library/pathlib.html
- **Real Python — Reading and Writing CSV:** https://realpython.com/python-csv/
