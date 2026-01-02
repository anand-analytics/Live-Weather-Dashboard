## 🌡️ Data Refresh Indicator

### Last Updated Timestamp
**Purpose:**  
Displays the most recent API refresh date to assure users the data is live.

```DAX
Last_Updated_Date_Curr =
"Last Updated, "
    & FORMAT(
        FIRSTNONBLANK('Current'[current.last_updated], ""),
        "dd mmm"
    )
```

