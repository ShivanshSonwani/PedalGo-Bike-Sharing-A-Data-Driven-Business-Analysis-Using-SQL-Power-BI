# PedalGo Bike Share Dashboard

### Dashboard Link: [Add your Power BI dashboard link here]

## Problem Statement

PedalGo, a bike-sharing company, requires a dashboard to analyze key performance metrics and provide data-driven insights for decision-making. The goal is to evaluate hourly revenue trends, seasonal revenue patterns, and rider demographics while ensuring an intuitive dashboard design that aligns with company branding.

**Steps Followed:**

**Step 1**: Set up a SQL database using SQL Server Management Studio (SSMS) for data analysis.

**Step 2**: Integrated three tables: bike_share_yr_0, bike_share_yr_1, and cost_table.

**Step 3**: Used SQL to consolidate both yearly bike share data into a common table using a Common Table Expression (CTE).

**Step 4**: Joined the consolidated data with cost information to calculate revenue and profits.

**Step 5**: Exported the processed SQL data into Power BI for dashboard visualization.

**Step 6**: Created visualizations to represent seasonal revenue, hourly demand, rider demographics, and profit trends.

**Step 7**: Analyzed pricing impact and recommended future pricing strategies based on findings.

## Data Source & Setup

A SQL database was created in SQL Server Management Studio (SSMS) containing three tables:
![Image](https://github.com/user-attachments/assets/33aae4ec-7672-40c4-b16b-21e64f95a6cc)


1. **bike_share_yr_0** – Contains bike-sharing data for the previous year.
2. **bike_share_yr_1** – Contains bike-sharing data for the current year.
3. **cost_table** – Includes the year, price per ride, and cost of goods sold (COGS).

### SQL Query Used:

```sql
WITH cte AS (
    SELECT * FROM bike_share_yr_0
    UNION ALL 
    SELECT * FROM bike_share_yr_1
)

SELECT 
    dteday, season, a.yr, weekday, hr, rider_type, riders, price, COGS,
    riders * price AS revenue,
    riders * price - COGS AS profits
FROM cte a 
LEFT JOIN cost_table b
ON a.yr = b.yr;
```

![Image](https://github.com/user-attachments/assets/76fe7dbe-ee29-488b-acdc-695da417b247)



**Explanation:**
- A **Common Table Expression (CTE)** was used to merge both years' data.
- The final query calculates **hourly revenue and profit** by multiplying the number of riders with the price per ride and subtracting COGS.
- The dataset was then exported to Power BI for visualization.

## Steps Followed in Power BI

1. **Data Import:** Exported SQL Server data into Power BI.
2. **Data Cleaning & Transformation:** Checked for missing values and ensured data consistency.
3. **Calculated Measures:** Created new measures to analyze revenue, profit trends, and rider demographics.
4. **Visualization:** Designed interactive reports using slicers and charts for easier analysis.
5. **Publishing:** Published the final dashboard to Power BI Service for access and sharing.


## Key Insights

- **Price Increase:**
  - Last year's price: **$3.99** → This year's price: **$4.99** (25% increase).
- **Rider Growth:**
  - Last year: **1,243,103 riders**
  - This year: **2,049,576 riders**
  - Growth: **64% increase in ridership**
- **Price Elasticity of Demand:**
  - **2.56**, indicating strong demand despite the price hike.
- **Seasonal Trends:**
  - Peak usage in summer and weekends.
  - Business commuters contribute significantly to weekday ridership.
  
 - **Rider Demographics:**
   - Regular riders accounted for the majority of trips, indicating strong customer retention.

## Recommendations

1. **Gradual Price Increase:** Given the strong demand elasticity, a **10-15% increase** could be feasible without losing riders.
   - Potential price points: **$5.49 (10% increase) or $5.74 (15% increase).**
2. **Market Research:** Conduct customer surveys and competitor analysis before finalizing the price increase.
3. **Tiered Pricing Model:**
   - Different pricing for **casual riders vs. subscribers** to maximize retention.
4. **Real-Time Monitoring:**
   - Continuously track demand changes post-price adjustment to avoid negative impact.

## Next Steps

- **Further Refinements:** Implement dynamic pricing based on seasonality.
- **Customer Sentiment Analysis:** Leverage surveys and reviews to understand rider behavior.
- **Expansion Analysis:** Evaluate new locations based on ridership trends.



## Dashboard Screenshots

![Image](https://github.com/user-attachments/assets/fdf52766-5274-4612-8352-ee34fd2b10f2)

![Image](https://github.com/user-attachments/assets/e54a92ca-1fb6-4035-8fc7-cfa3aba6786e)

![Image](https://github.com/user-attachments/assets/fc7394e2-dded-411f-8028-15886e549ebe)

---

###  Conclusion

This Power BI dashboard provides a comprehensive view of **PedalGo’s revenue trends, seasonal variations, and customer demographics**. The insights gained will help in **strategic pricing decisions and business growth** while maintaining customer satisfaction.
