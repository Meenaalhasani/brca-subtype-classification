# Feature Dimensionality Outweighs Model Complexity in Breast Cancer Subtype Classification Using TCGA-BRCA Gene Expression Data

This repository contains the manuscript files, figures, and analysis notebook for the arXiv preprint **"Feature Dimensionality Outweighs Model Complexity in Breast Cancer Subtype Classification Using TCGA-BRCA Gene Expression Data."**

Author: **Meena Al Hasani**

## Overview

This project evaluates how feature dimensionality and model complexity affect breast cancer subtype classification using TCGA-BRCA RNA-seq gene expression data. The study compares logistic regression, random forest, and support vector machine models across multiple feature sizes to determine whether more complex models improve classification performance in high-dimensional biological datasets.

The results show that model complexity alone does not guarantee better performance. Logistic regression achieved the most stable and balanced performance across breast cancer subtypes, while random forest and SVM showed limitations related to class imbalance and high-dimensional feature spaces.

## Research Question

This project investigates whether increased model complexity improves breast cancer subtype classification, how reducing the number of gene expression features affects performance, whether accuracy alone is sufficient for evaluating imbalanced biological classification tasks, and how model behavior differs across individual breast cancer subtypes.

## Dataset

The analysis uses the **TCGA Breast Cancer PanCancer Atlas 2018** dataset from cBioPortal, including RNA-seq gene expression data and molecular subtype annotations.

Breast cancer subtypes analyzed:

- BRCA_Basal
- BRCA_Her2
- BRCA_LumA
- BRCA_LumB
- BRCA_Normal

After aligning expression and clinical subtype data, the final dataset contained **981 samples** and **20,518 gene expression features**.

## Methods

The workflow includes data preprocessing, alignment of gene expression data with clinical subtype labels, removal of samples with missing subtype annotations, variance-based feature selection, model training, and stratified 5-fold cross-validation.

Feature selection was performed within each training fold to avoid data leakage. Genes were ranked by variance, and the top N genes were selected for each experiment.

The following feature sizes were evaluated:

- 50 genes
- 75 genes
- 100 genes
- 1,000 genes
- 20,518 genes

## Models Compared

Three machine learning models were compared:

- Logistic Regression
- Random Forest
- Support Vector Machine with RBF kernel

These models were selected to compare a simpler linear model, an ensemble tree-based model, and a nonlinear kernel-based model.

## Evaluation Metrics

Model performance was evaluated using:

- Accuracy
- Macro F1 score
- Weighted F1 score
- Per-subtype F1 score

Macro F1 score was emphasized because the dataset is imbalanced and includes minority subtypes such as BRCA_Normal. Accuracy alone can overestimate performance by favoring the dominant subtype, BRCA_LumA.

## Main Findings

Logistic regression achieved the most stable and balanced performance across subtypes. It maintained strong macro F1 scores and performed better on minority classes compared with the other models.

Random forest achieved strong overall accuracy but underperformed on minority subtypes, especially BRCA_Normal. This suggests that its performance was influenced by dominant classes.

SVM performed competitively at intermediate feature sizes, especially around 1,000 genes, but declined at full dimensionality. This suggests sensitivity to very high-dimensional feature spaces.

Accuracy alone was insufficient for evaluating model performance because it masked subtype-specific failures. Macro F1 and per-subtype F1 scores provided a more informative view of model behavior.

Performance generally improved from 50 genes to 1,000 genes, then plateaued. The top 1,000 highest-variance genes provided a strong balance between dimensionality reduction and classification performance.

## Figures Included

This repository includes the main figures used in the manuscript:

- `accuracy_plot.png` — Accuracy across feature sizes for logistic regression, random forest, and SVM.
- `macro_f1_plot.png` — Macro F1 score across feature sizes for all models.
- `heatmap_cv_1000genes.png` — Per-subtype F1 score comparison at 1,000 genes using 5-fold cross-validation averages.
- `subtype_plot.png` — Subtype-level F1 performance across models and feature sizes.

## Manuscript Files Included

This repository includes the LaTeX manuscript files:

- `main.tex` — Main manuscript source file.
- `references.bib` — Bibliography file.
- Figure image files used in the manuscript.

## How to Run the Analysis

Open the notebook file in Jupyter Notebook or JupyterLab and run the cells in order.

The notebook performs the main analysis, including data loading, preprocessing, feature selection, cross-validation, model training, metric calculation, and figure generation.

## Requirements

This project was implemented in Python using common data analysis and machine learning libraries, including:

- pandas
- numpy
- scikit-learn
- matplotlib
- seaborn
- scipy
- jupyter

## Data Availability

The TCGA Breast Cancer PanCancer Atlas 2018 data used in this project are publicly available through cBioPortal:

https://www.cbioportal.org/study/clinicalData?id=brca_tcga_pan_can_atlas_2018

The associated cBioPortal study page is available here:

https://www.cbioportal.org/study/summary?id=brca_tcga_pan_can_atlas_2018

Processed data files may not be included in this repository due to size or redistribution limits. Users should download the data from the original source and follow the preprocessing steps in the notebook.

## Code Availability

The analysis notebook and manuscript files are provided in this repository. The notebook contains the code used to generate the model performance results, tables, and figures.

## Citation

If using this repository or analysis, please cite the associated manuscript:

Al Hasani, M. **Feature Dimensionality Outweighs Model Complexity in Breast Cancer Subtype Classification Using TCGA-BRCA Gene Expression Data.**

Preprint available on arXiv:

https://arxiv.org/abs/2605.06562

## Author

**Meena Al Hasani**  
Independent Researcher

## License

No license has been selected for this repository. Please contact the author for reuse permissions.
