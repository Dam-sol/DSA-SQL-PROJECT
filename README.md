# DSA-SQL-PROJECT
## Project Overview
This analysis explores the Kultra Mega Stores order dataset (2009-2012) to derive insights into sales performance, customer segments, regional profitability, and operational efficiency. The primary tool used for data manipulation and aggregation was SQL, with findings presented to guide strategic business decisions.

## Tools Used

Database: SQLite

Analysis Tool: DB Browser for SQLite

Reporting & Version Control: GitHub

🧩 CASE SCENARIO I – Operational & Sales Insights

1️⃣ Which product category had the highest sales?

| Product Category | Total Sales (₦) |
| ---------------- | --------------- |
| **Technology**   | ₦5,984,248.18   |
| Furniture        | ₦5,178,590.54   |
| Office Supplies  | ₦3,752,762.10   |

2️⃣ Top 3 and Bottom 3 regions in terms of sales

| Rank | Region                | Total Sales (₦) |
| ---- | --------------------- | --------------- |
| 🥇 1 | **West**              | ₦3,597,549.00   |
| 🥈 2 | **Ontario**           | ₦3,063,212.00   |
| 🥉 3 | **Prarie**            | ₦2,837,305.00   |
| 🔻 6 | Yukon                 | ₦975,867.40     |
| 🔻 7 | Northwest Territories | ₦800,847.30     |
| 🔻 8 | **Nunavut**           | ₦116,376.50     |

3️⃣ Total sales of appliances in Ontario
₦202,346.84

✅ Insight: Appliances in Ontario generated moderate revenue. Targeted promotions or bundle offers may help boost this.

4️⃣ How to increase revenue from the bottom 10 customers?

Engage low-frequency buyers with personalized offers and win-back campaigns to boost repeat purchases.

Upsell/cross-sell based on their order history with bundles, discounts, or product recommendations.

Improve loyalty through targeted incentives, account managers, or subscription options to increase order value and frequency.

5️⃣ Shipping method with the highest total cost

| Shipping Mode      | Total Shipping Cost (₦) |
| ------------------ | ----------------------- |
| **Delivery Truck** | ₦51,971.94              |
| Regular Air        | ₦48,008.19              |
| Express Air        | ₦7,850.91               |

🧠 CASE SCENARIO II – Customer Behavior & Strategy

6️⃣ Who are the most valuable customers and what products do they purchase?

| Customer Name     | Total Sales (₦) | Top Products Purchased                   |
| ----------------- | --------------- | ---------------------------------------- |
| **Emily Phan**    | ₦117,124.44     | Office Machines, Telecom & Communication |
| Deborah Brumfield | ₦97,433.14      | Copiers & Fax, Office Machines           |
| Roy Skaria        | ₦92,542.15      | Bookcases, Copiers & Fax                 |
| Sylvia Foulston   | ₦88,875.76      | Chairs, Office Machines                  |
| Grant Carroll     | ₦88,417.00      | Binders, Chairs                          |
| Alejandro Grove   | ₦83,561.93      | Binders, Tables                          |

7️⃣ Which small business customer had the highest sales?

🏆 Dennis Kane: ₦75,967.59

8️⃣ Which Corporate Customer placed the most number of orders (2009–2012)?

🏆 Adam Hart: 27 orders

9️⃣ Most profitable consumer customer

🏆 Emily Phan: ₦34,005.44 profit

🔟 Which customer(s) returned items, and what segments do they belong to?

Assuming negative profit or zero sales as a proxy for returns:

📦 ~951 customers had returned-like transactions

Segments involved:

Consumer

Corporate

Small Business

Home Office

1️⃣1️⃣ Was shipping cost appropriately spent based on Order Priority?

| Order Priority | Delivery Truck (₦) | Express Air (₦) | Regular Air (₦) |
| -------------- | ------------------ | --------------- | --------------- |
| Critical       | 10,783.82          | 1,742.10        | 8,586.76        |
| High           | 11,206.88          | 1,453.53        | 10,005.01       |
| Medium         | 9,461.62           | 1,633.59        | 9,418.72        |
| Low            | 11,131.61          | 1,551.63        | 10,263.62       |
| Not Specified  | 9,388.01           | 1,470.06        | 9,734.08        |

✅ Insight:

Express Air (most expensive) was used more evenly, even for Low or Medium priority orders.

Delivery Truck (most economical) was used heavily even for Critical orders.

📌 Recommendation:

Create a logistics policy aligning shipping method strictly with priority:

Critical = Express Air

Medium = Regular Air

Low = Delivery Truck

This ensures better budget use and delivery reliability.




