# Coffee-Sales-Performance-Dashboard---Product-and-Market-Analysis-Excel-

## 1. Executive Summary

This project analyzes historical coffee sales data to understand **revenue trends over time**, **performance by coffee variety**, and **sales distribution across countries**. Using an Excel-based dashboard, the analysis highlights top-performing products, seasonal volatility, and market concentration. The results help business stakeholders quickly identify where revenue is coming from and where growth opportunities exist.

---

## 2. Business Problem

**2.1 The Problem**

Every business needs an easy-to-read view of sales performance across products and regions. Decision-makers in the coffee industry specifically need answers to:

- Which coffee types drive the most revenue over time?
- How stable or volatile are monthly sales?
- Which countries contribute the most to total sales?
- Where should the business focus its commercial and marketing efforts?

**2.2 The Solution**

I built an **interactive Excel dashboard** that consolidates raw transactional data into clear visual summaries:

- **Time-series analysis** of sales by coffee type
- **Country-level revenue comparison**
- Clean, formatted charts designed for executive consumption

The dashboard allows stakeholders to quickly spot trends, compare products, and assess market concentration without manually reviewing spreadsheets.

---

## 3. Methodology

### **3.1 Data Cleaning and Preparation**

The dataset used for this project originates from the **RawCoffeeOrders** Excel workbook (available on GitHub). Before analysis, the raw data required cleaning and enrichment to ensure consistency, accuracy, and usability for reporting. All preparation steps were performed directly in **Excel**.

First, column names were standardized across tables to improve readability and maintain consistency. Data types were also corrected to ensure proper analysis, with dates formatted as Date fields and all pricing and sales-related fields formatted as currency.

During this process, several key fields in the **Orders** table were initially unpopulated. These included: Customer Name, Email, Country, Coffee Type, Roast Type, Size, Unit Price, Sales.

To populate these missing fields, lookup-based data enrichment techniques were applied. Specifically, **XLOOKUP()** and **INDEX()** functions were used depending on the lookup logic and key structure.

**XLOOKUP() Example**

XLOOKUP() was used to retrieve customer-related attributes (such as **Email, Customer Name, and Country**) by matching the **Customer ID between the Orders and Customers tables**. In some cases, IF() logic was incorporated to handle conditional mapping and ensure clean, readable outputs.

![image.png](attachment:d76350a4-78ec-4c44-9ec5-39df8fef3697:image.png)

**Index Matching Example** 
The INDEX() function was used to populate product-related attributes by matching **Product ID between the Orders and Products tables**. This same approach was applied consistently to populate **Coffee Type, Roast Type, Size, Unit Price, and Sales fields**.

![image.png](attachment:d3d67b28-5025-4700-a724-65171a4c06f6:5d190f0d-bfa8-45d5-a4aa-d2f49545f415.png)

Similarly, the Sales Column was calcuated as a simple formula of:

Sales =Unit Price * Quantity

The Loyalty Card column was populated using XLOOKUP between orders and customers tables. And, the columns Coffee Type Name and Roast Type Name were used for better understanding of column values during visualization by using the IF() function.

### **3.2 Entity Relationship Diagram**

![image.png](attachment:c09c8aa4-a089-4f63-9ebb-e3c41839a3c2:image.png)

This ERD represents a **star-schema–style sales data model** centered around an **Orders** fact table, with **Products** and **Customers** as dimension tables. It was built using Power BI.

- **Orders** captures transactional sales data
- **Products** provides product attributes (coffee type, size, price, roast)
- **Customers** provides customer attributes (location, loyalty status, contact info)

The relationships in the model include: 

- **Products  ➔ Orders**
    - This is a **1 to many relationship**, which means that one product can appear in many order, but each order line references one product.
    - The relationship key is **Products.ProductID ➔ Orders.ProductID**
- **Customers ➔ Orders**
    - This is a **1 to many relationship** as well, which means that one customer can place many orders but each orders belong to one customer.
    - The relationship key is **Customers.Customer ID ➔ Orders.Customer ID**

