---
{"dg-publish":true,"permalink":"/public/course/course-datarian/course-datarian/datarian/","tags":["REGEXP"],"created":"2025-08-27T14:42:37.098+09:00","updated":"2025-08-29T16:08:46.121+09:00"}
---


```mysql

select

  title

  , genres

  , language

  , netflix

  , runtime

  , imdb

from movies

where runtime < 5

  and title not REGEXP '^[AEIOU]'

  

;
```