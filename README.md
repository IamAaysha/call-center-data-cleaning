# Call Center Data Cleaning and Analysis  

## Database and Table Selection  
```sql
USE call_centerdata;
SELECT * FROM call_center;
```

## Data Cleaning  

### Disable Safe Updates  
```sql
SET SQL_SAFE_UPDATES = 0;
```

### Changing Date Format  
```sql
UPDATE call_center  
SET call_timestamp = STR_TO_DATE(call_timestamp, "%m/%d/%Y");
```

### Updating Empty Values to NULL  
```sql
UPDATE call_center  
SET csat_score = NULL  
WHERE csat_score = '';
```

### Enable Safe Updates  
```sql
SET SQL_SAFE_UPDATES = 1;
```

### View Sample Data  
```sql
SELECT * FROM call_center LIMIT 10;
```

## Counting Rows and Columns  

### Number of Rows  
```sql
SELECT COUNT(*) AS num_rows FROM call_center;
```

### Number of Columns  
```sql
SELECT COUNT(*) AS num_columns  
FROM information_schema.columns  
WHERE table_name = 'call_center' AND table_schema = 'call_centerdata';
```

## Distinct Values in Each Column  

### Unique Sentiments  
```sql
SELECT DISTINCT sentiment FROM call_center;
```

### Unique Cities  
```sql
SELECT DISTINCT city FROM call_center;
```

### Unique Call Centers  
```sql
SELECT DISTINCT call_center FROM call_center;
```

## Count and Percentage of Distinct Values  

### Count and Percentage of Each City  
```sql
SELECT city,  
  COUNT(*) AS count,  
  COUNT(*) * 100.0 / (SELECT COUNT(*) FROM call_center) AS percentage  
FROM call_center  
GROUP BY city;
```

## Call Count Analysis  

### Calls Per Day of the Week  
```sql
SELECT DAYNAME(call_timestamp) AS day_of_week,  
COUNT(*) AS call_count  
FROM call_center  
GROUP BY day_of_week  
ORDER BY call_count DESC;
```

## Statistical Calculations  

### Call Duration Statistics  
```sql
SELECT  
  MIN(`call duration in minutes`) AS min_duration,  
  MAX(`call duration in minutes`) AS max_duration,  
  AVG(`call duration in minutes`) AS avg_duration  
FROM call_center;
```

### CSAT Score Statistics (Ignoring Zero Scores)  
```sql
SELECT  
  MIN(csat_score) AS min_csat,  
  MAX(csat_score) AS max_csat,  
  ROUND(AVG(csat_score), 2) AS avg_csat  
FROM call_center  
WHERE csat_score <> 0;
```

### Response Time Analysis  
```sql
SELECT call_center, response_time, COUNT(*) as count  
FROM call_centerdata.call_center  
GROUP BY 1, 2  
ORDER BY 1, 3 DESC;
```

### Maximum Call Duration Per Day  
```sql
SELECT  
  DATE(call_timestamp) AS call_day,  
  MAX(`call duration in minutes`) AS max_call_duration  
FROM call_center  
GROUP BY call_day  
ORDER BY call_day;
