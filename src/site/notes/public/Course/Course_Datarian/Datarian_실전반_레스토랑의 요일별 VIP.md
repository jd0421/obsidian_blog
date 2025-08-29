---
{"dg-publish":true,"permalink":"/public/course/course-datarian/datarian-vip/","tags":["SUBQUERY"],"created":"2025-08-27T14:59:48.465+09:00","updated":"2025-08-29T16:08:46.200+09:00"}
---

https://solvesql.com/problems/restaurant-vip/

```MYSQL
-- 최고 금액

-- select

--   day

--   , max(total_bill) as max_total_bill

-- from tips

-- group by 1

  

-- result

select

  *

from

  tips

where (day, total_bill) in (

  select

    day

    , max(total_bill) as max_total_bill

  from tips

  group by 1

)

-- limit 10

;
```

