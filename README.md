# Hypothesis Testing in Soccer: Are More Goals Scored in Women's Matches?

A data science project completed as part of the **DataCamp** curriculum, applying statistical hypothesis testing to real-world international soccer data.

---

##  Project Overview

As a sports journalist at a major online media company, the goal of this project was to investigate a long-held gut instinct: **are more goals scored in women's international soccer matches than in men's?**

To answer this rigorously, a formal statistical hypothesis test was conducted using historical FIFA World Cup match data (excluding qualifiers) from **January 1, 2002 onwards** — scoped to control for the sport's evolution over time and tournament-level variance.

---

##  Research Question

> Are more goals scored in women's international soccer matches than men's?

**Null Hypothesis (H₀):** The mean number of goals scored in women's international soccer matches is the same as in men's.

**Alternative Hypothesis (Hₐ):** The mean number of goals scored in women's international soccer matches is *greater* than in men's.

**Significance Level:** α = 0.10

---

##  What I Did

1. **Loaded and explored the data** — Read two CSV datasets (`men_results.csv`, `women_results.csv`) containing results of international matches dating back to the 19th century.

2. **Cleaned and prepared the data** — Converted date columns from `object` to `datetime` dtype, checked for null values, and inspected unique value distributions across all columns.

3. **Filtered for relevance** — Isolated only official FIFA World Cup matches from 2002 onwards for both datasets.

4. **Feature engineering** — Created a `total_goals` column by summing `home_score` and `away_score` for each match.

5. **Exploratory Data Analysis** — Visualized goal distributions using histograms (via Seaborn/Matplotlib) to understand the shape of the data.

6. **Normality testing** — Applied the **Shapiro-Wilk test** to both distributions. Results indicated the data was **not normally distributed**, ruling out a standard t-test.

7. **Hypothesis testing** — Used the **Mann-Whitney U test** (a non-parametric alternative) via the `pingouin` library to compare goal distributions between women's and men's matches.

8. **Drew a conclusion** — Extracted the p-value and applied the decision rule: reject H₀ if p ≤ 0.10.

---

##  Results

The Mann-Whitney U test returned a p-value **below the 0.10 significance level**, leading to the conclusion:

 **Reject H₀** — There is statistically significant evidence that more goals are scored in women's FIFA World Cup matches than in men's.

---

##  What I Learned

- How to frame a real-world question as a **formal statistical hypothesis**
- The importance of **checking assumptions** (normality) before selecting a statistical test
- When and why to use **non-parametric tests** like the Mann-Whitney U test instead of a t-test
- How to use **`pingouin`** for clean, readable hypothesis testing in Python
- Data cleaning workflows: dtype conversion, null checking, and value inspection
- Filtering and transforming pandas DataFrames for targeted analysis
- Communicating statistical results clearly with a defined significance level

---

##  Tools & Libraries Used

| Tool / Library | Purpose |
|---|---|
| `pandas` | Data loading, cleaning, filtering, and feature engineering |
| `matplotlib` | Plotting and visualization |
| `seaborn` | Histogram plots for EDA |
| `scipy.stats` | Shapiro-Wilk normality test |
| `pingouin` | Mann-Whitney U hypothesis test |
| Python 3 | Core programming language |

---

##  Dataset

- `men_results.csv` — Results of men's international soccer matches (scraped from a reliable online source)
- `women_results.csv` — Results of women's international soccer matches

Both datasets contain match-level data including date, tournament name, home score, away score, and other match metadata.

---

##  How to Run

```bash
# Clone the repository
git clone https://github.com/your-username/soccer-hypothesis-test.git
cd soccer-hypothesis-test

# Install dependencies
pip install pandas matplotlib seaborn scipy pingouin

# Run the notebook
jupyter notebook notebook.ipynb
```

---

*Project completed as part of the DataCamp Data Analyst in Python curriculum.*