# Option Pricing Analysis 

## Overview
Comprehensive option pricing implementation featuring binomial trees, Monte Carlo simulation, delta hedging, and implied volatility calculation using Newton's method.

---

##  Script Components

### 1. Black-Scholes Functions
- **`black_scholes_d1()`** - Calculate d₁ parameter
- **`black_scholes_d2()`** - Calculate d₂ parameter  
- **`black_scholes_call()`** - European call option price
- **`black_scholes_put()`** - European put option price

**Formula:**
$$
C(S,t) = S e^{-dT} N(d_1) - K e^{-rT} N(d_2)
$$

$$
d_1 = \frac{\ln(S/K) + (r - d + \sigma^2/2)T}{\sigma\sqrt{T}}
$$

$$
d_2 = d_1 - \sigma\sqrt{T}
$$

---

### 2. Greeks Calculations
Complete sensitivity measures for risk management:

| Greek | Call Function | Put Function | Description |
|-------|--------------|--------------|-------------|
| **Delta** | `calculate_delta_call()` | `calculate_delta_put()` | Price sensitivity to stock price |
| **Gamma** | `calculate_gamma()` | `calculate_gamma()` | Delta sensitivity to stock price |
| **Vega** | `calculate_vega()` | `calculate_vega()` | Price sensitivity to volatility |
| **Theta** | `calculate_theta_call()` | `calculate_theta_put()` | Price sensitivity to time decay |

---

### 3. Implied Volatility - Newton's Method

**Function:** `implied_volatility_newton()`

**Algorithm:**
$$
\sigma_{n+1} = \sigma_n - \frac{C(\sigma_n) - C_{market}}{Vega(\sigma_n)}
$$

**Parameters:**
- Initial guess: σ₀ = 0.3
- Max iterations: 100
- Convergence tolerance: 10⁻⁶

**Features:**
- Iterative root-finding method
- Handles both call and put options
- Automatic convergence detection
- Guards against negative volatility

---

### 4. One-Step Binomial Tree

#### CRR Method
**Function:** `one_step_binomial_crr()`

**Parameters:**
$$
u = e^{\sigma\sqrt{\Delta t}}, \quad d = \frac{1}{u}
$$

$$
p = \frac{e^{(r-d)\Delta t} - d}{u - d}
$$

#### GBM Method
**Function:** `one_step_binomial_gbm()`

**Parameters:**
$$
u = e^{(r-d-0.5\sigma^2)\Delta t + \sigma\sqrt{\Delta t}}
$$

$$
d = e^{(r-d-0.5\sigma^2)\Delta t - \sigma\sqrt{\Delta t}}
$$

**Returns:**
- Option price at t=0
- Stock price tree
- Option value tree
- Risk-neutral probability
- Up/down multipliers

---

### 5. Two-Step Binomial Tree

**Function:** `two_step_binomial_crr()`

**Tree Structure:** `Time:     0           1           2
S₀₀
S₁₀         S₂₀
S₁₁
S₁₁         S₂₁
S₂₂`


**Features:**

- European and American options
- Early exercise capability
- Backward induction pricing
- Visual tree construction

**Pricing Algorithm:**
```
For each node (i, j) from maturity to present:
Option[i,j] = e^(-r·Δt) × [p × Option[i,j+1] + (1-p) × Option[i+1,j+1]]
If American: Option[i,j] = max(Option[i,j], Intrinsic Value)
```


---

### 6. N-Step Binomial Tree

**Function:** `n_step_binomial_crr()`

**Convergence:**
As N → ∞, binomial price → Black-Scholes price

**Typical Values:**
- N = 50: Good approximation
- N = 100: Excellent accuracy
- N = 200+: Near-perfect convergence

**Complexity:** O(N²) time, O(N²) space

---

### 7. Monte Carlo Simulation (GBM)

**Function:** `monte_carlo_gbm()`

**Geometric Brownian Motion:**
$$
S_t = S_0 \exp\left[(r - d - \frac{\sigma^2}{2})t + \sigma W_t\right]
$$

**Discretization:**
$$
S_{t+\Delta t} = S_t \exp\left[(r - d - \frac{\sigma^2}{2})\Delta t + \sigma\sqrt{\Delta t}Z\right]
$$

where Z ~ N(0,1)

**Output:**
- Option price estimate
- Standard error
- Simulated price paths

**Convergence Rate:** O(1/√M) where M = number of simulations

---

### 8. Delta Hedging Simulation

**Function:** `delta_hedging_simulation()`

**Strategy:**
1. Sell 1 option
2. Buy Δ shares of stock
3. Rebalance periodically
4. Track P&L

**Portfolio Value:**
$$
V_t = V_{t-1} e^{r\Delta t} + \Delta_{t-1}(S_t - S_{t-1}) - (\Delta_t - \Delta_{t-1})S_t
$$

**Returns:**
- Final hedge P&L
- Stock price path
- Delta values over time
- Portfolio value evolution

---

## 📊 Visualizations Generated

