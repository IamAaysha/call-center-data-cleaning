# Call Center Data Cleaning and Analysis  

## Project Overview  
This project focuses on cleaning and analyzing call center data to improve data quality and derive insights. The SQL script performs data preprocessing, exploratory analysis, and statistical calculations.  

## Dataset  
The project utilizes the `call_center` table from the `call_centerdata` database, which contains:  
- **Call details:** Timestamp, duration, response time  
- **Customer feedback:** CSAT score, sentiment  
- **Geographic data:** City, call center location  

## Key Steps  

### 1. Data Cleaning  
- **Converted** date formats for consistency  
- **Replaced** empty CSAT scores with `NULL` values  

### 2. Data Exploration  
- **Counted** the number of rows and columns  
- **Extracted** distinct values for key categorical columns (city, sentiment, call center)  
- **Calculated** the distribution of calls per city  

### 3. Call Analysis  
- **Determined** call volume per day of the week  
- **Computed** statistics for call duration (min, max, average)  
- **Analyzed** CSAT scores while excluding zero values  

### 4. Response Time and Duration Insights  
- **Grouped** data by call center and response time  
- **Identified** the maximum call duration per day  

## Technologies Used  
- **SQL** for data cleaning and analysis  
- **MySQL Workbench** or any compatible SQL environment  

## How to Run the Project  

1. **Clone the repository:**  
   ```bash
   git clone <repo-link>
   ```
2. **Connect to your SQL database** and ensure the `call_centerdata` database is available.  
3. **Execute the SQL script** to clean and analyze the data.  

## Next Steps & Improvements  
- Implement data visualization using Python or Power BI  
- Apply machine learning to predict customer satisfaction scores  
- Optimize SQL queries for large datasets  

## Disclaimer  
This project is for educational purposes and should be used with anonymized or synthetic data to protect privacy.  
