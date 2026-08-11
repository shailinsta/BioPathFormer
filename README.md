# BioPathFormer

## Pathway-Aware Graph Learning and Bayesian Uncertainty Modeling for Interpretable Biomarker Discovery and Drug Response Prediction in Pancreatic Ductal Adenocarcinoma

---

## Overview

BioPathFormer is a **pathway-aware computational framework** for pharmacogenomic drug-response prediction and interpretable biomarker discovery in **Pancreatic Ductal Adenocarcinoma (PDAC)**.

The framework integrates biological pathway knowledge from **KEGG** and **Reactome**, multimodal Transformer representation learning, explainable artificial intelligence, Bayesian uncertainty modeling, and leakage-free validation within a unified computational pipeline.

Unlike conventional pharmacogenomic prediction methods that primarily optimize predictive accuracy, BioPathFormer incorporates biological interpretability, uncertainty quantification, and pathway-level reasoning to identify reliable biomarkers and improve prediction robustness for precision oncology.

A defining feature of the framework is the explicit integration of **genome-wide CRISPR dependency profiles** alongside transcriptomic and genomic data, capturing functional vulnerability information that is not recoverable from static molecular state alone.

---

## Paper

**Title**

**Pathway-Aware Graph Learning and Bayesian Uncertainty Modeling for Interpretable Biomarker Discovery and Drug Response Prediction in Pancreatic Ductal Adenocarcinoma**

**Authors**

- **S.M**
- **S.T**
- **A.A**

---

## Abstract

Pancreatic ductal adenocarcinoma (PDAC) exhibits substantial molecular heterogeneity, making robust biomarker discovery and drug-response prediction particularly challenging.

BioPathFormer introduces a biologically informed computational framework that combines multimodal pharmacogenomic profiles — gene expression, somatic mutation and CRISPR dependency — with curated pathway knowledge, Transformer-based representation learning, SHAP explainability, Bayesian uncertainty estimation, and **strict cell-line-disjoint validation** within a unified analytical pipeline.

The proposed framework enhances predictive robustness while improving biological interpretability through pathway-aware feature representations, confidence-aware biomarker prioritization, and biological pathway enrichment analysis. Evaluation is performed on cell lines never observed during training or model selection, providing an estimate of generalisation to unseen biological entities rather than to unseen drug–cell-line combinations. The implementation supports reproducible pharmacogenomic research and precision oncology applications.

---

## Main Contributions

- Disease-specific focus on PDAC rather than pan-cancer aggregation, removing tissue-of-origin as a dominant predictive shortcut.
- Integration of **genome-wide CRISPR dependency scores** as a first-class modality alongside expression and mutation.
- Pathway-aware feature representation using KEGG and Reactome biological pathways.
- Gene–pathway interaction graph construction for modeling higher-order biological relationships.
- Transformer-based multimodal fusion with gated attention pooling.
- **Strict cell-line-disjoint validation** to eliminate information leakage across partitions.
- SHAP-based explainable biomarker discovery.
- Bayesian posterior stability estimation for confidence-aware biomarker ranking.
- Multi-seed component ablation with automated validation gating.
- Functional pathway enrichment using KEGG and Reactome.
- Network hub discovery for biological interpretation.
- End-to-end reproducible computational workflow executable on CPU hardware.

---

## Repository Structure

```
BioPathFormer/
│
├── notebooks/
│   └──PDAC.ipynb
│
├── datasets/
│
├── pathway_data/
│
├── results/
│   ├── figures/
│   ├── tables/
│
├── figures/
│
├── requirements.txt
└── README.md
```

---

# Computational Pipeline

BioPathFormer consists of a biologically informed computational workflow composed of nineteen sequential stages.

| Stage | Description |
|--------|-------------|
| 1 | Pharmacogenomic Data Acquisition (DepMap / CCLE / GDSC1) |
| 2 | Data Harmonization and PDAC Cohort Extraction |
| 3 | Multi-Omics Quality Control and Cleaning |
| 4 | Compound Annotation and SMILES Retrieval |
| 5 | Master Multi-Omics Dataset Construction |
| 6 | Variance Filtering and Mutual-Information Feature Selection |
| 7 | KEGG and Reactome Pathway Node Construction |
| 8 | Gene–Pathway Edge Construction |
| 9 | Biological Prior Matrix Construction |
| 10 | Cell-Line-Disjoint Partitioning and Standardization |
| 11 | Multimodal Tokenization |
| 12 | Transformer Encoding and Gated Attention Pooling |
| 13 | Regression Head Training |
| 14 | Bootstrap Evaluation and Uncertainty Quantification |
| 15 | Multi-Seed Component Ablation |
| 16 | SHAP Explainability |
| 17 | Bayesian Posterior Stability Estimation |
| 18 | KEGG and Reactome Pathway Enrichment |
| 19 | Network Centrality Analysis and Hub Discovery |

