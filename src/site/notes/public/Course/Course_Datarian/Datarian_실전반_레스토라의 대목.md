---
{"dg-publish":true,"permalink":"/public/course/course-datarian/datarian/","tags":["SUBQUERY"],"created":"2025-08-27T14:55:04.970+09:00","updated":"2025-08-29T16:08:46.143+09:00"}
---

https://solvesql.com/problems/high-season-of-restaurant/

```mysql
-- 1500 넘는 요일  

-- SELECT

--   day

--   , sum(total_bill) as `sum_total_bill`

-- from tips

-- group by 1

-- having sum(total_bill) >= 1500

-- ;

  

-- result

select

  *

from tips

where day in (

  SELECT

    day

  from tips

  group by 1

  having sum(total_bill) >= 1500

)
```