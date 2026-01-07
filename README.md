# Final Report: Strategic & Environmental Determinants of F1 Performance

## 1. Motivation
Formula 1 is often viewed as a competition of pure engineering, but race strategy and environmental conditions play a massive role in the outcome. This project aims to quantify the impact of "uncontrollable" variables (weather) and "strategic" variables (pit stops/grid position) on a driver's ability to over-perform their qualifying pace. The central question is: *Can we predict a driver's performance gain solely based on starting position and weather conditions?*

## 2. Data Sources
This project enriches a primary F1 dataset with a secondary weather dataset, meeting the course requirement for data enrichment.
* **Primary Source:** **Ergast Developer API** (via Jolpica Mirror). Contains race results, grid positions, and circuit data for the 2019–2023 seasons.
* **Enrichment Source:** **Kaggle F1 Weather Dataset**. Contains granular weather logs (Rainfall, Air Temp, Track Temp) matched to specific Grand Prix locations.
* **Collection Method:** Data was collected programmatically using Python scripts (`requests` library) and merged using a composite key of `Year` and `Round Number`.

## 3. Methodology
The project followed a standard Data Science pipeline:
1.  **Data Collection:** Automated fetching of 5 years of race data.
2.  **Cleaning & Merging:** Handling missing values (DNFs) and synchronizing race dates with weather logs.
3.  **Feature Engineering:** * Created `PositionDelta` (Grid Position - Finishing Position) as the target variable.
    * Normalized weather metrics (AirTemp, TrackTemp).
4.  **Machine Learning:** Implemented a **Random Forest Regressor** to predict performance changes.

## 4. Findings & Analysis
The analysis yielded statistically significant results regarding what drives performance in F1.

### Key Finding 1: The Dominance of Grid Position
Using a Random Forest model, we achieved an **R2 Score of 0.99**, indicating extremely high predictive accuracy. The Feature Importance analysis revealed that **Grid Position** is the single most critical factor in determining a driver's ability to gain places. This suggests that modern F1 is highly dependent on qualifying performance.

### Key Finding 2: Weather Impact
Contrary to the initial hypothesis that "Rain" would be the biggest disruptor, **Air Temperature** proved to be the second most important feature, outweighing Rainfall and Humidity. This implies that thermal management (engine cooling, tyre temperatures) may have a more consistent impact on race pace than sporadic rain events.

### Key Finding 3: Hypothesis Test
A T-Test confirmed (p < 0.05) that drivers starting in the "Top 3" positions have a significantly different `PositionDelta` compared to the midfield. Top drivers rarely gain positions (because they are already at the front), whereas mid-field drivers have higher variance.

## 5. Limitations & Future Work
* **Limitations:** The model's extremely high accuracy (0.99) suggests "Grid Position" might be too strong of a predictor, potentially overshadowing subtle strategy variables like tyre compound choices.
* **Future Work:** A future iteration of this project would remove "Grid Position" from the features to force the model to learn purely from weather and pit stop strategy.

## 6. How to Reproduce
1.  Clone this repository.
2.  Install dependencies: `pip install -r requirements.txt`
3.  Run the analysis notebook: `final_project_analysis.ipynb`
