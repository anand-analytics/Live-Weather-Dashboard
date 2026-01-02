# 📐 DAX Measures – Live Weather Dashboard (Power BI)

This document contains all **DAX measures** used in the **Real-Time Live Weather Dashboard** project.  
Each measure is documented with its **purpose** and **clean, readable DAX code**, following GitHub and industry best practices.

---

## 🌡️ Temperature Measures

### Current Temperature (°C)
**Purpose:**  
Displays the current temperature with unit formatting for KPI cards.

```DAX
Current_Temp_C =
SUM('Current'[current.temp_c]) & " C"
Forecast_Temp_C =
AVERAGE(Forecast_Day[forecast.forecastday.day.avgtemp_c]) & " C"

