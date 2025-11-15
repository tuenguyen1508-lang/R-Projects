# 🦠 COVID-19 Data Integration, Exploration, and Predictive Modelling  

This project uses four CSV files containing COVID-19 data from multiple countries and regions between 1 January 2020 and 5 May 2020. The files were sourced online and include inconsistencies, missing values, and formatting issues, so the first priority is to transform them into a clean, well-structured dataset suitable for analysis and modelling.  

Task 1 focuses on **data preparation and wrangling**. The goal is to integrate the separate files into a unified master DataFrame that captures daily COVID-19 metrics by country. This involves importing each CSV into appropriately named DataFrames, tidying the `Recovered.csv` file so that each row represents the number of recovered patients for a specific country on a specific date, and renaming columns for consistency. All date variables are standardised to a common format to ensure smooth merging and time-series operations.  

From there, key variables from the supporting files are merged into the main `Covid19.csv` DataFrame. Five new columns are added: **Recovered**, **NewTests**, **Population**, **GDP**, and **GDPCapita**. Missing values in the merged data are converted to zeros to improve robustness for downstream analysis. Additional time-based features, **Month** and **Week**, are derived from the existing `Date` variable. Cumulative metrics are then engineered, including **CumCases**, **CumDeaths**, **CumRecovered**, and **CumTests**, each representing the total counts up to a given date for each country. Two further variables, **Active** (CumCases − (CumDeaths + CumRecovered)) and **FatalityRate** (CumDeaths / CumCases), quantify ongoing infection burden and severity. Finally, rate-per-million indicators—**Cases_1M_Pop**, **Deaths_1M_Pop**, **Recovered_1M_Pop**, and **Tests_1M_Pop**—enable fair comparisons across countries with different population sizes.  

Task 2 centres on **exploratory data analysis (EDA)** and visual storytelling. A series of plots are developed to understand global and country-level patterns. One graph tracks the global cumulative trajectories of infected cases, deaths, recoveries, and tests over time. Another visualises total cases over time for the top 10 countries (identified earlier) using a log-scaled y-axis to handle large disparities between countries. A faceted plot for the 10 countries with the highest active cases shows how new cases, deaths, and recoveries evolve over time, again using log scaling and colour coding to distinguish each metric. Additional graphs highlight the 10 countries with the highest tests per million population, comparing their total cases, total tests, and test rates. Finally, summary statistics (total, average, median) of confirmed cases are presented by continent to reveal regional differences.  

<img width="1130" height="721" alt="Screenshot 2025-11-15 110730" src="https://github.com/user-attachments/assets/280c2073-aaa2-4ffc-a256-6d49077a85e5" />

<img width="1004" height="729" alt="Screenshot 2025-11-15 110814" src="https://github.com/user-attachments/assets/eacff7d6-02a3-4fa2-ba66-4f319627479b" />

<img width="1083" height="727" alt="Screenshot 2025-11-15 110832" src="https://github.com/user-attachments/assets/d1b62f12-f71c-4ad4-a4c9-d0f7f4768edd" />

<img width="1069" height="633" alt="Screenshot 2025-11-15 110847" src="https://github.com/user-attachments/assets/dcb49997-9384-44fd-94c8-8ce7e152d414" />

<img width="1010" height="747" alt="Screenshot 2025-11-15 110913" src="https://github.com/user-attachments/assets/b7507c99-0b3b-4df4-9298-d35c86d4bd0e" />

Task 3 moves into **modelling and inference**. A correlation matrix is computed and visualised for a modelling subset (`cor_data`) to identify relationships between cumulative cases and economic or demographic variables. The distribution of cumulative cases is examined both on the original scale and with a log-transformed axis to manage skewness. Two regression models are then trained and evaluated.  

<img width="861" height="726" alt="Screenshot 2025-11-15 111145" src="https://github.com/user-attachments/assets/1328d1ca-8c53-4cd1-95af-663a21205bc9" />

<img width="1087" height="732" alt="Screenshot 2025-11-15 111202" src="https://github.com/user-attachments/assets/b2399970-dbc4-4733-996e-8c9405f8ed25" />

<img width="1013" height="728" alt="Screenshot 2025-11-15 111210" src="https://github.com/user-attachments/assets/75690c8b-ccfe-445c-b6b0-b7288e5b6319" />


Model 1 uses **GDP only** to predict cumulative cases (CumCases ~ GDP). It is statistically significant but explains only about 21% of the variance (R² ≈ 0.21), with a relatively high RMSE (~37,857), making it useful mainly as a simple benchmark.

Model 2 is a **multivariate regression** including CumTests, Population, GDP, and GDPCapita. This model explains around 77% of the variance (R² ≈ 0.77) and achieves a lower RMSE (~17,883), indicating substantially better predictive performance. Both models are highly significant, but Model 2 provides a more realistic basis for forecasting cumulative cases and supporting public health and economic planning, while still leaving room for refinement with additional predictors or more complex methods.  

