/* =========================================================
   REAL-TIME LIVE WEATHER DASHBOARD – DAX MEASURES
   ========================================================= */

/* PURPOSE: Displays current temperature with unit */
Current_Temp_C =
SUM('Current'[current.temp_c]) & " C"

/* PURPOSE: Displays average forecast temperature */
Forecast_Temp_C =
AVERAGE(Forecast_Day[forecast.forecastday.day.avgtemp_c]) & " C"

/* PURPOSE: Converts PM10 to AQI status text */
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

/* PURPOSE: AQI health recommendation */
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

/* PURPOSE: Conditional formatting color for AQI */
PM10_Color =
VAR AQI =
    ROUND(SELECTEDVALUE('Current'[current.air_quality.pm10]), 0)
RETURN
SWITCH(
    TRUE(),
    AQI <= 50, "#43d946",
    AQI <= 100, "#fff570",
    AQI <= 150, "#ff9800",
    AQI <= 200, "#d99343",
    AQI <= 300, "#ff5b0f",
    "#d95243"
)

/* PURPOSE: Shows last API refresh date */
Last_Updated_Date_Curr =
"Last Updated, "
    & FORMAT(
        FIRSTNONBLANK('Current'[current.last_updated], ""),
        "dd mmm"
    )

/* PURPOSE: Maximum AQI scale */
Max_Value = 300

/* PURPOSE: Remaining AQI gauge value */
Left_Value_PM10 =
[Max_Value] - SUM('Current'[current.air_quality.pm10])

/* PURPOSE: Remaining rain probability gauge value */
Left_Value_Rain =
100 - SUM(Forecast_Day[forecast.forecastday.day.daily_chance_of_rain])

/* PURPOSE: Wind speed with unit */
Wind_Speed =
SUM('Current'[current.wind_kph]) & " KPH"
