### Weather Analysis

There is a table with daily weather data over the last 6 months of 2020, including the maximum, minimum, and average temperatures.
Write a query that gives month, monthly maximum, monthly minimum, monthly average temperatures for the six months.
Note: Round the average to the nearest integer.

#### Schema
![Screenshot 2023-11-08 110532](https://github.com/Pluto0104/hackerrank-certification-solutions-using-javascript/assets/136573674/0534ac53-5fee-4829-9873-4aff30777c9b)

#### Sample Input
![Screenshot 2023-11-08 110543](https://github.com/Pluto0104/hackerrank-certification-solutions-using-javascript/assets/136573674/25dbfdd3-22b0-4d11-82b3-c87e8ea088ce)

#### Sample Output
![Screenshot 2023-11-08 110555](https://github.com/Pluto0104/hackerrank-certification-solutions-using-javascript/assets/136573674/4d953f70-5df5-4e1e-b1e9-ec60125e0dd0)

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
