## 🌡️ Temperature Measures

### Current Temperature (°C)
**Purpose:**  
Displays the current temperature with unit formatting for KPI cards.

```DAX
Current_Temp_C =
SUM('Current'[current.temp_c]) & " C"
```
### Forecast Average Temperature (°C)
**Purpose:**  
Shows the average forecasted temperature for the day.
```DAX
Forecast_Temp_C =
AVERAGE(Forecast_Day[forecast.forecastday.day.avgtemp_c]) & " C"



