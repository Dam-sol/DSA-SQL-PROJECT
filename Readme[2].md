# Case Study 2: Kultra Mega Stores (KMS) Inventory Analysis

### Project Overview

This analysis explores the Kultra Mega Stores order dataset (2009-2012) to derive insights into sales performance, customer segments, regional profitability, and operational efficiency. The primary tool used for data manipulation and aggregation was **SQL**, with findings presented to guide strategic business decisions.

### Tools Used

- **Database:** SQLite
- **Analysis Tool:** DB Browser for SQLite
- **Reporting & Version Control:** GitHub

---

## Analysis, Findings, and Insights

This section details the answers to the business questions from the case scenarios. Each question is addressed with the corresponding SQL query and a brief insight based on the result.

### Case Scenario I

#### 1. Which product category had the highest sales?
- **SQL Query:**
  ```sql
  SELECT
      "Product Category",
      SUM("Sales") AS TotalSales
  FROM
      Orders
  GROUP BY
      "Product Category"
  ORDER BY
      TotalSales DESC
  LIMIT 1;
  ```
- **Result:**
  | Product Category | TotalSales |
  |-------------------|-----------------|
  | Technology | 5984248.182 |
From the result we can see that Technology has the highest sales.

#### 2. What are the Top 3 and Bottom 3 regions in terms of sales?

- **SQL Query:**

  ```sql

  WITH TopRegions AS (
      SELECT
          "Region",
          SUM("Sales") AS TotalSales
      FROM
          Orders
      GROUP BY
          "Region"
      ORDER BY
          TotalSales DESC
      LIMIT 3
  ),
  BottomRegions AS (
      SELECT
          "Region",
          SUM("Sales") AS TotalSales
      FROM
          Orders
      GROUP BY
          "Region"
      ORDER BY
          TotalSales ASC
      LIMIT 3
  )
  SELECT "Region", "TotalSales" FROM TopRegions
  UNION ALL
  SELECT "Region", "TotalSales" FROM BottomRegions;
  ```

- **Result:**
  | Region | TotalSales |
  |-----------------------|--------------|
  | West | 3597549.2755 |
  | Ontario | 3063212.4795 |
  | Prarie | 2837304.6015 |
  | Nunavut | 116376.4835 |
  | Northwest Territories | 800847.3295 |
  | Yukon | 975867.371 |
The Top 3 are West, Ontario and Prarie, while the Bottom 3 are Nunavut, Northwest and Yukon. 

#### 3. What were the total sales of appliances in Ontario?

- **SQL Query:**
  ```sql
  SELECT
  SUM("Sales") AS TotalAppliancesSalesInOntario
  FROM
      Orders
  WHERE
      "Product Category" = 'Appliances' AND "Province" = 'Ontario';
  ```
- **Result:**
  |TotalAppliancesSalesInOntario|
  |-----------------------|
  | NULL |
Ontario did not make any sales.

#### 4. Advise the management of KMS on what to do to increase the revenue from the bottom 10 customers.

- **SQL Query:**
  ```sql
  SELECT
      "Customer Name",
      SUM("Sales") AS TotalSales,
      COUNT(DISTINCT "Order ID") AS NumberOfOrders
  FROM
      Orders
  GROUP BY
      "Customer Name"
  ORDER BY
      TotalSales ASC
  LIMIT 10;
  ```
- **Result:**
  | Customer Name | TotalSales | NumberOfOrders |
  | --- | --- | --- |
  | Jeremy Farry | 85.72 | 2 |
  | Natalie DeCherney | 125.9 | 1 |
  | Nicole Fjeld | 153.03 | 2 |
  | Katrina Edelman | 180.76 | 2 |
  | Dorothy Dickinson | 198.08 | 1 |
  | Christine Kargatis | 293.22 | 2 |
  | Eric Murdock | 343.328 | 4 |
  | Chris McAfee | 350.18 | 2 |
  | Rick Huthwaite | 415.82 | 2 |
  | Mark Hamilton | 450.99 | 1 |
**To increase revenue from bottom 10 customers:**  

1. **Engage low-frequency buyers** with personalized offers and win-back campaigns to boost repeat purchases.  
2. **Upsell/cross-sell** based on their order history with bundles, discounts, or product recommendations.  
3. **Improve loyalty** through targeted incentives, account managers, or subscription options to increase order value and frequency.

#### 5. KMS incurred the most shipping cost using which shipping method?

- **SQL Query:**
  ```sql
  SELECT
      "Ship Mode",
      SUM("Shipping Cost") AS TotalShippingCost
  FROM
      Orders
  GROUP BY
      "Ship Mode"
  ORDER BY
      TotalShippingCost DESC
  LIMIT 1;
  ```
- **Result:**
  | Ship Mode | TotalShippingCost |
  | --- | --- |
  | Delivery Truck | 51971.94 |
KMS incurred the most shipping cost using the delivery truck method costing about 51971.94.

#### 6. Who are the most valuable customers, and what products or services do they typically purchase?

This is a two-step question. First, find the customers. Then, analyze one of them.

- **SQL Query:**
  ```sql
  SELECT
      "Customer Name",
      SUM("Sales") AS TotalSales
  FROM
      Orders
  GROUP BY
      "Customer Name"
  ORDER BY
      TotalSales DESC
  LIMIT 5;
  ```
- **Result:**
  | Customer Name | TotalSales |
  | --- | --- |
  | Emily Phan | 117124.438 |
  | Deborah Brumfield | 97433.1355 |
  | Roy Skaria | 92542.153 |
  | Sylvia Foulston | 88875.7575 |
  | Grant Carroll | 88417.0025 |

