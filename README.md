# UK House Price & Affordability Forecasting (Multi-Task LSTM)

MSc Data Science dissertation project, Manchester Metropolitan University, 2026.

## About this project

House prices and affordability don't always move together — a region can get
more expensive while wages catch up, or fall further behind even as prices
grow slowly. This project looks at both, forecasting house prices *and*
affordability across five UK regions, and testing whether a single model
that learns both at once (a multi-task LSTM) actually does better than
training separate models or using traditional statistical methods.

## Regions

London, North West, South East, Wales, Yorkshire and The Humber.

## Data used

- UK House Price Index — HM Land Registry (monthly, 2000–2026)
- Regional earnings — ONS Annual Survey of Hours and Earnings (via Nomis)
- CPI — Office for National Statistics
- Bank of England base rate history

## What's in this repo

- `dissertation.ipynb` — the full pipeline, start to finish: merging the
  data, stationarity testing, feature engineering, baseline models, the LSTM
  models, statistical testing, a rolling backtest, bootstrap confidence
  intervals, and SHAP explainability
- `requirements.txt` — exact package versions used
- CSV files with results for every model and evaluation method
- The chart images used in the dissertation

## Models and evaluation methods

- Naive persistence baseline
- ARIMA / SARIMA
- Single-task LSTM (house prices only)
- Single-task LSTM, multivariate (house prices + macro features)
- Multi-task LSTM (house prices + affordability, shared encoder)
- Diebold-Mariano test, to check whether differences between models are
  actually statistically significant rather than noise
- A rolling 24-month one-step-ahead backtest
- Bootstrap confidence intervals for the affordability forecasts
- SHAP for feature importance (permutation-based). DeepExplainer was also
  attempted as a cross-check but failed consistently due to a TensorFlow/SHAP
  compatibility issue in this environment — that's documented in the
  dissertation rather than hidden

## What I found

The statistical baselines (Naive, ARIMA, SARIMA) beat both LSTM models across
every region and both prediction targets. The multi-task LSTM didn't come
out ahead of the single-task LSTM or the statistical models anywhere, most
likely because there just isn't much training data to work with — around
312 monthly observations per region. It's not the result I set out expecting,
but it's a genuine one, and I've written it up honestly in the dissertation
rather than dressing it up as a success.

## Author

Jerusha Johanna Janetrin Julies David Dass
MSc Data Science, Manchester Metropolitan University
Supervisor: Dr Abeynayake
