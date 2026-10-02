# Black Friday Sales Prediction

This repository contains an exploratory Jupyter notebook for predicting `Purchase` from customer and product fields using decision-tree and random-forest regressors. The notebook is an educational example, not a production-ready prediction service.

## Data

The dataset is **not included** in this repository. The notebook expects a CSV named `Black Friday Dataset.csv` in the repository root, or a different path supplied through the `BLACK_FRIDAY_DATA` environment variable. The expected input is the Black Friday sales CSV with the columns used by the notebook, including `Purchase`, `Gender`, `Age`, `Occupation`, `City_Category`, `Stay_In_Current_City_Years`, `Marital_Status`, and `Product_Category_1` through `Product_Category_3` (plus `User_ID` and `Product_ID`, which the notebook drops before modeling).

No dataset download URL or redistribution permission has been verified for this repository. Obtain the data from a source you are authorized to use, review its terms, and do not commit it unless redistribution is permitted. The saved notebook output has been cleared, so it does not provide data or reproducible results.

## Setup and run

Use Python 3.9 or newer in a virtual environment. From the repository root:

```bash
python -m venv .venv
# Linux/macOS
source .venv/bin/activate
# Windows PowerShell: .venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

Place the CSV at `Black Friday Dataset.csv` in the repository root, then run:

```bash
jupyter notebook "Black Friday Sales Prediction.ipynb"
```

To use another location, set `BLACK_FRIDAY_DATA` before launching Jupyter. For example, on Linux/macOS:

```bash
BLACK_FRIDAY_DATA=/path/to/Black\ Friday\ Dataset.csv jupyter notebook "Black Friday Sales Prediction.ipynb"
```

On Windows PowerShell:

```powershell
$env:BLACK_FRIDAY_DATA = "C:\path\to\Black Friday Dataset.csv"
jupyter notebook "Black Friday Sales Prediction.ipynb"
```

Run cells in order after confirming the CSV has the expected columns. If the file is absent, the first data-loading cell reports how to provide it.

## What the notebook currently does

The notebook explores the data, drops `User_ID` and `Product_ID`, applies `LabelEncoder` independently to object-typed columns, creates dummy columns for `Stay_In_Current_City_Years`, fills missing values in `Product_Category_2` and `Product_Category_3` with zero, and fits decision-tree and random-forest regressors using a random row-level train/test split. This is the notebook's current workflow, not a claim that this is the best encoding, missing-value strategy, or validation design. In particular, label-encoding nominal categories imposes integer codes, and the row split does not test generalization to unseen users or products.

The notebook reports only R² in its original analysis and does not establish performance beyond its particular split. There are no saved metrics in the cleaned notebook. **No model training or performance result has been independently reproduced for this repository update**; results must not be inferred from this README.

## Dependencies

Direct package versions are pinned in [`requirements.txt`](requirements.txt) to make environment setup more repeatable. The dataset itself remains an external prerequisite.
