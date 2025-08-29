---
{"dg-publish":true,"permalink":"/public/course/course-datarian/datarian/","created":"2025-08-29T13:50:32.099+09:00","updated":"2025-08-29T16:08:46.626+09:00"}
---

https://solvesql.com/problems/orders-of-singapore-customers/


싱가포르 고객을 먼저 CTE 로 FILTER
INNER JOIN 을 통해 타겟 테이블에 존재하는 값만 FILTER

```MYSQL
with step1 as (

  select

    customer_id

    , country

    -- distinct(country)

  from customers

  where country = 'Singapore'

)

  

select

  step1.country

  , step1.customer_id

  , o.order_date

  , o.order_id

from orders o inner join step1 on o.customer_id = step1.customer_id

order by order_date desc

;
```