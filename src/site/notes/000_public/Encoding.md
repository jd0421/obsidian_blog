---
{"dg-publish":true,"permalink":"/000-public/encoding/","tags":["encoding","prerocessing","nominal_data","LabelEncoding"],"created":"2025-08-20T13:39:15.632+09:00","updated":"2025-08-20T13:59:14.130+09:00"}
---


> Nominal data

- LabelEncoding
	- 동작방식
		- `LabelEncoder`는 **문자열(카테고리 값)을 숫자로 단순히 치환**합니다.
		- 이 숫자는 **사전순(알파벳 오름차순 또는 유니코드 순서)** 으로 부여됩니다.
		- 순서를 부여하지만, 그 숫자가 '우열'이나 '크기 비교'를 의미하지는 않습니다.
		- 단순히 "이 값은 몇 번째 클래스인가"를 나타내는 인덱스일 뿐입니다.
	- 주의
		- 트리 기반 모델(Decision Tree, RandomForest, XGBoost 등)에서는 큰 문제가 되지 않습니다. 이 값이 단순 분할 기준으로만 쓰이기 때문입니다.
	    - 그러나 선형 모델(Logistic Regression, Linear Regression 등)에서는 **숫자 간의 크기 차이가 의미 있는 값처럼 잘못 해석**될 수 있습니다.
		- 예: `red=2`, `blue=0`, `green=1` → `red`가 `blue`보다 "2만큼 더 크다"는 식으로 오해됨.
		- Ordinal 데이터인 경우 `LabelEncoder` 대신 **OrdinalEncoder**를 써서 직접 순서를 지정하는 것이 적절합니다.

> Ordinal data

- OrdinalEncoder
	- 동작방식
		- 이 클래스는 각 범주의 순서를 지정할 수 있어 순서형 데이터에 적합합니다.
		- 

```python
eocoder_train = OrdianlEncoder(categories = [['Preschool', '1st-4th', 'Doctorate']]) # 인코더 초기화 및 범주 순서 설정
train_ex3['education'] = encoder_train.fit_transform(train_ex3[['education']]).astype(int) # fit_transofrm 메서드를 사용하여 교육 수준 데이터에 OrdinalEncoder 를 적용하고, 결과를 정수형으로 반환합니다.

display(encoder_train.categories_) # 인코딩 순서를 확인
display(train_ex3.head())
display(train_ex3['education'].dtype()) # 데이터 타입 체크
display(train_ex3['education'].unique()) # unique 값 유지 여부 체크



```

> 딕셔너리를 이용한 하드 인코딩

- map()
```python

order_map = {'낮음' : 1, '중간' : 2, '높음' : 3}
data['변수명'] = data['변수명'].map(order_map)

```

- replace()
```python
education_map = {'Preschool': 0, '1st-4th' : 1, 'Doctorate', 15}
train_ex2['education'] = train_ex2['education'].replace(education_map)

```

- 수정 후 
```python
train_ex2.head() # 잘 바뀌었는지
train_ex2['education'].dtype() # 희망하는 data type 인지
train_ex2['education'].unique() # unique 동일한지 

```


