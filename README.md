# research-multimodal-mafia

## Setup 

First, create your virtual environment (venv) called mmenv by running the following command:
    
```bash
python3 -m venv mmenv
```

Then, activate your venv by running the following command:

```bash
source mmenv/bin/activate
```

Finally, install the required packages by running the following command:

```bash
pip install -r requirements.txt
```

## Pre-Experiment Checklist

- Check configs

```yaml
use_optuna: True

gpus: [0, 1, 2, 3]

model_name: "transformer_baseline_reid_v2”

# Weights and Biases Logging
use_wandb: True
wandb_project: "mm-mafia-reid-baseline" # generally stays same
study_name: "transformer_baseline_v2_rn100_param=5m_no_downsampling_patch=24" # experiment level
wandb_run_name: "transformer_baseline_v2_rn100_param=5m_no_downsampling_patch=24" # keep same as study_name
wandb_trial_name: "elarger patch size=64, lower seq_len=4, e-5-6lr, transformer_encoder=3" # trial_name under study
```

- If using optuna for hyperameter search:
    - use_optuna, if True then make sure to use train_optuna.py
        - check the lr and weight decay range specified at the beginning of train_optuna.py
- Activate virtual environment
    
    ```bash
    source mmenv/bin/activate
    ```
    
- Run job scheduler interface
    ```bash
    python webapp_ui/app.py
    ```