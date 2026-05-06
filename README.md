# Customer_Behaviour_Analysis
This is an end-to-end data analytics project that analyzes customer purchasing behaviour to uncover insights about revenue trends, customer segments, product performance, and buying patterns.
The project covers the full analytics workflow — from raw data loading and cleaning in Python, to SQL-based analysis, interactive Power BI dashboards, and a final business presentation.

📁 Dataset
DetailInfoDataset NameCustomer Behaviour DatasetSourceKaggle / Custom DatasetRows~3,900 recordsColumns18 columns
Key columns include:

customer_id — Unique customer identifier
age, gender, location — Customer demographics
item_purchased, category — Product details
purchase_amount — Transaction value
frequency_of_purchases — Buying frequency
discount_applied, promo_code_used — Discount details
review_rating — Customer satisfaction score
previous_purchases — Purchase history count


🛠️ Tools & Technologies
ToolPurposePython (Pandas, NumPy, Matplotlib, Seaborn)Data loading, EDA, cleaningPostgreSQL / pgAdminSQL analysis & queryingPower BIInteractive dashboard & visualizationsGammaBusiness presentation (PPT)GitHubVersion control & project sharingJupyter NotebookPython development environment

🔄 Project Steps
Step 1 — Data Loading 🐍

Loaded the dataset using Pandas
Explored shape, data types, and initial statistics
Previewed the first few rows to understand structure

Step 2 — Exploratory Data Analysis (EDA) 🔍

Analyzed distributions of age, purchase amount, and ratings
Identified top-selling categories and items
Explored gender-wise and location-wise purchasing trends
Visualized correlations using heatmaps and bar charts

Step 3 — Data Cleaning 🧹

Handled missing values and null entries
Removed duplicate records
Standardized column formats (dates, text casing)
Mapped frequency labels to numeric values (e.g. Weekly → 7 days)
Fixed data type inconsistencies

Step 4 — SQL Analysis 🗄️
Ran structured queries on PostgreSQL to answer key business questions:
sql-- Q1. Total revenue by gender
SELECT gender, SUM(purchase_amount) AS revenue
FROM customer
GROUP BY gender;

-- Q2. Top 3 items per category by order count
WITH item_counts AS (
  SELECT category, item_purchased,
         COUNT(customer_id) AS total_orders,
         ROW_NUMBER() OVER (PARTITION BY category ORDER BY COUNT(customer_id) DESC) AS item_rank
  FROM customer
  GROUP BY category, item_purchased
)
SELECT * FROM item_counts WHERE item_rank <= 3;

-- Q3. Customer segmentation by purchase history
SELECT customer_segment, COUNT(*) AS total_customers
FROM (
  SELECT customer_id,
    CASE
      WHEN previous_purchases = 1 THEN 'New'
      WHEN previous_purchases BETWEEN 2 AND 10 THEN 'Returning'
      ELSE 'Loyal'
    END AS customer_segment
  FROM customer
) t
GROUP BY customer_segment;
Step 5 — Power BI Dashboard 📊

Imported cleaned CSV data into Power BI
Created DAX measures for KPIs
Built interactive visuals including bar charts, pie charts, and cards
Added slicers for gender, category, and season filters

Step 6 — Report & Presentation 📝

Summarized key findings in a structured report
Created a business presentation using Gamma
Highlighted actionable recommendations for stakeholders

