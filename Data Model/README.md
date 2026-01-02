# 🧩 Data Model Overview

This project uses a **star-schema–inspired data model** designed for
performance, scalability, and clarity.

The model separates:
- Fact-like weather measurements
- Dimension-like location metadata
- Forecast granularity (day & hour)
- Centralized DAX measures

This structure ensures:
- Faster query performance
- Cleaner DAX logic
- Easier maintenance and scalability
