---
{"dg-publish":true,"permalink":"/public/course/course-datarian/datarian/","tags":["Session"],"created":"2025-08-27T16:46:34.745+09:00","updated":"2025-08-29T16:08:46.296+09:00"}
---

https://solvesql.com/problems/session-scroll/

```
-- 입문반 페이지를 본 세션

WITH STEP1 AS (

  SELECT

  user_pseudo_id

  , ga_session_id

  , event_timestamp_kst

FROM

  ga

)

,

pv AS (SELECT

  user_pseudo_id

  , ga_session_id

  , event_timestamp_kst

FROM

  ga

WHERE

  page_title = '백문이불여일타 SQL 캠프 입문반'

  AND event_name = 'page_view')

,

scroll AS (SELECT

  user_pseudo_id

  , ga_session_id

  , event_timestamp_kst

FROM

  ga

WHERE

  page_title = '백문이불여일타 SQL 캠프 입문반'

  AND event_name = 'scroll')

  
  

SELECT

  COUNT(DISTINCT STEP1.user_pseudo_id, STEP1.ga_session_id) AS total

  , COUNT(DISTINCT STEP1.user_pseudo_id, STEP1.ga_session_id) - COUNT(DISTINCT pv.user_pseudo_id, pv.ga_session_id) AS pv_no

  , COUNT(DISTINCT pv.user_pseudo_id, pv.ga_session_id) - COUNT(DISTINCT scroll.user_pseudo_id, scroll.ga_session_id) AS pv_yes_scroll_no

  , COUNT(DISTINCT scroll.user_pseudo_id, scroll.ga_session_id) AS pv_yes_scroll_yes

FROM STEP1

  LEFT JOIN pv ON STEP1.user_pseudo_id = pv.user_pseudo_id

              AND STEP1.ga_session_id = pv.ga_session_id

              AND STEP1.event_timestamp_kst <= pv.event_timestamp_kst

  LEFT JOIN scroll ON pv.user_pseudo_id = scroll.user_pseudo_id

                  AND pv.ga_session_id = scroll.ga_session_id

                  AND pv.event_timestamp_kst <= scroll.event_timestamp_kst

  
  
  
  
  
  

-- pv AS (SELECT

--   user_pseudo_id

--   , ga_session_id

--   , event_timestamp_kst AS pv_at

-- FROM

--   ga

-- WHERE

--   page_title = '백문이불여일타 SQL 캠프 입문반'

--   AND event_name = 'page_view')

-- ,

-- -- 입문반 페이지를 스크롤한 세션

-- scroll AS (SELECT

--   user_pseudo_id

--   , ga_session_id

--   , event_timestamp_kst AS scroll_at

-- FROM

--   ga

-- WHERE

--   page_title = '백문이불여일타 SQL 캠프 입문반'

--   AND event_name = 'scroll')

  
  

-- -- left join 하는 이유, inner join을 하게 되면 pv, scroll 교집합 세션만 남게 되고,

-- -- pv(페이지 본 세션 수) 가 날라가기 때문에 left join으로 진행

  

-- SELECT

--   , COUNT(DISTINCT pv.user_pseudo_id, pv.ga_session_id) AS pv_no

--   , COUNT(DISTINCT scroll.user_pseudo_id, scroll.ga_session_id) AS scroll_after_pv

--   , COUNT(DISTINCT scroll.user_pseudo_id, scroll.ga_session_id) / COUNT(DISTINCT pv.user_pseudo_id, pv.ga_session_id) AS pv_scroll_rate

-- FROM pv

--   LEFT JOIN scroll ON pv.user_pseudo_id = scroll.user_pseudo_id

--                   AND pv.ga_session_id = scroll.ga_session_id

--                   AND pv.pv_at <= scroll.scroll_at

  

-- FROM STEP1

--   LEFT JOIN pv ON
```