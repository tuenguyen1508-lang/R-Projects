# 📌 Executive Overview  

This project analyses customer purchasing behaviour and revenue drivers for Marry’s online store using a combination of exploratory data analysis, visualisation, and predictive modelling. The core questions include: which product categories sell best and worst, how preferences differ across demographics, and how factors such as gender, age, quantity, and price shape revenue. Monthly sales patterns are examined to detect seasonal peaks, and a one-year revenue forecast is produced to support planning. Techniques used include bar and pie charts, time-series plots, boxplots, correlation analysis, linear regression, decision trees, seasonal naïve forecasting, and residual diagnostics. Together, these methods provide Marry with a clear picture of revenue performance, customer profiles, and satisfaction levels to inform future operational and marketing strategies.  

---

## 🧾 Dataset & Key Variables  

The dataset contains 13 fields: `customer_id`, `order_date`, `product_id`, `category_id`, `category_name`, `product_name`, `quantity`, `price`, `payment_method`, `city`, `review_score`, `gender`, and `age`. A statistical summary shows that customers typically purchase between 1 and 5 items per order, with an average of about 3. Prices range from \$10.72 to \$499.50, averaging around \$251.85. Review scores fall between 1 and 5, with a mean close to 4, although 201 customers did not leave feedback. Customer ages span from 18 to 75 years.  

A new variable, **Revenue** (`quantity × price`), was engineered and used throughout the analysis as the main performance indicator. This allowed comparisons of revenue by gender, age group, product category, and product type, as well as correlation analysis and revenue forecasting. Revenue was chosen as the target variable because it directly reflects business outcomes and combines two key sales drivers: price and quantity.  

---

## 🔍 Customer & Sales Insights  

Payment behaviour was explored using bar charts of quarterly totals, revealing that **Cash on Delivery** is consistently the most popular method in every quarter. Age distribution was examined with a boxplot, showing customers are mainly between 32 and 61 years old, with a median age of 48 and no apparent outliers. This supports the reliability of the data and indicates a stable, mature customer base.  

<img width="1083" height="733" alt="Screenshot 2025-11-15 104517" src="https://github.com/user-attachments/assets/61681d08-cff4-4723-9f0b-d6e484866858" />


Review scores are strongly skewed towards positive feedback: more than 300 customers awarded the top rating of 5, while a score of 2 was least common, and 201 customers provided no review. Overall, this suggests high satisfaction with products and services. A time-series plot of monthly sales shows the lowest revenue in March 2024 and a clear peak in December 2024, indicating stronger demand toward year-end.  

<img width="1048" height="611" alt="Screenshot 2025-11-15 104550" src="https://github.com/user-attachments/assets/6cd569dc-95bc-49ce-b85c-3ffd24f5df12" />

<img width="1024" height="695" alt="Screenshot 2025-11-15 104622" src="https://github.com/user-attachments/assets/4280a1fb-8128-4320-b5ea-b2ac6c0a9248" />

<img width="1040" height="723" alt="Screenshot 2025-11-15 105733" src="https://github.com/user-attachments/assets/2314d3d0-d1d2-4733-a074-fcaca711f376" />



Comparing the top 10 revenue-generating products by gender uncovered expected bestsellers such as laptops, smartphones, and headphones, as well as a surprising pattern: **yoga mats** generated more revenue from male customers than from female customers. Category-level analysis found Category 10 (electronics) as the strongest performer and Category 40 (books & stationery) as the weakest.  

<img width="1174" height="711" alt="Screenshot 2025-11-15 104743" src="https://github.com/user-attachments/assets/4b9b271e-3682-4652-9809-d4a7a142cdaf" />

<img width="1019" height="735" alt="Screenshot 2025-11-15 105820" src="https://github.com/user-attachments/assets/bc10cb2c-8f33-4e37-ab77-2ae203b446e0" />

<img width="1093" height="721" alt="Screenshot 2025-11-15 104909" src="https://github.com/user-attachments/assets/8cac9244-115d-400a-bd4e-caaf5b9b0cf8" />

---

## 🤖 Revenue Modelling & Forecasting  

Correlation analysis confirmed that **quantity** has a strong positive relationship with revenue (0.61), which is expected given the formula for revenue. In contrast, encoded product, category, and gender variables show only weak relationships with revenue, and age has virtually no correlation, suggesting it does not materially drive spending.  

<img width="857" height="721" alt="Screenshot 2025-11-15 104945" src="https://github.com/user-attachments/assets/3b737ad1-18b8-49fa-9510-efbe136be54a" />


Several predictive models were developed to estimate revenue, with the **decision tree model** performing best. It achieved an R² of 0.93, indicating high explanatory power, low prediction error, and no signs of severe overfitting based on residual analysis.  

<img width="1021" height="743" alt="Screenshot 2025-11-15 105719" src="https://github.com/user-attachments/assets/2d52d869-08e7-47c2-baf1-f7927b206e5e" />


Finally, a **Seasonal Naive** model was used to forecast revenue one year ahead, using data from March 19, 2024 to March 19, 2025. The forecast suggests revenue is likely to peak again at roughly \$8,000 around the fifth and ninth forecast months, mirroring past seasonal patterns and providing a practical guide for inventory, marketing, and staffing decisions.  

<img width="1089" height="686" alt="Screenshot 2025-11-15 105052" src="https://github.com/user-attachments/assets/df756315-d4ff-45be-b4eb-34451f991199" />


