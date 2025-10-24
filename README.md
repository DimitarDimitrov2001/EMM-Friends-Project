# EMM Friends Project

## Overview
This project studies the Friends TV series by combining subgroup discovery (SD) with natural language processing (NLP). We extract sentiment, emotion, and humor scores from dialogue, engineer episode-level features, and then run SD experiments to uncover interpretable behavioral patterns that relate to episode ratings.

## Data Sources
- Friends dialogue scripts, made by Bree Nguyen and Blesson Densil: https://www.kaggle.com/datasets/brzy56/friends-tv-television-scripts-all-dialogue-csv
- IMDb ratings dataset, made by Mohammad Reza Ghari and Moulik Dhade: https://www.kaggle.com/datasets/rezaghari/friends-series-dataset/data

## Repository Layout
| Files | Description |
| --- | --- |
| `raw_data/` | Original Kaggle downloads (`friends_all_episodes_clean.csv`, `friends_episodes_v3.csv`). |
| `preprocessed_data/` | Cleaned, preprocessed versions produced by the parser (`df_script.csv`, `df_rating.csv`). |
| `dialogue_lines_results_data/` | Line-level NLP outputs from the emotion, sentiment, and humor transformer models (`df_dialogue_emotion.csv`, `df_dialogue_humor.csv`, `df_dialogue_sentiment.csv`). |
| `feature_engineered_data/df_final.csv` | Aggregated episode-level feature table used for SD analysis. |
| `result_files/*.txt` | Text dumps of SD quality scores for different measures (Beta Coverage Weighting, Kullback-Leibler, Welch's t-statistics). |
| `data_parser.ipynb` | Has EDA analysis, cleans the raw scripts and ratings, computes location proportions, and exports the proprocessed data in `preprocessed_data/`. |
| `feature_engineering.ipynb` | Uses the preprocessed data to create NLP features from the episode scripts and creates `df_final.csv` with those features. |
| `accuracy_checks.ipynb` | Validates sentiment, emotion, humor predictions and location extraction accuracy. |
| `Framework_SD.ipynb` | Runs subgroup discovery experiments across several quality measures. |
| `Results_SD.ipynb` | Explores and summarizes SD outcomes. |

## Workflow
1. **Data Parsing** – Open `data_parser.ipynb` to preprocess the Kaggle datasets, and export `df_script.csv` and `df_rating.csv` to `preprocessed_data/`.
2. **Feature Engineering** – Run `feature_engineering.ipynb` to create the NLP features per episode, and export the final dataset to `feature_engineered_data/df_final.csv` and also export the transformer models' outputs per dialogue line to `dialogue_lines_results_data/`.
3. **Quality Validation** – Use `accuracy_checks.ipynb` to inspect the performance of the NLP models and verify location extraction consistency.
4. **Subgroup Discovery** – Execute `Framework_SD.ipynb` to search for subgroups, using `df_final.csv`, with respect to ratings and the extracted NLP features. The scores are written to `result_files/`.
5. **Result Analysis** – Review `Results_SD.ipynb` to see and interpret the discovered subgroups and compare alternative quality measures.

## Reproducing the Pipeline
1. **Set up Python** – Create virtual environment (Python 3.9+ recommended) and install all required libraries by running in the terminal:
    ```
    pip install -r requirements.txt
    ```
2. **Place Raw Data** – Ensure the two Kaggle CSV files are available under `raw_data/` with the expected filenames.
3. **Execute Notebooks** – Run the notebooks in the order outlined above. Each notebook writes its outputs into the corresponding data folder.
4. **Inspect Outputs** – Final episode-level dataset is seen in `feature_engineered_data/`, while SD score summaries and visual analyses can be found in `result_files/` and `Results_SD.ipynb`.

## Team Note
- The intermediate datasets are also uploaded to the repository to make the experiments reproducible without rerunning every notebook.
