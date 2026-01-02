/* ===============================
   TEMPERATURE MEASURES
   =============================== */

/* PURPOSE:
   Displays the current temperature with unit formatting
   for KPI cards and summary visuals.
*/
Current_Temp_C =
SUM('Current'[current.temp_c]) & " C"


/* PURPOSE:
   Displays the average forecasted temperature for the
   selected day with unit formatting.
*/
Forecast_Temp_C =
AVERAGE(Forecast_Day[forecast.forecastday.day.avgtemp_c]) & " C"



/* ===============================
   AIR QUALITY INDEX (AQI)
   =============================== */

/* PURPOSE:
   Converts PM10 values into standard AQI status categories
   for health-based interpretation.
*/
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


/* PURPOSE:
   Provides real-time health recommendations based on
   current air quality conditions.
*/
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


/* PURPOSE:
   Assigns hex color codes based on AQI severity to enable
   conditional formatting in visuals.
*/
PM10_Color =
VAR AQI =
    ROUND(SELECTEDVALUE('Current'[current.air_quality.pm10]), 0)
RETURN
SWITCH(
    TRUE(),
    AQI <= 50, "#43d946",      // Good (Green)
    AQI <= 100, "#fff570",     // Moderate (Yellow)
    AQI <= 150, "#ff9800",     // Poor (Orange)
    AQI <= 200, "#d99343",     // Unhealthy
    AQI <= 300, "#ff5b0f",     // Severe
    "#d95243"                  // Hazardous
)



/* ===============================
   DATA REFRESH INDICATOR
   =============================== */

/* PURPOSE:
   Displays the most recent API refresh date to assure
   users that the dashboard is showing live data.
*/
Last_Updated_Date_Curr =
"Last Updated, "
    & FORMAT(
        FIRSTNONBLANK('Current'[current.last_updated], ""),
        "dd mmm"
    )



/* ===============================
   GAUGE & VISUAL HELPER MEASURES
   =============================== */

/* PURPOSE:
   Defines the maximum AQI scale value used for gauge visuals.
*/
Max_Value = 300


/* PURPOSE:
   Calculates the remaining portion of the AQI gauge
   after accounting for current PM10 levels.
*/
Left_Value_PM10 =
[Max_Value] - SUM('Current'[current.air_quality.pm10])


/* PURPOSE:
   Calculates the remaining portion of the rain probability
   gauge to create a stylized visual representation.
*/
Left_Value_Rain =
100 - SUM(Forecast_Day[forecast.forecastday.day.daily_chance_of_rain])



/* ===============================
   WIND METRICS
   =============================== */

/* PURPOSE:
   Displays wind speed with unit formatting for KPI
   and summary visuals.
*/
Wind_Speed =
SUM('Current'[current.wind_kph]) & " KPH"

