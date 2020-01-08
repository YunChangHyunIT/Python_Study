# 7일차 공부

## 컬렉션 관리
- 컬렉션 관리 함수
  - enumerate
  - zip
- 람다 함수
  - filter
  - map
- 컬렉션의 사본


### enumerate
- 순서 값과 요소값 둘을 한꺼번에 구해 주는 내장 함수이다.
- 리스트의 순서값과 요소값을 튜플로 묶은 컬렉션을 리턴한다.
```python
enumerate(리스트, 시작할 순서)
```

#### 학생의 순서와 점수를 출력해보자
```python
# 일반적으로 생각해 볼 수 있는 방식
score = [88, 95, 70, 100, 99]
for no in range(len(score)):
  print(no + 1, "번 학생의 성적 :", score[no])
  
# enumerate를 사용하는 방식
for no, s in enumerate(score, 1) :  # no에는 순서가 s에는 score 하나하나의 값이 들어가게 된다.
# enumerate가 튜플을 리턴해서 5일차에 공부 했었던 튜플 언패킹으로 no, s에 값을 넣어줄 수 있게 된다.
  print(no, "번 학생의 성적 : ", s)
```


### zip
- 여러 개의 컬렉션을 합쳐 하나로 만든다.
- 리스트의 대응되는 요소끼리 짝을 지어 튜플의 리스트(튜플 안에 리스트가 있는 형태)를 생성한다.
- 리스트의 길이가 달라도 상관없다.
- 짧은 리스트 기준으로 맞추어진다.
```python
zip(컬렉션, ...., 컬렉션)
```

#### 요일과 메뉴를 합쳐보자
```python
yoil = ["월", "화", "수", "목", "금", "토", "일"]
food = ["갈비탕", "순대국", "칼국수", "삼겹살"]

for y, f in zip(yoil, food):  # y에 요일, f에 음식이 하나하나 들어가게 된다.
# zip이 튜플의 리스트를 리턴하기 때문에 튜플 언패킹으로 y, f에 리스트가 들어가게 된다.
  print("%s요일 메뉴 : %s" % (y, f))
```

### 람다 함수
- 이름이 없고 입력과 출력만으로 함수를 정의하는 축약된 방법이다.
- lambda로 시작하고 인수와 리턴한 값을 밝힌다.
- 인수는 콤마로 구분하여 여러 개 값을 가질 수 있다.
```python
lambda 인수 : 식
```


#### 람다 함수 - filter
- 함수의 결과가 참인지 거짓인지에 따라, 해당 요소를 포함할지를 결정한다.

```python
score = [45, 89, 72, 53, 94]
for s in filter(lambda x: x < 60, score):
  print(s)
```

#### 람다 함수 - map
- 요소들에 함수를 적용해주는 함수이다.
```python
score = [45, 89, 72, 53, 94]
for s in map(lambda x: x /2, score): 
  print(s)
```

### 컬렉션의 사본
- 컬렉션에서는 대입 연산자로 값을 복사 했을 경우 같은 메모리를 가리키고 있다.
- 독립적인 사본을 만들려면 copy 메서드로 복사본을 생성 해야한다.

```python
list1 = [1, 2, 3] 
list2 = list1   # 이렇게 대입하게되면 list1의 메모리주소를 list2가 가지게 된다.

list2[1] = 100  # list1[1] = 100 과 같은 의미이다.
print(list1)
print(list2)

# is 연산자를 통해 같은 객체 인지 확인할 수 있다.
print("list1 == list2 :", list1 is list2)
```

#### copy 메서드
```python
list1 = [1, 2, 3]
list2 = list1.copy()

list2[1] = 100 # 위와 다르게 list2[1] 만 값이 바뀐다 ( 독립적인 리스트가 되므로 )
print(list1)
print(list2)

print("list1 == list2 :", list1 is list2)
```
- list 안에 list가 있을 때 copy를 하면 어떻게 될까?
```python
list1 = [1, 2, 3]
list2 = [list1, 4, 5]
list3 = list2.copy()

list3[0][1] = 99 
# list2[0]에 list1 의 값들이 온전히 담기는 것이아니고 list1의 메모리 주소가 들어가기 때문에
# list3[0][1] 을 바꿀시 list2, list1의 값들이 바뀐다.
list3[1] = 10 # 메모리 주소가 담기지 않는 값들은 list3 에서만 바뀐다.

print(list1) 
print(list2) 
print(list3)

print("list1 == list2 :", list1 is list2)
print("list1 == list3 :", list1 is list3)
print("list2 == list3 :", list2 is list3) 
# list1의 주소 값을 갖는 건 맞지만 다른 값들이 독립적으로 복사가 되므로 다른 객체이다.
```
#### deepcopy 메서드
- list의 요소들 중 메모리 주소를 갖는 값이 있으면 그 메모리 주소 안의 값까지 복사해 온다.
```python
import copy

list1 = [1, 2, 3]
list2 = [list1, 4, 5]
list3 = copy.deepcopy(list2)

list3[0][1] = 99 # copy와 다르게 list3 안에 값만 바뀐다.

print(list1)
print(list2) 
print(list3)
```
