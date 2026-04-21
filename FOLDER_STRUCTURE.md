# Clean Folder Structure and File Descriptions

Use a simple structure like this:

```text
project_root/
├── btc_rv_window_horizon_experiments.ipynb   # main notebook with all experiments
├── README.md                                 # project overview, setup, execution
├── requirements.txt                          # package list and versions
├── REPRODUCE.md                              # exact reproduction steps
├── models/
│   └── experiment_cache.pkl                  # cached outputs generated after running
├── results/
│   └── btc_rv_window_horizon_results.csv     # final aggregated results generated after running
└── figures/
    ├── loss_curves.png                       # optional exported training/validation plot
    ├── rmse_comparison.png                   # optional exported comparison plot
    └── prediction_example.png                # optional exported actual-vs-predicted figure
```

## File descriptions

- **btc_rv_window_horizon_experiments.ipynb**  
  Contains the full project pipeline: imports, seed setup, data download, preprocessing, feature engineering, model definitions, training, evaluation, plots, and result export.

- **README.md**  
  Explains what the project does, how to install dependencies, and how to run the notebook.

- **requirements.txt**  
  Lists the Python packages needed to run the notebook.

- **REPRODUCE.md**  
  Gives a clean step-by-step guide for graders to reproduce the results.

- **models/experiment_cache.pkl**  
  Stores cached outputs from finished experiments, so later reruns do not need to retrain everything.

- **results/btc_rv_window_horizon_results.csv**  
  Stores the aggregated final table reported in the notebook.

- **figures/**  
  Optional folder for exported images

