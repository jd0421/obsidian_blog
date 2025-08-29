---
{"dg-publish":true,"permalink":"/public/course/course-datarian/datarian/","created":"2025-08-29T12:14:52.206+09:00","updated":"2025-08-29T16:08:46.375+09:00"}
---

https://solvesql.com/problems/rich-customer/

```mysql
select

  day

  , time

  , size

from tips

where total_bill = (select max(total_bill) from tips)

limit 10;
```