---
{"dg-publish":true,"permalink":"/public/course/course-datarian/course-datarian/datarian/","tags":["Session"],"created":"2025-08-27T16:36:44.543+09:00","updated":"2025-08-29T16:08:46.276+09:00"}
---



https://solvesql.com/problems/session-pv/

```mysql
  

with step1 as (

  select

    count(distinct user_pseudo_id, ga_session_id) as `total` # 1644

  from ga

  -- where

  --   page_title = "백문이불여일타 SQL 캠프 입문반" and event_name = "page_view"

)

  

, step2 as (

  select

    count(distinct user_pseudo_id, ga_session_id) as `pv_yes` # 1135

  from ga

  where

    page_title = "백문이불여일타 SQL 캠프 입문반"

    and event_name = "page_view"

)

  

SELECT

  step1.total

  , step1.total - step2.pv_yes as `pv_no`

  , step2.pv_yes  

from step1, step2
```