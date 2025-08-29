---
{"dg-publish":true,"permalink":"/public/course/course-datarian/course-datarian/datarian-week-2/","tags":["MySQL","SQL"],"created":"2024-12-03T05:03:18.466+09:00","updated":"2025-08-29T16:08:45.616+09:00"}
---

- 뭘 배웠나
	- DBMS 뭐 써보셨어요?  묻는다면 MYSQL
	- COUNT()는 null 값 무시
	- SQL 입문반 WEEK 2 복습 자료 https://datarian.notion.site/SQL-Week-2-ffed78b13eed4687bf48721a7848a929?pvs=4

- link
	- 포트폴리오와 테크 블로그 https://datarian.io/player/content/1/lecture/1030
	- 사칙연산 - MYSQL 공식 문서 https://dev.mysql.com/doc/refman/8.0/en/arithmetic-functions.html
	- 연산함수 - MYSQL 공식 문서 https://dev.mysql.com/doc/refman/8.0/en/mathematical-functions.html
	- 14.7 Date and Time Functions https://dev.mysql.com/doc/refman/8.0/en/date-and-time-functions.html
	- 설득의 시작, 데이터 제대로 보여주는 법 5월 세미나 슬라이드 https://datarian.io/blog/slide-webinar-may
	- 사용자 행동 데이터 분석 (1) 사용자 행동 데이터 왜 필요할까요 https://datarian.io/blog/why-is-user-activity-log-analysis-important
	-  RFM 고객 세분화 분석 팁 3가지 https://datarian.io/blog/tips-for-customer-segmentation-analysis
	- 이탈 기준 정하기 https://datarian.io/blog/make-a-criterion-for-churn
	- https://boxnwhis.kr/
	- RFM 고객 세분화 분석에서 합리적으로 기준을 잡는 방법 https://datarian.io/blog/how-to-make-your-rfm-customer-segmentation-reasonable
	- RFM 고객 세분화 분석이란 무엇일까요 https://datarian.io/blog/what-is-rfm
	- **고객 행동 분석을 통한 E-commerce 마케팅 전략 제안** https://nebulous-snarl-ec3.notion.site/E-commerce-14c6284ed29580f69e8ae8c1ff19946f
	- 데이터 분석을 위한 SQL 참고도서 추천 https://datarian.io/blog/sql-books?utm_source=sql-camp&utm_medium=camp&utm_campaign=referral&utm_content=sql-basic

