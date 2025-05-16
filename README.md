# Ventilation-Prediction
Using machine learning to predict when ICU patients need to go on mechanical ventilation.

## Notebooks
* `ventilation_data_collection.py`:
  * Selects train and test sets from MIMIC-IV databse using Google BigQuery
* `ventilation_wrangling.py`:
  * Preprocesses data for machine learning models
  * Requires data from `ventlation_data_collection.py`
* `ventilation_feature_selection_and_baseline_modeling.py`:
  * Performs feature selection, establishes baseline performance, and performs error analysis
  * Requires data from `ventilation_wrangling.py`
* `ventilation_dl_preprocessing.py`:
  * Further preprocesses data for deep learning model
  * Requires data from `ventilation_wrangling.py`
* `ventilation_deep_learning.py`:
  * trains and evaluates a multimodal deep learning model for ventilation prediction
  * requires preprocessed data from `ventilation_dl_preprocessing.py`

## Setup
1. Clone the repository:
  ```bash
  git clone https://github.com/your-username/ventilation-prediction.git
  cd ventilation-prediction
  ```
2. Set up a virtual environment:
  ```bash
  python -m venv env
  source env/bin/activate  # Windows: env\Scripts\activate`
  ```
3. Install dependencies:
  ```bash
  pip install -r requirements.txt
  ```
4. Hardware: A GPU (e.g., NVIDIA T4) is recommended for training the deep learning model

## Data Requirements
This project uses data from the MIMIC-IV dataset, available via PhysioNet. You must have authorized access and comply with the MIMIC-IV data use agreement. 

## Usage
1. Prepare Data
  * Obtain train and test data CSVs from `ventilation_data_collection`
  * Place in "data/processed" (done automatically in code)
  * Obtain preliminary preprocessed data from `ventilation_wrangling.py`
2. Train and evaluate baseline models
  * Load wrangled data from `ventilation_wrangling.py`
3. Further preprocess data for deep learning
  * Load time series data from `ventilation_wrangling.py`
  * Obtain preprocesed DL data from `ventilation_dl_preprocessed.py`
4. Train and evaluate DL model
  * Load data from `ventilation_dl_preprocessed.py`

## Data Exclusion
The `.gitignore` file ensures no MIMIC-IV data (raw or derived) is uploaded. Generated files (`data/processed/*.csv`) must not be shared publicly.


