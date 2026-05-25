# Paper Blueprint — Practical Perspective Extension

**Venue:** Information & Management (Elsevier)
**Template:** `elsarticle.cls`
**Status:** Blueprint — pending writing

---

## One-Sentence Contribution

> "We provide the first multi-dimensional practical evaluation of price-aware recommender systems, benchmarking CoHHN, PASBR, and PUP across 11 practitioner-relevant characteristics—spanning accuracy, price sensitivity, catalog diversity, fairness, robustness, and computational efficiency—to guide method selection and configuration in real-world deployments."

---

## Scope: 11 Characteristics in 4 Blocks

```
BLOQUE A: Recommendation Quality (3)
├── #3  Recommendation Accuracy          ✅ datos listos
├── #4  Ranking Quality                  ✅ datos listos
└── #2  Price Sensitivity Adaptation     ✅ datos listos (N=2,10,30,50)

BLOQUE B: Catalog Utilization (5)
├── #5  Catalog Coverage                 ✅ datos listos (RQ4)
├── #6  Recommendation Diversity         ✅ datos listos (RQ4)
├── #8  Long-Tail Promotion              ✅ datos listos (RQ4)
├── #7  Popularity Bias & Fairness       ✅ datos listos (RQ4)
└── #14 Accuracy vs Fairness Trade-off   ✅ derivable de existentes

BLOQUE C: Robustness (2)
├── #13 Stability Across Datasets        ✅ datos listos
└── #1  Data Sparsity Robustness         ⚠️ experimento acotado pendiente

BLOQUE D: Efficiency (1)
└── #9  Computational Efficiency         ⚠️ medición pendiente (bajo esfuerzo)
```

---

## Paper Structure

### 1. INTRODUCTION (~1.5 páginas)

**Hook:** Price is a critical factor in e-commerce purchase decisions, yet most recommender systems treat it as secondary — or ignore it entirely.

**Flujo narrativo:**

| Párrafo | Contenido |
|---------|-----------|
| P1 | El problema: price-aware RS existen pero sin guía práctica para elegir |
| P2 | Lo que hicimos: evaluación 3×6×11 dimensiones |
| P3 | Hallazgos principales (CoHHN domina 9/11, PASBR polarizado, price level crítica) |
| P4 | Contributions (4 bullets) |
| P5 | Roadmap |

**Contributions:**
1. Primer framework multidimensional práctico para price-aware RS
2. Benchmark unificado 3 métodos × 6 datasets × 11 dimensiones
3. Guía de selección basada en características prácticas (decision matrix)
4. Evidencia de que la discretización de precio es un hiperparámetro crítico subestimado

---

### 2. BACKGROUND AND RELATED WORK (~2 páginas)

#### 2.1 Price-Aware Recommender Systems (~1 pág)
- Panorama: de price elasticity a arquitecturas neuronales [umberto:2015, jannach:2017, chen:2021]
- **CoHHN**: Heterogeneous hypergraph + co-guided learning [zhang:2022]
- **PASBR**: GNN session-based + 6 capas [feng:2023]
- **PUP**: GCN collaborative filtering + two-branch [zheng:2020]
- Gap: nunca comparados bajo condiciones controladas

#### 2.2 Practical Evaluation in Recommender Systems (~1 pág)
- Beyond-accuracy: diversity [zhou:2010], fairness [ekstrand:2022], exposure [boratto:2022]
- Gap statement: ningún framework multidimensional práctico para price-aware RS

---

### 3. A MULTI-DIMENSIONAL PRACTICAL EVALUATION FRAMEWORK (~4 páginas)

#### 3.1 Methods Under Evaluation (~0.5 pág)
- Tabla: Método × Paradigma × Price mechanism × Original datasets × Code

#### 3.2 Datasets and Experimental Setup (~1 pág)
- Tabla de datasets (6 datasets con estadísticas)
- Protocolo unificado de preprocessing
- Price discretization: N=2,10,30,50
- Hardware/software

#### 3.3 The 11-Dimension Evaluation Framework (~1.5 pág)
**Tabla central (T1):**

| Dimension | Practical Question | Metrics | Block |
|-----------|-------------------|---------|-------|
| Accuracy | How well does it predict? | HR@20, NDCG@20, MRR@20 | Quality |
| Ranking Quality | How well are relevant items ranked? | NDCG@20, MRR@20 | Quality |
| Price Sensitivity | Does price discretization affect performance? | HR/NDCG/MRR across price levels, CV | Quality |
| Catalog Coverage | What fraction of the catalog is ever recommended? | Item Coverage, User Coverage | Catalog |
| Diversity | How varied are the recommendations? | Gini Index, Shannon Entropy | Catalog |
| Long-Tail Promotion | Are niche items surfaced? | LT Coverage, LT Rec Ratio | Catalog |
| Popularity Bias | Is exposure concentrated on popular items? | Gini, EPC | Fairness |
| Accuracy-Fairness Trade-off | Can we have both? | HR vs Gini, NDCG vs Coverage | Fairness |
| Cross-Dataset Stability | Does performance generalize? | σ of HR/NDCG/MRR across datasets | Robustness |
| Sparsity Robustness | Does it work with little data? | HR@20 at varying sparsity levels | Robustness |
| Computational Cost | What are the resource requirements? | Training time, inference time | Efficiency |

