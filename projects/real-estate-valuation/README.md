# Real Estate Price Estimation

A regression project that estimates house price per unit area from house age, distance to the nearest MRT (metro) station, number of nearby convenience stores, and location (latitude and longitude). The dataset has 414 house sales.

## Files

- `Assignment_1.ipynb`: the full notebook with code, plots, and written analysis.
- `Real_estate_valuation_data_set.xlsx`: the sales data used in the notebook.

## Approach

1. Split the data into 331 training houses and 83 test houses, stratified by distance to the nearest MRT station.
2. Explore correlations and geography. Distance to the MRT station was the strongest signal, and a log transform made it more linear.
3. Prepare features with a scikit-learn pipeline: median imputation, a log transform for distance, location clusters from latitude and longitude, and standard scaling.
4. Compare linear regression, a decision tree, and a random forest with 10-fold cross-validation.
5. Tune the random forest with grid search and randomized search.

## Results

- Cross-validation RMSE for the tuned model was about 5.7.
- Test RMSE was about 12, with a 95% confidence interval of roughly 8.0 to 20.6. The test set includes the highest and lowest prices in the data, which fall outside the training range. The random forest cannot predict outside the range it was trained on.
- The model still beats always predicting the average price (test RMSE about 15.9).

## Tools

Python, pandas, NumPy, scikit-learn, matplotlib, SciPy, Jupyter.

## Limitations

The data covers about one year of sales, so prices may have changed since. The test set is small (83 houses), so the error estimate is noisy.
