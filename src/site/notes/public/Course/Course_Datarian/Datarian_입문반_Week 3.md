---
{"dg-publish":true,"permalink":"/public/course/course-datarian/datarian-week-3/","tags":["SQL","MySQL"],"created":"2024-12-04T12:46:33.680+09:00","updated":"2025-08-29T16:08:45.639+09:00"}
---

- [[입문반 프로젝트 안내 \|입문반 프로젝트 안내 ]]
- [데이터 분석을 위한 sql 참고도서 추천](https://datarian.io/blog/sql-books?utm_source=sql-camp&utm_medium=camp&utm_campaign=referral&utm_content=sql-basic) 
- EDA 하는 방법에 정답은 없지만 자기만의 체크리스트를 가지고 있으면 익숙하지 않은 환경에서 데이터를 빠르게 파악하는 데에 도움이 될 수 있습니다. 
- 본인만의 체크리스트를 만들기 전에는 캠프에서 제공해 드리는 EDA 항목을 참고해서 응용해 보세요.
- 또, EDA를 해도 데이터를 읽는데 오해나 실수가 있을 수는 있습니다. 하지만 아예 안 하는 것보다는 백배, 천배 낫습니다!

- [데이터리안 SQL 캠프 입문반 | Week 3 - RFM 분석](https://docs.google.com/spreadsheets/d/1Zxuz72DTNqgFjynZ5Hpn7ejiBuNzFbt59dcncQVa_V0/edit?gid=2003586152#gid=2003586152) 

- RFM 분석
	- case if, group by

- 피벗테이블
	- step 1-3 까지 쭉 짤 줄 알아야 함
- #UNION #UNION_ALL
	- 형식이 같아야 함, 컬럼 개수와 컬럼 데이터 형식 
	- UNION : 중복을 제외하고 위아래 데이터 붙이기
	- UNION ALL : 중복 유지하고 위아래 데이터 붙이기
```SQL
SELECT *
FROM customer_before_2021

UNION 

SELECT *
FROM customer_before_2022

```

```SQL
SELECT *
FROM customer_before_2021

UNION ALL

SELECT *
FROM customer_before_2022

```

- #JOIN
* INNER JOIN 은 가장 기본적인 JOIN 방법이라 그냥 JOIN이라고 작성해도 MYSQL 에서 INNER JOIN으로 인식합니다. 
* 테이블 명에 ALIAS 설정 가능, 설정 이후 기존 테이블명 사용 시 에러 발생
```sql
SELECT
    c.country
    , SUM(oi.price * oi.quantity) AS sales

FROM
  orders AS o
    INNER JOIN customers AS c ON o.customer_id = c.customer_id
    INNER JOIN order_items AS oi ON o.order_id = oi.order_id

WHERE
  oi.order_id NOT LIKE "C%"
  AND (o.order_date BETWEEN '2019-01-01' AND '2019-01-31')

GROUP BY
  c.country

ORDER BY
  sales DESC
;
```

- 입문반 프로젝트 안내
- Week 3 마무리 
- 입문반 Week 3 복습자료 https://datarian.notion.site/SQL-Week-3-9457f7992042493481d1e65f25f1fabe?pvs=4