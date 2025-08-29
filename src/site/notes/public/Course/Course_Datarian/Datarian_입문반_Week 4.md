---
{"dg-publish":true,"permalink":"/public/course/course-datarian/datarian-week-4/","created":"2024-12-05T18:05:08.605+09:00","updated":"2025-08-29T16:08:45.689+09:00"}
---

- [sql join visualizer](https://sql-joins.leopard.in.ua/)
- [[데이터리안] SQL 캠프 입문반 | Week 4 - 데이터 연결하기 2](https://docs.google.com/spreadsheets/d/1PWUl3NAQzY0-cSyHIsgFfvCRTNfc5cXNbkdlgVhNrSA/edit?gid=0#gid=0)

- innter join
![Pasted image 20241205181618.png](/img/user/000_1/Z_image_repository/Pasted%20image%2020241205181618.png)
```sql
SELECT 
	* 
FROM 
	TableA A 
		INNER JOIN TableB B ON A.key = B.key
```


- outer join

- left (outer) join
![Pasted image 20241205181313.png](/img/user/000_1/Z_image_repository/Pasted%20image%2020241205181313.png)
```sql
SELECT * FROM TableA A LEFT JOIN TableB B ON A.key = B.key
```

- right (outer) join
![Pasted image 20241205181327.png](/img/user/000_1/Z_image_repository/Pasted%20image%2020241205181327.png)

```sql
SELECT * FROM TableA A RIGHT JOIN TableB B ON A.key = B.key
```

- full outer join
- [[데이터리안] SQL 캠프 입문반 | Week 4 - 데이터 연결하기 2](https://docs.google.com/spreadsheets/d/1PWUl3NAQzY0-cSyHIsgFfvCRTNfc5cXNbkdlgVhNrSA/edit?gid=1586018726#gid=1586018726)
Full Outer Join은 `JOIN`으로 연결된 두 테이블의 모든 데이터를 표시하고 싶을 때 사용합니다.

예를 들어 고객 정보 테이블에는 주문을 한 번도 하지 않은 고객이 들어있고, 주문 테이블에는 고객 정보가 없는 주문 건이 들어있는 경우. 두 테이블의 모든 데이터를 한 번에 뽑고 싶을 때 Full Outer Join을 사용할 수 있습니다.

MySQL은 Full Outer Join을 공식적으로 지원하지는 않습니다. MySQL에서는 `LEFT JOIN` 한 테이블과 `RIGHT JOIN`한 테이블을 `UNION`으로 결합하여 Full Outer Join을 구할 수 있습니다.

![Pasted image 20241205181258.png](/img/user/000_1/Z_image_repository/Pasted%20image%2020241205181258.png)
```sql
SELECT * FROM TableA A FULL OUTER JOIN TableB B ON A.key = B.key
```



- self join

[[데이터리안] SQL 캠프 입문반 | Week 4 - 데이터 연결하기 2](https://docs.google.com/spreadsheets/d/1PWUl3NAQzY0-cSyHIsgFfvCRTNfc5cXNbkdlgVhNrSA/edit?gid=657567395#gid=657567395)

SELECT *
FROM students AS mentees
           INNER JOIN students AS mentors ON mentees.mentor_id = mentors.student_id

- 이건 다시 풀어보자 [다음날도 서울숲의 미세먼지 농도는 나쁨 😢](https://solvesql.com/problems/bad-finedust-measure/)
	- from 절에서도 date_add 함수를 쓸 수 있다
	- 