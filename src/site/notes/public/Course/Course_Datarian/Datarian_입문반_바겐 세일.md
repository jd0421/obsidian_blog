---
{"dg-publish":true,"permalink":"/public/course/course-datarian/datarian/","created":"2025-08-29T15:39:20.151+09:00","updated":"2025-08-29T16:08:46.784+09:00"}
---

https://solvesql.com/problems/bargain-sale/


전체 상품 판매 개수가 10개 이상
80% 이상 할인 판매 상품이 적어도 1개 이상인 케이스
```mysql
  

select

  order_date

  , sum(case when discount >= 0.8 then quantity end) as `big_discount_items`

  , sum(quantity) as `all_items`

from records

group by 1

HAVING all_items >= 10 and big_discount_items >= 1

order by 2 desc

  

;
```