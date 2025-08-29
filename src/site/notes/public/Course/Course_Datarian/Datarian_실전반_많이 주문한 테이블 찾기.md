---
{"dg-publish":true,"permalink":"/public/course/course-datarian/datarian/","tags":["SUBQUERY"],"created":"2025-08-27T14:34:43.123+09:00","updated":"2025-08-29T16:08:46.049+09:00"}
---

https://solvesql.com/problems/find-tables-with-high-bill/

간단한 쿼리는 서브쿼리로 가능
유지보수를 목적으로 한다면 cte 테이블로 관리

```mysql
select

  *

from tips

where total_bill >= (select avg(total_bill) from tips)

;
```