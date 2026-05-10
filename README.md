# 🛒 Customer Behaviour Analysis
[![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![SQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)](https://www.postgresql.org/)
[![PowerBI](https://img.shields.io/badge/PowerBI-F2C811?style=for-the-badge&logo=power-bi&logoColor=black)](https://powerbi.microsoft.com/)

This is an end-to-end data analytics project that analyzes customer purchasing behaviour to uncover insights about revenue trends, customer segments, and buying patterns.

## 📊 Dashboard Preview
<img width="845" height="633" alt="image" src="https://github.com/user-attachments/assets/5b337456-809a-421e-8627-0c620e261e44" />

---

## 💡 Key Business Insights
* **Revenue Drivers:** Male customers contribute significantly to the total revenue, with specific interest in the **Clothing** and **Accessories** categories.
* **Seasonal Trends:** Significant peaks in purchasing frequency were observed during the **Fall** season, suggesting a need for increased inventory during this period.
* **Customer Loyalty:** Approximately **15%** of the customer base is categorized as "Loyal" (over 10 previous purchases), yet they account for a disproportionate amount of total sales.
* **Discount Impact:** Use of promo codes resulted in a higher average transaction value compared to non-promo transactions.

---

## 🛠️ Tools & Technologies
| Tool | Purpose |
| :--- | :--- |
| **Python** | Data loading, Cleaning, and EDA (Pandas, Seaborn) |
| **PostgreSQL** | Structured data storage and complex business queries |
| **Power BI** | Building interactive visual reports and KPIs |
| **Jupyter** | Development environment for data exploration |

---

## 🗄️ SQL Analysis Highlights
I used PostgreSQL to answer specific business questions. Here is an example of the segmentation logic used:

```sql
-- Customer segmentation by purchase history
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
```
---

## 🚀 How to Run
---

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/bsanghvi78/Customer-Behaviour-Analysis.git](https://github.com/bsanghvi78/Customer-Behaviour-Analysis.git)
2. Install Dependencies:
Make sure you have Python installed, then run:
Bash
pip install pandas matplotlib seaborn
3. Run the Analysis:
Open Customer_shopping_behaviour.ipynb in Jupyter Notebook or VS Code to view the analysis.

## 📁 Repository Structure

* `Customer_shopping_behaviour.ipynb`: The main Python notebook containing data cleaning and EDA.

* `customer_shopping_behavior.csv`: The raw dataset used for the analysis.

* `SQL-Queries.pdf`: Documentation of SQL scripts used for database analysis.

* `Customer-Shopping-Behavior-Analysis.pptx`: Final presentation of business findings.

* `Customer Shopping Behavior Analysis.pdf`: Comprehensive written report.
