---
{"dg-publish":true,"permalink":"/public/course/course-datarian/rfm-1-rfm/","created":"2025-08-29T13:25:56.443+09:00","updated":"2025-08-29T16:08:46.566+09:00"}
---

https://solvesql.com/problems/rfm-1-scoring/



```mysql
select

  customer_id

  , last_order_date

  , cnt_orders

  , sum_sales

  , case when last_order_date between date_sub('2021-01-01', interval 1 month) and '2021-01-01' then 'recent' else 'past' end as `recency`

  , case when cnt_orders >= 3 then 'high' else 'low' end as `frequency`

  , case when sum_sales >= 500 then 'high' else 'low' end as `monetary`

from customer_stats

;
```