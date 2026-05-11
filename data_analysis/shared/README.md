# Data Analysis

This directory contains the main statistical analysis pipeline for:
- semiparametric transformation models (initial estimator)
- semi-supervised learning (SSL)
- Black-adjusted SNP models
- uncertainty quantification (UQ)
- PCA/SNP extraction workflows

---

# Main Scripts

## Core Analysis

- [Source/Full R Example.R](Source/Full%20R%20Example.R)

  Minimal workflow demonstrating by using compact function:
  - all-population initial model
  - all-population SSL model
  - Black-adjusted initial model
  - Black-adjusted SSL model
  - AUC / concordance uncertainty evaluation

Note: If the compact parallel functions fail due to memory limits or cluster issues, use the corresponding block-code scripts in `Source/`. The block-code workflow is mainly organized into four steps, where Step 2 and Step 4 contain the main model-running procedures and are generally more stable for large-scale runs.

## Block-Code Workflow

For large-scale runs, the block-code workflow in `Source/` is organized into four main steps:

- Step 1: model input construction and preprocessing.
- Step 2: All Race model fitting.
- Step 3: Race specific SNP selection.
- Step 4: final Race-adjusted model fitting and evaluation.

Uncertainty quantification is mainly implemented in the later model-running scripts, especially Step 4, where perturbation-based training uncertainty and test-set bootstrap AUC evaluation are combined. Concordance uncertainty is evaluated over the outer perturbation layer.
---

## Versioned Analysis Scripts

The repository also contains multiple historical and intermediate analysis versions used during development and experimentation.

Examples include:
- V6: all-population SSL / Black-adjusted experiments (Main analysis in main text)
- Comorbidities V2: final comorbidity-inclusive workflow with 70/30% Training Testing (Supplementary)
- PCA V6.5: Main analysis with PCA-adjusted covariates.
  Ancestry SNP extraction workflow:
  [RA_SNP_Ancestry.ipynb](../../extra/RA_SNP_Ancestry.ipynb)
- PCA V1: Commorbidity Analysis with PCA adjusted covariates
- V12 / V13: custom mapping workflow where the cohort is constructed and case/control status is defined using R. This version is optional and mainly preserved for comparison. 

These scripts are preserved for reproducibility and version tracking.

# Shared Functions

The `shared/` directory contains all core functions used throughout the analysis pipeline, including:

- semiparametric transformation model estimation
- SSL perturbation procedures
- uncertainty quantification
- evaluation metrics
- parallel computation helpers

Main entry point:

- [shared/source_all_functions.R](shared/source_all_functions.R)

Key modules include:

- [shared/beta_delta.R](shared/beta_delta.R)
- [shared/beta_delta_perturb.R](shared/beta_delta_perturb.R)
- [shared/SSLPerturb.R](shared/SSLPerturb.R)
- [shared/Sk_sym.R](shared/Sk_sym.R)
- [shared/Sk_sym_perturb.R](shared/Sk_sym_perturb.R)
- [shared/W_hat_adaPCA.R](shared/W_hat_adaPCA.R)
- [shared/Evaluation.R](shared/Evaluation.R)
- [shared/parallel.R](shared/parallel.R)
- [shared/data_io.R](shared/data_io.R)

---

# Notes

Some notebooks require:
- All of Us Researcher Workbench
- Hail
- Terra / GCS environment
