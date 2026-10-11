---
name: lda-qda-analysis
description: Analyze a supplied classification dataset using LDA, QDA, and permitted combinations; report results concisely.
---

# LDA/QDA analysis and report

Use this skill only when explicitly invoked. The caller must separately identify the dataset, response, predictors, class coding, and available computing environment. Do not assume or hard-code any dataset, variable names, observed results, or coding. Preserve the supplied response coding and predictor definitions unless the caller requests a change; disclose any necessary data exclusions or recoding.

## Analysis procedure

1. Inspect the supplied data and report the sample size, class counts, missingness, and any obstacles that affect the analysis. Do not silently drop observations or impute values; use a defensible, training-only approach and disclose it.
2. Before comparing or tuning models, use the supplied random seed (or choose and report one) to reserve a test set. Keep the test set untouched until model choices and settings are locked. Use stratification where appropriate and state the split.
3. On training data only, create one fixed set of stratified cross-validation folds and use those same folds for every candidate and setting. State the fold count and seed. Any preprocessing, feature selection, or dimension reduction must be estimated anew from each fold's analysis portion and applied to its validation portion. Never use validation or test outcomes to fit preprocessing.
4. Compare ordinary LDA and ordinary QDA at minimum. Seek good predictive performance using only LDA, QDA, or combinations of their predicted class probabilities. Optional candidates include LDA/QDA after PCA or another lower-dimensional representation, and a probability blend of LDA and QDA. A dimension-reduction step may transform predictors but must not replace LDA/QDA as the classifier. Do not introduce other classifier families.
5. Use misclassification rate as the primary comparison and selection criterion. Report fold-wise or aggregated cross-validation results and the method used to aggregate them. Select settings using only the shared training folds; define a simple tie-break rule before applying it. Avoid an unnecessarily broad search, and identify the candidate configurations considered.
6. After selection, refit all preprocessing and the selected classifier on the complete training set. Evaluate this fitted pipeline once on the reserved test set. Report test misclassification count and rate, with denominator. Do not revise the model in response to test performance. Distinguish this held-out estimate from cross-validation estimates.
7. Check that the fitted model is numerically valid (for example, class covariance estimates are nonsingular enough for the method). If a candidate fails, report the issue and use a justified LDA/QDA-based alternative selected without test information. Do not hide failures or present fabricated results.

## Required deliverable

Produce a clearly readable analysis report that fits on **at most one printed page**. Include:

- A concise title and a short statement of the response, predictors, class coding, and data split.
- A compact table listing ordinary LDA, ordinary QDA, and each selected extension/configuration, with cross-validation misclassification results; identify the selected candidate. Include the final test misclassification count, rate, and denominator.
- One legible figure that helps compare candidate cross-validation errors (for example, a dot or bar plot with a clear error scale and labels). Do not use test results to choose or tune candidates. Keep the figure and table readable when printed.
- Brief numerical model-fitting results sufficient to describe the selected fitted procedure (such as selected dimensions/blend weight, fitted pipeline settings, and relevant class/sample information). Do not dump full coefficient matrices unless needed to interpret the analysis.
- A concise explanation of the main predictive findings, the selection rule, and important limitations (for example, sampling variability, class imbalance, small sample size, or modeling assumptions).
- The random seed, cross-validation design, and explicit distinction between training cross-validation performance and the one-time test estimate.

Use compact labels, captions, and rounding; define the reported metric. Keep prose economical and avoid claims of certainty. Ensure the exported or rendered report actually occupies no more than one printed page; reduce nonessential detail or adjust layout if needed. If the environment cannot produce a figure or verify pagination, say so explicitly rather than claiming completion.
