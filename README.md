# Global Aviation Disruption & Financial Loss Analysis

### Exploratory Data Analysis · Machine Learning · Interactive Visualization

This project explores disruptions to civil aviation in the context of geopolitical tensions involving Iran and the United States. Using Python, it examines airline cancellations, flight rerouting, airport disruptions, airspace closures, and estimated financial losses. It also compares regression models for estimating airline financial losses.

> **Data transparency:** The notebook references six CSV datasets, but their original sources and collection methods are not documented in the notebook. The findings below describe the supplied datasets and should not be interpreted as independently verified real-world losses or conflict impacts. Confirm whether the datasets are real, synthetic, or illustrative before presenting them as factual evidence.

## Interactive Visualizations

Explore the interactive Plotly visualizations developed for this project:

🌍 **[Global Aviation Financial Losses – Interactive Map](https://enya32.github.io/Global-Aviation-Disruption-Analysis/aviation_map.html)**

📊 **[Operational Disruption vs Financial Loss – Interactive Scatter Plot](https://enya32.github.io/Global-Aviation-Disruption-Analysis/aviation_scatter.html)**

These visualizations allow users to explore geographic patterns, flight cancellations, and estimated financial losses interactively.

## Project Objectives

- Explore patterns in aviation disruptions across airlines, airports, regions, and dates.
- Examine relationships between cancellations, reroutes, delays, fuel costs, and estimated financial losses.
- Visualize geographic and temporal differences using interactive Plotly charts.
- Engineer features and compare regression models for estimating airline financial losses.
- Interpret model behavior using feature importance and SHAP.

## Datasets

The notebook loads six CSV files:

| File | Analysis area |
| --- | --- |
| `airline_losses.csv` | Airline-level operational and financial impacts |
| `airport_disruptions.csv` | Airport disruption severity and operational effects |
| `airspace_closures.csv` | Airspace restrictions and closure durations |
| `conflict_events.csv` | Geopolitical events and severity |
| `flight_cancellations.csv` | Flight cancellations and temporal trends |
| `flight_reroutes.csv` | Rerouting, delays, and additional fuel costs |

These datasets must be provided locally to rerun the notebook. Their provenance and usage permissions should be documented before public release.

## Tools and Libraries

**Python**, **pandas**, **NumPy**, **Matplotlib**, **Seaborn**, **Plotly**, **scikit-learn**, **XGBoost**, and **SHAP**.

## Analysis Workflow

1. **Data loading and exploration:** Inspect the six datasets and their variables.
2. **Exploratory data analysis:** Compare airline losses, revenue-loss percentages, correlations, and airport disruptions.
3. **Regional analysis:** Explore geographic differences and visualize estimated financial losses on a world map.
4. **Time-series analysis:** Examine daily cancellations, rolling averages, delays, fuel costs, volatility, and disruption peaks.
5. **Feature engineering and modeling:** Predict `estimated_loss_usd` using `cancellations_count`, `reroutes_count`, and `revenue_loss_pct`.
6. **Model interpretation:** Compare feature importance and examine SHAP values.

## Machine Learning Results

The notebook uses an 80/20 train-test split (`random_state=42`) and evaluates three regression models. The following values are rounded from the notebook's reported results:

| Model | R² | Mean Absolute Error (USD) |
| --- | ---: | ---: |
| Linear Regression | 0.447 | $141.77 million |
| **Random Forest** | **0.723** | **$85.79 million** |
| XGBoost | 0.640 | $106.76 million |

**Random Forest** performs best on this particular test split. These results are dataset-specific and are not evidence of performance on new real-world events.

**Modeling caveat:** `revenue_loss_pct` may contain information closely related to the target `estimated_loss_usd`. Its availability at prediction time and potential target leakage should be investigated before claiming practical forecasting performance.

## Visualizations

The notebook includes a global financial-loss choropleth and a bubble chart relating flight cancellations to estimated losses, along with additional exploratory plots.

When exported, the interactive Plotly files can be opened in a browser with hover details, zooming, and legend controls:

- `aviation_map.html` — Global Aviation Financial Losses
- `aviation_scatter.html` — Operational Disruption vs Financial Loss

The PNG versions (`aviation_map.png` and `aviation_scatter.png`) are suitable for sharing on LinkedIn. To share the interactive HTML publicly, publish the files through a static hosting service such as GitHub Pages and add their links here.

## How to Run

1. Clone or download this repository.
2. Install the required Python packages:

   ```bash
   pip install jupyter pandas numpy matplotlib seaborn plotly scikit-learn xgboost shap kaleido
   ```

3. Place the six CSV files in the working directory expected by the notebook.
4. Open the `.ipynb` file in Jupyter Notebook and run its cells in order.

**Note:** Plotly PNG export with recent Kaleido versions also requires a compatible Chrome/Chromium installation. Interactive HTML export does not require Kaleido.

## Limitations and Future Work

- Document dataset sources, collection dates, geographic coverage, and licensing.
- Establish whether the data are observed or simulated and verify the financial-loss estimation methodology.
- Assess target leakage and compare against a baseline using only features available at prediction time.
- Apply cross-validation or temporal validation where appropriate.
- Publish interactive charts through GitHub Pages and link them from this README.

## Project Scope

This repository is intended as a **Data Science portfolio project** demonstrating data exploration, visualization, regression modeling, and model explainability. Its results should be interpreted within the limitations of the underlying datasets.
