1. WHAT IS THE MINIMUM NUMBER OF CASES IN THIS TABLE WHERE THE VALUE IS NOT NULL?
```SQL
SELECT
  MIN(value) AS minimum_cases
FROM bigquery-public-data.world_bank_health_population.health_nutrition_population
WHERE
  value IS NOT NULL
```

<img width="289" alt="image" src="https://github.com/kaustubha011110/KaustubhaN/assets/154294135/c0b9b030-9486-45f5-b8b6-71802be5fafc">

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

<img width="223" alt="Screenshot 2024-02-04 182305" src="https://github.com/kaustubha011110/KaustubhaN/assets/154294135/b5f2f3a9-06d6-4eef-9535-62a0777f7431">

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

<img width="662" alt="Screenshot 2024-02-04 183628" src="https://github.com/kaustubha011110/KaustubhaN/assets/154294135/2bc4da15-2341-4690-b317-cc402b98fc95">

5. LIST THE COUNTRY_NAME FROM THE TABLE AND LIMIT IT TO 5
```SQL
SELECT
Distinct (country_name)
FROM bigquery-public-data.world_bank_health_population.health_nutrition_population
LIMIT
```
<img width="267" alt="Screenshot 2024-02-04 183719" src="https://github.com/kaustubha011110/KaustubhaN/assets/154294135/058d4c4e-4ac1-4c4e-a45c-d1c9d69562ee">

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
<img width="187" alt="Screenshot 2024-02-04 184007" src="https://github.com/kaustubha011110/KaustubhaN/assets/154294135/4cc13937-b764-4728-b399-0c1199e549f9">

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

<img width="328" alt="Screenshot 2024-02-04 184205" src="https://github.com/kaustubha011110/KaustubhaN/assets/154294135/e6fb5ecb-b88b-4fe8-8868-00b2b812bef5">

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

<img width="173" alt="Screenshot 2024-02-04 184435" src="https://github.com/kaustubha011110/KaustubhaN/assets/154294135/34fa1763-02bc-488b-9f47-78fca5e1a925">

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

<img width="364" alt="Screenshot 2024-02-04 184745" src="https://github.com/kaustubha011110/KaustubhaN/assets/154294135/4ca175c0-360d-4128-81df-5a72bb3c5e5e">

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
