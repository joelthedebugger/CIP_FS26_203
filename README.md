# CIP_FS26_203
Analysis of the impact of meteorological conditions on electricity prices and load in Switzerland (2015–2025)
# Impact of Meteorological Conditions on Electricity Prices in Switzerland

**Course:** CIP – Coding in Practice  
**Team:** Timo Schildknecht, Joel Rieser, Aurora Rigo  
**Period of Analysis:** 2015 – 2025  
**Geographic Scope:** Switzerland (Zurich, Basel, Geneva, Lugano)

---

## Project Description

Switzerland's electricity system is heavily dependent on hydropower (~60% of domestic production), making it sensitive to meteorological conditions. This project investigates how weather variables such as temperature, solar radiation, wind speed, and cloud cover influence electricity prices and electricity load in Switzerland. Data from multiple public sources is combined into a unified dataset and analysed using correlation analysis and regression models.

---

## Research Questions

| # | Research Question | Key Features | Metric |
|---|---|---|---|
| RQ1 | To what extent does daily mean temperature correlate with day-ahead electricity spot prices in Switzerland over 2015–2025? | `Temperature`, `price` | Pearson r |
| RQ2 | How strongly do temperature and solar radiation explain weekly electricity load variability in Switzerland? | `Temperature`, `radiation`, `load` | R² |
| RQ3 | How accurately can weather variables predict day-ahead electricity prices? | `Weather variables` → `price` | MAE (2023–2025 test set) |

---

## Data Sources

| Source | Data | Access |
|---|---|---|
| [Open-Meteo](https://open-meteo.com/) | Historical weather data (temperature, radiation, wind, etc.) | Free API, no key required |
| [ENTSO-E Transparency Platform](https://transparency.entsoe.eu/) | Day-ahead electricity prices (CH bidding zone, EUR/MWh) | API via `entsoe-py`, free registration |
| [Swissgrid](https://www.swissgrid.ch/en/home/operation/grid-data/generation.html) | National electricity load (MW) | Public Excel downloads (.xlsx) |

---

## Project Structure

```
CIP_FS26_203/
├── data/
│   ├── raw/
│   │   ├── weather/        ← Open-Meteo API responses
│   │   ├── prices/         ← ENTSO-E day-ahead prices
│   │   └── load/           ← Swissgrid Excel files per year
│   └── processed/          ← cleaned and merged datasets
├── notebooks/
│   ├── 01_data_acquisition.ipynb
│   ├── 02_data_cleaning.ipynb
│   └── 03_analysis.ipynb
├── figures/                ← .gitkeep
├── output/                 ← .gitkeep
├── requirements.txt        ← Python dependencies
├── .gitignore
└── README.md
```

---

## Reproducibility

Install required packages:

```bash
pip install -r requirements.txt
```

Then run the notebooks in order:

```
01_data_acquisition.ipynb  →  02_data_cleaning.ipynb  →  03_analysis.ipynb
```

> **Note:** An ENTSO-E API key is required for price data. Register for free at [transparency.entsoe.eu](https://transparency.entsoe.eu/) and store your key in a `.env` file:
> ```
> ENTSOE_API_KEY=your_key_here
> ```
> The `.env` file is excluded from version control via `.gitignore`.

---

## Code Contributions

| Team Member | Contribution |
|---|---|
| Timo Schildknecht | ENTSO-E sections in `notebooks`, RQ1, report |
| Joel Rieser | Open-Meteo sections in `notebooks`, RQ2, report |
| Aurora Rigo | Swissgrid sections in `notebooks`, RQ3, report |

---

## Key Libraries

```python
requests          # API calls (Open-Meteo)
entsoe-py         # ENTSO-E API wrapper
pandas            # data cleaning & transformation
numpy             # numerical operations
scikit-learn      # regression models
matplotlib        # visualization
seaborn           # visualization
```
