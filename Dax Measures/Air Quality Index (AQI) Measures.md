## 🌫️ Air Quality Index (AQI) Measures

### AQI Status Text
**Purpose:**  
Classifies air quality into standard health categories based on PM10 levels.

```DAX
AQI_Status =
VAR AQI =
    ROUND(SELECTEDVALUE('Current'[current.air_quality.pm10]), 0)
RETURN
SWITCH(
    TRUE(),
    AQI <= 50, "Good",
    AQI <= 100, "Moderate",
    AQI <= 150, "Unhealthy for Sensitive",
    AQI <= 200, "Unhealthy",
    AQI <= 300, "Very Unhealthy",
    "Hazardous"
)
```
### AQI Health Suggestion
**Purpose:**  
Provides real-time health recommendations based on current air quality.
```DAX
AQI_Suggestion =
VAR AQI =
    SELECTEDVALUE('Current'[current.air_quality.pm10])
RETURN
SWITCH(
    TRUE(),
    AQI <= 50, "Air is clean and healthy",
    AQI <= 100, "Acceptable air quality, stay active",
    AQI <= 150, "Sensitive groups should reduce outdoor time",
    AQI <= 200, "Limit prolonged outdoor exertion",
    AQI <= 300, "Avoid outdoor activity if possible",
    "Stay indoors, wear mask if outside"
)
```


