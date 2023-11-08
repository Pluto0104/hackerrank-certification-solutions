### Winners Chart

There were a number of contests where participants each made multiple attempts. The attempt with the highest score is the only one considered. Write a query to list the
contestants ranked in the top 3 for each contest. If multiple contestants have the same score in a contest, they are at the same rank.
Report event_id, rank 1 name(s), rank 2 name(s), rank 3 name(s). Order the contests by event_id. Names that share a rank should be ordered alphabetically and separated by a comma.
Order the report by event_id.

#### Schema

#### Sample Input

#### Sample Output & Explanation

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