---

# Dataset

The datasets required to reproduce the experiments are publicly available through **Hugging Face**.

## Dataset Repository

https://huggingface.co/datasets/ShamsTahzib/PDAC

The repository includes the processed pharmacogenomic datasets used throughout the study, including

- Gene expression profiles
- Mutation profiles
- CRISPR dependency profiles
- Drug response (AUC) measurements
- Drug metadata
- KEGG pathway mappings
- Reactome pathway mappings
- Gene–pathway interaction files
- Graph construction resources

After downloading, place the datasets inside

```
datasets/
```

before executing the notebook.

## Cohort Composition

| Attribute | Value |
|-----------|------:|
| PDAC cell lines | 24 |
| Therapeutic compounds | 401 |
| Drug–cell-line observations | 8,119 |
| Gene-expression features (selected) | 3,000 |
| Somatic-mutation features | 432 |
| CRISPR dependency features (selected) | 2,000 |
| Total feature dimension | 5,432 |
| Training / validation / test observations | 5,495 / 1,332 / 1,292 |
| Training / validation / test cell lines | 16 / 4 / 4 |

The 24-line cohort is the **complete intersection** of four required data layers — expression, mutation, CRISPR dependency and quality-controlled GDSC1 dose–response — within public repositories. Starting from 891 / 1,171 / 705 models with resolvable Sanger identifiers, PDAC annotation reduces these to 28 / 31 / 28; tri-modal intersection yields 26; matching to GDSC1 response records yields 24. No model satisfying all four requirements was excluded.

---

# Experimental Configuration

| Component | Configuration |
|-----------|---------------|
| Programming Language | Python 3.12 |
| Deep Learning Framework | PyTorch |
| Graph Analysis | NetworkX |
| Explainability | SHAP |
| Enrichment Analysis | GSEApy, g:Profiler |
| Optimizer | AdamW |
| Loss Function | SmoothL1Loss |
| Learning Rate | 3 × 10⁻⁴ |
| Weight Decay | 1 × 10⁻⁴ |
| Batch Size | 64 |
| Learning-Rate Schedule | Cosine annealing |
| Early Stopping | Patience 15, min-delta 1 × 10⁻⁴ |
| Random Seeds | 42 (primary); 42, 43, 44 (ablation) |
| Validation Strategy | **Strict cell-line-disjoint hold-out** |
| Bootstrap Resamples | 1,000 |
| Bayesian Posterior Draws | 5,000 |
| Execution Platform | Google Colaboratory |
| Hardware | **CPU only (x86_64), 12.67 GB RAM; CUDA unavailable** |

The complete pipeline — including training, bootstrap analysis, SHAP attribution, Bayesian posterior sampling and twelve ablation runs — executes on commodity CPU hardware without GPU acceleration.

---

# Biological Knowledge Sources

| Database | Version | Pathways | Purpose |
|-----------|---------|---------:|---------|
| KEGG Human | KEGG_2019_Human | 308 | Biological pathway annotation |
| Reactome | Reactome_2022 | 1,816 | Functional pathway annotation |

Knowledge graph statistics: **19,125** gene nodes, **2,124** pathway nodes, **133,247** gene–pathway edges, with **11,550** genes carrying at least one pathway annotation (60.39 % coverage).

---

# Results Summary

## Primary Regression Performance

Independent cell-line-disjoint test set (n = 1,292 observations from 4 unseen cell lines). Mean ± SD and confidence intervals from 1,000 bootstrap resamples.

| Metric | Mean ± SD | 95 % CI |
|---------|----------:|:-------:|
| RMSE | **0.1157 ± 0.0049** | [0.1067, 0.1256] |
| MAE | **0.0766 ± 0.0025** | [0.0720, 0.0816] |
| R² | **0.6222 ± 0.0318** | [0.5552, 0.6800] |
| Pearson Correlation | **0.7904 ± 0.0190** | [0.7514, 0.8256] |
| Spearman Correlation | **0.7777 ± 0.0146** | [0.7490, 0.8059] |

