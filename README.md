## Principal Component Analysis (PCA): African Economic Indicators ##

## 1. Project Overview ##

This project implements PCA using nupy for computation, matplolib for plots and python for function. We applied PCA to a dataset of African economic indicators (1980-2022) to reduce mant related economic measures into a smaller set of components while keeping most of the information (variance).

## 2. The Dataset ##

- **Source:** [Add source and link]
- **File:** `ObservationData_lavlqce.csv` (included in this repo)
- **Coverage:** African countries, years 1980-2022
- **Size:** **2,322 rows** (country-year observations)
- **Numeric columns:** **29** economic indicators
- **Non-numeric column:** `Country` (text)
- **Missing values:** **3,193** missing cells

**Indicators include:**

- GDP growth rates and GDP (current and constant US$)
- Household and government consumption
- Gross capital formation (private and public)
- Exports and imports
- Central government revenue, expenditure and fiscal balance
- Current account balance
- Inflation

**Why this data?**

- It is **Africa-focused**.
- It has **real missing values**.
- It has a **non-numeric column**.
- It has **more than 7 columns**.

---

## 3. What the Notebook Does (Step by Step)

1. **Load data:** read the CSV and separate `Country` and `Year` from the numeric columns.
2. **Check missing values:** count them per column and per year.
3. **Encode non-numeric data:**
   - Map each country to one of **5 regions** (North, West, East, Central, Southern Africa).
   - One-hot encode the regions into 5 columns of 0/1.
   - *Why:* PCA needs numbers, not text.
4. **Impute missing values:**
   - Replace each missing value with its **column median**.
   - *Why:* the median is not thrown off by extreme values such as huge GDP figures.
5. **Standardize:**
   - Apply **z = (x - mean) / std** to every column.
   - *Why:* so large-number columns (US$) do not dominate.
6. **Covariance matrix:**
   - Compute **(Z^T Z) / (n - 1)**, a 34 x 34 matrix.
   - *Why:* it shows how each pair of features varies together.
7. **Eigendecomposition:**
   - Compute the eigenvalues and eigenvectors of the covariance matrix.
   - *Why:* eigenvectors are the component directions, and eigenvalues show their importance.
8. **Sort components** from largest to smallest eigenvalue.
9. **Explained variance:** eigenvalue / sum of eigenvalues x 100.
10. **Select components:** automatically pick the smallest number that reaches **90%** cumulative variance.
11. **Project:** multiply the standardized data by the chosen eigenvectors.
12. **Visualize:** plot before PCA vs. after PCA, coloured by region.

---

## 4. Key Results

- **Original features (after encoding):** **34** (29 indicators + 5 region columns)
- **Components kept:** **13**
- **Variance kept:** **91.48%**
- **PC1 explained variance:** 33.26%
- **PC2 explained variance:** 12.30%
- **PC1 + PC2 together:** 45.56%
- **Reduced data shape:** **(2322, 13)**

**Sanity checks passed:**

- Every standardized column has **mean = 0** and **standard deviation = 1**.
- The covariance matrix is **symmetric** (34 x 34).
- The **sum of eigenvalues equals the trace** of the covariance matrix (34.01).
- **PC1 variance (11.31) > PC2 variance (4.18)**, and the projected means are about 0.
- The **number of points is unchanged** (2,322) before and after PCA.

---

## 5. Interpretation

> **Note:** The written explanations are in the notebook, in the group's own words. Short summaries are below.

- **Before vs. after PCA visual:** [Group to write a short summary]
- **Why 13 components and the trade-offs:** [Group to write a short summary]
- **What information is lost (economic activity, population pressure):** [Group to write a short summary]

---

## 6. Limitations

- **Median imputation** fills gaps with one value per column, which slightly reduces natural variation. This matters most for **1980**, where about 20% of values were missing.
- **Region encoding** replaces individual countries with 5 broad regions, so country-level differences are not captured.
- **Interpretability:** each component is a mixture of many indicators, so it is harder to explain than an original indicator.
- **No direct population variable** exists, so "population pressure" is only reflected indirectly.

---


## 7. How to Run

1. Open **PCA_Notebook.ipynb** in **Google Colab** (or Jupyter).
2. Upload **ObservationData_lavlqce.csv** and update the file path in the first code cell if needed.
3. Run the cells **in order**, from top to bottom.

**Libraries used:** `numpy` and `matplotlib` only.


---

## 8. Links

- **GitHub repo:** [paste link]
- **Colab notebook:** [paste link]

