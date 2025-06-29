# Exploring London's Travel Network

This project uses SQL to analyze a dataset containing Transport for London (TfL) journey information from 2010 to 2022. The goal is to understand how Londoners travel across different transport modes and identify trends in usage.

## Project Description

London's public transport network, managed by Transport for London, supports over 1.5 million journeys daily. This dataset is loaded into a Snowflake database with one main table: `TFL.JOURNEYS`. The table contains monthly data on journey volumes by transport type.

### Dataset Schema (`TFL.JOURNEYS`)

| Column            | Description                                             | Data Type |
|-------------------|---------------------------------------------------------|-----------|
| `MONTH`           | Month number (e.g., 1 = January)                        | INTEGER   |
| `YEAR`            | Year                                                    | INTEGER   |
| `DAYS`            | Number of days in the month                             | INTEGER   |
| `REPORT_DATE`     | Date the data was reported                              | DATE      |
| `JOURNEY_TYPE`    | Mode of transport (e.g., Bus, Underground & DLR, Tram) | VARCHAR   |
| `JOURNEYS_MILLIONS`| Number of journeys (in millions)                       | FLOAT     |

## Key Analyses

- Identified the most popular transport types over the years (e.g., Bus, Underground & DLR).  
- Examined peak usage periods of the Emirates Airline cable car.  
- Highlighted rare periods when the Underground (“the tube”) was less busy.

Example query used to find the most popular transport methods:

```sql
SELECT journey_type, SUM(journeys_millions) AS total_journeys_millions
FROM TFL.JOURNEYS
GROUP BY journey_type
ORDER BY total_journeys_millions DESC;
```
