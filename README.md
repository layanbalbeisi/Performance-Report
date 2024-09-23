# Performance Report in Power BI

- [Project Overview](#project-overview)
- [Data Source](#data-source)
- [Dashboard](#Dashboard)
- [Tools & Technologies](#tools--technologies)
- [Methodology](#methodology)
- [DAX Measures](#dax-measures)

## 📊 Project Overview
An interactive **Power BI** dashboard designed to monitor key business metrics and KPIs effectively. This dashboard enhances decision-making with real-time insights and user-friendly navigation. It provides a comprehensive view of sales performance, gross profit, and other vital metrics to support strategic planning and operational efficiency.

## 📊 Data Source
- **Fact Table**: Contains transaction-level data such as sales amount, quantity sold, and timestamps.
- **Dimension Tables**: 
  - **Dim_Date**: Provides date attributes for time-based analysis.
  - **Dim_Product**: Contains product details for sales categorization.
  - **Dim_Customer**: Holds customer information to analyze sales trends by demographics.

## 📹 Dashboard Demo
![Performance Report Dashboard](assest/Dashboard/Performance%20Report.png)


Watch the demo of the Performance Report Dashboard [here](https://app.powerbi.com/groups/me/reports/f5e48328-c8ef-4aa3-8ffd-6cc7199c854f?ctid=c7142531-dd68-4a6f-b036-039ec52d6bd1&pbi_source=linkShare&bookmarkGuid=5a9844fe-7c99-4584-a1b1-95fd287d22a3).


## 🛠️ Tools & Technologies
- **Power BI**: Data visualization and business intelligence tool.
- **DAX (Data Analysis Expressions)**: Used for creating custom calculations and measures.

## 📐 Methodology
1. **Data Extraction**: 
   - Imported data from various sources, including Excel files.
2. **Data Transformation**: 
   - Cleaned and structured data to prepare it for analysis within Power BI.
3. **Modeling**: 
   - Created relationships between fact and dimension tables in Power BI.
4. **Visualization**: 
   - Designed interactive dashboards with charts, graphs, and KPIs.

## 📊 DAX Measures
- **Gross Profit Percentage (GP%)**: 
  ```dax
  GP% = DIVIDE([Gross Profit], [Sales])
  ```

- **Previous Year-to-Date (PYTD) Measures**:
    ```dax
    PYTD_GrossProfit = 
    CALCULATE([Gross Profit], SAMEPERIODLASTYEAR(Dim_Date[Date]), Dim_Date[Inpast] = TRUE)
    ```
- **Quantity**:
  ```dax
  PYTD_Quantity = 
  CALCULATE([Quantity], SAMEPERIODLASTYEAR(Dim_Date[Date]), Dim_Date[Inpast] = TRUE)
  ```
- **Sales**:
   ```dax
   PYTD_Sales = 
   CALCULATE([Sales], SAMEPERIODLASTYEAR(Dim_Date[Date]), Dim_Date[Inpast] = TRUE)
    ```
- **PYTD (S_PYTD)**:
   ```dax
    S_PYTD = 
    VAR selected_value = SELECTEDVALUE(Slc_Values[Values])  
   VAR result = 
   SWITCH(
    selected_value,
   "Sales", [PYTD_Sales],
    "Quantity", [PYTD_Quantity],
    "Gross Profit", [PYTD_GrossProfit],
    BLANK()
    ) 
    RETURN result
  ```

- **Year-to-Date (YTD)**
   ```dax
   YTD_GrossProfit = TOTALYTD([Gross Profit], Fact_Sales[Date_Time])
  ```

- **YTD vs PYTD**:
  ```dax
  YTD vs PYTD = [S_YTD] - [S_PYTD]
  ```

## 📝 Conclusion
The Performance Report Dashboard in Power BI serves as a powerful tool for visualizing key business metrics and facilitating data-driven decision-making. By leveraging DAX measures and interactive visualizations, this dashboard provides stakeholders with essential insights into sales performance and profitability. The project showcases my ability to analyze data effectively and create meaningful reports that support strategic business objectives. I look forward to further enhancing my skills in data visualization and analytics as I continue to explore more complex projects.



