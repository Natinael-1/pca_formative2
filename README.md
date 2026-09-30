## Principal Component Analysis (PCA): African Economic Indicators ##

## 1. Project Overview ##

This project implements PCA using nupy for computation, matplolib for plots and python for function. We applied PCA to a dataset of African economic indicators (1980-2022) to reduce mant related economic measures into a smaller set of components while keeping most of the information (variance).

## 2. The Dataset ##

**Source:** [Add source, e.g. African Development Bank / UN data portal, and link]
**File:** ObservationData_lavlqce.csv (included in this repo)
**Coverage:** African countries, years 1980-2022
**Size:** 2,322 rows (country-year observations)
**Numeric columns:**	29 economic indicators
**Non-numeric columns:**	Country (text)
**Missing values:** 3,193 missing cells across the numeric columns

##Sanity checks passed:##

*Standardized data has mean = 0 and standard deviation = 1 for every column.
*The covariance matrix is symmetric (34 x 34).
*The sum of eigenvalues equals the trace of the covariance matrix (34.01).
*PC1 variance (11.31) is greater than PC2 variance (4.18), and the projected means are about 0.
*The number of points is the same before and after PCA (2,322).
