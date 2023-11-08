### Weather Analysis

There is a table with daily weather data over the last 6 months of 2020, including the maximum, minimum, and average temperatures.
Write a query that gives month, monthly maximum, monthly minimum, monthly average temperatures for the six months.
Note: Round the average to the nearest integer.

#### Schema

#### Sample Input

#### Sample Output & Explanation

### Solution

```sql
SELECT
    MONTH(record_date) AS month,
    MAX(CASE WHEN data_type = "max" THEN data_value END) AS max,
    MIN(CASE WHEN data_type = "min" THEN data_value END) AS min,
    ROUND(AVG(CASE WHEN data_type = "avg" THEN data_value END)) AS avg
FROM temperature_records
WHERE record_date BETWEEN "2020-07-01" AND "2020-12-31"
GROUP BY month
ORDER BY month;
```
