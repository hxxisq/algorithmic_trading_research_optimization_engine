# Algorithmic Trading Research & Optimization Engine

A systematic analysis of five iterative trading engine versions, benchmarking performance improvements from a baseline model through increasingly selective risk and entry filters. The goal: find the optimal balance between trade quality and frequency.

---

## Experiment Versions

| Version | Label | Key Change |
|---------|-------|------------|
| v1 | Baseline | Control — no constraints applied |
| v2 | Risk Management | Stop loss bounds + max RR + exit RR logic |
| v3 | Time Filter | Entry restricted to specified hour windows |
| v4 | High Selectivity ★ | Min RR = 4 + improved data quality |
| v5 | Extreme Selectivity | Min RR = 6 |

### v1 — Baseline
Initial model used as the control. No additional constraints or filters applied. Serves as the reference point for all comparisons.

### v2 — Risk & Trade Management Enhancements
Builds on v1 with structured risk controls:
- Minimum and maximum stop loss (SL) bounds
- Maximum risk-to-reward (RR) constraint
- Exit RR logic

Objective: improve trade quality and consistency through tighter risk controls.

### v3 — Time-Based Entry Filter
Builds on v2 with a time-of-day filter:
- Entry restricted to specified hour windows

Objective: filter out trades during low-quality time periods.

### v4 — High Selectivity + Improved Data Quality ⭐
- Minimum RR = 4 (only trades with at least 4:1 reward-to-risk)
- Deeper preprocessing and cleaning on the news dataset

This version achieves the best balance of expectancy, drawdown control, and win rate. **Identified as the optimal engine.**

### v5 — Extreme Selectivity
- Minimum RR = 6

Pushes selectivity further, but over-filters — win rate regresses despite the higher RR threshold.

---

## Analysis Notebook

`Algorithmic_Trading_Research_&_Optimization_Engine.ipynb` runs a full comparative study across all five versions, including:

- **Executive Summary** — side-by-side metrics table (win rate, total PnL, expectancy, W/L ratio, max drawdown, consecutive loss streaks, organic PnL %)
- **Equity Curves** — cumulative PnL overlay with drawdown panel, across all versions from 2018–2026
- **Annual Performance Breakdown** — year-by-year PnL bars and win rate lines per version
- **Monte Carlo Simulation** — 10,000 simulations projecting median equity paths, 5th/95th percentile bands, final PnL distributions, and max drawdown distributions
- **Optimisation Radar** — spider chart normalising six key metrics across all versions
- **Optimisation Curve** — expectancy and drawdown trajectories from v1 to v5, with v4 marked as the sweet spot

---

## Key Findings

- **v4 is the optimal engine** — expected value per trade improved 235% (+27.5 → +92.0 pts) with a 75% reduction in max drawdown (-1,540 → -383 pts)
- v5 over-filters: adding more selectivity beyond min RR = 4 causes win rate regression without a commensurate gain
- The progression from v1 to v4 delivers meaningful improvements in expectancy, drawdown, and win rate while reducing total trade count

---

## Requirements

```
pandas
numpy
matplotlib
seaborn
```

Install with:

```bash
pip install pandas numpy matplotlib seaborn
```

---
