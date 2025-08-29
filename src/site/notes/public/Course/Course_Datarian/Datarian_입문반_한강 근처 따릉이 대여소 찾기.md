---
{"dg-publish":true,"permalink":"/public/course/course-datarian/datarian/","created":"2025-08-29T12:27:48.035+09:00","updated":"2025-08-29T16:08:46.429+09:00"}
---

https://solvesql.com/problems/bike-station-with-han-river/



```MYSQL
select

  station_id

  , name

  , local

  , address

from station

where local in ('광진구', '동작구', '마포구', '성동구', '영등포구')

;
```