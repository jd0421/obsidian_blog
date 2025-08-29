---
{"dg-publish":true,"permalink":"/public/course/course-datarian/course-datarian/datarian/","created":"2025-08-29T12:16:56.680+09:00","updated":"2025-08-29T16:08:46.393+09:00"}
---



https://solvesql.com/problems/find-high-rated-movies/

```mysql
select

  title

  , year

  , age

  , imdb

  , rotten_tomatoes

from

  movies

WHERE

  netflix = '1'

  and year = '2020'

  and (imdb >= '9.0' or rotten_tomatoes >= 90)
```