#### 3.4 Metrics and Measurement Protocol (~0.5 pág)
- K=20 estándar
- Beyond-accuracy a K=20, N=2 price levels
- Price sensitivity: CV a través de N=2,10,30,50
- Mean, stdev, CV reportados

---

### 4. RESULTS: A PRACTITIONER'S GUIDE (~8-10 páginas)

#### 4.1 Recommendation Quality (~2.5 pág)
- **T2:** HR@20, NDCG@20, MRR@20 globales (3×6)
- **T3:** Price sensitivity: CV por método × dataset
- **F1:** Line plot HR@20 vs price level (Amazon + Yelp)
- Claims: CoHHN domina accuracy; inmune al price level; PASBR se degrada en Yelp

#### 4.2 Catalog Utilization (~2.5 pág)
- **T4:** Coverage, Gini, SE, LT Coverage, LT Rec Ratio
- **F2:** Grouped bar: Coverage + Gini + LT Coverage
- Claims: CoHHN mejor coverage/diversidad; PASBR colapso en Yelp; PUP narrow catalog

#### 4.3 Fairness and Exposure (~1.5 pág)
- **T5:** Gini + EPC + LT Rec Ratio
- **F3:** Scatter HR vs Gini (CoHHN en esquina superior-izquierda)
- Claims: CoHHN rompe accuracy-diversity trade-off; PASBR economic filter bubble

#### 4.4 Robustness and Efficiency (~1.5 pág)
- **T6:** Cross-dataset CV + computation times
- Claims: PASBR menos generalizable; CoHHN más consistente

#### 4.5 Synthesis: A Decision Framework (~2 pág)
- **T7: Decision Matrix** — 11 filas × 3 métodos con ✅/⚠️/❌
- **F4:** Radar chart 3 métodos superpuestos
- Decision tree textual para 4-5 escenarios prácticos
- **T8:** Configuration guidelines (price levels recomendados)

---

### 5. DISCUSSION (~3 páginas)

#### 5.1 Architectural Signatures (~1 pág)
| Método | Paradigma | Firma práctica |
|--------|-----------|---------------|
| CoHHN | Heterogeneous hypergraph | The generalist: 9/11 dimensiones, inmune al price level |
| PASBR | GNN session-based | The specialist: excelente en Yoochoose, peligroso fuera |
| PUP | GCN collaborative filtering | The narrow cataloger: accuracy limitada, LT ratio competitivo |

#### 5.2 Practical Configuration Guidelines (~1 pág)
- Price discretization: CoHHN no necesita tuning; N=10-30 sweet spot general
- Domain considerations
- Deployment budget

#### 5.3 Limitations and Future Work (~1 pág)
- Sin descomposición por price range
- Sin métricas de negocio (revenue)
- Sin cold-start / scalability / real-time
- 3 métodos — no exhaustivo
- Solo e-commerce

---

### 6. CONCLUSION (~0.5 pág)
- Re-statement de contribución
- 3 hallazgos clave
- Implicación práctica principal
- Llamado a evaluación multidimensional como estándar

---

## Tables and Figures Inventory

| # | Type | Section | Content |
|---|------|---------|---------|
| T1 | Table | §3.3 | 11 dimensions: characteristic → question → metrics |
| T2 | Table | §4.1 | HR/NDCG/MRR global (3 methods × 6 datasets) |
| T3 | Table | §4.1 | Price sensitivity: CV by method × dataset |
| T4 | Table | §4.2 | Beyond-accuracy (Coverage, Gini, SE, LT Cov, LT Rec) |
| T5 | Table | §4.4 | Cross-dataset stability + computation |
| T6 | Table | §4.5 | Decision Matrix: 11 dimensions × 3 methods |
| F1 | Figure | §4.1 | HR@20 vs. price level (line plot, 2 datasets) |
| F2 | Figure | §4.2 | Coverage + Gini + LT Coverage (grouped bar) |
| F3 | Figure | §4.3 | HR vs Gini scatter plot |
| F4 | Figure | §4.5 | Radar chart: 3 methods on normalized dimensions |

---

## Data Inventory

| Data                                             | Location                                                                           | Status         |
| ------------------------------------------------ | ---------------------------------------------------------------------------------- | -------------- |
| Accuracy metrics by price level                  | `notes/accuracy-metrics/`                                                          | ✅ Ready        |
| Beyond-accuracy by price level (Gini, Diversity) | `notes/already-worked-docs/resultados-beyond-acuracy.md`                           | ✅ Ready        |
| RQ4 beyond-accuracy aggregate                    | `notes/already-worked-docs/first-draft-beyond.md`                                  | ✅ Ready        |
| Original SIGIR draft (accuracy RQ2-RQ3)          | `notes/MAIN_pars_reproducibility_SIGIR_2026_cm-2/`                                 | ✅ Ready        |
| Rejected extension draft (I&M)                   | `notes/Information___Management__SIGIR_2026_extension_price_aware_recommendation/` | Reference only |
| Sparsity subsets                                 | Not yet generated                                                                  | ⚠️ Pending     |
| Training/inference time measurements             | Not yet recorded                                                                   | ⚠️ Pending     |
