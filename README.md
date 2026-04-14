# Music Listening Behavior & Weather Analysis
**DSA 210 — Spring 2026**

> Does weather affect how and what I listen to? This project analyzes 8 years of personal Apple Music history against historical weather data for Istanbul.

---

## Data Sources
| Dataset | Source | Description |
|---------|--------|-------------|
| Apple Music history | Apple Data & Privacy portal | ~93k records total, filtered to Oct 2023–2026 |
| Weather (Istanbul) | [Open-Meteo](https://open-meteo.com/) | Daily temperature, precipitation, sunshine, weather code |
| Audio features | [Spotify Web API](https://developer.spotify.com/) | Valence, energy, danceability, tempo, acousticness |

---

## Project Structure
```
.
├── Apple_Music_-_Play_History_Daily_Tracks.csv   # raw Apple Music data
├── music_weather_colab.ipynb                     # main notebook (EDA + tests)
├── music_weather_merged.csv                      # cleaned track-level dataset (generated)
├── music_weather_daily.csv                       # daily aggregates (generated)
├── weather_istanbul.csv                          # cached weather data (generated)
├── requirements.txt
└── README.md
```

---

## How to Reproduce

### 1. Open in Google Colab
Upload `music_weather_colab2.ipynb` to [colab.research.google.com](https://colab.research.google.com).

### 2. Mount Google Drive
Run **Step 0** — sign in and set your save folder path.

### 3. Upload your data
Run **Step 1** — a file picker will appear, select `Apple_Music_-_Play_History_Daily_Tracks.csv`.

### 4. Run all cells
Weather data is fetched automatically from Open-Meteo (no API key needed). All outputs are saved to your Google Drive.

> Data is filtered to **October 2023 – present** (~2.5 years).

---

## Hypotheses Tested
| # | Hypothesis | Test |
|---|-----------|------|
| H1 | Rainy days → more listening time | Mann-Whitney U |
| H2 | Temperature correlates with listening duration | Spearman correlation |
| H3 | Listening activity differs across seasons | Kruskal-Wallis |
| H4 | Weekends have different skip rates than weekdays | Mann-Whitney U |
| H5 | Song valence is lower on rainy days *(Spotify required)* | Mann-Whitney U |
| H6 | Precipitation correlates with number of plays | Spearman correlation |

---

## AI Tool Usage
Parts of this code were drafted with the assistance of Claude (Anthropic). Prompts included requests to structure the data cleaning pipeline, select appropriate statistical tests, and write plotting code. All outputs were reviewed and adapted.
