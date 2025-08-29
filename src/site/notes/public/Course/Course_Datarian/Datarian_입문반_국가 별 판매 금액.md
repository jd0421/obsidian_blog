---
{"dg-publish":true,"permalink":"/public/course/course-datarian/datarian/","created":"2025-08-29T15:35:16.017+09:00","updated":"2025-08-29T16:08:46.748+09:00"}
---

https://solvesql.com/problems/sales-per-country/

```mysql
with step1 as (

  select

    c.customer_id

    , c.country

    , o.order_id

    , o.order_date

    , oi.price * oi.quantity as `total_price`

  from customers as c

    inner join orders as o on c.customer_id = o.customer_id

    inner join order_items as oi on o.order_id = oi.order_id

  where date_format(o.order_date, "%Y-%m") = '2019-01'

    and o.order_id not like 'C%'

)

  

select

  country

  , sum(total_price) as `sales`

from step1

group by 1

order by 2 desc

;
```