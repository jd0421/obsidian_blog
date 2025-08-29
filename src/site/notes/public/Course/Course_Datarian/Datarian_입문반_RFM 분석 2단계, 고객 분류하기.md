---
{"dg-publish":true,"permalink":"/public/course/course-datarian/datarian-rfm-2/","created":"2025-08-29T13:26:19.914+09:00","updated":"2025-08-29T16:08:46.584+09:00"}
---

https://solvesql.com/problems/rfm-2-classifying/

```mysql
select

  case when last_order_date between date_sub('2021-01-01', interval 1 month) and '2021-01-01' then 'recent' else 'past' end as `recency`

  , case when cnt_orders >= 3 then 'high' else 'low' end as `frequency`

  , case when sum_sales >= 500 then 'high' else 'low' end as `monetary`

  , count(distinct customer_id) as `customers`

from customer_stats

group by 1, 2, 3

;
```