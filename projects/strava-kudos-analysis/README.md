# Strava Kudos Analysis

A statistical analysis of what earns kudos on 178 Strava runs (March 2024 to October 2026). It covers one runner's public activities, so it's a case study rather than a general result.

## Files

- `Strava_Kudos_Analysis.ipynb`: the notebook for Parts 1 to 5, with code, outputs, and written interpretation.

## Live dashboard

The results are also shown in an interactive dashboard: https://strava-dashboard-lovat-one.vercel.app/kudos

## Approach

1. **Part 1:** data cleaning, exploration, and choosing a time control to account for follower growth. A quadratic trend fit best.
2. **Part 2:** an OLS baseline with diagnostics, influential-run checks, and time-control variants.
3. **Part 3:** Poisson count models, overdispersion checks, likelihood-ratio tests, and rate ratios.
4. **Part 4:** time-series checks on the residuals, robustness refits, and a VIF check on the final model.
5. **Part 5:** a logistic model for "breakout" runs, with test-set performance, a summary of seven hypotheses, and recommendations.

## Main findings

- A photo or video is associated with about 20% more kudos.
- Each extra kilometre is associated with about 4% more kudos.
- Weekend posting doesn't help by itself. Weekend runs get more kudos mainly because they're longer.
- Pace, PRs, and captions don't show a clear effect once distance, photos, and audience are accounted for.

## Limitations

The data is observational, so the photo effect may partly reflect that photos are taken on more special runs. Follower counts aren't available, so the models use time and recent kudos as stand-ins for audience size.

## Tools

Python, pandas, NumPy, statsmodels (OLS, Poisson, and logistic regression), scikit-learn, SciPy, and matplotlib.
