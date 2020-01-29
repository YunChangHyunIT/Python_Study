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

## 파일 입출력
- 프로그램에서 생성한 정보를 영구적으로 저장할 때는 파일에 기록한다.
- 메모리는 전원이 끊기면 내용을 잊어버리기 때문에 하드디스크에 저장해야한다.
- open 함수를 사용해 파일을 연다.
![파일입출력1](https://user-images.githubusercontent.com/58713853/73336215-8d46df00-42b4-11ea-9d7c-423f93abea6e.PNG)

- open 함수는 파일의 입출력을 준비한다.
- read, write 메소드를 호출해 파일을 사용한다.
- 파일을 다 사용하고 나면 close 메소드를 호출 한다.
![파일입출력2](https://user-images.githubusercontent.com/58713853/73339950-1feb7c00-42bd-11ea-9867-62d8180a87c8.PNG)

### 파일 쓰기
#### live.txt 파일을 생성하고 내용을 저장해 보는 예제
```python
file = open("live.txt", "w", encoding='UTF-8') // 한글을 사용하려면 인코딩을 해주어야 한다.
file.write(""" 삶이 그대를 속일지라도 슬퍼하거나 노하지 말라! 우울한 날들을 견디면 믿으라, 기쁨의 날이 오리니 """) 
file.close()
```

### 파일 읽기
#### live.txt 파일을 읽어서 출력해 보는 예제
```python
try:
  file = open("live.txt","r")
  text = file.read()
  print(text)
except FileNotFoundError:
  print("파일이 없습니다.")
finally:
  file.close()
```

#### 한 줄 씩 읽어서 출력해 보는 예제
```python
file = open("live.txt", "r")
line = 1
while True:
  row = file.readline()
  if not row:
    break
  print(str(line) + " :" + row, end='')
  line += 1
file.close()
```
### 파일 내용 추가
#### live.txt 파일에 내용을 추가 해보는 예제
```python
file = open("live.txt","a")
file.write("\n\n푸쉬킨 형님의 말씀이었습니다.")
file.close()
```

### 파일 관리 함수
- 파일 입출력이 아닌 파일 복사, 삭제, 폴더 복사, 삭제 등 파일을 관리한다.
![파일입출력3](https://user-images.githubusercontent.com/58713853/73340513-347c4400-42be-11ea-9ee4-2d5c1ec73551.PNG)

### 폴더 관리 함수
- 폴더를 관리 하는 함수이다.
![파일입출력4](https://user-images.githubusercontent.com/58713853/73340514-347c4400-42be-11ea-95b6-0196755e025f.PNG)

### 경로(PATH) 관리 함수
- 폴더 경로를 조사하고 파일 및 폴더를 구분하는 핫무를 제공한다.
![파일입출력5](https://user-images.githubusercontent.com/58713853/73340512-33e3ad80-42be-11ea-934e-c339f4830c60.PNG)

#### 지정한 경로에 파일 목록을 출력해보는 예제
```python
def dumpdir(path):
  files = os.listdir(path)
  for f in files:
    fullpath = path + "/" + f
    if os.path.isdir(fullpath):
      print("[" + fullpath + "]")
      dumpdir(fullpath)
    else:
      print("\t" + fullpath)
      
dumpdir("/Users/Yun/Documents") // 해당하는 경로를 쓰면 된다.
```
