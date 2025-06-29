# International Students’ Mental Health Analysis

This project analyzes a survey dataset of Japanese university students to explore the mental health impact on international students compared to domestic students. The data was collected in 2018 and published following ethical approval.

## Project Description

The study found that international students are at a higher risk of mental health difficulties than the general population. Key factors predictive of depression include:

- Social connectedness (sense of belonging to a social group)  
- Acculturative stress (stress from adapting to a new culture)  

This project uses PostgreSQL to analyze the `students` dataset, exploring whether length of stay in Japan affects depression scores among international students.

## Dataset Overview (`students` table)

| Field Name    | Description                                      |
| ------------- | ------------------------------------------------ |
| `inter_dom`     | Student type: international or domestic          |
| `japanese_cate` | Japanese language proficiency                     |
| `english_cate`  | English language proficiency                      |
| `academic`      | Academic level: undergraduate or graduate        |
| `age`           | Age of student                                    |
| `stay`          | Length of stay in Japan (years)                   |
| `todep`         | Depression score (PHQ-9 test total)                |
| `tosc`          | Social connectedness score (SCS test total)       |
| `toas`          | Acculturative stress score (ASISS test total)     |

## Key Analyses

- Compare depression risk between international and domestic students  
- Examine how length of stay correlates with depression, social connectedness, and acculturative stress among international students  

Example query to summarize depression and related scores by length of stay for international students:

```sql
SELECT stay, COUNT(*) AS count_int, 
       ROUND(AVG(todep), 2) AS average_phq, 
       ROUND(AVG(tosc), 2) AS average_scs, 
       ROUND(AVG(toas), 2) AS average_as
FROM students
WHERE stay IS NOT NULL 
  AND inter_dom = 'Inter'
GROUP BY stay
ORDER BY stay DESC;
```

## Links

- **DataCamp Project:** [Analyzing Students' Mental Health
](https://app.datacamp.com/learn/projects/analyzing_students_mental_health/guided/SQL)  
- **Learning Track:** [Associate Data Engineer in SQL](https://www.datacamp.com/completed/statement-of-accomplishment/track/47ec0e5d34abb761796b9f55d0f7d3a09d98c700)
