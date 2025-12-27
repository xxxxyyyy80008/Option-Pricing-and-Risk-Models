# Option Pricing and Risk Models
A collection of Jupyter notebooks implementing Black-Scholes, binomial trees, Monte Carlo simulations, and risk models for option pricing. Includes Greeks analysis and implied volatility surfaces.


## Notebooks Overview
1. **Black-Scholes Option Pricing and Monte Carlo** - Implements the classic Black-Scholes formula and Monte Carlo simulations for European options.
2. **Black-Scholes Option Pricing with Comprehensive Greeks Analysis** - Calculates and visualizes Delta, Gamma, Theta, Vega, and Rho.
3. **Black-Scholes Option Pricing - Implied Volatility Surface Analysis** - Builds and analyzes IV surfaces using interpolation.
4. **Option Pricing Binomial Tree** - American and European option pricing via Cox-Ross-Rubinstein binomial model.
5. **Option Pricing and Risk Models** - Integrates VaR, CVaR, and scenario analysis.

## Prerequisites
- Python 3.8+
- Jupyter Lab or Notebook
- Libraries: See `requirements.txt`

## Setup Instructions
1. Clone the repo: `git clone https://github.com/yourusername/option-pricing-notebooks.git`
2. Install dependencies: `pip install -r requirements.txt`
3. Launch Jupyter: `jupyter lab`
4. Open the notebooks folder and run them in order.

## Usage Notes
- Notebooks use synthetic data; replace with real market data for production.
- Outputs (plots, tables) are generated inline—ensure Matplotlib is configured for notebooks.
- For reproducibility, set random seeds in Monte Carlo sections.

## Contributing
Feel free to open issues or PRs for improvements!

## License
MIT License (see LICENSE file).
