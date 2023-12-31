### Crypto Market Algorithms Report

A number of algorithms are used to mine cryptocurrencies. As part of a comparison, create a query to return a list of algorithms and their volumes for each quarter of the year 2020.
The result should be in the following format: algorithm name, Q1, Q2, Q3, Q4 transactions.

- Q1 through Q4 contain the sums of transaction volumes for the algorithm for each calendar quarter of 2020 precise to 6 places after the decimal.
- Results should be sorted ascending by algorithm name.

#### Schema
![Screenshot 2023-11-08 094417](https://github.com/Pluto0104/hackerrank-certification-solutions-using-javascript/assets/136573674/f239279d-1788-44fc-98fa-0a10b3936715)

#### Sample Input
![Screenshot 2023-11-08 094444](https://github.com/Pluto0104/hackerrank-certification-solutions-using-javascript/assets/136573674/21497813-ab25-4456-a8d3-b0eec7b2cc23)

![Screenshot 2023-11-08 094430](https://github.com/Pluto0104/hackerrank-certification-solutions-using-javascript/assets/136573674/18bf097d-5d03-4e77-87ba-d3a3660084c3)

#### Sample Output
![Screenshot 2023-11-08 094451](https://github.com/Pluto0104/hackerrank-certification-solutions-using-javascript/assets/136573674/796cad65-260d-40e5-944f-f98dbaa50210)

### Solution

```sql
SELECT
    c.algorithm AS algorithm,
    ROUND(SUM(CASE WHEN EXTRACT(MONTH FROM t.dt) BETWEEN 1 AND 3 THEN t.volume ELSE 0 END), 6) AS transaction_Q1,
    ROUND(SUM(CASE WHEN EXTRACT(MONTH FROM t.dt) BETWEEN 4 AND 6 THEN t.volume ELSE 0 END), 6) AS transaction_Q2,
    ROUND(SUM(CASE WHEN EXTRACT(MONTH FROM t.dt) BETWEEN 7 AND 9 THEN t.volume ELSE 0 END), 6) AS transaction_Q3,
    ROUND(SUM(CASE WHEN EXTRACT(MONTH FROM t.dt) BETWEEN 10 AND 12 THEN t.volume ELSE 0 END), 6) AS transaction_Q4
FROM
    coins c
JOIN
    transactions t ON c.code = t.coin_code
WHERE
    EXTRACT(YEAR FROM t.dt) = 2020
GROUP BY
    c.algorithm
ORDER BY
    c.algorithm ASC;
```
