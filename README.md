# Luigi-Pit_Stop
DSA 210 project analyzing F1 race strategy and weather.

### 1. Project Motivation

I'm a huge Formula 1 fan and I've always been fascinated by the strategy, especially how much the technology and the environment play a role. It feels like a race can be completely decided by a good pit strategy or a sudden change in the weather.

My project idea is to actually test this with data. I want to see how strongly weather conditions (like rain, track temperature, etc.) and tyre strategy (like which compounds were used and when they pitted) correlate with a driver's final race result.

My main question is: **Can we find a clear, data-backed link between strategy, weather, and a driver's ability to "over-perform" (i.e., finish much higher than their starting grid position)?**

### 2. Data I'm Planning to Use

As required by the project guidelines, I'll be using two separate public datasets and merging them:

* **Primary Data Source:** Historical F1 race data. This will include race results, driver starting positions, lap times, and detailed pit stop information (what lap, what tyre compound).
* **Enrichment Data Source:** Historical weather data for F1 race locations. I found a public dataset that has details like air temperature, track temperature, and whether it was raining during the race.

### 3. My Plan for Data Collection

1.  **Get the Race Data:** I'll use the **Ergast Developer API**. It's a free, public API with tons of F1 history in JSON format. I'm planning to write a Python script (using `requests` and `pandas`) to pull the race, lap, and pit stop data for the last several seasons.
2.  **Get the Weather Data:** I'll use a public dataset (like one from Kaggle) that already has historical F1 weather info. This data is usually in a simple CSV file, so I can just download it.
3.  **Combine Them:** The main task will be to clean and merge these two datasets. I'll use the race date and the circuit (e.g., "Silverstone") as the key to match the weather from one dataset to the race results from the other. This will give me one "enriched" master dataset to start my analysis on.
