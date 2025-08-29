---
{"dg-publish":true,"permalink":"/public/course/course-datarian/course-datarian/datarian-stickiness/","created":"2025-08-27T16:17:36.162+09:00","updated":"2025-08-29T16:08:46.255+09:00"}
---

https://solvesql.com/problems/stickiness-of-shoppingmall/

1차 테이블에서 정의된 값을 기준으로 2차 테이블의 값을 나눈다 

```mysql
SELECT

  r1.order_date as `dt`

  , count(distinct customer_id) as `dau`

  , (select count(distinct customer_id) from records `r2` where r2.order_date between date_sub(r1.order_date, interval 6 day) and r1.order_date) as `wau`

from records r1

where date_format(order_date, '%Y-%m') = '2020-11'

group by

  dt

order by

  dt asc
```