Pearson *p* = 2.48 × 10⁻²⁷⁸; Spearman *p* = 9.14 × 10⁻²⁶⁴.

**Negative control:** permuting response labels across 100 repetitions reduces R² to a mean of −0.0070, confirming that predictive skill derives from genuine molecular–response structure.

## Secondary Threshold-Based Classification

BioPathFormer is a regression model. The following metrics are derived by dichotomising continuous AUC predictions and are reported as a secondary analysis.

| Threshold | Accuracy | Precision | Recall | F1 | ROC-AUC | PR-AUC |
|----------:|---------:|----------:|-------:|---:|--------:|-------:|
| 0.80 | 0.8498 | 0.8809 | 0.9028 | 0.8917 | 0.9255 | 0.9664 |
| 0.85 | 0.8351 | 0.8458 | 0.8920 | 0.8683 | 0.9109 | 0.9436 |
| 0.90 | 0.8398 | 0.8539 | 0.8402 | 0.8470 | 0.9068 | 0.9186 |
| 0.95 | 0.6749 | 0.9592 | 0.1843 | 0.3092 | 0.8850 | 0.8464 |

At the most stringent threshold the model becomes highly conservative — precision 0.959 but recall 0.184 — and should not be thresholded at 0.95 for screening without recalibration.

## Component Ablation

Twelve independent training runs (4 configurations × 3 seeds), reported as mean ± SD.

| Architecture Variant | RMSE ↓ | R² ↑ | ΔRMSE |
|----------------------|-------:|-----:|------:|
| BioPathFormer (full) | **0.1185 ± 0.0017** | **0.6055 ± 0.0113** | Baseline |
| w/o prior biological graph | 0.1186 ± 0.0011 | 0.6044 ± 0.0072 | +0.14 % |
| w/o pathway embeddings | 0.1251 ± 0.0019 | 0.5601 ± 0.0135 | +5.59 % |
| w/o Transformer encoder | 0.4359 ± 0.0237 | −4.3492 ± 0.5880 | +267.88 % |

The Transformer encoder is the decisive component. Pathway embeddings contribute a substantial and consistent improvement. **The prior biological graph produces a change within seed-to-seed variation and is reported as a null result** — it functions as a structural regulariser and interpretability scaffold rather than a predictive accelerator.

## Modality Contribution

| Modality | Features | Aggregated \|SHAP\| | Share |
|----------|---------:|--------------------:|------:|
| Gene expression | 3,000 | 0.060545 | 58.49 % |
| CRISPR dependency | 2,000 | 0.041332 | 39.93 % |
| Somatic mutation | 432 | 0.001641 | 1.59 % |

CRISPR dependency features occupy **fourteen of the top twenty** SHAP positions. On a per-feature basis, dependency scores are the most information-dense modality in the representation.

## Biomarker and Pathway Findings

Leading biomarkers by Bayesian posterior mean: **HEPHL1** (expression), **THRA**, **PTP4A3**, **SP6**, **ERLN** (CRISPR dependency). Genes satisfying both magnitude and stability criteria — HEPHL1, PTP4A3, ANAPC16, FSCN1, LMNA, WNT4 — are the strongest candidates for experimental follow-up.

Network analysis identifies **ANAPC16** as the dominant hub by every centrality measure (degree 41, betweenness 0.627, eigenvector 0.601).

> **Enrichment significance caveat.** Nine of twenty prioritised genes carry curated pathway annotations. Three KEGG pathways reach nominal significance — thyroid hormone signalling (*p* = 0.0034), Hippo signalling (*p* = 0.0063), neuroactive ligand–receptor interaction (*p* = 0.0267) — but **the minimum FDR-adjusted *p*-value across all tested terms is 0.136, and no pathway is significant at the 5 % FDR level.** This is the expected consequence of a nine-gene query set. Enrichment results are reported as hypothesis-generating and should not be cited as independent statistical confirmation.

---

# Generated Outputs

Executing the notebook produces publication-quality outputs, including

