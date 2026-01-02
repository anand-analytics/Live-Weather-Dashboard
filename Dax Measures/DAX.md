## 🌡️ Temperature Measures

### Current Temperature (°C)
**Purpose:**  
Displays the current temperature with unit formatting for KPI cards.

```DAX
Current_Temp_C =
SUM('Current'[current.temp_c]) & " C"
