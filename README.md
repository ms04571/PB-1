# PB-1



## select sql

```sql
SELECT naslov, ROUND(ocena) AS zaokrožena_ocena
FROM film
WHERE ocena > 8 AND glasovi > 10000
ORDER BY ocena DESC, naslov;

SELECT naslov, ROUND(ocena)
FROM film
WHERE ROUND(ocena) = (
    SELECT MIN(ROUND(ocena))
    FROM film
    );

```