- Drug response heatmaps
- Molecular heterogeneity visualizations (UMAP and PCA)
- Multi-omics correlation analysis
- Training and validation learning curves
- Actual versus predicted drug-response plots
- Residual error distributions
- Ablation comparison plots
- Receiver Operating Characteristic (ROC) curves
- Precision–Recall (PR) curves
- SHAP summary and dependence plots
- Bayesian posterior distributions, forest plots and stability rankings
- Biomarker ranking tables
- KEGG pathway enrichment analysis
- Reactome pathway enrichment analysis
- Gene–pathway association networks
- Network hub discovery
- Publication-ready figures and tables

---

# Installation

Clone the repository

```bash
git clone https://github.com/shailinsta/BioPathFormer.git
```

Navigate to the project directory

```bash
cd BioPathFormer
```

Install the required Python packages

```bash
pip install -r requirements.txt
```

Alternatively, create a virtual environment before installing the dependencies.

---

# Running BioPathFormer

Launch Jupyter Notebook

```bash
jupyter notebook
```

Open

```
notebooks/BioPathFormer_PDAC_Pipeline.ipynb
```

Execute all notebook cells sequentially.

The notebook performs the complete computational workflow, including

- Pharmacogenomic data preprocessing
- Pathway-aware feature construction
- Gene–pathway graph construction
- Multimodal Transformer representation learning
- Drug-response prediction
- Cell-line-disjoint evaluation with bootstrap uncertainty quantification
- Multi-seed component ablation
- SHAP explainability
- Bayesian posterior stability estimation
- Biomarker prioritization
- KEGG enrichment analysis
- Reactome enrichment analysis
- Network hub discovery
- Publication-quality figure generation

---

# Reproducing the Experiments

1. Clone this repository.
2. Download the dataset from Hugging Face.
3. Place the downloaded files in the `datasets/` directory.
4. Install all required dependencies using `requirements.txt`.
5. Execute the notebook `BioPathFormer_PDAC_Pipeline.ipynb` from beginning to end.

Determinism is enforced by a global seed function fixing Python, NumPy and PyTorch random state. Feature standardisation parameters are estimated on the training partition alone. No test-set observation, statistic or label influences model fitting, hyper-parameter selection or early stopping at any point in the pipeline.

## Authoritative Result Artefacts

The following files are the authoritative source for the reported results:

- `Statistical_Analysis.csv` — primary regression metrics
- `ablation_repeated_runs.csv`, `ablation_mean_sd.csv` — ablation study
- `classification_metrics.csv` — threshold analysis
- `Posterior_Statistics.csv`, `Posterior_Credible_Intervals.csv` — Bayesian analysis
- `KEGG_Enrichment_ORA.csv`, `Reactome_Enrichment_ORA.csv` — enrichment
- `Network_Centrality.csv`, `Top_Hub_Biomarkers.csv` — network analysis

---

# Known Limitations

- The 24-line cohort, while census-complete for the modality requirements of this study, restricts external validity. Independent replication on patient-derived organoid panels remains necessary.
- Compounds are represented by learned identity embeddings rather than molecular structure, so the model cannot generalise to unseen chemical entities. Structure-aware extension is the primary planned development.
- Pathway enrichment does not survive FDR correction at the nine-gene query size and is reported as hypothesis-generating only.
- Somatic mutation contributes marginally under the present binary encoding; richer variant representations may recover signal the current formulation cannot express.
- The prior biological graph does not measurably improve predictive accuracy (+0.14 %) and is retained for interpretability rather than performance.

---

# Acknowledgements

The authors acknowledge the developers and maintainers of the following open-source projects and biological resources used in this work:

- PyTorch
- Scikit-learn
- SHAP
- NetworkX
- GSEApy
- g:Profiler
- KEGG
- Reactome
- DepMap / CCLE
- GDSC
- Google Colaboratory

Their contributions have made this research possible.

---

**GitHub Repository**
https://github.com/shailinsta/BioPathFormer

**Dataset**
https://huggingface.co/datasets/ShamsTahzib/PDAC

**GitHub Profile**
https://github.com/shailinsta
https://github.com/Dazedcoder1
---

## Project Status

**Current Status:** Under Review

The repository will be updated with

- Published manuscript
- DOI
- Zenodo archive
- Trained model checkpoints
- Supplementary material
- Additional documentation

---

<div align="center">

### BioPathFormer

**A Pathway-Aware Computational Framework for Interpretable Pharmacogenomic Drug-Response Prediction and Biomarker Discovery in Pancreatic Ductal Adenocarcinoma**

</div>