- **SQL Query:**
  ```sql
  SELECT
      "Product Category",
      COUNT(*) as PurchaseFrequency
  FROM
      Orders
  WHERE
      "Customer Name" = 'Emily Phan'
  GROUP BY
      "Product Category"
  ORDER BY
      PurchaseFrequency DESC;
  ```
- **Result:**
  | Product Category | PurchaseFrequency |
  | --- | --- |
  | Office Supplies | 5 |
  | Technology | 4 |
  | Furniture | 1 |
The most valuable customers are Emily Phan, Deborah Brumfield, Roy Skaria, Sylvia Foulston, Grant Carrol and they usually purchase Office Supplies, Technology services and Furniture.

#### 7. Which small business customer had the highest sales?

- **SQL Query:**
  ```sql
  SELECT
      "Customer Name",
      SUM("Sales") AS TotalSales
  FROM
      Orders
  WHERE
      "Customer Segment" = 'Small Business'
  GROUP BY
      "Customer Name"
  ORDER BY
      TotalSales DESC
  LIMIT 1;
  ```
- **Result:**
  | Customer Name | TotalSales |
  | --- | --- |
  | Dennis Kane | 75967.5905 |
Dennis Kane had the highest sales of about 75967.5905.

#### 8. Which Corporate Customer placed the most number of orders in 2009 – 2012?

- **SQL Query:**
  ```sql
  SELECT
      "Customer Name",
      COUNT(DISTINCT "Order ID") AS NumberOfOrders
  FROM
      Orders
  WHERE
      "Customer Segment" = 'Corporate'
  GROUP BY
      "Customer Name"
  ORDER BY
      NumberOfOrders DESC
  LIMIT 1;
  ```
- **Result:**
  | Customer Name | NumberOfOrders |
  | --- | --- |
  | Roy Skaria | 18 |
Roy Skaria placed the most number of orders in 2009 - 2012

#### 9. Which consumer customer was the most profitable one?

- **SQL Query:**
  ```sql
  SELECT
      "Customer Name",
      SUM("Profit") AS TotalProfit
  FROM
      Orders
  WHERE
      "Customer Segment" = 'Consumer'
  GROUP BY
      "Customer Name"
  ORDER BY
      TotalProfit DESC
  LIMIT 1;
  ```
- **Result:**
  | Customer Name | TotalProfit |
  | --- | --- |
  | Emily Phan | 34005.44 |
The most profitable consumer customer is Emily Phan.

#### 10. Which customer returned items, and what segment do they belong to?

- **SQL Query:**
  ```sql
  SELECT
      "Customer Name",
      "Customer Segment",
      SUM("Profit") AS NetProfit
  FROM
      Orders
  GROUP BY
      "Customer Name", "Customer Segment"
  HAVING
      NetProfit < 0
  ORDER BY
      NetProfit ASC;
  ```
- **Result:**
  Customer Name | Customer Segment | NetProfit
  --- | --- | ---
  Julia West | Home Office | -13057.2
  Laurel Workman | Home Office | -12587.05
  Adrian Barton | Small Business | -11853.03
  Dave Kipp | Consumer | -11116.83
Julia West, Laurel Workman, Adrian Barton, Dave kipp returned items and they belonged to the following segment Home Office, Small  Business and Consumer.

#### 11. If the delivery truck is the most economical... do you think the company appropriately spent shipping costs based on the Order Priority?

- **SQL Query:**
  ```sql
  SELECT
      "Order Priority",
      "Ship Mode",
      COUNT(*) AS NumberOfOrders,
      AVG("Shipping Cost") AS AverageCost
  FROM
      Orders
  GROUP BY
      "Order Priority", "Ship Mode"
  ORDER BY
      "Order Priority", AverageCost DESC;
  ```
- **Result:**
  | Order Priority | Ship Mode | NumberOfOrders | AverageCost |
  | --- | --- | --- | --- |
  | Critical | Delivery Truck | 228 | 47.2974561403509 |
  | Critical | Express Air | 200 | 8.7105 |
  | Critical | Regular Air | 1180 | 7.27691525423729 |
  | High | Delivery Truck | 248 | 45.1890322580645 |
  | High | Regular Air | 1308 | 7.64909021406728 |
  | High | Express Air | 212 | 6.85627358490566 |
  | Low | Delivery Truck | 250 | 44.52644 |
  | Low | Express Air | 190 | 8.16647368421053 |
  | Low | Regular Air | 1280 | 8.018453125 |
  | Medium | Delivery Truck | 205 | 46.154243902439 |
  | Medium | Express Air | 201 | 8.12731343283582 |
  | Medium | Regular Air | 1225 | 7.68875102040816 |
  | Not Specified | Delivery Truck | 215 | 43.6651627906977 |
  | Not Specified | Express Air | 180 | 8.167 |
  | Not Specified | Regular Air | 1277 | 7.62261550509005 |
Based on the data, **the company is NOT appropriately spending on shipping costs relative to order priority** because:  

1. **Delivery Truck (most expensive)** is used heavily across all priorities—even for "Low" and "Not Specified" orders—despite cheaper options (Express/Regular Air) being available.  
2. **Critical orders** (highest priority) use Delivery Truck **5–6x more expensively** than Express/Regular Air, which may be unnecessarily costly if speed isn't the truck's advantage.  
3. **Cost inconsistency**: Low-priority orders sometimes cost more (e.g., "Low" + Regular Air averages **$8.02**) than High-priority orders using Express Air (**$6.86**).  

**Recommendation**: Reserve Delivery Truck for bulk/low-urgency orders and prioritize faster/cheaper methods (Express Air) for Critical/High-priority shipments unless delivery time justifies the cost.
