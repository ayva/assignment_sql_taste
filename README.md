# assignment_sql_taste
A delicious appetizer of SQL-ey goodness
Olga and Nick


## Queries

SELECT *
FROM tutorial.us_housing_units
LIMIT 10;

SELECT year,
       month_name,
       midwest
FROM tutorial.us_housing_units

SELECT *
FROM tutorial.us_housing_units
WHERE month_name = 'December' AND year > 1985

SELECT *
FROM tutorial.us_housing_units
WHERE month > 6 AND year >= 1990

SELECT *
FROM tutorial.us_housing_units
WHERE south > 30

SELECT year,
       month,
       south + west + midwest + northeast AS sum_of_regions
FROM tutorial.us_housing_units;

SELECT *
  FROM tutorial.us_housing_units
  WHERE south+west+midwest+northeast > 70

SELECT *
  FROM tutorial.us_housing_units
  WHERE south+west+midwest+northeast BETWEEN 50 AND 80

SELECT (south+west+midwest+northeast)/4 AS avr
  FROM tutorial.us_housing_units
  WHERE south+west+midwest+northeast > 70
 
SELECT *
FROM tutorial.us_housing_units
WHERE south > (west+midwest+northeast) 

SELECT south/(south+west+midwest+northeast) AS south_per,
      west/(south+west+midwest+northeast) AS west_per,
      midwest/(south+west+midwest+northeast) AS midwest_per,
      northeast/(south+west+midwest+northeast) AS northeast_per

FROM tutorial.us_housing_units
WHERE year >= 1990

______Billboard




SELECT song_name
FROM tutorial.billboard_top_100_year_end
WHERE artist LIKE 'Elvis Presley' AND year_rank <100

SELECT *
FROM tutorial.billboard_top_100_year_end
WHERE artist ILIKE '%Tony%'

SELECT *
FROM tutorial.billboard_top_100_year_end
WHERE song_name ILIKE '%love%'

SELECT *
FROM tutorial.billboard_top_100_year_end
WHERE artist ILIKE 'A%'

SELECT *
FROM tutorial.billboard_top_100_year_end
WHERE year BETWEEN 1960 AND 1969
ORDER BY year_rank ASC, year ASC
LIMIT 30

SELECT *
FROM tutorial.billboard_top_100_year_end
WHERE artist LIKE 'Elivs Presley' OR artist LIKE 'The Rolling Stones' OR artist LIKE 'Van Halen'

SELECT *
FROM tutorial.billboard_top_100_year_end
WHERE year = 1970 AND year_rank BETWEEN 10 AND 20

SELECT *
FROM tutorial.billboard_top_100_year_end
WHERE year BETWEEN 1990 AND 2000 AND year_rank < 50 AND artist LIKE 'Madonna'

SELECT *
FROM tutorial.billboard_top_100_year_end
WHERE year = 1985 AND artist NOT LIKE 'Madonna' OR artist NOT LIKE 'Phil Collins'

SELECT *
FROM tutorial.billboard_top_100_year_end
WHERE year_rank = 1

SELECT *
FROM tutorial.billboard_top_100_year_end
WHERE artist IS NULL

SELECT *
FROM tutorial.billboard_top_100_year_end
WHERE artist LIKE 'Madonna'
ORDER BY year_rank ASC

SELECT *
FROM tutorial.billboard_top_100_year_end
WHERE artist LIKE 'Madonna'
ORDER BY year ASC, year_rank ASC

SELECT *
FROM tutorial.billboard_top_100_year_end
WHERE year >= 1990 AND year_rank < 4
ORDER BY year ASC, year_rank ASC


Intermediate


SELECT MIN(year_rank)
FROM tutorial.billboard_top_100_year_end
WHERE artist LIKE 'Phil Collins'


SELECT AVG(year_rank)
FROM tutorial.billboard_top_100_year_end
WHERE artist LIKE 'Michael Jackson'

SELECT AVG(year_rank)
FROM tutorial.billboard_top_100_year_end
WHERE artist LIKE 'Madonna' AND year_rank <=10

SELECT COUNT(artist) AS artist_appearanes,
        artist
FROM tutorial.billboard_top_100_year_end
WHERE year>1985
GROUP BY artist
ORDER BY artist_appearanes DESC
LIMIT 10

SELECT COUNT(song_name) AS hits

FROM tutorial.billboard_top_100_year_end
WHERE year_rank <= 10 AND artist LIKE 'Elvis%'
    OR artist LIKE 'Madonna' 
      OR artist LIKE 'Beatles' 
      OR artist LIKE 'Elton John' 

ORDER BY hits DESC

SELECT COUNT(DATE)
FROM tutorial.aapl_historical_stock_price
WHERE (high - low) > 5

SELECT MAX(high - low)
FROM tutorial.aapl_historical_stock_price
WHERE year = 2012

SELECT date,
       (high - low) / 2 AS average
FROM tutorial.aapl_historical_stock_price
WHERE volume > 10000000

SELECT COUNT(date)
FROM tutorial.aapl_historical_stock_price
WHERE year = 2002
GROUP BY month

SELECT MAX(high),
       year
FROM tutorial.aapl_historical_stock_price
GROUP BY year
ORDER BY year ASC

SELECT AVG((high + low) / 2) AS avg_price,
       AVG(volume) AS avg_volume,
       month
FROM tutorial.aapl_historical_stock_price
GROUP BY month
ORDER BY month ASC

SELECT AVG((high + low) / 2),
       year
FROM tutorial.aapl_historical_stock_price
WHERE year > 2007
GROUP BY year, month
ORDER BY year DESC, month ASC

SELECT AVG((high + low) / 2)
FROM tutorial.aapl_historical_stock_price
WHERE volume > 25000000


SELECT AVG((high+low)/2) AS average,
      month,
      AVG(volume) AS avg_volume
FROM tutorial.aapl_historical_stock_price

GROUP BY month
HAVING AVG(volume) > 10000000

SELECT       MAX(high) AS highest,
      MIN(low) AS lowest,
      AVG(volume) AS average_volume,
      year

FROM tutorial.aapl_historical_stock_price
WHERE year BETWEEN 2005 AND 2010
GROUP BY year
HAVING AVG(volume) > 10000000

SELECT  AVG((high+low)/2) AS average,
        month
FROM tutorial.aapl_historical_stock_price
WHERE (close-open > 25) OR (open-close > 25)
GROUP BY month

SELECT  month, AVG(volume)
FROM tutorial.aapl_historical_stock_price
WHERE month > 6 AND volume < 10000000
GROUP BY month 
ORDER BY month ASC


SELECT  month, 
        AVG(volume) AS avg_volume
FROM tutorial.aapl_historical_stock_price
GROUP BY month 
ORDER BY avg_volume DESC

SELECT  COUNT(DISTINCT month) AS unique_month
FROM tutorial.aapl_historical_stock_price
 
SELECT  COUNT(DISTINCT year) AS unique_year
FROM tutorial.aapl_historical_stock_price

SELECT  COUNT(DISTINCT (high+low)/2) AS unique_avg_prices
FROM tutorial.aapl_historical_stock_price


### Example

```
SELECT *
  FROM tutorial.us_housing_units
  WHERE month = 1
```
