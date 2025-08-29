---
{"dg-publish":true,"permalink":"/public/course/course-datarian/course-datarian/top-3/","tags":["ROW_NUMBER","DENSE_RANK","RANK"],"created":"2025-08-26T15:16:41.185+09:00","updated":"2025-08-29T16:08:45.925+09:00"}
---

https://solvesql.com/problems/top-3-bill/
구분 순서가 필요하면 ROW_NUMBER, DENSE_RANK, RANK 로 접근

```MYSQL
with step1 as (

  SELECT

    *

    , DENSE_RANK() OVER(PARTITION BY day ORDER BY total_bill desc) as rk

  FROM

    tips

)

select

  day

  , time

  , sex

  , total_bill

  -- , rk

from step1

where rk <= 3

;
```