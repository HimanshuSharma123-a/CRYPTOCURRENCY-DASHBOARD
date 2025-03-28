# Cryptocurrency Dashboard Analysis

![Cryptocurrency Dashboard](https://github.com/HimanshuSharma123-a/CRYPTOCURRENCY-DASHBOARD/blob/main/CRYPTOCURRENCY%20DASHBOARD.png)

**Dataset Link:** [Add your dataset link here]

##  Overview
This cryptocurrency dashboard provides a detailed analysis of crypto market trends using key financial indicators such as High, Low, Open, Close, Volume, and Market Capitalization over time. It was created using **Power BI**, integrating data cleaning, transformations, and DAX calculations to extract meaningful insights.

##  **Key Features**
- **Time-based Filters**: Select data from specific years (2017-2021).
- **Crypto Selection**: Analyze different cryptocurrencies like Bitcoin, Ethereum, Dogecoin, etc.
- **Price Trends**: Visual comparison of High vs. Low and Open vs. Close prices.
- **Market Capitalization**: Overall market trends visualized over time.
- **KPIs (Key Performance Indicators)**:
  - **Total Trading Volume**: 664.10 Billion
  - **Highest Price**: $690.9 📈
  - **Average Price**: $296.5
  - **Lowest Price**: $35.2 📉
  - **Total Market Cap**: 8.58 Trillion

---

##  **Data Cleaning & Preprocessing**
Before visualization, data was cleaned using **Power Query (M Language)**:
1. **Handling Missing Values**: Removed null values and filled missing prices using the previous day's values.
2. **Date Formatting**: Ensured all dates were in `YYYY-MM-DD` format.
3. **Data Type Correction**: Converted numerical values (Open, Close, High, Low, Volume, MarketCap) to `Decimal`.
4. **Duplicate Removal**: Eliminated duplicate records for accuracy.
5. **Column Standardization**: Renamed columns for clarity.

---

##  **DAX Calculations Used**
Below are the **DAX formulas** used to derive insights:

### **1 Moving Average Calculation** (For Trend Analysis)
```DAX
MovingAvg = 
CALCULATE(
    AVERAGE(Crypto[Close]), 
    DATESINPERIOD(Crypto[Date], MAX(Crypto[Date]), -7, DAY)
)
```
This helps smooth out price fluctuations over a 7-day window.

### **2 Percentage Change Calculation** (Daily Change in Price)
```DAX
% Change = 
VAR PrevClose = LOOKUPVALUE(Crypto[Close], Crypto[Date], EARLIER(Crypto[Date])-1)
RETURN IF(ISBLANK(PrevClose), BLANK(), (Crypto[Close] - PrevClose) / PrevClose * 100)
```
Shows the percentage increase/decrease in price from the previous day.

### **3 Total Market Cap Calculation**
```DAX
TotalMarketCap = SUM(Crypto[Marketcap])
```
Calculates the overall market capitalization of selected cryptocurrencies.

---

## **Insights & Conclusions**
1. **High Market Volatility**: Prices showed sharp rises and falls, indicating high volatility in the crypto market.
2. **Bull Run in Early 2021**: A significant uptrend was observed in Q1 & Q2 of 2021, followed by a decline.
3. **Trading Volume & Price Correlation**: Higher volumes were seen during price surges, indicating increased market activity.
4. **Market Capitalization Fluctuations**: The total crypto market cap followed price trends, peaking around major price hikes.
5. **Bitcoin Dominance**: Bitcoin had a major influence on the overall market trends.

---

## **Tools & Technologies Used**
- **Power BI**: For dashboard creation & visualization.
- **Power Query**: Data Cleaning & Transformation.
- **DAX (Data Analysis Expressions)**: Custom calculations.
- **SQL (Optional)**: Data extraction & preprocessing (if database used).

---

## **Final Thoughts**
This dashboard provides a **professional-level** cryptocurrency analysis by combining **data cleaning, DAX formulas, and interactive visuals**. It helps traders & analysts **identify trends, monitor market cap, and make informed decisions.**

---
**Next Steps:**
- Implement **AI-based forecasting** for price prediction.
- Add **real-time API integration** for live data updates.
- Enhance UI with **advanced visualizations**.
