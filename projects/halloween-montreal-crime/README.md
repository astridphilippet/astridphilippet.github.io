# Halloween and Crime in Montréal

A group project for INSY 674. It uses City of Montréal police reports (2015–2025) to predict high-crime days and to test whether Halloween changes the crime pattern.

## Files

- `Model_Building.ipynb`: the full notebook, with exploration, feature engineering, model comparison, the Halloween analysis, and the 2026 forecast. Saved outputs are included.

The source dataset (`actes-criminels.xlsx`) is not included. It is public police data from the City of Montréal open-data portal.

## Approach

1. Define a high-crime day as one above the 75th percentile of daily crime counts in the training years (2015–2023).
2. Compare four model families with time-aware validation: logistic regression, Bayesian negative binomial regression, random forest, and a neural network.
3. Use sliding-window cross-validation, a 29-day gap before each prediction date to avoid leakage, and a held-out test set (2024–2025) used once at the end.
4. Tune the shortlisted models with random search, then combine them into an ensemble.
5. Analyze Halloween by crime type, time of day, and police district, and forecast mischief for Oct 30 – Nov 2, 2026.

## Results

- Development-period AUC for the final ensemble was 0.814 (±0.064).
- On the 2024 and 2025 test years, the final model scored 0.664 and 0.674 AUC. The seasonal-naive baseline scored 0.649 and 0.648. The model's advantage over the baseline is small.
- The strongest Halloween finding is a shift in crime mix rather than more total crime. Logistic regression estimated about 22% higher odds of mischief and 23% higher odds of robbery in the Halloween window. The Bayesian model gave similar estimates.
- The district-level Halloween effect was not statistically significant at the 5% level (p = 0.067).

## Limitations

The dataset records when incidents were reported, not when they happened, so the Halloween effect may be blurred. The models also don't account for weather, major events, or school schedules.

## Team

INSY 674 group project. [Add team member names here.]

## Tools

Python, pandas, scikit-learn, PyMC, ArviZ, statsmodels, SciPy, matplotlib, holidays. Developed in Google Colab.
