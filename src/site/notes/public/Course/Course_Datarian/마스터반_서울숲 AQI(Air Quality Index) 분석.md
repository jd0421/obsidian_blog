---
{"dg-publish":true,"permalink":"/public/course/course-datarian/aqi-air-quality-index/","tags":["CASE","CTE함수"],"created":"2025-08-26T15:50:16.370+09:00","updated":"2025-08-29T16:08:45.884+09:00"}
---

https://solvesql.com/problems/seoulforest-aqi/

```mysql
with step1 as (

  SELECT

    *

    , CASE

      when pm2_5 between 0 and 9.0 then 1

      when pm2_5 between 9.1 and 35.4 then 2

      when pm2_5 between 35.5 and 55.4 then 3

      when pm2_5 between 55.5 and 125.4 then 4

      when pm2_5 between 125.5 and 225.4 then 5

      when pm2_5 >= 225.5 then 6

    end as us_aqi_level

  FROM measurements

)

  

, step2 as (

  select

    us_aqi_level

    , count(case when measured_at between '2022-01-01' and '2022-03-31' then us_aqi_level else null end) as q1

    , count(case when measured_at between '2022-04-01' and '2022-06-30' then us_aqi_level else null end) as q2

    , count(case when measured_at between '2022-07-01' and '2022-09-30' then us_aqi_level else null end) as q3

    , count(case when measured_at between '2022-10-01' and '2022-12-31' then us_aqi_level else null end) as q4

  from step1

  group by 1

  order by 1 asc

)

  

select

  us_aqi_level

  , round(q1 / sum(q1) over() * 100, 2) as q1

  , round(q2 / sum(q2) over() * 100, 2) as q2

  , round(q3 / sum(q3) over() * 100, 2) as q3

  , round(q4 / sum(q4) over() * 100, 2) as q4

from step2
```