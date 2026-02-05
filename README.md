# Energy Market Forecasting

This repository demonstrates an end-to-end pipeline for **day-ahead electricity price forecasting** using modern time series methods.

## Overview

The project is built around the [Darts](https://unit8co.github.io/darts/) library and compares several forecasting approaches:

- Naïve baseline (simple historical benchmark)
- **XGBoost point model**
- **XGBoost quantile (probabilistic) model – final chosen model**
- LSTM point model
- LSTM quantile (probabilistic) model

Hyperparameters are tuned with **Optuna**, and both **point** and **probabilistic** performance are evaluated (MAE/RMSE and interval coverage).

On the test set, the probabilistic XGBoost model reduces MAE from **3.62 → 2.61** and RMSE from **4.89 → 3.45**, corresponding to roughly **28% (MAE)** and **30% (RMSE)** improvement over the naïve baseline, while providing well-calibrated prediction intervals.

## Project structure

- `hourly_energy_demand_forecasting.ipynb` – main notebook containing data processing, model training, evaluation, and plots.
- `pyproject.toml` / `uv.lock` – dependencies and environment configuration.
- `models/` – local directory for trained models (ignored in Git).
- `optuna_*.db` – local Optuna study databases (ignored in Git).

## Usage

1. Clone the repository:
   ```bash
   git clone https://github.com/Jackson00Han/energy_market_forecasting.git
   cd Energy_Market_Forecasting

2. Create and activate a Python environment by 
    ```bash
    uv sync

    source .venv/bin/activate
    ```
3. Open the main notebook and run hourly_energy_demand_forecasting.ipynb to reproduce the experiments.

Note: This repository is a work in progress. A more detailed guide (data description, feature engineering, and model configuration) will be added soon.
