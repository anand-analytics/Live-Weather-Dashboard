## 🌡️ Gauge & Visual Helper Measures

### Maximum AQI Value
**Purpose:**  
Defines the upper limit for AQI-based gauge visuals.

```DAX
Max_Value = 300

```
### PM10 Gauge – Left Value
**Purpose:**  
Calculates the remaining portion of the AQI gauge.
```DAX
Left_Value_PM10 =
[Max_Value] - SUM('Current'[current.air_quality.pm10])
```
### Rain Probability – Left Value
**Purpose:**  
Creates a stylized gauge for rain probability.
```DAX
Left_Value_Rain =
100 - SUM(Forecast_Day[forecast.forecastday.day.daily_chance_of_rain])

```

