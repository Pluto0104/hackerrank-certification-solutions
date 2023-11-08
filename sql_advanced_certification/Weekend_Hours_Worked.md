### Weekend Hours Worked

The times that employees log in and out are recorded over the course of a month. For each employee, determine the number of hours worked during the weekends. For simplicity, hours worked in a day, hours are truncated to their integer part.
For example, there are 10 hours between '2000:01:01 00:45:00' and '2000:01:01 10:45:00. There are 9 hours between '2000:01:01 00:46:00' and '2000:01:01 10:45:00'.
Return a list of employee ids and weekend hours worked, descending by hours worked.

#### Schema

#### Sample Input

#### Sample Output & Explanation

### Solution

```sql
SELECT
    a.emp_id,
    ROUND(SUM(HOUR(TIMEDIFF(b.timestamp, a.timestamp))) / 2) AS work_hours
FROM
    attendance a
JOIN
    attendance b ON a.emp_id = b.emp_id
    AND DATE(a.timestamp) = DATE(b.timestamp)
    AND WEEKDAY(a.timestamp) IN (5, 6)
GROUP BY
    a.emp_id
ORDER BY
    work_hours DESC;
```
