# Comparative Analysis of Jakarta Composite Index (JCI) Forecasting Using Traditional and Machine Learning Time Series Approaches

A university project comparing statistical forecasting methods and Artificial Neural Networks (ANN) for Jakarta Composite Index (JCI/IHSG) closing prices.

The project explores data preprocessing, stationarity testing, model fitting, residual diagnostics, and performance evaluation using R.

## Dataset

The supplied dataset contains **558 trading-day observations**, from **January 2, 2024, to May 13, 2026**. The project report identifies Investing.com as the data source.

The analysis uses the closing-price column (`Terakhir`) from `Data Historis Jakarta Stock Exchange Composite.csv`. Prices are converted from Indonesian number formatting into numeric values.

## Methods

The project implements six forecasting approaches:

- Basic Naive
- Naive with Drift
- Simple Exponential Smoothing (SES)
- Double Exponential Smoothing (DES)
- ARIMA
- Artificial Neural Network (ANN)

The workflow includes log transformation, differencing, Augmented Dickey–Fuller tests, ACF/PACF plots, and ARIMA residual checks.

The supplied ANN configuration uses lags **1 and 3**, two hidden layers with **10 and 20 neurons**, and six random seeds. Performance is evaluated using **RMSE**, **MAE**, and **MAPE**.

## Reported Results

The following values come from the project report and have not been independently reproduced.

| Model | RMSE | MAE | MAPE (%) |
|---|---:|---:|---:|
| Basic Naive | 163.831 | 138.889 | 1.937 |
| Naive with Drift, h = 112 | 135.308 | 103.035 | 1.446 |
| SES, α = 0.3 | 154.408 | 115.498 | 1.629 |
| DES, α = 0.1, β = 0.05 | 156.138 | 118.946 | 1.675 |
| ARIMA(2,1,2) | 165.317 | 140.875 | 1.963 |
| ANN, lags 1 and 3, hidden layers 10–20 | 55.514 | 44.115 | 0.6149 |

The ANN configuration had the lowest reported errors among these selected models, with results averaged across six random seeds. Naive with Drift had the lowest errors among the traditional models shown.

**Evaluation context:** The supplied code processes the CSV in descending date order and normalizes ANN inputs before splitting the data. Its ANN evaluation also uses observed lagged values and a different test length from the traditional models. These results therefore describe the original experiment rather than a directly comparable, forward-in-time forecasting benchmark.

## Tools

- **R**
- `forecast` for baseline and exponential smoothing models
- `tseries`, `car`, `lmtest`, and `nortest` for statistical testing
- `neuralnet` for ANN modeling
- `dplyr` for lag creation
- `Metrics` for performance evaluation

## How to Run

1. Place `code.R` and the CSV file in the same folder.
2. Open `code.R` in R or RStudio.
3. Install the packages loaded by the script:

   ```r
   install.packages(c(
     "pracma", "nortest", "forecast", "lmtest", "car",
     "tseries", "Metrics", "nnet", "neuralnet", "dplyr"
   ))
   ```
   
4. Update the `setwd()` path to your project folder.
5. Run the script section by section to inspect the model comparisons, diagnostics, and ANN prediction plot.

`Code.Rmd` provides an additional R Markdown version of the analysis.

## Authors

- Marcell Prasetyo
- Aaron Jeremy Alexander

Time Series Analysis  
BINUS University
