---
{"dg-publish":true,"permalink":"/public/course/course-datarian/datarian/","tags":["Datarian"],"created":"2024-11-26T10:19:09.770+09:00","updated":"2025-08-29T16:10:32.075+09:00"}
---

- https://datarian.io/
	- [[public/Course/Course_Datarian/Datarian_입문반\|Datarian_입문반]]
	- [[public/Course/Course_Datarian/Datarian_실전반\|Datarian_실전반]]
	- [[public/Course/Course_Datarian/Datarian_마스터반\|Datarian_마스터반]]

- [Practice](https://solvesql.com/u/dc2e0968-e03b-4ae1-a10c-addddaefa87e/)
	- [외부 대시보드](https://solvesql.com/u/dc2e0968-e03b-4ae1-a10c-addddaefa87e/) 
	- https://solvesql.com/collections/advent-of-sql-2024/

- tips
	- Between
		- Between은 경계값을 포함 x between 20 and 30 , x >= 20 and x <= 30 
	- where 절에서는 윈도우 함수를 그대로 사용 불가, cte 함수로 돌려서 사용
	- Window
		- LEAD, LAG
			- [LEAD, LAG : 이전 행 값, 이후 행 값을 불러오는 함수 (ex. 누적도수분포로부터 도수를 구하기, 급여 차이 구하기, 성적 차이 구하기)](https://m.blog.naver.com/regenesis90/222192641844)
	- ROW_NUMBER, RANK, DENSE_RANK
		- [RANK(), DENSE_RANK(), ROW_NUMBER 개념 및 차이](https://seung-nari.tistory.com/entry/SQL-RANK-DENSERANK-ROWNUMBER-%EA%B0%9C%EB%85%90-%EB%B0%8F-%EC%B0%A8%EC%9D%B4)
	- count
		- **`COUNT(*)`** → 모든 행(Row)을 센다. `NULL` 포함.
	    - **`COUNT(column)`** → 해당 컬럼 값이 `NULL`인 경우는 제외하고, `NOT NULL`인 값만 센다.
	- timestamp면 filter 조건을 반드시 timestamp 형식으로 기입하여 진행하기
		- where order_purchase_timestamp between '2018-01-01 00:00:00' and '2018-01-31 23:59:59'
	- date_add
		- https://extbrain.tistory.com/58


- SQL 데이터 분석 캠프 패키지 / 등록 완료 https://datarian.io/bootcamp/sql-package
- SQL 데이터 분석 캠프 마스터반 https://datarian.io/bootcamp/sql-master


- [[public/Practice/HackerRank/HackerRank\|HackerRank]]
- [[public/Practice/leetcode/leetcode\|leetcode]]
- Stackoverflow




