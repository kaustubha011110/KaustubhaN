1. WHAT IS THE MINIMUM NUMBER OF CASES IN THIS TABLE WHERE THE VALUE IS NOT NULL?
```SQL
SELECT
  MIN(value) AS minimum_cases
FROM bigquery-public-data.world_bank_health_population.health_nutrition_population
WHERE
  value IS NOT NULL
```
2. LIST THE YEARS WITH LIMIT AS 10
```SQL
SELECT
  year
FROM bigquery-public-data.world_bank_health_population.health_nutrition_population
WHERE
  year IS NOT NULL
LIMIT
  10
```
3. SELECT THE ENTIRE TABLE
```SQL
SELECT
  *
From bigquery-public-data.world_bank_health_population.health_nutrition_population
```
4. COUNT COUNTRY_CODE
```SQL
SELECT COUNT(country_code)
FROM `bigquery-public-data.world_bank_health_population.health_nutrition_population`;
```
5. LIST THE COUNTRY_NAME FROM THE TABLE AND LIMIT IT TO 5
```SQL
SELECT
Distinct (country_name)
FROM bigquery-public-data.world_bank_health_population.health_nutrition_population
LIMIT
```
6. FIND THE AVERAGE VALUES AND LIMIT IT TO 10
```SQL
SELECT
AVG(value) AS average_value
FROM bigquery-public-data.world_bank_health_population.health_nutrition_population
GROUP BY
  country_name
LIMIT
  10
```
7. FIND THE COUNTRIES WITH THE HIGHEST POPULATION, LIMIT IT TO 10 AND ARRANGE IN DESCENDING ORDER
```SQL
SELECT
  country_name, MAX(value) as Highest_Population
FROM bigquery-public-data.world_bank_health_population.health_nutrition_population
GROUP BY
  country_name
ORDER BY
  Highest_Population DESC
LIMIT
  10
```
8. FIND THE COUNTRY WITH LOWEST LIFE EXPECTANCY, LIMIT IT TO 10 AND ARRANGE IN ASCENDING ORDER
```SQL
SELECT
MIN(value) as Lowest_LifeExpectancy
FROM bigquery-public-data.world_bank_health_population.health_nutrition_population
GROUP BY
  country_name
ORDER BY
   Lowest_LifeExpectancy ASC
LIMIT
  10
```
9. FIND, WHERE RELATED INDICATORS AND COUNTRY CODE ARE EQUAL BY LEFT JOINING THE WORLD BANK SERIES SUMMARY.
```SQL
SELECT
  related_indicators, country_code
FROM bigquery-public-data.world_bank_health_population.health_nutrition_population
LEFT JOIN bigquery-public-data.world_bank_health_population.series_summary AS additional_data
ON
  country_code = additional_data.related_indicators
LIMIT
  10
```
10. FIND THE HEALTH DATA AND THE ADDITIONAL DATA FOR COUNTRY_CODE BY LEFT JOINING THE COUNTRY SUMMARY BETWEEN THE YEARS 1970 AND 2000
```SQL
SELECT
  health_data.*,
  additional_data.*
FROM
  `bigquery-public-data.world_bank_health_population.health_nutrition_population` AS health_data
LEFT JOIN
  `bigquery-public-data.world_bank_health_population.country_summary` AS additional_data
ON
  health_data.country_code = additional_data.country_code
WHERE 
  YEAR BETWEEN 1970 AND 2000
```
