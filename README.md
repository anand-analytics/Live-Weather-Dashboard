# 🌦️ Real-Time Live Weather Dashboard (Power BI)

## 📌 Project Overview
This project is an **end-to-end Power BI dashboard** built on a **live API-driven architecture**, moving beyond traditional static CSV-based reporting.  
The dashboard delivers **real-time weather analytics**, **multi-city comparisons**, and **environmental health monitoring** through an interactive and visually modern interface.

The primary objective is to demonstrate **professional data analyst skills** in:
- API integration
- JSON data transformation
- Advanced data modeling
- DAX-driven insights
- UX-focused dashboard design

---

## 🚀 Why This Project?
Most Power BI projects rely on **historical, static datasets**.  
This project stands out by integrating a **live Weather API**, handling:
- Real-time JSON data streams
- API call limits (up to 1 million calls/month)
- Scheduled refresh using Power BI Service

As a result, the dashboard always reflects **current weather conditions**, making it closer to real-world BI solutions used in production environments.

---

## ✨ Key Features

### 🌐 Live API Integration
- Direct connection to **:contentReference[oaicite:0]{index=0}**
- JSON-based data ingestion via Power Query
- Auto-refresh support through Power BI Service

---

### 🏙️ Multi-City Master Table
- Separate city-level API queries (Hyderabad, Mumbai, Noida, etc.)
- Appended into a single **Master Table**
- Efficient workaround for free-tier API limitations

---

### 🎨 Modern UI / UX
- Dark-themed professional dashboard
- Custom **Figma-designed backgrounds**
- Utilizes **Power BI New Card Visuals** for a sleek, modern appearance

---

### 🌫️ Air Quality Index (AQI) Monitoring
- Real-time pollutant tracking (PM10, CO)
- Dynamic AQI status indicators:
  - 🟢 Good
  - 🟡 Moderate
  - 🔴 High Alert
- Color-coded alerts based on health risk thresholds

---

### 📈 Predictive Weather Forecasts
- 7-day weather trend analysis
- Hourly temperature variations
- Forecast-driven decision insights

---

### 🌅 Astronomical Insights
- Automated Sunrise & Sunset tracking
- Daily updates via API refresh

---

## 🏗️ Data Architecture & Modeling
The project follows a **star-schema-inspired design** to ensure scalability and performance:

1. **Master Table**  
   Central staging table combining all city API responses

2. **Location Table**  
   City, region, and country metadata

3. **Current Data Table**  
   Live metrics such as temperature, wind speed, visibility, and pressure

4. **Forecast Day / Hour Tables**  
   Granular forecast data for trend and time-series analysis

5. **Measures Table (`_Measures`)**  
   Dedicated table for all DAX calculations to maintain model clarity

---

## 🛠️ Technical Workflow

### 1️⃣ Data Acquisition (Power Query)
- Connected using **Get Data → Web** with API URL and private token
- JSON data parsing and normalization
- Weather icons required URL correction:
  - Used **Replace Values** to prefix `http:` so icons render correctly
- Removed duplicate current readings to ensure **latest city-level data**

---

### 2️⃣ DAX & Measures
- 🌡️ Dynamic temperature labels with `°C`
- 🌫️ AQI conditional logic using `SWITCH / IF`
- 🌧️ Rain probability visuals using calculated “Left Value” logic  
  *(100 – Chance of Rain)*

---

### 3️⃣ Visualization Design
- 📉 Line charts for 7-day weather trends
- 📊 KPI icons for Wind, Humidity, Pressure
- 🎛️ Custom slicer panel for instant city switching

---

## 🔧 Setup Instructions

1. **Get API Key**  
   Sign up at **WeatherAPI.com** to obtain a free API token

2. **Update Source**  
   In Power BI Desktop → Transform Data  
   Replace the API key in the Source step of each city query

3. **Refresh Data**  
   Click **Refresh** to fetch live weather data

4. **Publish & Schedule**  
   Publish the `.pbix` file to Power BI Service  
   Configure scheduled refresh for real-time updates

---

## 💡 AQI Monitoring – Simple Analogy
Think of the **AQI Status Indicator** as a **traffic signal for health**:

- 🟢 Green → Safe to go outside  
- 🟡 Yellow → Moderate risk, caution advised  
- 🔴 Red → High alert, unhealthy air  

Just like traffic lights prevent accidents, AQI alerts help users make **health-aware decisions**.

---

## 📌 Acknowledgments
- Dashboard concept inspired by **The Developer (YouTube)**
- Weather data powered by **Weather API**
