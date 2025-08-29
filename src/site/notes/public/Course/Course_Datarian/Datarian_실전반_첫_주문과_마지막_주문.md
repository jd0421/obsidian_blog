---
{"dg-publish":true,"permalink":"/public/course/course-datarian/datarian/","tags":["datae_format"],"created":"2025-08-27T14:29:47.491+09:00","updated":"2025-08-29T16:08:46.070+09:00"}
---

https://solvesql.com/problems/first-and-last-orders/

```mysql
select

  date_format(min(order_purchase_timestamp), '%Y-%m-%d') as `first_order_date`

  , date_format(max(order_purchase_timestamp), '%Y-%m-%d') as `last_order_date`

from olist_orders_dataset

limit 100

;
```