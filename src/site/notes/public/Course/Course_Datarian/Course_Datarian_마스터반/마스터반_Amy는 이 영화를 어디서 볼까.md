---
{"dg-publish":true,"permalink":"/public/course/course-datarian/course-datarian/amy/","tags":["CASE"],"created":"2025-08-26T13:59:14.079+09:00","updated":"2025-08-29T16:08:45.792+09:00"}
---

https://solvesql.com/problems/ott-used-by-amy/
 2021년 개봉 영화 목록
 `platform` 컬럼에 Amy가 가장 자주 사용하는 플랫폼의 정보만 기록합니다. 
 Amy가 OTT 플랫폼을 사용하는 빈도는 netflix > prime_video > disney_plus > hulu 순 입니다.

```mysql
  

select

  title,

  `year`,

  genres,

  directors,

  CASE

    when netflix = 1 then 'netflix'

    when prime_video = 1 then 'prime_video'

    when disney_plus = 1 then 'disney_plus'

    when hulu = 1 then 'hulu'

  end as `platform`

from movies

where year = 2021

order by title asc

;
```