# 4일차 공부

## 문자열

### 첨자
- 앞에서도 셀수 있고 뒤에서도 셀수 있다.
![첨자](https://user-images.githubusercontent.com/58713853/71160927-c8a0c780-228b-11ea-9575-1ab1b520ea14.PNG)

### 문자열 변경
- 파이썬의 문자열은 변경 불가능한 자료형이다.
- 한번 초기화되면 바꿀 수 없다.

### 슬라이스
- [] 괄호에 범위를 지정하면 부분 문자열을 추출 한다.
- range 함수 구조와 같다. (begin 부터 end 바로 직전 까지 step 만큼)
- 맨처음 시작 인덱스가 0이다.
```python
s = "python"
print(s[2:5]) # 2번째부터 4번째 까지
print(s[3:])  # 3번째부터 끝까지
print(s[:4])  # 처음부터 3번째까지
print(s[2:-2])  # 2번째 부터 끝에서 2번째 까지
```

### 문자열 검색
- 특정 문자의 위치를 검색하는 메서드를 제공한다.
- len 내장 함수는 문자열의 길이를 리턴한다.
  - 뒤에 나올 리스트, 튜플에서도 사용 가능하다.
![문자열 검색](https://user-images.githubusercontent.com/58713853/71161446-b07d7800-228c-11ea-8c36-b59056f88a26.PNG)

### 문자열 조사
- 특정 문자가 있는지 없는지만 알고 싶을 때 in 구문을 사용한다.
- in은 함수가 아닌 키워드이다.
  - 단어 in 문자열
- not in은 포함되어 있는지 않은지 조사한다.
```python
s = "python programming"
print('a' in s)
print('z' in s)
print('pro' in s)
print('x' not in s)
```

#### 문자열 조사 메서드
![문자열 조사](https://user-images.githubusercontent.com/58713853/71161733-3ef1f980-228d-11ea-9d26-745811e9d79b.PNG)
