# Subgroup Discovery FRIENDS Project
This project aims to combine subgroup discovery (SD) with natural language processing (NLP), 
specifically with sentiment analysis and emotion or humor detection. NLP features are extracted 
from a TV show script, specifically the Friends TV series.
The datasets used are from Kaggle.
- A dataset of the FRIENDS script, made by users Bree Nguyen and Blesson Densil, accessible [here](https://www.kaggle.com/datasets/brzy56/friends-tv-television-scripts-all-dialogue-csv).
- A dataset of th IMDB rating per FRIENDS episode, made by users Mohammad Reza Ghari and Moulik Dhade, 
accessible [here](https://www.kaggle.com/datasets/rezaghari/friends-series-dataset/data).

---
## Installation Instructions


---
## File Descriptions
This section details the use and purpose of each file in the repository.

### Data files

- `friends_all_episodes_clean.csv` is the script dataset from Kaggle.
- `friends_episodes_v3.csv` is the ratings dataset from Kaggle.
- `df_script.csv` is the preprocessed and cleaned script dataset.
- `df_rating.csv` is the preprocessed and cleaned rating dataset.
- In the folder `/dialogue_lines_results_data/`:
    - `df_dialogue_emotion.csv` contains the detected emotion for each dialogue line.
    - `df_dialogue_humor.csv` contains the detected whether each dialogue line was humorous or not.
    - `df_dialogue_emotion.csv` contains the calculated sentiment for each dialogue line.
- In the folder `/feature_engineering_data/`:
    - `df_final.csv` contains the final feature engineered data for data analysis and SD.

### Code files

- `data_parser.ipynb` preprocesses `friends_all_episodes_clean.csv` and `friends_episodes_v3.csv` and calculates 
location proportions based on the script. It produces two CSV datasets, `df_script.csv` and `df_rating.csv` 
(location proportions are stored in the cleaned ratings dataset).
- `feature_engineering.ipynb` combines and parses `df_script.csv` and `df_rating.csv` to produce a variety of NLP and
script features. It produces the data files in the folders `/dialogue_lines_results_data/` 
and `/feature_engineering_data/`
- `Framework.ipynb` runs the SD algorithm and various quality measure experiments.
- `accuracy_checks.ipynb` evaluates the performance of the sentiment, emotion, and humor (NLP) models. Also checks the
error of the location extraction process.

