
## Contribution
> This work provides the first evaluation of price-aware recommender systems, benchmarking CoHHN, PASBR, PUP across 5 practical perspectives: Recommendation Quality, Catalog Related, Fairness, Robustness, Efficiency.


## Scope
```
Perspective N°1: Recommendation Quality (3)
├── #3  Recommendation Accuracy          ✅ datos listos (SIGIR)
├── #4  Ranking Quality                  ✅ datos listos (SIGIR)
└── #2  Price Sensitivity Adaptation     ✅ datos listos (N=2,10,30,50)

Perspective N°2: Catalog Related (5)
├── #5  Catalog Coverage                 ✅ datos listos (RQ4)
├── #6  Recommendation Diversity         ✅ datos listos (RQ4)
├── #8  Long-Tail Promotion              ✅ datos listos (RQ4)

Perspective N°3
├── #7  Popularity Bias & Fairness       ✅ datos listos (RQ4)
└── #14 Accuracy vs Fairness Trade-off   ✅ derivable de existentes

Perspective N°4: Robustness (2)
├── #13 Stability Across Datasets        ✅ datos listos
└── #1  Data Sparsity Robustness         - pendiente

Perspective N°5: Efficiency (1)
└── #9  Computational Efficiency         - pendiente
```

## Metrics Scope
| Scope                       | Metrics                          | Perspective |
| --------------------------- | -------------------------------- | ----------- |
| Accuracy                    | HR@20, NDCG@20, MRR@20           | Rec Quality |
| Ranking Quality             | NDCG@20, MRR@20                  | Rec Quality |
| Price Sensitivity           | HR/NDCG/MRR across price levels  | Rec Quality |
| Catalog Coverage            | Item Coverage                    | Catalog Rel |
| Diversity                   | Gini Index, Shannon Entropy      | Catalog Rel |
| Long-Tail Promotion         | LT Coverage, LT Rec Ratio        | Catalog Rel |
| Popularity Bias             | Gini, EPC                        | Fairness    |
| Accuracy-Fairness Trade-off | HR vs Gini, NDCG vs Coverage     | Fairness    |
| Cross-Dataset Stability     | σ of HR/NDCG/MRR across datasets | Robustness  |
| Sparsity Robustness         | HR@20 at sparsity levels         | Robustness  |
| Computational Cost          | Training time, Test time         | Efficiency  |
