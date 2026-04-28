# Probabilistic Inventory Optimization for Perishable Food Items

This project models an inventory control problem for perishable food items under uncertain demand, stochastic lead times, stockouts, and waste. The goal is to compare simple ordering rules against optimized policies using simulation, grid search, and a Markov Decision Process (MDP).

The project was developed as an academic Operations Research project and is presented here as a public portfolio repository focused on supply chain analytics, inventory optimization, and decision science.

---

## Project Motivation

Perishable food inventory creates a difficult tradeoff:

- Ordering too little causes stockouts and unmet demand.
- Ordering too much causes waste.
- Demand is uncertain and right-skewed.
- Lead times may vary.
- Simple rules based only on average demand can perform poorly.

This project studies that tradeoff using sandwich demand data and compares several inventory policies:

1. Mean-demand ordering policy
2. Newsvendor-style policy
3. Optimized static order-up-to policy
4. Dynamic MDP policy

---

## Key Result

The project shows that simple policies perform poorly under uncertain and skewed demand, while optimized policies substantially improve service levels and reduce expected daily cost.

| Policy | Cost/day | Fill Rate | Waste/day | Unmet/day |
|---|---:|---:|---:|---:|
| Mean Policy, S = 9 | $13.75 | 40.2% | 0.01 | 5.49 |
| Newsvendor Policy, S = 10 | $12.86 | 44.2% | 0.02 | 5.13 |
| Optimized Static Policy, S* = 33 | $3.07 | 94.1% | 1.14 | 0.55 |
| MDP Policy | $2.68 | 94.4% | 0.92 | 0.52 |

The MDP policy achieved the lowest simulated daily cost while maintaining a high fill rate and reducing waste compared with the optimized static policy.

---

## Methods Used

- Demand modeling
- Empirical probability mass function estimation
- Monte Carlo simulation
- Baseline inventory policy comparison
- Grid search over order-up-to levels
- Markov Decision Process formulation
- Value iteration
- Sensitivity analysis
- Visualization of policy behavior and performance

---

## Repository Structure

```text
inventory-optimization-mdp/
│
├── data/
│   ├── processed/
│   │   ├── sandwich_daily_demand.csv
│   │   ├── sandwich_daily_demand_cleaned.csv
│   │   ├── sandwich_daily_by_weekday.csv
│   │   └── sandwich_P_of_D.csv
│   │
│   └── raw/
│       └── README.md
│
├── docs/
│   └── OR7230_Report.pdf
│
├── notebooks/
│   ├── 01_data_cleaning.ipynb
│   ├── 02_demand_distribution.ipynb
│   ├── 03_demand_validation.ipynb
│   ├── 04_baseline_simulation.ipynb
│   ├── 05_policy_optimization.ipynb
│   ├── 06_mdp.ipynb
│   └── 06b_sensitivity.ipynb
│
├── outputs/
│   ├── figures/
│   └── tables/
│
├── .gitignore
├── README.md
└── requirements.txt
