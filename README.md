# BioPathFormer

## Pathway-Aware Graph Learning and Bayesian Uncertainty Modeling for Interpretable Biomarker Discovery and Drug Response Prediction in Pancreatic Ductal Adenocarcinoma

---

## Overview

BioPathFormer is a **pathway-aware computational framework** for pharmacogenomic drug-response prediction and interpretable biomarker discovery in **Pancreatic Ductal Adenocarcinoma (PDAC)**.

The framework integrates biological pathway knowledge from **KEGG** and **Reactome**, graph representation learning, Graph Transformer-based prediction, explainable artificial intelligence, Bayesian uncertainty modeling, and leakage-free validation within a unified computational pipeline.

Unlike conventional pharmacogenomic prediction methods that primarily optimize predictive accuracy, BioPathFormer incorporates biological interpretability, uncertainty quantification, and pathway-level reasoning to identify reliable biomarkers and improve prediction robustness for precision oncology.

---

## Paper

**Title**

**Pathway-Aware Graph Learning and Bayesian Uncertainty Modeling for Interpretable Biomarker Discovery and Drug Response Prediction in Pancreatic Ductal Adenocarcinoma**

**Authors**

- **S.M**
- **S.T**
- **A.A**
---

---

## Abstract

Pancreatic ductal adenocarcinoma (PDAC) exhibits substantial molecular heterogeneity, making robust biomarker discovery and drug-response prediction particularly challenging.

BioPathFormer introduces a biologically informed computational framework that combines pharmacogenomic molecular profiles, curated pathway knowledge, graph representation learning, Graph Transformer prediction, SHAP explainability, Bayesian uncertainty estimation, and Drug-Disjoint GroupKFold validation within a unified analytical pipeline.

The proposed framework enhances predictive robustness while improving biological interpretability through pathway-aware feature representations, confidence-aware biomarker prioritization, and biological pathway enrichment analysis. The implementation supports reproducible pharmacogenomic research and precision oncology applications.

---

## Main Contributions

BioPathFormer introduces the following methodological contributions:

- Pathway-aware pharmacogenomic feature representation using KEGG and Reactome biological pathways.
- Gene–Pathway interaction graph construction for modeling higher-order biological relationships.
- Graph Transformer-based drug-response prediction.
- Drug-Disjoint GroupKFold validation to eliminate information leakage.
- SHAP-based explainable biomarker discovery.
- Bayesian uncertainty estimation for confidence-aware biomarker ranking.
- Functional pathway enrichment using KEGG and Reactome.
- Network hub discovery for biological interpretation.
- End-to-end reproducible computational workflow for precision oncology research.

---

## Repository Structure

