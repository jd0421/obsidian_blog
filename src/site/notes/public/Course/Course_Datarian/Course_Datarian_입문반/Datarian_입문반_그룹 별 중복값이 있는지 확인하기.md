---
{"dg-publish":true,"permalink":"/public/course/course-datarian/course-datarian/datarian/","created":"2025-08-29T12:13:51.346+09:00","updated":"2025-08-29T16:08:46.358+09:00"}
---

https://solvesql.com/problems/duplicate-in-group/

```mysql
select

  quartet

  , x

  , count(x) as `cnt`

from points

group by 1, 2

having `cnt` >= 2

;
```