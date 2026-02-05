# Multi-Stock Return Forecasting

Per-ticker **Ridge** models to forecast next-period returns; **Bayesian-optimized alphas** to optimize regularization coefficent 

## Project Layout
```
multi-stock-trading/
├── training.ipynb      # End-to-end workflow: data → features → ridge → BO weights → eval
├── saved_models/       
└── README.md
```

## Core Idea (at a glance)
- **Universe**: AAPL, NVDA, TSLA, MSFT  
- **Target**: next-period return per ticker  
- **Features**: price-derived (rolling stats/momentum/etc.) defined in the notebook  
- **Models**: independent Ridge per ticker → predicted returns  
- **Optimize**: Bayesian Optimization learns alpha
- **Outputs**: Graphs for prediction on validation data; Models saved in saved_models

## Pipeline (conceptual)
```
Prices ─► Features ─► Ridge + bayes_opt (per ticker) ─► Predicted Prices

```
## Notes
- Results show very small improvements and R² near 0, meaning the features carry weak predictive signal for next‑day returns.
- the pipeline works correctly, but the signal‑to‑noise is low, so better features or models are needed for meaningful performance.