```
BioPathFormer/
│
├── notebooks/
│   └── BioPathFormer_PDAC_Pipeline.ipynb
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
| 1 | Pharmacogenomic Data Acquisition |
| 2 | Data Preprocessing and Harmonization |
| 3 | Feature Engineering and Dimensionality Reduction |
| 4 | KEGG and Reactome Pathway Mapping |
| 5 | Pathway Representation Learning |
| 6 | Gene–Pathway Graph Construction |
| 7 | Graph Representation Learning |
| 8 | Network Centrality Analysis |
| 9 | Drug-Disjoint GroupKFold Validation |
| 10 | BioPathFormer Prediction Module |
| 11 | Drug Response Prediction |
| 12 | SHAP Explainability |
| 13 | Bayesian Uncertainty Estimation |
| 14 | Biomarker Ranking |
| 15 | Biomarker Prioritization |
| 16 | KEGG Pathway Enrichment |
| 17 | Reactome Pathway Enrichment |
| 18 | Network Hub Discovery and Biological Interpretation |
| 19 | Precision Oncology Applications |

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

---

# Experimental Configuration

The BioPathFormer framework was implemented using Python and modern deep learning libraries.

| Component | Configuration |
|-----------|---------------|
| Programming Language | Python 3.10 |
| Deep Learning Framework | PyTorch 2.x |
| Graph Learning | PyTorch Geometric |
| Graph Analysis | NetworkX |
| Gradient Boosting | XGBoost |
| Explainability | SHAP |
| Hyperparameter Optimization | Optuna |
| Random Seed | 42 |
| Validation Strategy | Drug-Disjoint GroupKFold (5-Fold) |
| Execution Platform | Google Colaboratory |
| Hardware | NVIDIA Tesla GPU (CUDA-enabled) / CPU |

---

# Biological Knowledge Sources

BioPathFormer integrates curated biological knowledge from publicly available pathway databases.

| Database | Purpose |
|-----------|---------|
| KEGG 2021 Human | Biological pathway annotation |
| Reactome 2022 | Functional pathway annotation |

The identified genes are mapped to curated biological pathways prior to graph construction, enabling pathway-aware feature learning and biologically meaningful representations.

---

# Results Summary

The experimental evaluation demonstrates the effectiveness of BioPathFormer for pathway-aware drug-response prediction and interpretable biomarker discovery.

| Metric | Value |
|---------|------:|
| ROC–AUC | **0.927** |
| Average Precision (AP) | **0.967** |
| RMSE | **0.1153** |
| MAE | **0.0726** |
| R² | **0.6266** |
| Pearson Correlation | **0.7980** |
| Spearman Correlation | **0.7819** |
| Validation Strategy | Drug-Disjoint GroupKFold |

The framework further identifies biologically meaningful biomarkers through SHAP explainability and Bayesian uncertainty modeling, followed by KEGG and Reactome enrichment analyses to support biological interpretation.

---

# Generated Outputs

Executing the notebook produces publication-quality outputs, including

- Drug response heatmaps
- Molecular heterogeneity visualizations (UMAP and PCA)
- Multi-omics correlation analysis
- Training and validation learning curves
- Actual versus predicted drug-response plots
- Residual error distributions
- Receiver Operating Characteristic (ROC) curves
- Precision–Recall (PR) curves
- SHAP summary and dependence plots
- Bayesian uncertainty estimation
- Biomarker ranking tables
- KEGG pathway enrichment analysis
- Reactome pathway enrichment analysis
- Gene–pathway interaction networks
- Network hub discovery
- Publication-ready figures and tables

---

# Installation

Clone the repository

```bash
https://github.com/shailinsta/BioPathFormer.git
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
- Graph representation learning
- Drug-response prediction
- Drug-disjoint GroupKFold validation
- SHAP explainability
- Bayesian uncertainty estimation
- Biomarker prioritization
- KEGG enrichment analysis
- Reactome enrichment analysis
- Network hub discovery
- Publication-quality figure generation

---

# Reproducing the Experiments

To reproduce the experimental results reported in the manuscript:

1. Clone this repository.
2. Download the dataset from Hugging Face.
3. Place the downloaded files in the `datasets/` directory.
4. Install all required dependencies using `requirements.txt`.
5. Execute the notebook `BioPathFormer_PDAC_Pipeline.ipynb` from beginning to end.

The notebook reproduces the complete computational pipeline described in the manuscript, including preprocessing, pathway-aware graph learning, model training, evaluation, explainability analysis, Bayesian uncertainty modeling, biomarker prioritization, and biological pathway enrichment.

---

# Acknowledgements

The authors acknowledge the developers and maintainers of the following open-source projects and biological resources used in this work:

- PyTorch
- PyTorch Geometric
- Scikit-learn
- XGBoost
- SHAP
- Optuna
- NetworkX
- GSEApy
- KEGG
- Reactome
- Google Colaboratory

Their contributions have made this research possible.

---

**GitHub Repository**

https://github.com/shailinsta/BioPathFormer

**Dataset**

https://huggingface.co/datasets/ShamsTahzib/PDAC

**GitHub Profile**

https://github.com/shailinsta

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

