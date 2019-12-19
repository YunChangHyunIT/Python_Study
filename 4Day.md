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

#### 문자열 조사 메서드 예제
```python
height = input("키를 입력하세요 :")
if height.isdecimal(): 
  print("키 :", height)
else:
  print("숫자만 입력하세요.")
```

### 문자열 변경
- lower : 영문자 전부 소문자로 변경한다.
- upper : 영문자 전부 대문자로 변경한다.
- swapcase : 대문자를 소문자, 소문자를 대문자로 변경한다.
- capitalize : 첫 글자를 대문자로 변경한다.
- title : 첫 글자와 공백다음 문자를 대문자로 변경한다.

#### 문자열 변경 예제
```python
python = input("파이썬의 영문 철자를 입력하시오 :")
if python.lower() == "python":
  print("맞췄습니다.") 
else:
  print("땡!!!")
```

### 문자열 분할
- 구분자를 기준으로 문자열을 분할 할 수 있다.

```python
s = "짜장 짬뽕 탕수육"
print(s.split())  # [짜장, 짬뽕, 탕수육] 으로 결과 나옴 (분리되서)

s2 = "서울->대전->대구->부산"
print(s2.split("->"))

for city in s2.split("->"):
  print(city, "찍고", end=" ")
```

### 문자열 대체
- replace : 특정 문자열을 찾아 다른 문자열로 바꾼다.

### 문자열 삽입
- 문자열 사이에 설정한 문자를 넣어 준다.

```python
print(",".join("abcd")) 
print(",".join(["a", "b", "c", "d"]))
# 출력 결과는 a, b, c, d 로 같다
```

### 문자열 포맷팅
- 문자열 사이사이에 다른 정보를 삽입하여 조립하는 기법이다.
- 문자열 중간에 많은 값이 삽입되면 보기가 어려워 진다.
  - 문자열 포맷팅을 사용하면 가독성이 높아 진다.
- 문자열에 삽입될 값이 두개 이상이라면 (값1, 값2) 식으로 괄호로 묶어 사용한다.
  - ()괄호로 묶은 값의 집합을 튜플이라고 한다.
- {} 괄호를 적고 foramt 메서드의 인수로 넣어주는 신형 포맷팅 방법도 있다.
  
```python
month = 8
day = 15 
anni = "광복절"

print(str(month) + "월 " + str(day) + "일은 " + anni + "이다.") # 기존 사용법
print("%d월 %d일은 %s이다." % (month, day, anni))  # 문자열 포맷팅 

print("{}월 {}일은 {}이다.".format(month, day, anni)) # 신형 포맷팅
print("{2}월 {0}일은 {1}이다.".format(day, anni, month)) # 번호에 맞는위치 순서대로 들어간다 (2 = month, 0 = day, 1 = anni)
print("{month}월 {day}일은 {anni}이다.".format(day = day, anni = anni, month = month))  # 정해준 이름에 맞는 위치에 들어간다.
```
