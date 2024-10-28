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

# 28.10.

# 1.
SELECT naslov, ime FROM film
JOIN vloga on film.id = vloga.film
JOIN oseba on vloga.oseba = oseba.id
WHERE tip = 'I' AND mesto = 1
ORDER BY ime, naslov

# 2.
SELECT oseba.id, ime, SUM(dolzina) FROM oseba
JOIN vloga ON oseba.id = vloga.oseba
JOIN film ON film.id = vloga.film
WHERE vloga.tip = 'R'
GROUP BY ime
ORDER BY ime

# 3.
SELECT naziv, COUNT(DISTINCT igralci.oseba) AS st_igralcev, COUNT(DISTINCT reziserji.oseba) AS st_reziserjev FROM zanr
JOIN pripada ON zanr.id = pripada.zanr
JOIN vloga AS igralci ON pripada.film = igralci.film
JOIN vloga AS reziserji ON pripada.film = reziserji.film
WHERE igralci.tip = 'I' AND reziserji.tip = 'R'
GROUP BY zanr.naziv
ORDER BY st_igralcev + st_reziserjev DESC



```