# UEFA Nations League Match Prediction

## Project Overview

This project uses Machine Learning to predict UEFA Nations League match outcomes.

The model predicts three possible outcomes:

* H = Home win
* D = Draw
* A = Away win

The project also uses Monte Carlo simulation to explore possible tournament outcomes and estimate trophy-winning probabilities under the model's assumptions.

## Dataset

The historical dataset contains 49,547 international football matches from 1872 to 2026.

Important variables include:

* date
* home_team
* away_team
* home_score
* away_score
* tournament
* city
* country
* neutral

The historical data was cleaned, checked for duplicates and missing values, converted to chronological order, and transformed into machine-learning features.

## Feature Engineering

The model uses pre-match information only.

Main features:

* recent form
* average goals scored
* average goals conceded
* goal difference
* Elo rating
* home-specific form
* away-specific form
* neutral venue indicator

The features are calculated from information available before each match to reduce data leakage.

## Machine Learning

Two main models were tested:

* Logistic Regression
* Random Forest

A simple majority-class baseline was also used.

The initial test results were approximately:

* Baseline: 47.58%
* Logistic Regression: 59.62%
* Random Forest: 58.76%

Logistic Regression was retained as the main baseline model.

## Evaluation

The model was evaluated using:

* Accuracy
* Precision
* Recall
* F1-score
* Confusion Matrix

The analysis showed that predicting draws is considerably more difficult than predicting home wins and away wins.

## Nations League Prediction

The trained model was applied to the 2026/27 UEFA Nations League League A fixtures.

For each match, the model produces probabilities for:

* Home win
* Draw
* Away win

These probabilities are then used in tournament simulations.

## Tournament Simulation

A Monte Carlo approach was used to simulate possible competition outcomes.

The simulation repeatedly generates possible league-phase and knockout outcomes and counts how frequently teams reach later stages and win the tournament.

The resulting probabilities are model-based estimates, not guaranteed outcomes.

## Project Structure

```text
NationsLeague_ML_Project/
│
├── data/
│   ├── results.csv
│   ├── nations_league_2026_27_league_a.csv
│   └── processed/
│       └── historical_matches.csv
│
├── models/
│   └── nations_league_model.joblib
│
├── notebooks/
│   └── football_prediction.ipynb
│
├── results/
│   ├── matchday2_predictions.csv
│   ├── league_a_qualification_probability.csv
│   ├── trophy_probabilities.csv
│   └── trophy_probabilities.png
│
├── .venv/
├── requirements.txt
└── README.md
```

## Limitations

The model has limited predictive accuracy and should not be interpreted as a certainty.

The tournament simulation is a baseline simulation. In particular, the knockout implementation simplifies some details of the official UEFA format.

Future improvements could include:

* more advanced team-strength features
* better calibration of probabilities
* dynamic feature updates after every simulated match
* exact-score modelling
* a fully faithful implementation of the UEFA knockout draw and two-leg quarter-finals
* additional historical or ranking data

## Conclusion

The project demonstrates a complete Machine Learning workflow:

```text
Historical Football Data
        ↓
Data Cleaning
        ↓
Feature Engineering
        ↓
Machine Learning
        ↓
Model Evaluation
        ↓
Match Probabilities
        ↓
Tournament Simulation
        ↓
Trophy Probability Analysis
```