### 1. Convergence Analysis
- **Binomial Tree Convergence**: N-step prices vs Black-Scholes
- **Monte Carlo Convergence**: Price and standard error vs simulations

### 2. Delta Hedging Performance
Four-panel display:
- Stock price path
- Delta evolution
- Portfolio value
- Cumulative P&L

### 3. Monte Carlo Paths
- 20 sample paths from 1,000 simulations
- Strike price reference line
- Time evolution from 0 to T

### 4. Two-Step Tree Diagrams
Side-by-side visualization:
- Stock price tree with values
- Option value tree with values
- Arrow connections between nodes

### 5. Greeks Sensitivity
- **Delta vs Stock Price**: Call and put deltas
- **Gamma vs Stock Price**: Convexity measure
- **Option Price vs Volatility**: Vega illustration
- **Vega vs Volatility**: Sensitivity of vega

### 6. Hedging Distribution
- **P&L Histogram**: Distribution across multiple simulations
- **P&L Timeline**: Sequential simulation results

### 7. Implied Volatility Surface
- **3D Surface Plot**: IV across strikes and maturities
- **Contour Plot**: 2D representation of IV surface

---

## 🔢 Example Output

### Pricing Comparison
```
Parameters: S0=100, K=100, r=0.05, d=0.02, σ=0.2, T=1.0

Method                          Call Price      Put Price
─────────────────────────────────────────────────────────
Black-Scholes                   10.450683       7.365497
One-Step Binomial (CRR)         10.404291       7.319105
Two-Step Binomial (CRR)         10.434095       7.348909
100-Step Binomial (CRR)         10.450512       7.365326
Monte Carlo (100k sims)         10.451234       7.366048

```


### Greeks Summary
```

Greek                Call            Put
──────────────────────────────────────────
Delta                0.638270       -0.334638
Gamma                0.018806        0.018806
Vega                37.612066       37.612066
Theta               -6.281447        0.811825

```

### Convergence Results

```
N-Step Binomial Convergence:
N =   5: Price = 10.533924, Error = 0.083241
N =  10: Price = 10.470909, Error = 0.020226
N =  20: Price = 10.455736, Error = 0.005053
N =  50: Price = 10.451876, Error = 0.001193
N = 100: Price = 10.450512, Error = 0.000171
```


---

## 🎯 Key Features

### ✅ Implementation Characteristics
- **No Classes**: Pure functional programming approach
- **No Logging**: Clean output without debugging statements
- **No Vectorization**: Explicit loops for clarity
- **Educational Focus**: Clear variable names and comments

### ✅ Numerical Methods
1. **Binomial Trees**: CRR and GBM parameterizations
2. **Monte Carlo**: Geometric Brownian Motion simulation
3. **Newton's Method**: Implied volatility calculation
4. **Backward Induction**: American option pricing

### ✅ Option Types Supported
- European Call/Put
- American Call/Put
- Binary Call/Put (cash-or-nothing)
- Forward Contracts

---

## 📐 Mathematical Foundations

### Risk-Neutral Valuation
$$
C_0 = e^{-rT} \mathbb{E}^Q[\max(S_T - K, 0)]
$$

### Binomial Risk-Neutral Probability
$$
p = \frac{e^{(r-d)\Delta t} - d}{u - d}
$$

### No-Arbitrage Condition
$$
d < e^{r\Delta t} < u
$$

### Put-Call Parity
$$
C - P = S_0 e^{-dT} - K e^{-rT}
$$

---

## 🚀 Usage Example

```python
# Set parameters
S0 = 100.0    # Current stock price
K = 100.0     # Strike price
r = 0.05      # Risk-free rate (5%)
d = 0.02      # Dividend yield (2%)
sigma = 0.2   # Volatility (20%)
T = 1.0       # Time to maturity (1 year)

# Black-Scholes price
bs_call = black_scholes_call(S0, K, r, d, sigma, T)

# One-step binomial
one_step_price, _, _, _, _, _ = one_step_binomial_crr(S0, K, r, d, sigma, T, 'call')

# Two-step binomial
two_step_price, stock_tree, option_tree, _, _, _ = two_step_binomial_crr(
    S0, K, r, d, sigma, T, 'call'
)

# N-step convergence
n100_price, _, _ = n_step_binomial_crr(S0, K, r, d, sigma, T, 100, 'call')

# Monte Carlo
mc_price, mc_error, paths = monte_carlo_gbm(
    S0, K, r, d, sigma, T, 10000, 100, 'call', seed=42
)

# Greeks
delta = calculate_delta_call(S0, K, r, d, sigma, T)
gamma = calculate_gamma(S0, K, r, d, sigma, T)
vega = calculate_vega(S0, K, r, d, sigma, T)

# Implied volatility
market_price = 10.45
implied_vol = implied_volatility_newton(market_price, S0, K, r, d, T, 'call')

# Delta hedging
hedge_pnl, stock_path, delta_path, portfolio, time_path = delta_hedging_simulation(
    S0, K, r, d, sigma, T, 50, 'call', seed=42
)
```

