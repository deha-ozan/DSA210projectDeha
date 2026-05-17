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

Upload `music_weather_colab2.ipynb` to [colab.research.google.com](https://colab.research.google.com) and run all cells. The notebook fetches the dataset directly from this GitHub repository — no uploads or API keys required.

---

## Hypotheses Tested

| # | Hypothesis | Test | Result |
|---|---|---|---|
| H1 | Rainy days → more listening time | Mann-Whitney U | Not significant (p=0.0774) |
| H2 | Temperature correlates with listening duration | Spearman correlation | Significant (p<0.0001, ρ=−0.215) |
| H3 | Listening activity differs across seasons | Kruskal-Wallis | Significant (p<0.0001) |
| H4 | Weekends have different skip rates than weekdays | Mann-Whitney U | Significant (p=0.0081) |
| H5 | Precipitation correlates with number of plays | Spearman correlation | Not significant (p=0.1655, ρ=0.046) |

---

## Machine Learning Methods

Four supervised models were applied to predict listening behavior from weather and temporal features:

| Model | Type | Target | Key finding |
|---|---|---|---|
| Linear Regression | Regression | Daily listening duration | Weak predictive power from weather alone |
| Random Forest | Regression | Daily listening duration | Captures non-linear patterns; day-of-week dominates feature importance |
| K-Nearest Neighbors | Regression | Daily listening duration | Strong improvement when time features are added |
| Decision Tree | Classification | Rainy vs. non-rainy day | Listening patterns alone cannot predict weather |

**Key result:** Temperature and season significantly correlate with listening duration, but the direction is negative — I listen more in colder months. Day-of-week is a stronger predictor than weather overall. Rain alone does not significantly affect how much or how often I listen.

---

## Limitations

- Audio feature analysis (song valence, energy, danceability) via the Spotify Web API was planned but not feasible — Spotify deprecated the `/v1/audio-features` endpoint for apps created after November 2024.
- Raw Apple Music data is excluded from the repository for privacy reasons.
- Findings reflect one individual's listening habits and are not generalizable.

---

## AI Tool Usage

Parts of this code were drafted with the assistance of Claude (Anthropic). All outputs were reviewed and adapted.
