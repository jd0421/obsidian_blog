---
{"dg-publish":true,"permalink":"/public/course/course-datarian/datarian/","created":"2025-08-29T15:25:36.282+09:00","updated":"2025-08-29T16:08:46.703+09:00"}
---

https://solvesql.com/problems/bike-rent-stats/

대여, 반납 station_id 가 소속된 local(지자체) 정보를 나타내는 컬럼을 생성
all_rent : rent_at의 전체 count, not distinct 
same_local : 대여, 반납 station_id가 소속된 local 이 같은 경우 return at 값, 아닌 경우 null 값 처리,  return_at 전체 count, not distinct
diff_local : 대여, 반납 station_id 가 소속된 local이 다른 경우 return at 값, 아닌 경우 null 값 처리, return_at 전체 count, not distinct
기간 필터는 datetime 형식인 경우 filter 조건도 datetime 으로 진행하기 

```mysql
  

with step1 as (

  SELECT

    rh.bike_id

    , rh.rent_at

    , rh.rent_station_id

    , rent_s.local as rent_station_local

    , rh.return_at

    , rh.return_station_id

    , return_s.local as return_station_local

  from rental_history rh

    inner join station rent_s on rh.rent_station_id = rent_s.station_id

    inner join station return_s on rh.return_station_id = return_s.station_id

  

  where

    rh.rent_at between '2021-01-01 00:00:00' and '2021-01-31 23:59:59'

    and rh.return_at between '2021-01-01 00:00:00' and '2021-01-31 23:59:59'

)

  

select

  rent_station_local as local

  , count(rent_at) as all_rent

  , count(case when rent_station_local = return_station_local then return_at else null end) as same_local

  , count(case when rent_station_local != return_station_local then return_at else null end) as diff_local

from step1

group by 1

order by 2 desc

-- SELECT

--   *

-- from step1

-- limit 100

;
```

