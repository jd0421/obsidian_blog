---
{"dg-publish":true,"permalink":"/public/course/course-datarian/datarian-week-1-0/","created":"2024-12-06T18:39:06.164+09:00","updated":"2025-08-29T16:08:45.722+09:00"}
---


- FLOW
	- DESC 로 컬럼 별 타입 확인 
	```MYSQL
	DESC 테이블명 ; 
```
	- #LIMIT 으로 1차 출력하여 어떻게 생겼는지 확인

# SITES
- [W3CSCHOOLS](https://www.w3schools.com/sql/func_mysql_max.asp)
- [MYSQL 공식 문서](https://dev.mysql.com/doc/refman/8.0/en/string-functions.html) 
- [mysql regexp](https://dadev.tistory.com/entry/MY-SQL-%EC%A0%95%EA%B7%9C%EC%8B%9D-REGEXP)
- [SQL 입문반 Week 1 복습 자료](https://datarian.notion.site/SQL-Week-1-389af2de3740486d8db85dd804475dcd)
- [STRING FUNCTIONS AND OPERATORS](https://dev.mysql.com/doc/refman/8.0/en/string-functions.html#function_format)
- [Numeric Functions and Operators](https://dev.mysql.com/doc/refman/8.0/en/numeric-functions.html)
- [max syntax](https://dev.mysql.com/doc/search/?q=MAX%28%29+SYNTAX)
- [deepl](https://www.deepl.com/ko/pro)
- [mysql cloumn type check](https://limjunho.github.io/2021/10/16/MySql-type-check.html)
- [REGEXP](https://velog.io/@gillog/MySQL-REGEXPRegular-Expression%EC%A0%95%EA%B7%9C-%ED%91%9C%ED%98%84%EC%8B%9D)
- [MySQL NOT REGEXP operator](https://www.w3resource.com/mysql/string-functions/mysql-not-regexp-function.php)
- [[WHERE절 글자 수 조건 걸기](https://ggojang.com/144)](https://ggojang.com/144)
- [홀짝수](https://velog.io/@ljs7463/MySQL-%ED%99%80%EC%88%98-%EC%A7%9D%EC%88%98-%EC%B6%9C%EB%A0%A5)

# 생각해볼 것들
- 클린코딩

# Retrospect
- 파스텔과 크레용으로 그린 작품
	- Pastel, pastel, crayon, Crayon 
	- https://solvesql.com/problems/artworks-with-pastel-crayon/

```mysql
SELECT object_number
		 , title
		 , medium
		 , acquisition_date
		 , department
FROM artworks
WHERE medium LIKE '%pastel%'
    OR medium LIKE '%Pastel%'
    OR medium LIKE '%crayon%'
    OR medium LIKE '%Crayon%'
ORDER BY acquisition_date DESC
```


# 요약
```MYSQL
SELECT name
     , address
FROM station
WHERE local = '광진구'
ORDER BY 
	updated_at DESC, 
	station_id ASC    -- 2개 이상 조건으로 정렬하기
LIMIT 5
```


---
# 내용정리

-  주석은 두 가지
	- `--`
	- `/* */`

- #DISTINCT / 중복제거
	- SELECT DISTINCT local from station ;
	- 컬럼 2개 이상일 때 중복 제거 
		select distinct local, type, from station
			모든 컬럼이 같은 경우에만 동일한 데이터 다 라고 판단함

- #LIMIT / head기능과 동일

- #WHERE 조건 
	- SELECT name from station where local = '마포구';

- #DESC / 컬럼별 데이터타입 조회 


- #IN #BETWEEN __많이 써봐야겠음__
```MYSQL
SELECT *
	from station
	where lat > (SELECT lat from station where name = '서울북부지방법원');
	WHERE local in ('');
	WHERE lat BETWEEN x and y
```

- #IS_NULL, #IS_NOT_NULL  
```MYSQL
SELECT *
from rental_history
WHERE bike_id = "SPB-21745"
	and distance is null;
```

- #LIKE #NOT_LIKE #정규표현식 #REGEXP #AND #LIKE #NOT_LIKE __많이 써봐야겠음__
```MYSQL
SELECT *
from station
where address like "%망원동%"
```

- 이스케이프 문자 
```MYSQL
SELECT *
FROM olist_order_reviews_dataset
WHERE review_comment_message LIKE '%\_%'
LIMIT 10
```

```MYSQL
-- 이건 문법적으로 올바르지 않습니다
SELECT title, genres, language, netflix, runtime, imdb
from movies
where title
  not like ('A%'
  OR 'E%'
  OR 'I%'
  OR 'O%'
  OR 'U%'
  )
  AND runtime < 5

-- 문법적으로 올바른 쿼리문
SELECT title, genres, language, netflix, runtime, imdb
from movies
where runtime < 5
  AND title NOT LIKE 'A%'
  AND title NOT LIKE 'E%'
  AND title NOT LIKE 'I%'
  AND title NOT LIKE 'O%'
  AND title NOT LIKE 'U%'
```

#ORDER_BY  
```MYSQL
SELECT *
from station
ORDER BY station_id desc;
```
- 정렬 조건이 2개 이상일 때 
```mysql
SELECT *
from station
where local LIKE '광진구'
ORDER BY updated_at ASC, station_id ASC;
```

```mysql
tip_ratio 값 desc 순으로 출력되도록 코드를 수정 

SELECT 
  total_bill, 
  tip, 
  format(tip/total_bill*100, 2) AS tip_ratio, 
  sex, 
  smoker, 
  size
from tips
WHERE total_bill >= 30
ORDER BY format(tip/total_bill*100, 2) DESC;

```
-  FORMAT은 문자형으로 변경되므로, FORMAT 적용 후 ORDER BY 적용 시 문자열 기준으로 ORDER 가 됨
- 순서 염두 시 ROUND 를 활용해야 함 

- 문자열 자르기, 붙이기 
#LEFT #RIGHT #SUBSTR #CONCAT
```MYSQL
SELECT LEFT('Week1마지막연습문제', 5) -- 왼쪽 다섯 글자
SELECT RIGHT('Week1마지막연습문제', 4) -- 오른쪽 네 글자
SELECT SUBSTR('Week1마지막연습문제', 1, 5) -- 첫 번째 글자부터, 글자 5개
SELECT SUBSTR('Week1마지막연습문제', 6, 3) -- 여섯 번째 글자부터, 글자 3개
SELECT SUBSTR('Week1마지막연습문제', 6) -- 여섯 번째 글자부터, 끝까지
SELECT CONCAT('My', 'S', 'QL');
SELECT CONCAT('My', NULL, 'QL');
```

#SUBQUERY __많이 써봐야겠음__
- 서브쿼리문은 반드시 괄호 끼고 해야 함 
```mysql
SELECT day, time, size
FROM tips
WHERE total_bill = (SELECT max(total_bill) from tips);
```

#ROUND #CEILING #CEIL #FORMAT #FLOOR
```mysql
round() : 소수점 반올림
SELECT ROUND(5.842901, 3) -- 소수점 네 번째 자리에서 반올림, 세 번째까지 표시

CEILING() CEIL() : 소수점 올림
SELECT CEIL(5.5) -- 올림

floor() : 소수점 내림
SELECT FLOOR(5.5) -- 내림

FORMAT() : 숫자를 반올림하고 '#,###,###.##’ 형태로 보고 싶을 때
SELECT FORMAT(13000.36, 1)

```

q3. '서울북부지방법원' 정류소보다 위도(lat) 가 큰 정류소 데이터를 뽑아주세요 
	1. station 테이블에서 '서울북부지방법원' 정류소의 위도(lat)를 찾는다
	2. station 테이블에서 위도가 '서울북부지방법원' 정류소보다 큰 정류소의 목록을 뽑는 쿼리를 작성한다
		SELECT *
		from station
		where lat > (SELECT lat from station where name = '서울북부지방법원')


- **테이블(table)** : 표
- **로우(row)** : 행, 데이터
- **컬럼(column)** : 열, 각각의 데이터가 가지고 있는 특성
---
