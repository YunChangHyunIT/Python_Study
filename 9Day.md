# 9일차 공부

## 예외 처리
- 사람은 실수할 수 있고 사람이 만든 프로그램에도 실수를 포함 할 수 있다.
- 실행 중 예기치 않은 문제가 발생 할 수 있다.
- 사용자 입력을 받을 경우 입력값을 예상할 수 없다.
  - ex) 점수를 입력하세요 -> 사용자 입력 : 만점, 80점, 왜?, 안알랴줌..등
- 네트워크나 외부장치도 언제 어떻게 연결이 끊어질지 예상할 수 없다.

```python
try:
  실행할 명령
except 예외 as 변수:
  오류 처리문
else:
  예외가 발생하지 않을 때의 처리
```

### 예외의 종류
- 자주 발생하는 예외를 미리 정의하고 고유한 이름을 붙여 놓았다.
- 대표적으로 많이 발생하는 예외는 아래와 같다.

![예외처리](https://user-images.githubusercontent.com/58713853/73334619-8b7b1c80-42b0-11ea-9cb2-52a74d2b4df1.PNG)

#### 예외의 종류에 따라 적절한 처리 해보기
```python
str = "89"

try:
  score = int(str)
  print(score)
  a = str[5]
excpet ValueError:
  print("점수의 형식이 잘못되었습니다.")
except IndexError:
  print("첨자의 범위를 벗어났습니다.")
```

### raise
- raise 명령은 고의적으로 예외를 발생시킨다.
- 작업을 위한 조건이 맞지 않거나 더이상 진행할 수 없는 경우 사용한다.
- raise 뒤에 발생시킬 예외의 이름을 넣는다.

#### 1~n 합계를 구하는 함수에서 0보다 큰 인수를 받는 예제
```python
def calcsum(n):
  if n < 0:
    raise ValueError
  sum = 0
  for i in range(n+1):
    sum += i
  return sum
  
try:
  print("~10 =", calcsum(10))
  print("~5 =", calcsum(-5))
except ValueError:
  print("입력값이 잘못되었습니다.")
```

### 자원정리
- 예외 발생 여부와 상관없이 반드시 실행해야 할 명령을 지정한다.
- 메모리나 지원을 할당한 후 해제해야 할 때 finally 블록에 작성한다.
- finally 블록은 예외 발생 여부와 상관없이 항상 실행한다.

#### 네트워크 사용 후 자원을 종료하는 간단한 예제
```python
try:
  print("네트워크 접속")
  a = 2 / 0
  print("네트워크 통신 수행")
finally:
  print("접속 해제")
print("작업 완료")
```

