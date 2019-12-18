# 2일차 공부

## 조건문
- 조건문은 조건의 진위 여부에 따라 명령의 실행 여부를 결정하는 제어 문이다.

### if 문
```python
if 조건 :
  명령
```
- if 키워드를 쓰고 조건과 콜론(:)을 찍고 그 다음 줄에 조건이 참일 때 실행할 명령을 작성한다.
- 들여쓰기 수준이 같으면 여러 명령을 실행 시킬 수 있다.

#### else 문
- 거짓일 때 실행할 명령은 else 키워드를 쓰고 콜론(:)을 찍고 그 다음 줄에 실행할 명령을 작성한다.

#### elif 문
- if, else 문을 한 단계 더 확장하여 선택 할 수 있다.
- if, else 문 중간에 들어간다.

#### if, else, elif를 활용한 간단한 가위바위보 게임
```python
import random

user = int(input("1 ~ 3까지 입력하세요 "))
com = random.randint(1, 3)

if com == user:
  print("비겼습니다.")
elif user == 1 and com == 3:
  print("이겼습니다.") 
elif user == 2 and com == 1:
  print("이겼습니다.")
elif user == 3 and com == 2:
  print("이겼습니다.")
else:
  print("졌습니다.")
```

## 반복문
- 반복문은 유사한 명령을 계속 실행하는 제어문이다.
- 반복문에는 while 문과 for 문이 있다.


### while 반복문
- if 문과 유사한 형태
- 조건이 만족하는 동안 계속 실행
```python
while 조건 :
  명령
```

#### while을 활용한 구구단
```python
num = 1
while num < 10:
  print("2", "x", num, "=", 2*num)
  num += 1
```

### for 반복문
- for 문은 컬렉션의 요소를 순서대로 반복하면서 명령을 실행하는 반복문

```python
for 제어변수 in 컬렉션 :
  명령
```

#### range
- 순차적으로 증가하는 리스트를 만든다.
- 시작값부터 끝값 직전까지 증가값을 더해서 리스트를 만든다.
```python
range([시작], 끝, [증가값])

range(0, 10, 1) ## 0, 1, 2, 3, 4, 5, 6, 7, 8, 9
```

#### 1 ~ 10까지 홀수와 짝수를 구분하는 예제
```python
for num in range(1, 11):
  if num % 2 == 0 :
    print(num, "짝수")
  else
    print(num, "홀수")
```

### break
- 반복문이 실행 중에 반복을 중지 해야 할 때 사용
- 반복 로직 실행도중 break를 만났을 때, 그 즉시 해당하는 반복문을 종료한다.

#### list를 안 숫자를 출력하다 숫자가 0보다 작고 100보다 클 때 출력을 끝내는 예제
```python
score = [92, 86, 68, 120, 56]
for s in score:
  if s < 0 or s > 100:
    break
  print(s)
  
print("성적 처리 끝")
```


### continue
- 반복문의 한번을 건너뛰고 나머지를 수행할 때 사용한다.
- 반복 로직 실행도중 continue를 만났을 때, continue 밑에 있는 문장에 해당하는 로직을 건너뛴다.

#### list를 안 숫자를 출력하다 숫자가 -1 이면 건너뛰고 출력하는 예제
```python
score = [92, 86, 68, -1, 56]
for s in score:
  if s == - 1:
    continue
  print(s)
  
print("성적 처리 끝")
```


### 무한 루프
- 반복 횟수를 정하지 않고 무한히 반복하는 루프이다.
- 루프 중간에 조건을 점검하여 탈출하는 방식이다.
- while문으로 작성이 가능하고 for 문으로는 불가능하다.

#### 덧셈 문제를 출제하고 사용자로부터 정답을 입력받아 답을 체크하는 예제
```python
print("3 + 4 = ?")
while True:
  a = int(input("정답을 입력하시오 : "))
  if a == 7:      
    break 
    
print("참 잘했어요")
```
