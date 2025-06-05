<!---
nav:
    - Home=/
    - Statistics=/trading/statistics/note.md
left_pane: toc
--->

# 1 Basics

## Mean

The mean is just the **average** value.
It tells you where the center of your data is.

For *n* numbers: *x₁, x₂, ..., xₙ*, the mean *μ* is:

```
μ = (1/n) * Σ xᵢ
```

## Variance

The variance tells you how **spread out** the data is — how far from the mean the values tend to be.

- Big variance: values are spread out.
- Small variance: values are clustered close to the mean.

```
Variance = (1/n) * Σ (xᵢ - μ)²
```


Why square?

- So that positive and negative deviations don’t cancel out.
- Squaring also penalizes big deviations more.


## Standard Deviation

The standard deviation is just the **square root of variance**.
It is in the **same units** as the original data, easier to interpret.

```
σ = sqrt(Variance)
```


## Covariance

Covariance measures how **two variables move together**.

- If they both increase together, covariance is positive.
- If one increases while the other decreases, covariance is negative.
- If they are unrelated, covariance is close to zero.

For two variables *X* and *Y*, each with *n* values:

```
Cov(X, Y) = (1/n) * Σ (xᵢ - mean_X) * (yᵢ - mean_Y)
```

Intuition:

- If both X and Y are above or below their means at the same time, positive contribution.
- If one is above and the other is below, negative contribution.


## Correlation

Correlation is a **scaled version of covariance**, it removes the units and normalizes between -1 and +1.

- +1: perfect positive linear relationship
- -1: perfect negative linear relationship
- 0: no linear relationship

```
Corr(X, Y) = Cov(X, Y) / (StdDev(X) * StdDev(Y))
```


## Autocorrelation

Autocorrelation (also called serial correlation) measures how a time series is correlated with a lagged version of itself.
In simple terms, does today's value depend on past values? If yes, autocorrelation exists.

- If autocorrelation exists, we can potentially predict future values based on past.
- If not, the series is more like random noise.

For time series *Xₜ*, lag *k*:

```
Autocorrelation at lag k = Corr(Xₜ, Xₜ₋ₖ)
```

Interpretation

| Autocorrelation Value | Meaning |
|---|---|
| Close to +1 | Strong positive correlation, values repeat trend |
| Close to -1 | Strong negative correlation, values alternate up/down |
| Close to 0 | No correlation, no predictable pattern |


Autocorrelation Plot (ACF Plot)

- Shows autocorrelation at different lags.
- Helps identify patterns:
    - Trending series: slow decay of autocorrelation.
    - Mean-reverting series: negative autocorrelation at certain lags.
    - Random walk: no significant autocorrelation.

## Summary

| Concept    | Meaning |
|---|---|
| Mean      | Average — where the data centers |
| Variance  | How spread out the data is |
| Std Dev   | Square root of variance — easier to interpret as "typical deviation" |
| Covariance | Measures how two variables move together (units depend on X and Y) |
| Correlation| Scaled covariance, unit-free, ranges [-1, +1], easy to interpret |
| Autocorrelation  | How current value relates to past values. Detect trends, mean reversion, model building |

Why important in time series / trading?

- Mean return: is your asset trending up or down?
- Variance / Std Dev: how risky / volatile is this asset?
- Many trading signals depend on moving averages (mean) and volatility (variance)!
- In portfolio construction: want to select assets with low or negative correlation for diversification.
- In pairs trading: look for highly correlated or cointegrated pairs.
- In risk models: correlation matrix used to model portfolio risk.
- Trend following: positive autocorrelation (momentum).
- Mean reversion: negative autocorrelation.
- ARIMA models: built on autocorrelation patterns.
- Strategy testing: check if signals are statistically significant or just noise.
