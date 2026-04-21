# 🇺🇦 Analysis of Regional Indicators in Ukraine

This project is an interactive dashboard created in Power BI to visualize and analyze data by region in Ukraine.

## 📊 Dashboard Interface
<img width="962" height="540" alt="dashboard" src="https://github.com/user-attachments/assets/d948df1e-5fda-491c-8090-df9a757639c1](https://github.com/alinasemenyshyn/UkraineMapAnalytic/blob/main/zoom_map.MP4)" />

## 🎯 Project Goal
To create a user-friendly tool for quickly comparing metrics across different regions of Ukraine using an interactive shape map and a detailed table.

## 🛠 Tech Stack
* **Tool:** Power BI Desktop
* **Data Processing:** Power Query (data cleaning and formatting)
* **Calculations:** DAX (creating custom measures for dynamic captions)
* **Visualization:** Shape Map, Matrix/Table with custom cross-filtering.

## 🤖 DAX SCRIPT
* For card with visualization number of citizen in city I used:
* `CityName lbl = 
VAR CurrentRegion = "CityName"
VAR CurrentValue = FORMAT(CALCULATE(SUM(region_tbl[Value]), region_tbl[Region] = CurrentRegion), "#,##0")
VAR RegionExists = COUNTROWS(FILTER(region_tbl, region_tbl[Region] = CurrentRegion)) > 0
RETURN
    IF(RegionExists, IF(ISBLANK(CurrentValue) || CurrentValue = "0", CurrentRegion & ": 0", CurrentRegion & ": " & CurrentValue), CurrentRegion & ": No Data")
  `

## 💡 Key Dashboard Features
1. **Interactive Filtering (Cross-filtering):** When you click on any area on the map, the table on the right automatically filters, displaying data specific only to the selected region.
2. **Dynamic labels (DAX):** Custom value display on the map is configured to avoid cluttering the interface with unnecessary text (for example, logic to hide empty values is implemented).
3. **Color Formatting (Conditional Formatting):** The color intensity on the map and in the table automatically adjusts based on the indicator’s value (from light to dark red), allowing you to instantly identify leaders and laggards.

## 📁 File Structure
* `map.pbix` - the original Power BI project file.
* `data.csv` - the source dataset.
* `Ukraine-regions.json` - the Ukraine map download.
