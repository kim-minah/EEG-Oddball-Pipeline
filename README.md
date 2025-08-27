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
- **Directories**: `dataDir`, `voltDir`, `powDir`, `figDir` define where raw data live and where processed outputs and figures are written. fileciteturn1file0  
- **Sampling**: `samp_rate` is the sampling rate (Hz). fileciteturn1file0  
- **Epoch window**: `PRESTIM` and `POSTSTIM` (in ms) define the time window around stimulus; `DUR` and `stimOnset` are computed from these. fileciteturn1file0  
- **Time–frequency**: Morlet parameter `wavenum`, frequency bounds `lowFreq`–`highFreq`, and `nFreq` (number of frequencies). fileciteturn1file0  
- **Statistics**: `nIter` controls iterations for nonparametric permutation tests. fileciteturn1file0

> Keep `config.py` under version control so analyses are reproducible across machines.

## Requirements
- Python 3.9+
- Jupyter Notebook or JupyterLab

Common scientific stack (install as needed by your environment / notebooks):
```bash
pip install numpy scipy pandas matplotlib
# and any domain packages you use (e.g., mne, seaborn, pingouin)
```

## Quick Start
1. **Clone and set up**
   ```bash
   git clone <your-repo-url>
   cd <your-repo>
   python -m venv .venv && source .venv/bin/activate  # on Windows: .venv\Scripts\activate
   pip install -r requirements.txt  # if present; otherwise install the libs above
   ```

2. **Configure paths and parameters** in `config.py` to point `dataDir` at your raw files. fileciteturn1file0

3. **Run the notebooks in order**
   - **`1_preprocessing.ipynb`** → imports raw files from `data/`, applies cleaning/epoching, writes arrays to `volt/`.
   - **`2_erp_spectraldecomposition.ipynb`** → loads `volt/`, computes power/phase or time–frequency representations into `power/`.
   - **`3_stats_figures.ipynb`** → runs summary statistics / permutation tests and saves figures to `figs/`.

4. **Review outputs**
   - Cleaned/epoched voltage: `volt/`
   - Spectral power/phase: `power/`
   - Figures: `figs/`

## Reproducibility Tips
- Record your package versions (e.g., `pip freeze > requirements.txt`) after a working run.
- Commit `config.py` changes with informative messages (e.g., sampling rate, epoch window). fileciteturn1file0
- Use meaningful filenames for exported arrays and figures that encode condition/subject/session metadata.

## Citation
If you use or extend this workflow, please cite the repository and include a brief note describing the analysis stages (preprocessing → spectral decomposition → stats/figures).

---

*Maintainer: Minah Kim*

