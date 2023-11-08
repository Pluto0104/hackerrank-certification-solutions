### Winners Chart

There were a number of contests where participants each made multiple attempts. The attempt with the highest score is the only one considered. Write a query to list the
contestants ranked in the top 3 for each contest. If multiple contestants have the same score in a contest, they are at the same rank.
Report event_id, rank 1 name(s), rank 2 name(s), rank 3 name(s). Order the contests by event_id. Names that share a rank should be ordered alphabetically and separated by a comma.
Order the report by event_id.

#### Schema
![Screenshot 2023-11-08 111945](https://github.com/Pluto0104/hackerrank-certification-solutions-using-javascript/assets/136573674/9a88df0d-aed6-4dbb-960c-f2d99c36638b)

#### Sample Input
![Screenshot 2023-11-08 112004](https://github.com/Pluto0104/hackerrank-certification-solutions-using-javascript/assets/136573674/fdf720e2-6017-4cc2-931c-dd04e60c54ae)

#### Sample Output & Explanation
![Screenshot 2023-11-08 112012](https://github.com/Pluto0104/hackerrank-certification-solutions-using-javascript/assets/136573674/7a14c26c-8328-470d-a6ac-e0647b728a53)
![Screenshot 2023-11-08 112022](https://github.com/Pluto0104/hackerrank-certification-solutions-using-javascript/assets/136573674/dff1191f-f25e-4ab5-b8a2-7d7b3bb6480a)

### Solution

```sql
WITH ranked_scores AS (
    SELECT
        event_id,
        participant_name,
        score,
        DENSE_RANK () OVER (
            PARTITION BY event_id
            ORDER BY score DESC
        ) AS ranking
    FROM (
        SELECT
            event_id,
            participant_name,
            MAX(score) AS score
        FROM scoretable
        GROUP BY event_id, participant_name
    ) t
)

SELECT
    event_id,
    GROUP_CONCAT(
        CASE WHEN ranking = 1 THEN participant_name END
        ORDER BY participant_name
    ) AS first,
    GROUP_CONCAT(
        CASE WHEN ranking = 2 THEN participant_name END
        ORDER BY participant_name
    ) AS second,
    GROUP_CONCAT(
        CASE WHEN ranking = 3 THEN participant_name END
        ORDER BY participant_name
    ) AS third
FROM ranked_scores
WHERE ranking <= 3
GROUP BY event_id
ORDER BY event_id;
```
