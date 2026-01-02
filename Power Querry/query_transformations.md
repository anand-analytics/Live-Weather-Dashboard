  # 🧹 Power Query Transformations

Key transformations applied:

- Removed duplicate rows to retain latest weather update per city
- Changed data types for numeric fields (Temperature, Wind, PM10)
- Renamed technical API fields to user-friendly names
- Filtered null or irrelevant columns
- Created separate tables for:
  - Current data
  - Forecast (Day & Hour)
