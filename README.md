# Option Pricing and Risk Models
Implementations of Black-Scholes, binomial trees, Monte Carlo simulations, and risk models for option pricing. Includes Greeks analysis and implied volatility surfaces.


[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)](https://jupyter.org/)
[![Status](https://img.shields.io/badge/Status-Active-success.svg)]()


---

## Notebooks 

This repository contains notebooks that provide implementation of options pricing and risk analysis:

|#| Notebook|Details | Implementation |
|--|---------|----------------|--------|
|1| **Black-Scholes Option Pricing and Monte Carlo**  | Implements the classic Black-Scholes formula and Monte Carlo simulations for European options. |[Documentation](https://github.com/xxxxyyyy80008/Option-Pricing-and-Risk-Models/blob/main/docs/01_black_scholes_monte_carlo.md) , [Kaggle Notebook](https://www.kaggle.com/code/xxxxyyyy80008/black-scholes-option-pricing-and-monte-carlo/) , [Github Notebook](https://github.com/xxxxyyyy80008/Option-Pricing-and-Risk-Models/blob/main/notebooks/01_black_scholes_monte_carlo.ipynb)|
|2| **Black-Scholes Option Pricing with Comprehensive Greeks Analysis** | Calculates and visualizes Delta, Gamma, Theta, Vega, and Rho. | [Documentation](https://github.com/xxxxyyyy80008/Option-Pricing-and-Risk-Models/blob/main/docs/02_black_scholes_greeks_analysis.md) , [Kaggle Notebook](https://www.kaggle.com/code/xxxxyyyy80008/black-scholes-option-pricing-with-greeks-analysis) , [Github Notebook](https://github.com/xxxxyyyy80008/Option-Pricing-and-Risk-Models/blob/main/notebooks/02_black_scholes_greeks_analysis.ipynb)|
|3| **Black-Scholes Option Pricing - Implied Volatility Surface Analysis** | Builds and analyzes IV surfaces using interpolation. |[Documentation](https://github.com/xxxxyyyy80008/Option-Pricing-and-Risk-Models/blob/main/docs/03_black_scholes_implied_vol_surface.md) , [Kaggle Notebook](https://www.kaggle.com/code/xxxxyyyy80008/option-pricing-implied-volatility-surface/) , [Github Notebook](https://github.com/xxxxyyyy80008/Option-Pricing-and-Risk-Models/blob/main/notebooks/03_black_scholes_implied_vol_surface.ipynb)|
|4|  **Option Pricing Binomial Tree** | American and European option pricing via Cox-Ross-Rubinstein binomial model.|[Documentation](https://github.com/xxxxyyyy80008/Option-Pricing-and-Risk-Models/blob/main/docs/04_option_pricing_binomial_tree.md) , [Github Notebook](https://github.com/xxxxyyyy80008/Option-Pricing-and-Risk-Models/blob/main/notebooks/04_option_pricing_binomial_tree.ipynb), [Kaggle Notebook](https://www.kaggle.com/code/xxxxyyyy80008/option-pricing-binomial-tree)|
|5| **Delta Hedging** | Delta hedging strategies for European options, with detailed profit & loss (P&L) attribution and hedging error analysis |[Documentation](https://github.com/xxxxyyyy80008/Option-Pricing-and-Risk-Models/blob/main/docs/05_delta_hedging.md) , [Kaggle Notebook](https://www.kaggle.com/code/xxxxyyyy80008/option-pricing-delta-hedging) , [Github Notebook](https://github.com/xxxxyyyy80008/Option-Pricing-and-Risk-Models/blob/main/notebooks/05_delta_hedging.ipynb)|


Each notebook combines rigorous mathematical implementation with practical applications, featuring real market data integration and professional-grade visualizations.

---

##  Description

### 1.  Black-Scholes Option Pricing and Monte Carlo Simulation

**File**: `01_black_scholes_monte_carlo.ipynb` 

- **[Documentation](https://github.com/xxxxyyyy80008/Option-Pricing-and-Risk-Models/blob/main/docs/01_black_scholes_monte_carlo.md)**
- **[Kaggle Notebook](https://www.kaggle.com/code/xxxxyyyy80008/black-scholes-option-pricing-and-monte-carlo/)**
- **[Github Notebook](https://github.com/xxxxyyyy80008/Option-Pricing-and-Risk-Models/blob/main/notebooks/01_black_scholes_monte_carlo.ipynb)**

**Purpose**: Implement and validate Black-Scholes-Merton analytical pricing formulas using Monte Carlo simulation methods.

**Key Features**:
-  Analytical Black-Scholes pricing for European call/put options
-  Monte Carlo simulation using Geometric Brownian Motion (GBM)
-  Convergence analysis (100 to 300,000 simulations)
-  Real market data comparison (Boeing stock example)
-  Terminal price distribution validation
-  Sample path visualization (20+ paths)

**Highlights**:
- **Accuracy**: <0.5% error with 100,000 Monte Carlo simulations
- **Convergence**: Demonstrates O(1/√N) theoretical behavior
- **Validation**: Compares theoretical vs market prices from Yahoo Finance


---

### 2.  Black-Scholes Implied Volatility Surface Analysis

**File**: `02_implied_volatility_surface.ipynb`

- **[Documentation](https://github.com/xxxxyyyy80008/Option-Pricing-and-Risk-Models/blob/main/docs/02_black_scholes_greeks_analysis.md)**
- **[Kaggle Notebook](https://www.kaggle.com/code/xxxxyyyy80008/black-scholes-option-pricing-with-greeks-analysis)**
- **[Github Notebook](https://github.com/xxxxyyyy80008/Option-Pricing-and-Risk-Models/blob/main/notebooks/02_black_scholes_greeks_analysis.ipynb)**

**Purpose**: Calculate implied volatilities from market prices and generate 2D/3D volatility surfaces with advanced numerical methods.

**Key Features**:
-  **Three IV calculation methods**: Newton-Raphson, Brent's, Hybrid
-  **Real-time market data**: Yahoo Finance API integration
-  **Volatility surface generation**: 2D scatter plots and 3D interpolated surfaces
-  **Data quality filtering**: Strike range, time-to-expiry, volume, open interest
-  **Accuracy metrics**: MAE, RMSE, MAPE for price and IV errors
-  **Greeks calculation**: Vega for Newton-Raphson convergence

**Technical Capabilities**:

| Feature | Implementation |
|---------|----------------|
| **Pricing Model** | Black-Scholes-Merton with continuous dividend yield |
| **IV Algorithms** | Hybrid Newton-Raphson/Brent's with adaptive bounds |
| **Interpolation** | Cubic/linear griddata with Gaussian smoothing |
| **Success Rate** | Typically >90% IV computation success |
| **Convergence** | Tolerance 1e-8, max 150 iterations |

**Volatility Surface Visualizations**:
- **Computed IV Surface**: From calculated implied volatilities
- **Market IV Surface**: From market-quoted IVs (when available)
- **Difference Surface**: Identifies pricing discrepancies and arbitrage opportunities


---

### 3.  Black-Scholes Option Pricing with Comprehensive Greeks Analysis

**File**: `03_comprehensive_greeks_analysis.ipynb`

- **[Documentation](https://github.com/xxxxyyyy80008/Option-Pricing-and-Risk-Models/blob/main/docs/03_black_scholes_implied_vol_surface.md)**
- **[Kaggle Notebook](https://www.kaggle.com/code/xxxxyyyy80008/option-pricing-implied-volatility-surface/)**
- **[Github Notebook](https://github.com/xxxxyyyy80008/Option-Pricing-and-Risk-Models/blob/main/notebooks/03_black_scholes_implied_vol_surface.ipynb)**

**Purpose**: Calculate, visualize, and analyze all five primary Option Greeks with multi-dimensional sensitivity analysis and portfolio risk management applications.

**Key Features**:
-  **All five Greeks**: Delta, Gamma, Vega, Theta, Rho
-  **Multi-dimensional visualization**: 1D line plots, 2D heatmaps, 3D surfaces
-  **Sensitivity analysis**: Greeks vs spot price, volatility, time to maturity
-  **Monte Carlo validation**: Verify analytical Greeks through simulation
-  **Real market data**: Boeing (BA) options analysis
-  **Portfolio Greeks aggregation**: Multi-position risk management

**Greeks Suite**:

| Greek | Measures | Formula | Practical Use |
|-------|----------|---------|---------------|
| **Delta (Δ)** | Price sensitivity to spot | ∂V/∂S | Hedge ratio, directional exposure |
| **Gamma (Γ)** | Delta's rate of change | ∂²V/∂S² | Convexity risk, hedge rebalancing frequency |
| **Vega (ν)** | Volatility sensitivity | ∂V/∂σ | Volatility trading, implied vol exposure |
| **Theta (Θ)** | Time decay | ∂V/∂t | Daily P&L erosion, calendar strategies |
| **Rho (ρ)** | Interest rate sensitivity | ∂V/∂r | Rate risk, long-dated options |

**Visualization Types**:
1. **5-Panel Line Charts**: Greeks vs spot price (200 points)
2. **4-Panel Heatmaps**: Greeks vs spot & volatility (50×50 grid)
3. **3D Surface Plots**: Greeks vs spot & time (30×30 grid)
4. **Greeks Dashboard**: Tabular analysis across multiple strikes

**Portfolio Risk Management**:
```python
Example Portfolio:
├── +10 CALL K=$200, T=182 days
├──  -5 CALL K=$220, T=182 days
└──  +5 PUT  K=$180, T=182 days

Aggregate Greeks:
├── Delta:  +4.23  (net long)
├── Gamma:  +0.012 (positive convexity)
├── Vega:   +2.35  (long volatility)
├── Theta:  -0.46  (time decay cost)
└── Rho:    +1.23  (benefits from rate increases)
```


## Prerequisites
- Python 3.8+
- Jupyter Lab or Notebook
- Libraries: See `requirements.txt`

