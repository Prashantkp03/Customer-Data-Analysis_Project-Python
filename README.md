Business Problem Statement:
A mid-sized Indian retail company wants to analyze its customer base to improve
targeted marketing, retain valuable customers, and detect patterns in customer
behavior. You have been hired as a data analyst to clean, process, and analyze the
customer transaction data to generate actionable insights.
Your goal is to:
● Assess customer demographics and transaction behavior
● Clean and prepare the data for analysis
● Conduct RFM (Recency, Frequency, Monetary) analysis
● Visualize key patterns using charts
Key Goals:
● Detect incomplete, inconsistent, or duplicate customer records and improve data
quality, if applicable
● Segment customers based on demographics and purchase behavior
● Identify high-value customers using Recency-Frequency-Monetary (RFM) analysis
● Visualize customer distribution across geographies, age groups, or income
brackets
● Generate actionable insights for marketing department


Dataset Description
You are provided with a synthetic dataset of 23,050 retail transactions made by
1,000 unique customers.
There are two key datasets:
1. Customer Master Data
Column Name Description
CustomerID Unique identifier for each customer
Name Customer's full name
Email Customer's email ID
Gender Male, Female, or Not Disclosed


Column Name Description
Age Customer's age (between 18 and 75)
City City where the customer resides (Indian metro/tier-2 cities)
MaritalStatus Marital status: Single, Married, Divorced, Widowed
NumChildren Number of children in the household
JoinDate Date the customer first registered with the company
2. Transaction Data
Column Name Description
CustomerID Links back to the customer master dataset
TransactionDate Date on which the transaction occurred
TransactionAmount Amount spent by the customer in that transaction (₹)
RFM Analysis Instructions (Conceptual Explanation)
RFM (Recency, Frequency, Monetary) is a customer segmentation method that helps
identify high-value customers based on:
Metric Description
Recency How recently a customer made a purchase
Frequency How often a customer purchases
Monetary How much money a customer spends
Steps to Compute RFM Scores
Step 1: Set Reference Date
Choose a reference "today" date. Typically, this is the most recent
TransactionDate + 1 day.
Step 2: Calculate Individual RFM Metrics
For each CustomerID:
● Recency = Days between "today" and last transaction date
● Frequency = Total number of transactions
● Monetary = Sum of all TransactionAmount values
Store this in a new RFM table with columns: CustomerID, Recency, Frequency,
Monetary
Step 3: Assign RFM Scores
● Use quantiles or quintiles (e.g., 1–5 scale) to rank customers
● Example logic:
o Recency: Lower days = higher score (recent buyers)
o Frequency: Higher count = higher score
o Monetary: Higher spend = higher score


Metric 1 (Low) 5 (High)
Recency Stale Recent
Frequency Rare Frequent
Monetary Low High
Step 4: Combine Scores
Create a combined RFM segment by joining the 3 scores. Example:
● R=5, F=5, M=5 → "555" Champion
● R=1, F=1, M=1 → "111" Lost
Step 5: Define Segments (Optional)
Use the RFM score combinations to define:
● Champions (e.g., RFM 555)
● Loyal Customers
● At Risk
● Hibernating
● Potential Loyalists, etc.
