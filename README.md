# Multi-Stock Return Forecasting

Per-ticker **Ridge** models to forecast next-period returns; **Bayesian-optimized alphas** to combine signals into a portfolio.

## Project Layout
```
multi-stock-trading/
├── training.ipynb      # End-to-end workflow: data → features → ridge → BO weights → eval
├── saved_models/       # Artifacts from runs (models, weights, metadata)
└── README.md
```

## Core Idea (at a glance)
- **Universe**: AAPL, NVDA, TSLA, MSFT  
- **Target**: next-period return per ticker  
- **Features**: price-derived (rolling stats/momentum/etc.) defined in the notebook  
- **Models**: independent Ridge per ticker → predicted returns  
- **Allocation**: Bayesian Optimization learns per-asset alphas (e.g., Sharpe-max)  
- **Outputs**: metrics/plots + serialized artifacts in `saved_models/`

## Pipeline (conceptual)
```
Prices ─► Features ─► Ridge (per ticker) ─► Predicted returns
                                       │
                                       └─► BO (alphas) ─► Portfolio returns ─► Metrics + Artifacts
```

## Artifacts
- **Models**: fitted Ridge objects/coefficients per ticker  
- **Weights**: BO best alphas + search logs  
- **Run meta**: configs/seeds (if recorded), figures, tables

## Notes
- Minimal by design: one notebook = single source of truth.
- Extend tickers/features/objectives inside the notebook when needed.
