---
{"dg-publish":true,"permalink":"/public/course/course-datarian/course-datarian/datarian/","created":"2025-08-27T14:21:04.710+09:00","updated":"2025-08-29T16:08:45.989+09:00"}
---

https://solvesql.com/problems/average-purchase-cycle/


```mysql

with step1 as (

  select

    order_id

    , order_date

    , customer_id

    , row_number() over(partition by customer_id order by order_date) as rnk

    , lag(order_date) over(partition by customer_id order by order_date) as `order_date_lag`

  from orders

  where

    order_id not like 'C%'

    and customer_id is not null

)

  

, step2 as (

  select

    *

    , order_date - order_date_lag as `diff`

    , count(order_id) over(partition by customer_id) as order_cnt

  from step1

)

  

-- select *

-- from step2

-- limit 100

-- ;

  

select

  -- 4718 as `cnt_customers` -- count(distinct customer_id) as `cnt_customers` -- 4718

  -- , 1577 as `cnt_only_first_order` -- count(distinct case when order_cnt = 1 then customer_id else null end) as `cnt_only_first_order` -- 1577

  *  

  -- count(distinct case when order_cnt = 2 then customer_id else null end) as `cnt_second_order`

  -- , 3141 as `cnt_second_order` -- count(distinct case when order_cnt = 2 then customer_id else null end) as `cnt_second_order`

  -- , 82.33 as `avg_days_to_second_order` -- round(avg(diff), 2) as `avg_days_to_second_order`

  -- ,

from step2

where customer_id = '12347'

limit 100

  
  

-- SELECT

--   *

-- from step2

-- where order_id = '579171'

-- order by diff desc

-- limit 100

  

  -- count(distinct order_id) as `cnt_customers` -- 7859

  -- , count(order_id in (select order_id, count(rnk) from step2 group by 1 where count(rnk) = 1)) as `cnt_only_first_order`

  -- count(select order_id from step2 where rnk= 1)  -- 4718  

  -- , count(distinct (select order_id from step2 where rnk = 1)) as `cnt_only_first_order`

  
  

  -- customer_id

  -- , count(distinct customer_id) as `cnt_customers`

  -- , count()

  -- count(*) -- 19789

  -- count(*) as `cnt_customers`

  -- , case when

  

;

```