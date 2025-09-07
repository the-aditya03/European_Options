## Overview

This repository contains a comprehensive analysis comparing two foundational models for pricing European call and put options:

1. **Binomial Tree Model** (discrete‐time, multi‐step framework)
2. **Black‑Scholes Model** (continuous‐time, closed‐form solution)

Using historical market data for major ETFs (SPY, QQQ, DIA), the project:

* Implements both pricing models from first principles
* Fetches adjusted closing prices and dividend yields via Yahoo Finance
* Calibrates model inputs (volatility, risk‑free rate, dividend yield)
* Quantifies and visualizes pricing errors across maturities
* Interprets model performance in light of market characteristics
  
**Citation:** Hull, J. (2009). Options, futures and other derivatives. Pearson Education.
---

## Assumptions

1. **No Arbitrage**: Markets do not allow riskless profit opportunities.
2. **Risk‑Neutral Valuation**: All investors are indifferent to risk; expected returns equal the risk‑free rate.

| Assumption         | Binomial Tree Model                      | Black‑Scholes Model                        |
| ------------------ | ---------------------------------------- | ------------------------------------------ |
| Time Framework     | Discrete steps (N intervals of Δt)       | Continuous time (differential formulation) |
| Price Dynamics     | Up/down factor per step                  | Continuous lognormal diffusion             |
| Volatility         | Constant per step; converges to σ as N→∞ | Constant instantaneous volatility          |
| Interest Rate      | Discrete per‐period rate                 | Continuously compounded rate               |
| Dividend Treatment | Per‐step dividend yield q                | Continuous dividend yield δ                |

---

## Features

This project provides a comprehensive analysis of European option pricing using both **Binomial Tree** and **Black-Scholes** models. Key features include:

- **Option Pricing Models**
  - Implementation of the **Binomial Tree model** with variable step control.
  - Implementation of the **Black-Scholes closed-form model**.
  - Calculation of **Option Greeks** (Delta, Gamma, Vega, Theta, Rho) for risk sensitivity analysis.

- **Market Data Integration**
  - Automatic retrieval of **real market data** using Yahoo Finance (e.g., AAPL stock).
  - Calculation of **historical volatility** from market data.
  - Retrieval of valid future **option expiry dates** and **option chains**.

- **Convergence Analysis**
  - Study of **Binomial Tree convergence** to the Black-Scholes price with increasing steps.
  - Analysis of **absolute and percentage errors** at different step counts.
  - Visualization of convergence patterns for better understanding.

- **Computational Efficiency**
  - Evaluation of **computation time** as the number of steps in the Binomial Tree increases.
  - Comparison of computational complexity between **analytical** and **numerical methods**.

- **Sensitivity Analysis**
  - Study of option price sensitivity with respect to key parameters:
    - Volatility (σ)
    - Time to maturity (T)
    - Risk-free interest rate (r)
    - Strike price (K)
  - Side-by-side comparison of **Black-Scholes** vs **Binomial Tree** model behavior.

- **Pricing Accuracy**
  - Comparison of model prices against **market option prices**.
  - Analysis of **absolute and percentage errors** for different strike prices.
  - Identification of **regions of high deviation** (ATM, ITM, OTM).

- **Binomial Tree Visualization**
  - Graphical representation of **stock price tree** and **option value tree** (up to 5 steps).

- **Error Convergence Analysis**
  - Detailed study of how Binomial Tree errors decrease as the number of steps increases.
  - Visualization of **accuracy vs number of steps**.

- **Performance Analysis**
  - Summary of **assumptions** for both models.
  - Comparison of **analytical vs numerical approaches**.
  - Insights into **practical considerations** for real-world option pricing.

- **Interactive & Modular**
  - Functions are **modular**, allowing easy experimentation with different parameters, stocks, and option types.
  - Ready for **further extensions** like American options or dividend-adjusted pricing.

## Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/ss-prady/Quant-Finance-European-Option-Pricing.git
   ```
2. **Create a virtual environment (optional but recommended)**

   ```bash
   python3 -m venv venv
   source venv/bin/activate
   ```
3. **Install dependencies**

   ```bash
   pip install -r requirements.txt
   ```

---

## Methodology

1. **Parameter Estimation**

   * **Volatility (σ)**: Annualized standard deviation of log returns
   * **Dividend Yield (q)**: Trailing‐twelve‐month dividends / current price
   * **Risk‑Free Rate (r)**: Current 3‑month Treasury yield

2. **Model Computation**

   * **Binomial**: Forward induction to terminal payoffs, backward induction for present value
   * **Black‑Scholes**: Standard d₁, d₂ formulas for European options

3. **Error Metrics**

   * Absolute difference |ModelPrice – MarketPrice|
   * Aggregated statistics (mean, max) over maturity grid

---

## Key Findings

* **Short‑dated options (< 6 months)**: Both models produce comparable prices (errors < \$2).
* **Longer maturities (> 2 years)**:

  * Black‑Scholes errors grow significantly (up to \$25–30 for QQQ)
  * Binomial tree remains closer to market, likely due to discrete dividend handling
* **ETF-specific observations**:

  * QQQ’s higher volatility and tech‑sector skew amplify BS pricing error
  * DIA’s stability yields lower and more erratic errors for both models

---

## Dependencies

* Python ≥ 3.8
* numpy
* pandas
* scipy
* matplotlib
* yfinance

*All dependencies listed in* `requirements.txt`.

---

## Contributing

Contributions and suggestions are welcome. Please fork the repository and open a pull request with a clear description of your changes.

---

## License

This project is released under the [License](LICENSE).