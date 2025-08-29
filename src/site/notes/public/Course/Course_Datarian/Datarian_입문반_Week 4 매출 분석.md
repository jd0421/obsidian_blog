---
{"dg-publish":true,"permalink":"/public/course/course-datarian/datarian-week-4/","created":"2024-12-06T05:31:14.165+09:00","updated":"2025-08-29T16:08:45.673+09:00"}
---

- AARRR
- ARPU = Average Revenue Per User = 총 매출 / 활성 사용자 수
- ARPPU = Average Revenue Per Paying User = 총 매출 / 구매 고객 수 
	- 결제를 반드시 수반하는 이용 앱이 아니라면 구매 고객 수는 활성 사용자 수보다 항상 작다 
	- 그러므로 ARPU 는 ARPPU 보다 같거나 작을 수 밖에 없다 ARPU  < ARPPU 
	- 

**  
[학습 팁] 매출과 관련된 지표를 더 알고 싶다면**

매출과 관련된 지표에 ARPU, ARPPU만 있는 것은 아닙니다. 이외에도 LTV(Lifetime Value, 고객 생애 가치), LTR(Lifetime Revenue), MRR(Monthly Recurring Revenue) 등 여러 가지 지표들이 있는데요.

오늘 배운 ARPU, ARRPU에 대한 개념을 복습하고 매출과 관련된 다른 지표들에 대해서도 공부를 해보고 싶다면, **[그로스 해킹: 데이터와 실험을 통해 성장하는 서비스를 만드는 방법](http://www.yes24.com/Product/Goods/96576416)** 책의 3.5장 ‘수익화’ 섹션을 읽어보세요.


### 수업 요약

**AARRR**

- A(Acquisition, 획득): 광고 등의 방법으로 새로운 사용자를 얻어오는 단계

- A(Activation, 활성화): 회원 가입, 튜토리얼 등 사용자를 활성화 시키는 단계

- R(Retention, 리텐션): 지속적으로 서비스를 사용하게 만드는 단계

- R(Revenue, 매출): 매출을 만드는 단계

- R(Referral, 추천): 다른 사용자에게 제품을 추천하는 단계

**매출에 영향을 주는 요소**

- 활성 사용자 수

- 구매 고객 수(PU, Paying User)

- 고객 1인당 평균 구매액

- ARPU(Average Revenue Per User) : 전체 매출 / 활성 사용자 수
- ARPPU(Average Revenue Per Paying User) : 전체 매출 / 구매 고객 수



---

자주 묻는 문제
❔

**[자주 묻는 질문] EDA 할 때, 전체 데이터를 가져오는 쿼리를 실행해도 되나요?**

아니오, 웬만하면 회사에서 데이터를 볼 때 전체 데이터를 가져오는 쿼리는 실행시키지 않는 것이 좋습니다.

회사의 서비스 데이터를 담고 있는 테이블은 생각보다 엄-청 큽니다. 테이블에 들어있는 데이터의 규모가 어느 정도인지 파악되지 않은 상태에서 무턱대고 테이블 안에 있는 전체 데이터를 뽑는 쿼리를 실행한다면, 데이터베이스가 힘들어하다가 뻗어버릴 수 있어요.

때문에 EDA를 할 때는 전체 테이블을 조회하기보다는, 아래와 같이 특정 날짜 또는 시간으로 데이터를 작게 잘라서 조회하는 것이 더 현실적이고 안전한 방법입니다.

`-- UK E-Commerce Orders 데이터셋 SELECT * FROM orders WHERE order_date BETWEEN '2018-12-01' AND '2018-12-07'`

❔

**[자주 묻는 질문] WHERE 절에서 날짜와 시각 데이터를 필터링 할 때,** `**DATE()**` **같은 함수(또는** `**LIKE**`**)를 사용해도 될까요?**

안쓰는 것이 좋습니다. 먼저, 정석적인 날짜와 시각 데이터 필터링하는 방법을 보여드릴게요.

`-- 데이터셋: Delivery App Logs -- 2018년 4월 1일에 가입한 사람을 찾는 쿼리 SELECT * FROM customers WHERE created_at BETWEEN '2018-04-01 00:00:00' AND '2018-04-01 23:59:59'`

이번에는 `DATE()` 함수를 적용한 쿼리입니다.

`-- 데이터셋: Delivery App Logs -- 효율적이지 않은 코드 1 SELECT * FROM customers WHERE DATE(created_at) = '2018-04-01'`

이렇게 쿼리를 작성하면, DB는 대략 이렇게 동작합니다. (DB 마다 차이가 있을 수 있습니다.)

1. `created_at` 컬럼에 들어있는 모든 값을 `DATE()` 함수로 변환하는 연산을 수행

2. 변환한 값이 `‘2018-04-01’` 인지 판단

`created_at` 컬럼에 데이터가 적게 들어있다면 위 쿼리로도 계산이 되겠지만, 데이터가 굉장히 많은 경우에는 `DATE()` 함수를 적용하는 데만 많은 시간이 소요될 거예요.

꼭 날짜와 시각이 아니더라도, WHERE 절을 쓸 때에는 필터링하려는 컬럼에 함수를 적용하지 않는 것이 좋습니다.

비슷하게 자주 실수하는 것이 날짜와 시각 데이터 필터링 시 `LIKE`를 사용하는 거예요.

`-- 데이터셋: Delivery App Logs -- 효율적이지 않은 코드 2 SELECT * FROM customers WHERE created_at LIKE '2018-04-01 %'`

`LIKE` 구문은 문자열로 저장된 데이터의 패턴을 비교할 때만 사용할 수 있는 구문입니다. 따라서 위 쿼리는 대략 이렇게 동작합니다. (DB 마다 차이가 있을 수 있습니다.)

1. `created_at` 컬럼에 들어있는 모든 값을 문자열로 변환

2. 1단계에서 연산된 값이 ‘2018-04-01 %’ 패턴에 일치하는지 비교

컬럼에 함수를 적용한 것과 마찬가지로, `created_at` 컬럼을 변환하는 데 많은 시간을 낭비하게 됩니다.

지금까지 복잡한 얘기를 한 것 같지만 결론은 하나입니다. WHERE 절에서 필터링을 할 때에는 컬럼을 있는 그대로 사용해주세요. 함수를 적용하거나, 컬럼의 데이터 타입과 맞지 않는 연산을 하면 컬럼을 변형시키는데에 많은 시간을 쓰게 됩니다.

solvesql 에서는 연습문제 또는 플레이그라운드 우측에 있는 테이블 명세에서 대략적인 데이터 타입을 보실 수 있습니다.

참고 : **[https://stackoverflow.com/questions/17101436/mysql-datetime-field-with-index-get-a-range-like-vs-between-and-performance](https://stackoverflow.com/questions/17101436/mysql-datetime-field-with-index-get-a-range-like-vs-between-and-performance)**
