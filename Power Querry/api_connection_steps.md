# 🌐 Weather API Connection (Power Query)

## Step 1: Get API Key
A free API key was generated from WeatherAPI.com.

## Step 2: Connect via Web Source
Power BI → Get Data → Web  
API URL:


## Step 3: JSON Parsing
- Converted JSON response into tables
- Expanded nested records such as:
  - location
  - current
  - air_quality

## Step 4: Multi-City Strategy
Due to free-tier limitations:
- Separate queries were created per city
- All city queries were appended into a single **Master Table**

