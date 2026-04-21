# Bitcoin Realized Volatility Forecasting with LSTM and Transformers

This repository contains our final DATA/MSML 612 group project on **Bitcoin hourly realized volatility forecasting** using deep learning models.

## Project summary

We compare four models on the same forecasting task:

- Naive baseline
- LSTM
- Transformer with sinusoidal positional encoding
- Transformer with Time2Vec

Instead of predicting raw Bitcoin price, this final version predicts **future realized volatility** computed from hourly log returns. We evaluate multiple input window lengths and prediction horizons, and repeat each experiment across **5 random seeds** for more stable results.

## Dataset

We use the **Bitcoin Hourly OHLCV Dataset** from Kaggle:

- Source: Mouad Jaouhari, *Bitcoin Hourly OHLCV Dataset*
- Accessed through `kagglehub`

The notebook downloads the dataset automatically.

## Main file

- `btc_rv_window_horizon_experiments.ipynb`: full end-to-end notebook for data loading, feature engineering, model training, evaluation, plots, and final summary tables.

## Repository structure

```text
project_root/
├── btc_rv_window_horizon_experiments.ipynb   # main notebook
├── README.md                                 # setup and execution guide
├── requirements.txt                          # required Python packages
├── REPRODUCE.md                              # reproduction steps
├── models/
│   └── experiment_cache.pkl                  # cached experiment outputs (generated after running)
├── results/
│   └── btc_rv_window_horizon_results.csv     # exported summary table (generated after running)
└── figures/                                  # optional exported plots/screenshots for report
```

## Environment setup

### 1. Create a virtual environment

On macOS/Linux:

```bash
python -m venv .venv
source .venv/bin/activate
```

On Windows PowerShell:

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
```

### 2. Install dependencies

```bash
pip install --upgrade pip
pip install -r requirements.txt
```

## How to run

Open Jupyter Notebook or VS Code and run:

```bash
jupyter notebook btc_rv_window_horizon_experiments.ipynb
```

Then run the notebook cells from top to bottom.

## What the notebook does

1. Imports libraries and sets seeds
2. Defines experiment settings and model hyperparameters
3. Downloads and loads the Kaggle Bitcoin hourly OHLCV dataset
4. Builds volatility forecasting features and targets
5. Splits data chronologically into train/validation/test
6. Trains Naive, LSTM, Transformer-SinPE, and Transformer-Time2Vec
7. Repeats experiments over multiple `(window length, horizon)` settings and 5 seeds
8. Saves cached outputs to `models/experiment_cache.pkl`
9. Exports final summary results to `results/btc_rv_window_horizon_results.csv`

## Experiment settings

The notebook evaluates these `(WINDOW_LEN, HORIZON)` pairs:

- `(12, 3)`
- `(24, 3)`
- `(24, 6)`
- `(48, 6)`
- `(24, 12)`
- `(48, 12)`

Training settings used in the notebook:

- Batch size: `128`
- Epochs: `120`
- Patience: `8`
- Learning rate: `5e-4`
- Weight decay: `1e-5`
- Huber delta: `0.01`

## Reproducing the final results

Please see `REPRODUCE.md` for the exact sequence.

## Notes

- The notebook uses **chronological splitting**, not random shuffling, to avoid time leakage.
- Feature scaling is fit on the training split only.
- Results are reported as **mean ± standard deviation across 5 seeds**.
- The first full run can take time. Later runs are faster because cached results may be loaded from `models/experiment_cache.pkl`.

## Citation / reference implementation

This project adapts ideas from:

- Baruch and Aya, *Bitcoin Price Prediction Using Transformers*
- Vaswani et al., *Attention Is All You Need*
- Kazemi et al., *Time2Vec: Learning a Vector Representation of Time*

