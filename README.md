# ERP Processing and Spectral Decomposition

## Overview
This repository contains a three‑stage Jupyter Notebook workflow for preprocessing electrophysiology (ERP) data, performing time–frequency / spectral decomposition, and generating statistics and figures. A central `config.py` file defines paths and experiment‑level parameters so the pipeline stays consistent across runs. 

## Repository Contents
```
1_preprocessing.ipynb              # Import, clean, and epoch voltage data
2_erp_spectraldecomposition.ipynb  # Compute power/phase & time–frequency features
3_stats_figures.ipynb              # Run stats and render publication-ready figures
config.py                           # Project paths & constants used by the notebooks
data/                               # (you provide) raw input data
volt/                               # generated: cleaned/epoched voltage arrays
power/                              # generated: spectral power/phase outputs
figs/                               # generated: figures
```
> The output folders (`volt/`, `power/`, `figs/`) are created automatically by the notebooks if missing.

## Configuration
Project‑wide settings live in **`config.py`**. Update these first to match your environment:
- **Directories**: `dataDir`, `voltDir`, `powDir`, `figDir` define where raw data live and where processed outputs and figures are written. 
- **Sampling**: `samp_rate` is the sampling rate (Hz). 
- **Epoch window**: `PRESTIM` and `POSTSTIM` (in ms) define the time window around stimulus; `DUR` and `stimOnset` are computed from these. 
- **Time–frequency**: Morlet parameter `wavenum`, frequency bounds `lowFreq`–`highFreq`, and `nFreq` (number of frequencies). 
- **Statistics**: `nIter` controls iterations for nonparametric permutation tests. 

> Keep `config.py` under version control so analyses are reproducible across machines.

## Requirements
- Python 3.9+
- Jupyter Notebook or JupyterLab

Common scientific stack (install as needed by your environment / notebooks):
```bash
pip install numpy scipy pandas matplotlib
# and any domain packages you use (e.g., mne, seaborn, pingouin)
```
