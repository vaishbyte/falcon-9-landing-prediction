# Falcon 9 First-Stage Landing Prediction


**Short description**: A machine learning pipeline that predicts whether a SpaceX Falcon 9 first stage will perform a successful landing based on pre-launch telemetry, mission, and environmental features.


## Motivation
SpaceX saves costs by reusing the first stage. Predicting landing success helps competing providers estimate launch cost/risk and informs bidding strategy.


## Dataset
- Source: The dataset was created using publicly available information from SpaceX’s open data API and Wikipedia.  
- **Primary Source:** SpaceX REST API (https://api.spacexdata.com/v4/launches) — used to retrieve launch details such as payload mass, launch site, rocket type, mission outcome, and date.  
- **Secondary Source:** Wikipedia pages on *Falcon 9* and *Falcon Heavy* launches — (https://en.wikipedia.org/wiki/List_of_Falcon_9_and_Falcon_Heavy_launches),  web-scraped using BeautifulSoup to collect additional fields such as flight number, booster version, and landing outcome.  

- Rows: N (use exact number)
- Key features: `mission_id`, `payload_mass`, `launch_site`, `weather_conditions`, `trajectory_params`, `recovery_boat_available`, `previous_stage_reuse` etc.


## Approach
1. EDA and cleaning (missing values, outliers)
2. Feature engineering (engine burn metrics, normalized mass ratios, categorical encodings)
3. Model training (example: RandomForest / XGBoost / LogisticRegression)
4. Evaluation (accuracy, precision, recall, F1, ROC-AUC, confusion matrix)


## Results
- Best model: `XGBoostClassifier` with ROC-AUC = 0.92 (example)
- Top predictors: `max_q`, `payload_mass`, `wind_speed`, `previous_success_rate`


## How to run (local)
1. Clone the repo:
```bash
git clone https://github.com/<vaishbyte>/Falcon9-Landing-Prediction.git
cd Falcon9-Landing-Prediction
