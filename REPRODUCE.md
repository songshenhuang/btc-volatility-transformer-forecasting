# Reproducing Results

These are the exact steps a grader or teammate can follow to reproduce the project outputs.

## 1. Clone the repository

```bash
git clone <your-repo-url>
cd <your-repo-folder>
```

## 2. Create and activate a virtual environment

### macOS/Linux
```bash
python -m venv .venv
source .venv/bin/activate
```

### Windows PowerShell
```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
```

## 3. Install required packages

```bash
pip install --upgrade pip
pip install -r requirements.txt
```

## 4. Open the notebook

```bash
jupyter notebook btc_rv_window_horizon_experiments.ipynb
```

## 5. Run all cells from top to bottom

The notebook will:

- download the Bitcoin hourly OHLCV dataset using `kagglehub`
- preprocess the data
- engineer realized-volatility features
- train all models
- evaluate all settings across 5 random seeds
- create summary tables and plots
- save cached outputs

## 6. Generated files

After a successful full run, you should see:

- `models/experiment_cache.pkl`
- `results/btc_rv_window_horizon_results.csv`

## 7. Fast rerun option

If `models/experiment_cache.pkl` already exists, the notebook can load cached experiment outputs instead of retraining everything.

## 8. Expected final output

The final notebook cells should display:

- a summary table with **mean ± std across 5 seeds**
- comparison plots across models, windows, and horizons
- example train/validation curves
- example actual vs predicted plots

## 9. Important reproducibility notes

- Do not shuffle the dataset.
- Keep the chronological train/validation/test split.
- Keep the same experiment settings unless intentionally running an ablation study.
- Use the same random seed logic already defined in the notebook.

