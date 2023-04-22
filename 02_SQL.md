## Ranking:
Query:
SELECT ROW_NUMBER() OVER (ORDER BY SUM(NUM)) name_rank

## Cumulative Ranking:
Query:
SELECT sum(num) OVER (ORDER BY year) cumulative_ranking

## CTE(Common Table Expression):
WITH table_1 AS (
-- INSERT CTE EXPRESSION)

SELECT *
FROM table_1
