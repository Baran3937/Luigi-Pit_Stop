# Luigi-Pit_Stop
# Project: Strategic & Environmental Determinants of F1 Performance

## 1. Motivation
While Formula 1 is often viewed as a competition of engineering, race strategy and environmental conditions significantly influence outcomes. This project aims to quantify the impact of "uncontrollable" variables (weather) and "strategic" variables (pit stops, tyre degradation) on a driver's ability to over-perform their qualifying pace. The goal is to determine if statistical dependencies exist between specific weather patterns and the volatility of race results.

## 2. Data Sources
This project follows the course requirement to enrich a public dataset with a secondary data source.

* **Primary Source (Race Data):** * **Source:** Ergast Developer API (http://ergast.com/mrd/)
    * **Content:** Historical race results, qualifying data, lap times, pit stop timing, and circuit information from the 2018–2023 seasons.
* **Enrichment Source (Weather Data):** * **Source:** Kaggle F1 Weather Archive
    * **Content:** Precipitation levels, air temperature, and track temperature corresponding to the specific dates and geolocation of each Grand Prix.

## 3. Data Collection & Processing Plan
1.  **Ingestion:** Python scripts utilizing the `requests` library will iteratively fetch race data from the Ergast API and store it in pandas DataFrames.
2.  **Cleaning:** The pipeline will handle null values (DNFs) and parse time-delta strings (e.g., "+12.3s") into floating-point seconds.
3.  **Enrichment:** Weather data will be merged with race data using a composite key of `RaceID`, `Date`, and `CircuitLocation`.
4.  **Feature Engineering:** * `PositionDelta`: Calculated as `Grid Position - Finishing Position` to measure performance gain/loss.
    * `StrategyIndex`: A derived metric representing the number of pit stops relative to the race average.

## 4. Planned Analysis & Methodology
To analyze the correlation between strategy/weather and race outcomes, the following statistical and machine learning methods will be applied:

### A. Exploratory Data Analysis (EDA)
* **Distribution Analysis:** Histograms of `PositionDelta` to understand the variance of overtaking in modern F1.
* **Correlation Heatmaps:** Analyzing the relationship between Track Temperature, Tyre Compound choice, and Lap Time consistency.

### B. Hypothesis Testing (Target: Nov 28)
* **Test 1 (T-Test):** * *Null Hypothesis ($H_0$):* There is no significant difference in `PositionDelta` between drivers who follow the average pit strategy versus those who deviate (make extra/fewer stops).
* **Test 2 (Chi-Square Test of Independence):**
    * *Null Hypothesis ($H_0$):* The frequency of "Safety Car" interventions is independent of "Wet" weather declarations.

### C. Machine Learning (Target: Jan 02)
* **Predictive Modeling:** Training a **Random Forest Regressor** to predict a driver's final `PositionDelta` based on features: `GridPosition`, `Precipitation`, `TrackTemp`, and `ConstructorTier`.

## 5. Timeline
* **Oct 31:** Project Proposal & Git Setup (Completed)
* **Nov 28:** Data Collection, EDA, and Hypothesis Testing (In Progress)
* **Jan 02:** Machine Learning Model Implementation
* **Jan 09:** Final Report & Submission
