# ecsoc-temazepam-sleep-eeg

Two-regime detrended fluctuation analysis (DFA) of temazepam effects on sleep EEG scale-dependent temporal structure. Companion code for:

> Okabe, H. "Temazepam Reorganizes Scale-Dependent Temporal Structure in Human Sleep EEG: Distinct Effects on Global Scaling and Cross-Scale Asymmetry." *Sleep Medicine* (submitted, 2026).

## Overview

This repository contains the full analysis pipeline used in the manuscript above, implemented as a single Google Colab notebook. The analysis quantifies a scale-asymmetry index, **CHI = 2(α₁ − α₂)**, derived from short- and long-scale DFA exponents, and compares it against a conventional single-exponent DFA metric (α_global) across sleep stages under temazepam vs. placebo conditions.

## Data sources

All data are drawn from publicly available PhysioNet repositories. Raw data are **not** redistributed in this repository; the notebook assumes the relevant datasets have been downloaded separately and organized in Google Drive (see *Environment* below).

| Dataset | Role in analysis | Source |
|---|---|---|
| Sleep-EDF Expanded — Sleep Telemetry (ST) | Primary within-subject temazepam vs. placebo cohort (N=22) | https://physionet.org/content/sleep-edfx/1.0.0/ |
| Sleep-EDF Expanded — Sleep Cassette (SC) | Cross-cohort comparison and drug-free night-to-night variability control | https://physionet.org/content/sleep-edfx/1.0.0/ |
| DREAMS Subjects Database | Independent group-level replication of the CHI sleep-stage profile | https://physionet.org/content/dreams/1.0.0/ |
| Sleep Heart Health Study PSG Database (SHHS) | Single-subject cross-cohort check | https://physionet.org/content/shhpsgdb/1.0.0/ |

## Environment

- Google Colab (Python 3)
- Google Drive mount for data access
- Dependencies (installed at runtime by the notebook):
  `mne`, `pyEDFlib`, `scipy`, `numpy`, `pandas`, `matplotlib`, `seaborn`, `openpyxl`

To run the notebook on your own data copy, update the `DRIVE_ROOT` path and related folder variables in the "Path setup" step near the top to match where you have placed the downloaded PhysioNet files in your own Google Drive.

## Notebook structure

The notebook is organized into four sequential sections, matching the manuscript's Results and Supporting Information (S1–S3):

1. **Main analysis (Steps 1–11)** — ST cohort within-subject pipeline: file pairing via `ST-subjects.xls`, core CHI / α1 / α2 / R² / PhaseV / D_eff_rel computation, paired Wilcoxon signed-rank tests, rank-biserial effect sizes, Bayes factors, and figure generation.
2. **External validation (Steps 1–9b)** — SC cohort comparison, SHHS and DREAMS cross-cohort checks, slow-wave-activity (SWA) vs. CHI correlation with a gain-invariant control, order-effect analysis, and α1/α2 component decomposition.
3. **SC night-to-night control (Steps 1–5)** — drug-free within-subject variability control (75 participants, two nights each).
4. **Auxiliary analysis (Steps 1–8)** — comparison of CHI against other nonlinear EEG metrics (spectral slope, permutation entropy, Lempel–Ziv complexity, sample entropy), gain-confound checks, and robustness tests.

## Citation

If you use this code, please cite:

Okabe, H. (2026). Temazepam Reorganizes Scale-Dependent Temporal Structure in Human Sleep EEG: Distinct Effects on Global Scaling and Cross-Scale Asymmetry. *Sleep Medicine* (submitted).

## License

MIT License — see [LICENSE](./LICENSE).