- [DATE_FORMAT()](https://oneul-losnue.tistory.com/123)

- 갱신 명령어는 잘 쓰지 않음
```MYSQL
INSERT INTO 테이블명 VALUES()
UPDATE 주소록 SET 컬럼명 = '' WHERE 이름 = '' -- 어떤 조건 해당 자만 변경할지
DELETE FROM 주소록 WHERE 이름 = '성함' -- 컬럼 삭제
```

- 집계함수 // Aggregate Function
```mysql
count() / sum() / avg() / min() / max()
```
- 숫자연산
```MYSQL
SELECT 2 + 2
SELECT 2 - 2
SELECT 2 * 2
SELECT 2 / 2 -- 일반적인 나누기
4 DIV 2 정수 나누기 -- 몫만 출력
4 % 2, 4 MOD 2, MOD(ID, 2) 나머지 -- 둘 다 동일한 연산


```
- 연산함수 / 소수점처리
```MYSQL
ABS(-2) 절대값
ROUND(2.35, 1) 반올림
POWER(3, 2) 거듭제곱 -- 3의 2제곱
SQRT(9) 제곱근 -- 3

ROUND(5.556901, 4) 소수점 반올림
CEIL(2.3) 소수점 올림
FLOOR(2.3) 소수점 내림
FORMAT(13000.36, 1) 숫자를 반올림하고 '#,###,###.##’ 형태로 보고 싶을 때
```
- total_bill 쪽 null 값 존재로 AVG() 차이 
- AVG(total_bill) == SUM(total_bill) / COUNT(total_bill) != SUM(total_bill) / COUNT(*)  
![Pasted image 20241203055852.png](/img/user/000_1/Z_image_repository/Pasted%20image%2020241203055852.png)

- 데이터 요약
- Group by
	- 작성 컬럼 순서에 큰 의미는 없습니다. 
	- GROUP BY 컬럼에 컬럼 숫자를 적는 건 추천하지 않습니다.
	- WHERE : GROUP BY 전 필터링
	- HAVING : GROUP BY 후 연산 결과물을 필터링

- SELECT 문에서 별칭(Alias)을 준 컬럼을 WHERE 절에서 다시 불러오고 싶은데 왜 안 될까요?
	- 명령어가 실행되는 순서 때문입니다. 여러분들이 지금까지 배운 범위 안에서 SQL의 실행 순서를 적어 보자면 대략 아래와 같습니다.

1. FROM
2. WHERE
3. GROUP BY
4. HAVING
5. SELECT
6. ORDER BY
7. LIMIT

이 순서를 보면 WHERE 절을 실행할 때, 아직 SELECT 절이 실행되기 전이라는 것을 알 수 있어요. 
이런 이유로 SELECT 절에서 정의한 별칭은 WHERE 절에서 사용할 수 없습니다.
ORDER BY 같은 경우에는 SELECT 이후에 실행되기 때문에 SELECT에서 정의한 별칭을 사용할 수 있습니다.

GROUP BY, HAVING 은 좀 특이합니다. 실행 순서상 SELECT에서 정의한 별칭을 사용할 수 없는데요. 
특이하게 몇몇 데이터베이스에서는 GROUP BY에서도 SELECT에서 정의한 별칭을 사용할 수 있습니다. MySQL이 그중 하나입니다.

MySQL에서는 GROUP BY, HAVING, ORDER BY에서 SELECT에서 정의한 별칭을 사용할 수 있습니다. 
MySQL의 Alias 사용과 관련해서 더 자세하게 알고 싶다면 **[MySQL 튜토리얼 문서](https://www.mysqltutorial.org/mysql-alias/)**를 참고해 보세요.


- 할부는 몇 개월로 해드릴까요 https://solvesql.com/problems/installment-month/
	- ''신용카드로 주문한 내역'' 문구를 놓침
	- 주문 수에 대하여, "order_id 의 중복값 제거" 
	
- 일주일 후 안내 메일 발송 건수 계산하기 https://solvesql.com/problems/count-of-mail-to-be-sent/
	- '2016년 10월 1일부터 발급된 동물인 경우에만 메일' 조건 을 놓침

```MYSQL
select date_add(license_issue_date, interval 7 day) email_send_date
    ,  COUNT(DISTINCT license_number) email_cnts

FROM seattle_pet_licenses
WHERE license_issue_date >= DATE('2016-10-01')
GROUP BY date_add(license_issue_date, interval 7 day)
ORDER BY date_add(license_issue_date, interval 7 day) ASC
;
```

- 날짜 더하기 빼기 
 ```MYSQL
SELECT DATE_ADD("2021-12-18", INTERVAL 1 MONTH) → “2022-01-18”
SELECT DATE_SUB("2021-12-18", INTERVAL 1 MONTH) → “2021-11-18”
```

- CASE 문법
```mysql
-- 조건이 1개인 경우
SELECT sum(size)
    ,  CASE
          WHEN day IN ('Sat', 'Sun') THEN '주말'
          ELSE 'Weekdays'
        END AS Weekdays_weekends
FROM tips
GROUP BY Weekdays_weekends
;

-- 조건이 2개 이상인 경우
SELECT CASE
          WHEN total_bill >= 40 THEN '큰 금액'
          WHEN total_bill >= 10 AND total_bill < 40 THEN '평균 금액'
          ELSE '적은 금액'
        END AS BILL
      , COUNT(*)
FROM tips
GROUP BY BILL;
```

- IF 함수 조건문
```MYSQL
-- IF() 쿼리 예시
SELECT *
     , IF(size >= 5, '5인 이상', '5인 미만') AS size_category
FROM tips
```

- 조건이 1개면 IF함수 쓰고, 조건이 2개 이상으로 넘어가면 CASE 문 작성
```MYSQL
SELECT IF(day in ('Sat', 'Sun'), 'Weekends', 'Weekdays') AS WEEKD
     , SUM(size) AS sum_size
FROM tips
GROUP BY WEEKD
;
```

- case문만 딸랑 뽑지 말고, 다른 컬럼도 같이 뽑아서 비교해가면서 보기 
- RFM 분석
- 컬럼 네임만 뽑는 방법, 컬럼별 DISITNCT 값 출력

