# Music Listening Behavior & Weather Analysis

**DSA 210 — Introduction to Data Science | Spring 2026 | Ali Deha Ozan**

> Does Istanbul weather predict how much and what I listen to? This project analyzes ~93k personal Apple Music records against historical weather data for Istanbul across 2.5 years.

---

## Research Question

Can daily weather conditions (temperature, precipitation, sunshine) predict my personal music listening behavior, or do temporal habits (weekday vs. weekend, season) dominate?

---

## Data Sources

| Dataset | Source | Description |
|---|---|---|
| Apple Music history | Apple Data & Privacy portal | ~93k records, filtered to Oct 2023–present |
| Weather (Istanbul) | [Open-Meteo](https://open-meteo.com/) | Daily temperature, precipitation, sunshine duration, weather code |
| Audio features | [Spotify Web API](https://developer.spotify.com/) | Valence, energy, danceability, tempo, acousticness |

---

## Repository Structure

```
.
├── music_weather_colab2.ipynb    # Main notebook — EDA, hypothesis testing, ML
├── music_weather_daily.csv       # Daily aggregated dataset (generated)
├── music_weather_merged.csv      # Track-level merged dataset (generated)
├── DehaProjectProposal.pdf       # Phase 1 project proposal
├── requirements.txt              # Python dependencies
└── README.md
```

> **Note:** Raw Apple Music data (`Apple_Music_-_Play_History_Daily_Tracks.csv`) is not included in this repository for privacy reasons. The notebook fetches `music_weather_daily.csv` directly from GitHub — no local files needed to reproduce results.

---

## How to Reproduce

### Open in Google Colab

Upload `music_weather_colab2.ipynb` to [colab.research.google.com](https://colab.research.google.com) and run all cells. The notebook fetches the dataset directly from this GitHub repository — no uploads or API keys required.

---

## Hypotheses Tested

| # | Hypothesis | Test | Result |
|---|---|---|---|
| H1 | Rainy days → more listening time | Mann-Whitney U | — |
| H2 | Temperature correlates with listening duration | Spearman correlation | — |
| H3 | Listening activity differs across seasons | Kruskal-Wallis | — |
| H4 | Weekends have different skip rates than weekdays | Mann-Whitney U | — |
| H5 | Song valence is lower on rainy days *(Spotify required)* | Mann-Whitney U | — |
| H6 | Precipitation correlates with number of plays | Spearman correlation | — |

---

## Machine Learning Methods

Four supervised models were applied to predict listening behavior from weather and temporal features:

| Model | Type | Target | Key finding |
|---|---|---|---|
| Linear Regression | Regression | Daily listening duration | Weak predictive power from weather alone |
| Random Forest | Regression | Daily listening duration | Captures non-linear patterns; day-of-week dominates feature importance |
| K-Nearest Neighbors | Regression | Daily listening duration | Strong improvement when time features are added |
| Decision Tree | Classification | Rainy vs. non-rainy day | Listening patterns alone cannot predict weather |

**Key result:** Day-of-week and month are stronger predictors of listening duration than weather variables. Weather has a real but modest effect; listening behavior is primarily habit-driven.

---

## AI Tool Usage

Parts of this code were drafted with the assistance of Claude (Anthropic). All outputs were reviewed and adapted.
