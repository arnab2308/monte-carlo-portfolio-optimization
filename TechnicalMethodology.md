# Technical Methodology

This document details the technical methods employed in the portfolio optimization project.

## Mathematical Framework

1.  **Return Calculations:**

    *   Daily Returns:  `r_t = ln(P_t / P_{t-1})`
    *   Annualized Return: `R_a = (1 + R_d)^{252} - 1`
    *   Volatility: `σ = sqrt(252) * std(r_t)`

2.  **Portfolio Mathematics:**

    *   Portfolio Return: `R_p = Σ w_i * R_i`
    *   Portfolio Variance: `σ_p^2 = w^T Σ w`  where `Σ` is the covariance matrix and `w` is the vector of weights.

3.  **Optimization Objective:**

    *   Maximize Sharpe Ratio: `S = (R_p - R_f) / σ_p`
    *   Subject to:
        *   `Σ w_i = 1`
        *   `w_i ≥ 0` for all `i`

4.  **Monte Carlo Implementation:**

    *   Number of simulations: 10,000
    *   Random weight generation using Excel's `RAND()` function.
    *   Weight normalization to ensure `Σ w_i = 1`.

5.  **Risk Metrics:**

    *   Correlation matrix calculation.
    *   Covariance matrix calculation using daily returns.
    *   Portfolio variance calculation using matrix multiplication.

## Implementation Details

### Excel Functions Used

*   **Portfolio Returns:**
    *   `SUMPRODUCT` for weighted returns.
    *   `LN` for log returns.
    *   `AVERAGE` for mean calculations.

*   **Risk Calculations:**
    *   `MMULT` for matrix multiplication.
    *   `TRANSPOSE` for matrix operations.
    *   `STDEV` for volatility calculations.

*   **Optimization:**
    *   `Solver` for Sharpe ratio maximization.
    *   `INDEX`/`MATCH` for efficient lookups.
    *   `RAND` for Monte Carlo simulations.

## Validation Methods

*   Cross-verification of returns with market data.
*   Benchmark comparison with index returns.
*   Validation of correlation matrices.
*   Testing of portfolio constraints.