---
{"dg-publish":true,"permalink":"/public/course/course-datarian/datarian-amy/","created":"2025-08-29T15:41:03.787+09:00","updated":"2025-08-29T16:08:46.805+09:00"}
---



https://solvesql.com/problems/ott-used-by-amy/

케이스분기문

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