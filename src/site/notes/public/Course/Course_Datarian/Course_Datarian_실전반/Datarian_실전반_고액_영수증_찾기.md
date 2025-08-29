---
{"dg-publish":true,"permalink":"/public/course/course-datarian/course-datarian/datarian/","tags":["SUBQUERY"],"created":"2025-08-27T15:04:01.556+09:00","updated":"2025-08-29T16:08:46.181+09:00"}
---


https://solvesql.com/problems/highest-bill-per-size/


```mysql
-- 레스토랑에 함께 방문한 일행 수가 많아질수록 높은 금액을 결제하는지

-- 일행 수마다 결제 금액이 가장 높았던 결제 내역만 출력하는 쿼리

-- SELECT size, max(total_bill) as `max_total_bill`
-- from tips
-- group by 1


select *

from tips

where (size, total_bill) in (

  SELECT size, max(total_bill) as `max_total_bill`

  from tips

  group by 1

)

order by size asc

  

;
```