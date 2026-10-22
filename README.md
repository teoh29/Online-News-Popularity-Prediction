<div align="center">

<sub>SOCIAL & WEB ANALYTICS · FINAL PROJECT</sub>

# What Makes News Worth Sharing?

### Online News Popularity Analysis

Exploring article engagement through data analysis, machine learning, and Power BI.

**Python · pandas · scikit-learn · Matplotlib · Seaborn · Power BI**

[Explore the workflow](#02--from-articles-to-insights) · [Review the models](#03--five-models-one-question) · [Run the analysis](#06--run-it-yourself)

</div>

---

## 01 / The question behind the project

Some articles attract thousands of shares. Others receive far less attention. What can article characteristics tell us about that difference?

This project explores **online news popularity** using numerical features associated with Mashable articles. It combines exploratory data analysis, five classification models, and a Power BI report to examine patterns in content, publication timing, keywords, and sentiment.

Developed for **SWA2124 Social & Web Analytics**, the project connects technical analysis with questions relevant to publishers, editors, and digital-content teams.

### Research objectives

- Explore how social shares vary across articles, categories, and publication days.
- Examine relationships between article features and popularity.
- Compare five supervised classifiers using a common train/test split.
- Communicate patterns and model performance through charts and a Power BI report.

## 02 / From articles to insights

| Explore | Predict | Communicate |
| :--- | :--- | :--- |
| Inspect data quality and visualize engagement patterns. | Train five models to classify article popularity. | Present findings through evaluation charts, a written report, and Power BI. |

### Exploratory analysis

The first section of the Python script:

1. Loads the dataset and removes whitespace from column names.
2. Reports missing values and removes duplicate rows when present.
3. Filters records with `n_unique_tokens > 1`.
4. Removes `url` and `timedelta` from the analysis table.
5. Creates a popularity label and a log-transformed shares field.
6. Produces visualizations covering:
   - Popular versus non-popular article counts.
   - Raw and log-transformed share distributions.
   - Popularity rates by news category.
   - Popularity rates by publication day.
   - Correlations between selected features and popularity.

### Classification workflow

The modelling section independently reloads the CSV, removes metadata and the raw shares target from the predictors, and creates a binary target. It then uses an **80/20 stratified train/test split** with **`random_state=42`**.

`StandardScaler` is fitted on the training data and applied to the test data for Logistic Regression and KNN. Tree-based models use the unscaled features.

## 03 / Five models, one question

**Can article features help distinguish popular articles from less popular ones?**

| Model | Role in the comparison | Configuration in the script |
| --- | --- | --- |
| Logistic Regression | Linear baseline | `max_iter=1000`, scaled features |
| Decision Tree | Individual tree baseline | `random_state=42` |
| Random Forest | Ensemble of decision trees | `n_estimators=200` |
| Gradient Boosting | Sequential boosting model | `random_state=42` |
| K-Nearest Neighbours | Similarity-based classifier | `n_neighbors=15`, scaled features |

### Evaluation

| Metric | What it measures |
| --- | --- |
| Accuracy | Proportion of all predictions that are correct |
| Precision | Proportion of predicted popular articles that are actually popular |
| Recall | Proportion of actual popular articles identified by the model |
| F1-score | Harmonic mean of precision and recall |

The script ranks models by F1-score and generates confusion matrices for all five models, along with a separate confusion matrix for the highest-ranked model. It also plots Gradient Boosting importance values for six selected features.

### Results reported in the submission

The written report identifies **Gradient Boosting** as its best-performing model:

| Accuracy | Precision | Recall | F1-score |
| :---: | :---: | :---: | :---: |
| 0.666 | 0.674 | 0.725 | **0.699** |

These values are transcribed from the submitted report, not independently reproduced results. The report also describes higher weekend popularity rates and an association between keyword-related features and popularity. These are observational findings rather than evidence of causation.

<details>
<summary><strong>Read the reproducibility notes</strong></summary>

The supplied script has two separate processing sections that should be aligned before treating their outputs as one experiment:

- **Target boundary:** EDA labels articles popular when `shares > 1400`; the ML section uses `shares >= 1400`. Articles with exactly 1,400 shares therefore receive different labels.
- **Cleaning:** Duplicate removal and the unique-token filter are applied in EDA but are not reapplied after the ML section reloads the CSV.
- **File loading:** EDA checks several paths and offers a Colab upload fallback. The ML section always reads `OnlineNewsPopularity.csv` from the current working directory.
- **Evaluation scope:** The supplied script uses one held-out split. It does not implement cross-validation, hyperparameter search, or ROC-AUC calculation.
- **Feature importance:** The final chart shows six explicitly selected features, not necessarily the six highest-ranked features across the whole model.
- **Group label:** Filenames identify Group 10, while the script's opening comment says Group 27.

The README documents the submitted implementation; it does not modify the analysis code. Reconcile these details and rerun the analysis before publishing newly verified metrics.

</details>

## 04 / Explore the deliverables

| Deliverable | Open or download | Purpose |
| --- | --- | --- |
| Python analysis | [Analysis script](SWA2124_Group10_OnlineNewsPopularity.py) | EDA, model training, evaluation, and chart generation |
| Power BI | [Dashboard file](SWA2124_Group10_Online_News_Popularity.pbix) | Visual presentation of the project analysis |
| Written report | [Project report](SWA2124_Group10_OnlineNewsPopularity.docx) | Research context, methodology, reported findings, and discussion |

### Viewing the Power BI report

Download the `.pbix` file and open it in **Power BI Desktop**. The repository file is a downloadable report, not a published interactive web dashboard. If refreshing data prompts for a missing source, update the source location to your local copy.

## 05 / The dataset

The project uses the **Online News Popularity** dataset from the UCI Machine Learning Repository. It contains statistics associated with Mashable articles, including content structure, keywords, publication timing, and sentiment. The `shares` field records social-network shares.

**[Download the dataset from UCI →](https://archive.ics.uci.edu/dataset/332/online%2Bnews%2Bpopularity)**

The submission ZIP does **not** include `OnlineNewsPopularity.csv`. Download and extract it separately before running the script. The dataset contains article statistics rather than the full article text.

## 06 / Run it yourself

### Requirements

- Python 3.10 or later, as described in the project report.
- `pandas`, `numpy`, `matplotlib`, `seaborn`, and `scikit-learn`.
- Power BI Desktop to view the `.pbix` deliverable.

### Prepare the files

Place this README beside the original project files. Download the dataset and place the CSV in the same folder:

```text
online-news-popularity-analysis/
├── README.md
├── SWA2124_Group10_OnlineNewsPopularity.py
├── SWA2124_Group10_OnlineNewsPopularity.docx
├── SWA2124_Group10_Online_News_Popularity.pbix
├── OnlineNewsPopularity.csv                  # Download separately
└── .gitignore
```

This layout matches the supplied files without renaming them. If you organize them into `src/`, `docs/`, and `dashboard/`, update the links and commands accordingly.

### Install dependencies

Open a terminal in the project folder. An optional virtual environment keeps dependencies separate:

```bash
python -m venv .venv
```

Activate it on Windows PowerShell:

```powershell
.\.venv\Scripts\Activate.ps1
```

Or on macOS/Linux:

```bash
source .venv/bin/activate
```

Install the required libraries:

```bash
python -m pip install pandas numpy matplotlib "seaborn>=0.13" scikit-learn
```

This command installs the required packages but does not recreate a version-pinned original environment. The plotting code uses Seaborn's newer categorical-plot options.

### Run the script

```bash
python SWA2124_Group10_OnlineNewsPopularity.py
```

Run from the folder containing `OnlineNewsPopularity.csv`. Charts are displayed and saved during execution; depending on the plotting backend, close a chart window to allow the script to continue.

For Google Colab, upload the CSV to the notebook's working directory before executing the script. This ensures both data-loading sections can find the same filename.

## 07 / Outputs you can expect

Files are written to the current working directory. Re-running the script replaces outputs with the same names.

| Output | Content |
| --- | --- |
| `chart1_target_distribution.png` | Popularity class counts |
| `chart2_shares_distribution.png` | Raw and log-transformed share distributions |
| `chart3_category_popularity.png` | Popularity rates by news category |
| `chart4_weekday_weekend_popularity.png` | Popularity rates by publication day |
| `chart5_correlation_heatmap.png` | Correlations for selected features and target |
| `member4_model_comparison_results.csv` | Accuracy, precision, recall, and F1-score by model |
| `confusion_matrix_best_model.png` | Confusion matrix for the model ranked highest by F1 |
| `confusion_matrix_all_models.png` | Comparison of all five confusion matrices |
| `gb_feature_importance_selected.png` | Gradient Boosting importance for selected features |

Classification reports, dataset summaries, and the ranked model comparison are also printed to the terminal. The script does not save trained models to disk.

<div align="center">

**From article statistics to a clearer picture of engagement.**

SWA2124 · Social & Web Analytics · Online News Popularity

</div>

## Credits and references

- **Project:** SWA2124 Online News Popularity submission, identified as Group 10 in the deliverable filenames.
- **Dataset:** [UCI Online News Popularity](https://archive.ics.uci.edu/dataset/332/online%2Bnews%2Bpopularity).
- **Research references:** See the bibliography in the submitted project report.

No project license file is included in the supplied archive. Dataset and third-party material usage remains subject to the applicable source terms.
