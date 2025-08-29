---
{"dg-publish":true,"permalink":"/public/course/course-datarian/course-datarian/datarian-bmi/","created":"2025-08-29T12:22:30.487+09:00","updated":"2025-08-29T16:08:46.410+09:00"}
---




https://solvesql.com/problems/bmi-of-women-archery/

```MYSQL
select athlete_id, medal, sex, weight, height, round(weight / pow(height / 100, 2), 2) as bmi  

from records

where game_id = 49

  and event_id = 39

;
```
#POWER
