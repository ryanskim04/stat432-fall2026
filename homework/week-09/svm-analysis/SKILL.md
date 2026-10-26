---
name: svm-analysis
description: "Analyze a supplied classification dataset with support vector machines, select kernels and tuning settings using resampling, and report a concise, evidence-based final model."
disable-model-invocation: true
---

# SVM analysis and report

Use this skill only when the user explicitly invokes it. The user must supply or identify the data, response, predictors, class coding, and computing environment. Do not assume a dataset, variable names, or results.

## Analysis

1. Briefly introduce the analysis question and explain the response, predictors, class meanings, and any domain context provided. Inspect sample size, class counts, predictor types, missingness, and potential obstacles. Decide and report whether the data support SVM classification; disclose exclusions, encoding, or training-only imputation.
2. Choose a small, justified set of kernels. Consider linear for an approximately linear boundary, polynomial for plausible smooth interactions, and radial for flexible nonlinear boundaries. Explain choices in terms of the data and analysis goal; omit unsuitable kernels and avoid an unnecessarily broad search.
3. Name the tuning parameters and candidate values: cost C for all kernels; gamma for radial (and any kernel where applicable); degree and coefficient for polynomial if varied. State settings held fixed and limit the search to a defensible, manageable grid.
4. Use stratified k-fold cross-validation, or another justified resampling method, on the available training data to compare candidates. Keep folds identical across candidates. Standardize predictors and perform imputation, encoding, selection, or other learned preprocessing within each fold using its fitting portion only. Select by a stated primary metric and tie-break rule; report fold design, seed, candidate settings, and aggregated scores.
5. If data permit, reserve a test set before tuning. After selection, refit the complete pipeline on training data and evaluate it once on the untouched test set; do not use test results to change the model. If a separate test set is impractical, state that resampling provides the performance estimate.
6. Check convergence and numerical validity; report failed candidates rather than hiding them. Interpret the selected fit with key numerical results, including its kernel, tuned settings, primary CV score, and test score if available. Define metrics and class labels. If reporting a confusion matrix, identify the positive class and explain which cells are false/true positives/negatives.
7. End with a plain-language conclusion that names the preferred model and explains why its measured performance and trade-offs support the choice. State limitations and distinguish CV selection evidence from any one-time test estimate.

## Required report

Produce a readable report of **no more than one printed page at 11-point font**. Prioritize evidence needed to justify the final model: a brief context statement, concise selection rationale, compact table of candidate kernels/settings and CV scores with the selected model marked, and one compact legible figure comparing candidates on the selection metric. Include key fit and evaluation numbers, metric definitions, conclusion, and material limitations. Keep the figure and table consistent with the reported calculations; exclude nonessential output. Verify rendered pagination when possible, and disclose if it cannot be checked.
