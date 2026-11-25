# Causal Inference: MRT Distance and House Prices

A causal analysis of how being within 500 m of a metro (MRT) station affects house prices per unit area. It uses the same 414 house sales as the real estate price project.

## Files

- `Causal_Inference_Real_Estate.ipynb`: the notebook, with code, outputs, and written interpretation.
- The dataset is in the real estate project folder: `../real-estate-valuation/Real_estate_valuation_data_set.xlsx`. Put a copy next to the notebook to run it.

## Approach

1. **Treatment and controls.** The treatment is being within 500 m of an MRT station. Controls are location, house age, transaction date, and nearby stores.
2. **CausalML.** Estimates with an S-learner (linear regression), a T-learner (XGBoost), and their comparison, plus a check without the stores control.
3. **DoWhy.** The four-step workflow: model the assumptions, identify the effect, estimate it (linear regression, propensity score matching), and refute it with placebo, random common cause, and subset tests.
4. **Other treatments.** The same steps for houses with 5+ stores nearby and for houses under 10 years old.

## Main findings

- The naive price gap between near and far houses is about 16.8 per unit area.
- With stores as a control, the estimates are about 9.4 to 9.7. About 40% of the naive gap comes from other differences between near and far houses.
- The effect looks larger for newer houses and for houses further west, away from the centre. The confidence intervals overlap for the other treatments.
- The main estimate passed the placebo, random common cause, and subset refuters.

## Limitations

- The dataset has no information on house size, building type, or neighbourhood. A hidden confounder could affect both distance to a station and price, and the refuters can't detect that.
- Overlap is weak for about 17% of houses, where location almost determines whether a house is near a station.
- The result depends on the 500 m cut-off.
- With 414 houses, estimates for individual houses are noisy, so the averages are more reliable.

## Tools

Python, pandas, NumPy, scikit-learn, XGBoost, CausalML, DoWhy, and matplotlib. Developed in Python 3.12.
