# Online News Popularity Prediction

An end-to-end Machine Learning and Business Intelligence project analyzing article metadata and content features to classify and predict online news popularity.

---

## 📌 Project Overview
This project applies statistical preprocessing, feature engineering, and supervised machine learning classification algorithms to predict whether an article will gain high engagement (shares) based on factors such as publication timing, sentiment polarity, keyword metrics, and media content.

The repository includes:
* **Machine Learning Pipeline:** Data preprocessing, outlier detection, feature selection, model training, and performance evaluation.
* **Interactive Dashboard:** Power BI report (`.pbix`) detailing feature distributions and key engagement metrics.
* **Comprehensive Documentation:** Full technical coursework report and methodology analysis.

---

## 🛠️ Tech Stack & Tools
* **Programming Language:** Python 3.x
* **Core Libraries:** `pandas`, `numpy`, `scikit-learn`, `matplotlib`, `seaborn`
* **Data Visualization:** Microsoft Power BI (`.pbix`)
* **Environment:** Python Script / Jupyter Notebook

---

## 📂 Repository Structure
```text
├── docs/
│   ├── COVER_PAGE.pdf
│   └── SWA2124_Group10_OnlineNewsPopularity.docx  # Full project report
├── dashboard/
│   └── SWA2124_Group10_Online_News_Popularity.pbix # Power BI visualization
├── src/
│   └── SWA2124_Group10_OnlineNewsPopularity.py    # Main ML script
├── .gitignore
└── README.md
```

---

## 🚀 How to Run the Analysis

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/](https://github.com/)<your-username>/<your-repo-name>.git
   cd <your-repo-name>
   ```

2. **Set up a virtual environment (optional but recommended):**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install required packages:**
   ```bash
   pip install pandas numpy scikit-learn matplotlib seaborn
   ```

4. **Execute the Python script:**
   ```bash
   python src/SWA2124_Group10_OnlineNewsPopularity.py
   ```

5. **View the Dashboard:**
   Open `dashboard/SWA2124_Group10_Online_News_Popularity.pbix` using **Microsoft Power BI Desktop**.
