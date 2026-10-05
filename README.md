# Bayesian inference for dengue transmission, from scratch

Two notebooks that fit compartmental dengue models to monthly case counts, with every inference step written from
scratch in NumPy and SciPy (no probabilistic-programming library).

| Notebook | Model | Inference |
|---|---|---|
| `dengue_seasonal_mcmc.ipynb` | Mosquito–human (SIR–SI) transmission model with a seasonal transmission rate built from Fourier components of the case series | Bayesian: priors, negative-binomial likelihood, adaptive random-walk Metropolis MCMC with two chains, burn-in, R̂ convergence diagnostics, posterior summaries (including R₀), posterior predictive check |
| `sir_time_varying_r0_mle.ipynb` | SIR model with a time-varying reproduction number (piecewise change during an intervention) | Maximum likelihood with a negative-binomial likelihood, on a synthetic outbreak |

## Data

The models were developed on monthly reported dengue cases for Goa, India. That data is not public and is **not
included**. Both notebooks run on **synthetic data** instead:

- `dengue_seasonal_mcmc.ipynb` generates 12 years of monthly counts with a monsoon-season peak, year-to-year variation
  and negative-binomial noise (Step 2).
- `sir_time_varying_r0_mle.ipynb` uses a synthetic outbreak curve.

To run the seasonal model on your own data, set `DATA_PATH` in Step 1 of `dengue_seasonal_mcmc.ipynb` to an Excel or
CSV file with one row per month and a column named `infections`.

## Running

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
jupyter notebook dengue_seasonal_mcmc.ipynb
```
