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



### Example

```
SELECT *
  FROM tutorial.us_housing_units
  WHERE month = 1
```
