# Atherosclerosis Oxidative Stress Transcriptomics
### Differential Expression & Pathway Enrichment Analysis on Public GEO Data
[![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python)](https://python.org)
[![Jupyter](https://img.shields.io/badge/Jupyter-Lab-orange?logo=jupyter)](https://jupyter.org)
[![License: MIT](https://img.shields.io/badge/License-MIT-green)](LICENSE)
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/3o5k/oxidative-stress-atherosclerosis-transcriptomics/blob/main/atherosclerosis_oxidative_stress_analysis.ipynb)

## Overview

Transcriptomic analysis pipeline testing whether a curated **oxidative stress / antioxidant defense gene panel** distinguishes symptomatic from asymptomatic human carotid atherosclerotic plaque, using public microarray data from NCBI GEO (GSE21545, Biobank of Karolinska Endarterectomy). Includes a paired positive-control analysis validating that the pipeline detects real biological signal when it is present.

## Dataset

| | |
|---|---|
| Accession | [GSE21545](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE21545) — Biobank of Karolinska Endarterectomy (BiKE) |
| Platform | GPL570 — Affymetrix Human Genome U133 Plus 2.0 Array |
| Samples | 223 (paired carotid plaque + PBMC from ~111 patients) |
| Covariates | age, ischemic time, ischemic event, sample type |

## Oxidative Stress Panel

39 genes across seven functional modules: superoxide dismutases (SOD1/2/3), catalase & glutathione peroxidases, glutathione synthesis & redox cycling, thioredoxin/peroxiredoxin system, Nrf2-Keap1 response, ROS-generating enzymes, and metal-binding/auxiliary proteins.

## Notebook

| File | Contents |
|---|---|
| `atherosclerosis_oxidative_stress_analysis.ipynb` | Data acquisition, preprocessing, age-adjusted differential expression, two-method panel enrichment, positive-control validation, figures, interpretation |

## Key Findings

- Age-adjusted differential expression found **0/23,520 genes** significant between symptomatic and asymptomatic plaque, with no panel enrichment by either Fisher's exact or rank-based (Mann-Whitney) testing — a null result, consistent across both methods
- A positive-control comparison (plaque vs. matched PBMC, same patients) confirms the pipeline detects real signal: **~40% of genes** differ genome-wide by tissue type, and the oxidative-stress panel is enriched above that background (OR = 1.95, **p = 0.031**)
- An earlier dataset iteration (GSE57691) was found to carry a donor-vs-surgical-tissue batch confound, diagnosed via quantile normalization and a Mann-Whitney sensitivity check, and replaced before proceeding

## Tech Stack

`Python 3.10` · `Jupyter Lab` · `pandas` · `NumPy` · `SciPy` · `statsmodels` · `Matplotlib` · `Seaborn`

## Quick Start

**Colab (no setup):** click the badge above, then Runtime → Run all.

**Local:**
```bash
git clone https://github.com/3o5k/oxidative-stress-atherosclerosis-transcriptomics.git
cd oxidative-stress-atherosclerosis-transcriptomics
pip install -r requirements.txt
jupyter lab
```
Requires internet access — the notebook downloads data directly from NCBI GEO.

## Author

**Abdulmohsen Almutairi**
MSc Biochemistry, University of Jeddah, Saudi Arabia
abdulmohsen.khalef@gmail.com

## License

MIT — see [LICENSE](LICENSE).
