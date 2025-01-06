# 🏨 Revenue Insights in Hospitality Domain Dashboard 📊

## 🌟 Introduction 🎯
This project focuses on building an interactive Power BI dashboard to analyze and visualize key metrics in the hospitality industry. The dashboard provides actionable insights into property performance, revenue generation, occupancy trends, and platform efficiency, helping stakeholders optimize operational and financial outcomes.

---

## 🛎️ Background 🏨
The hospitality industry thrives on dynamic metrics like revenue per available room (RevPAR), occupancy rates, and average daily rates (ADR). This project aggregates data from bookings, capacity, and customer behavior to reveal actionable insights. The analysis spans critical areas, such as room utilization, platform contributions, and week-over-week trends.

---

## 🛠️ Tools I Used
- **📊 Power BI**: For creating dynamic and interactive dashboards.
- **📐 DAX**: For custom calculations and advanced analytics.

---

## 🔍 DAX Measures

### 📅 Date and Day Metrics
1. **Week Number (wn)**:
   ```DAX
   wn = WEEKNUM(dim_date[date])
```
2. ### 📊 Total Bookings

```DAX
Total Bookings = COUNT(fact_bookings[booking_id])
```
3. **Occupancy %**:
   ```DAX
   Occupancy % = DIVIDE([Total Successful Bookings], [Total Capacity], 0)
   ```
4. **ADR (Average Daily Rate)**:
   ```DAX
   ADR = DIVIDE([Revenue], [Total Bookings], 0)
   ```
5.  **RevPAR (Revenue Per Available Room)**:
   ```DAX
   RevPAR = DIVIDE([Revenue], [Total Capacity])
```
1. **Revenue WoW Change %**:
   ```DAX
   Revenue WoW change % = 
   VAR selv = IF(HASONEFILTER(dim_date[wn]), SELECTEDVALUE(dim_date[wn]), MAX(dim_date[wn]))
   VAR revcw = CALCULATE([Revenue], dim_date[wn] = selv)
   VAR revpw = CALCULATE([Revenue], FILTER(ALL(dim_date), dim_date[wn] = selv - 1))
   RETURN DIVIDE(revcw - revpw, revpw, 0)
```
2. **Occupancy WoW Change %**:
   ```DAX
   Occupancy WoW change % = 
   VAR selv = IF(HASONEFILTER(dim_date[wn]), SELECTEDVALUE(dim_date[wn]), MAX(dim_date[wn]))
   VAR occ_cw = CALCULATE([Occupancy %], dim_date[wn] = selv)
   VAR occ_pw = CALCULATE([Occupancy %], FILTER(ALL(dim_date), dim_date[wn] = selv - 1))
   RETURN DIVIDE(occ_cw - occ_pw, occ_pw, 0)
```

## 💡 Key Insights

### Property Performance:
- *Atliq City (Mumbai)* achieves the highest revenue of ₹87M with a premium ADR of ₹14,629.
- Occupancy rates peak at **53.4%** for properties like *Atliq Blu (Bangalore)*.

### Platform Analysis:
- Platforms like *Logtrip* and *Journey* lead with the highest realisation rates (~70.6%).

### Weekend vs Weekday Trends:
- Weekends outperform weekdays with higher **RevPAR (₹7,972)** and **Occupancy % (62.6%)**.

### Category Contribution:
- Luxury properties dominate with **61.62%** of total revenue, while business properties contribute **38.38%**.

---

## 📚 What I Learned
- Advanced **Power BI** and **DAX** skills for real-time analytics.
- Insights into hospitality domain metrics like **RevPAR**, **ADR**, and occupancy trends.
- Enhanced ability to translate data into actionable recommendations.

---

## ✅ Conclusion
This dashboard delivers critical insights into revenue streams, operational performance, and market trends in the hospitality sector. By leveraging **DAX** and **Power BI**, it empowers stakeholders to make data-driven decisions for optimizing profitability and efficiency.
