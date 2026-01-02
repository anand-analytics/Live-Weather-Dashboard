# 📊 Data Model Explanation

## 1. Master Table
Acts as the staging layer for all city-level API calls.
Used to consolidate multiple city queries into a single dataset.

## 2. Location Table
Contains unique geographic attributes:
- City
- Region
- Country

Functions as a **dimension table** for slicing and filtering.

## 3. Current Data Table
Stores real-time weather metrics:
- Temperature
- Wind Speed
- Visibility
- Air Quality (PM10)

This table behaves as the **fact table** for current conditions.

## 4. Forecast Day Table
Contains daily forecast metrics:
- Avg temperature
- Chance of rain
- Weather conditions

Used for trend and future analysis.

## 5. Forecast Hour Table
Stores hourly forecast details.
Enables granular time-based insights.

## 6. Measures Table (_Measures)
Dedicated table used only for DAX measures.
Keeps the model organized and improves readability.
