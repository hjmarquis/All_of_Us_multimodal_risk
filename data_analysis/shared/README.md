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

  Minimal end-to-end workflow demonstrating:
  - all-population initial model
  - all-population SSL model
  - Black-adjusted initial model
  - Black-adjusted SSL model
  - AUC / concordance uncertainty evaluation

- [project/Step1_Comorbidities_V2.R](project/Step1_Comorbidities_V2.R)

  Cohort construction and preprocessing.

- [project/Step2_V5Commor.R](project/Step2_V5Commor.R)

  Main Black-adjusted SSL analysis pipeline.

---

# SNP Extraction / PCA

- [project/RA_SNP_Ancestry.ipynb](project/RA_SNP_Ancestry.ipynb)

  Extract ancestry SNPs from All of Us WGS data using Hail.

- [project/RA_control_genomics_extraction.ipynb](project/RA_control_genomics_extraction.ipynb)

  Control cohort extraction workflow.

---

# Shared Functions

The `shared/` directory contains all core functions used throughout the analysis pipeline, including:

- semiparametric transformation model estimation
- SSL perturbation procedures
- uncertainty quantification
- evaluation metrics
- parallel computation helpers
- data loading and preprocessing

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
