---
{"dg-publish":true,"permalink":"/public/course/course-datarian/course-datarian/datarian-week-1/","tags":["MySQL","SQL"],"created":"2024-12-02T14:42:47.868+09:00","updated":"2025-08-29T16:08:45.593+09:00"}
---

[[public/Course/Course_Datarian/Course_Datarian_입문반/Datarian_입문반_Week 1 첫 걸음_0차\|Datarian_입문반_Week 1 첫 걸음_0차]]


- 수업자료 
	- [SQL 입문반 Week 1 복습 자료](https://datarian.notion.site/SQL-Week-1-389af2de3740486d8db85dd804475dcd)

- SITES
	- [W3CSCHOOLS](https://www.w3schools.com/sql/func_mysql_max.asp)
	- [MYSQL 공식 문서](https://dev.mysql.com/doc/refman/8.0/en/string-functions.html) 
	- [mysql regexp](https://dadev.tistory.com/entry/MY-SQL-%EC%A0%95%EA%B7%9C%EC%8B%9D-REGEXP)
	- [STRING FUNCTIONS AND OPERATORS](https://dev.mysql.com/doc/refman/8.0/en/string-functions.html#function_format)
	- [Numeric Functions and Operators](https://dev.mysql.com/doc/refman/8.0/en/numeric-functions.html)
	- [max syntax](https://dev.mysql.com/doc/search/?q=MAX%28%29+SYNTAX)
	- [deepl](https://www.deepl.com/ko/pro)
	- [mysql cloumn type check](https://limjunho.github.io/2021/10/16/MySql-type-check.html)
	- [REGEXP](https://velog.io/@gillog/MySQL-REGEXPRegular-Expression%EC%A0%95%EA%B7%9C-%ED%91%9C%ED%98%84%EC%8B%9D)
	- [MySQL NOT REGEXP operator](https://www.w3resource.com/mysql/string-functions/mysql-not-regexp-function.php)
	- [[WHERE절 글자 수 조건 걸기](https://ggojang.com/144)](https://ggojang.com/144)
	- [홀짝수](https://velog.io/@ljs7463/MySQL-%ED%99%80%EC%88%98-%EC%A7%9D%EC%88%98-%EC%B6%9C%EB%A0%A5)

- 생각해볼 것들
	- 클린코딩



- 내용정리
	- [[public/Course/Course_Datarian/SQL 주석\|SQL 주석]]
	- 테이블(table) : 표
	- 로우(row) : 행, 데이터
	- 컬럼(column) : 열, 각각의 데이터가 가지고 있는 특성

- IN BETWEEN 
	```MYSQL
	SELECT *
		from station
		where lat > (SELECT lat from station where name = '서울북부지방법원');
		WHERE local in ('');
		WHERE lat BETWEEN x and y
	```
- LIKE NOT_LIKE 정규표현식 REGEXP AND LIKE NOT_LIKE
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

- 이스케이프 문자 
	```MYSQL
	SELECT *
	FROM olist_order_reviews_dataset
	WHERE review_comment_message LIKE '%\_%'
	LIMIT 10
	```

- ORDER_BY  
	- 정렬 조건이 2개 이상일 때 
	```mysql
	SELECT *
	from station
	where local LIKE '광진구'
	ORDER BY updated_at ASC, station_id ASC;
```
- tip_ratio 값 desc 순으로 출력되도록 코드를 수정 
	-  FORMAT은 문자형으로 변경되므로, FORMAT 적용 후 ORDER BY 적용 시 문자열 기준으로 ORDER 가 됨
	- 순서 염두 시 ROUND 를 활용해야 함 
	```mysql
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

- 문자열 자르기, 붙이기 / LEFT RIGHT SUBSTR CONCAT
```MYSQL
SELECT LEFT('Week1마지막연습문제', 5) -- 왼쪽 다섯 글자
SELECT RIGHT('Week1마지막연습문제', 4) -- 오른쪽 네 글자
SELECT SUBSTR('Week1마지막연습문제', 1, 5) -- 첫 번째 글자부터, 글자 5개
SELECT SUBSTR('Week1마지막연습문제', 6, 3) -- 여섯 번째 글자부터, 글자 3개
SELECT SUBSTR('Week1마지막연습문제', 6) -- 여섯 번째 글자부터, 끝까지
SELECT CONCAT('My', 'S', 'QL');
SELECT CONCAT('My', NULL, 'QL');
```

- SUBQUERY 
	- 서브쿼리문은 반드시 괄호 끼고 해야 함 
	```mysql
	SELECT day, time, size
	FROM tips
	WHERE total_bill = (SELECT max(total_bill) from tips);
	```
- ROUND CEILING CEIL FORMAT FLOOR
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

