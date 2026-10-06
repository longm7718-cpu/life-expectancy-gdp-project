# Life Expectancy and GDP

Does a country's GDP move together with how long its people live?

This project compares life expectancy at birth and gross domestic product (GDP) for six countries from 2000 through 2015: Chile, China, Germany, Mexico, the United States, and Zimbabwe. The data comes from the World Health Organization and the World Bank.

A short write-up of the charts is on Medium: [Beyond the Trillions: What GDP Can (and Can't) Tell Us About Global Life Expectancy](https://medium.com/@longm7718/diminishing-returns-health-disparities-a-data-visualization-study-of-global-gdp-and-life-e16fd45387f9).

## What is in this repo

| File | What it is |
|---|---|
| `all_data.csv` | The dataset. 96 rows (6 countries × 16 years). |
| `life_expectancy_gdp.ipynb` | The analysis: cleaning, charts, and written findings. |
| `requirements.txt` | Python packages needed to run the notebook. |

### Columns in `all_data.csv`

| Column | Description |
|---|---|
| `Country` | Chile, China, Germany, Mexico, United States of America, or Zimbabwe |
| `Year` | 2000–2015 |
| `Life expectancy at birth (years)` | Expected lifespan in years |
| `GDP` | Total GDP in US dollars |

## Setup

Use Python 3.11 or newer.

```bash
git clone https://github.com/longm7718-cpu/life-expectancy-gdp-project.git
cd life-expectancy-gdp-project
python -m venv .venv
```

Activate the environment:

- Windows (PowerShell): `.\.venv\Scripts\Activate.ps1`
- macOS and Linux: `source .venv/bin/activate`

Then install the libraries and open the notebook:

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
jupyter notebook life_expectancy_gdp.ipynb
```

In Jupyter, use **Run All**. The notebook reads `all_data.csv` from the project folder, so start Jupyter there.

Running the notebook writes chart PNGs next to the notebook. Those files are gitignored. The charts shown on GitHub are the ones saved inside the notebook.

## What the analysis does

1. Load the CSV with pandas and rename the life-expectancy column to `LEABY`.
2. Check the shape of the data. There are 96 rows and no missing values.
3. Plot each country's average life expectancy and average GDP for 2000–2015. GDP is shown in trillions of US dollars.
4. Plot life expectancy and GDP by year, so the path over time is visible and not only the average.
5. Report the Pearson correlation between life expectancy and GDP for each country, then plot that relationship in its own panel.

## Findings

- Five countries sit in a narrow band of average life expectancy, about 74 to 80 years. Zimbabwe's average is about 50 years.
- The United States and China have by far the largest total GDP. Chile's life expectancy is still about the same as the United States. Total GDP mostly reflects country size.
- Inside every country, GDP and life expectancy rise together across these years. Life expectancy ended higher in 2015 than in 2000 everywhere. Zimbabwe's path dipped first: life expectancy bottomed in 2004, while GDP bottomed in 2008.
- For five of the six countries, life expectancy tracks the calendar year even more closely than it tracks GDP.

These charts show that the two measures moved together. They do not show that GDP by itself caused the change in life expectancy.

## Next steps

GDP per person would be a better economic measure for this question than national GDP. This file does not include population, so that comparison needs a second dataset.