### 3.3 Building the Pivot Tables and Dashboard Components

After cleaning and enriching the Orders table, Pivot Tables were used to aggregate transactional data and support dashboard visualizations. Each Pivot Table was built to answer a specific business question.

- **Total Sales Over Time:**
    
    A Pivot Table grouped Order Date by month and year, with Sales aggregated by Coffee Type Name. This was visualized as a line chart to analyze trends and seasonality.
    
    ![image.png](attachment:e0fbf510-1b35-4e32-aa81-b69211ef03ea:image.png)
    
- **Sales by Country:**
    
    A Pivot Table aggregated total Sales by Country and was visualized as a horizontal bar chart to compare market performance. 
    
    ![image.png](attachment:b3bcc2a6-0faa-4a67-b126-2b88fedddeb4:image.png)
    
- **Top Five Customers by Sales:**
    
    A Pivot Table aggregated total Sales by Customer and was visualized as a horizontal bar chart to compare market performance. Then, the filter of Top 5 Sales value was used to visualize the Top 5 customers.
    
    ![image.png](attachment:ab4e92a1-048c-4a92-9a26-2759bf448323:image.png)
    

To improve usability and interactivity, **slicers** and a **timeline** were added:

- **Slicers** allow users to filter the dashboard by attributes such as coffee type or country, enabling focused analysis on specific segments.

![image.png](attachment:55ed5bc4-6af4-4d53-bc28-dba5d184eab6:image.png)

- The **timeline** enables users to view sales for selected time periods (e.g., specific months or years), making it easy to isolate trends within a given date range.

![image.png](attachment:4959848a-2982-40cf-9d7a-2d4ed1250adf:image.png)

The final dashboard then combines all components into a clean, executive-friendly layout with consistent formatting, clear labels, and currency formatting, allowing stakeholders to explore different sections of the data without modifying the underlying tables.

![image.png](attachment:70970a93-defa-416c-8d91-4c1aa3f71de2:image.png)

### 3.4 Skills Used

- **Excel:** XLOOKUP, Index Matching, IF Functions, Pivot Tables and Pivot Charts, Time-series aggregation, Data cleaning and formatting, Dashboard design and layout optimization
- **Data Visualization:** Line chart for trend analysis, Bar charts for categorical comparison, and Axis scaling, labeling, and formatting for clarity

---

## 4. Results

- The analysis shows that total sales are heavily concentrated in a few countries, with one primary market contributing a disproportionate share of overall revenue. Secondary markets contribute meaningfully but at a much lower level.
- Sales trends vary significantly across coffee types. Certain varieties consistently outperform others over time, while some products show sporadic or lower demand. This suggests that product mix plays a major role in revenue stability.
- The time-series analysis reveals noticeable fluctuations in monthly sales rather than steady linear growth. This indicates the presence of **seasonality or demand cycles**, which can be leveraged for planning promotions, inventory, and staffing.

---

## 5. Business Recommendations

**1. Double Down on Top-Performing Products**

Focus marketing, inventory, and supply chain planning around the coffee types that consistently drive the highest sales. Lower-performing products should be evaluated for repositioning, bundling, or phased reduction.

**2. Mitigate Market Concentration Risk**

Given the heavy reliance on one or two countries, the business should explore targeted growth strategies in secondary markets, such as localized promotions or pricing adjustments.

**3. Align Promotions with Seasonal Trends**

Use observed sales peaks and troughs to time promotions and campaigns more effectively. Aligning inventory and staffing with high-demand periods can improve efficiency and reduce stockouts or overstocking.

**4. Use the Dashboard as a Decision Support Tool**

Encourage business users to actively use slicers and timelines to explore specific segments and time periods. This supports faster decision-making without requiring ad-hoc analysis requests.

---

## 6. Limitations and Next Steps

- The analysis is limited to historical sales data and does not include customer behavior metrics such as how often cutomers place orders or whether they are repeat buyers vs. new buyers.
- Future work could include profitability analysis, and customer segmentation (new buyers vs. repeat buyers.
