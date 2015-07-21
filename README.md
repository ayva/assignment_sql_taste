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



### Example

```
SELECT *
  FROM tutorial.us_housing_units
  WHERE month = 1
```
