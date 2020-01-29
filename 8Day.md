# 8일차 공부

## 모듈
- 파이썬 코드를 저장하는 기본 단위
- 파이썬 스크리브 하나를 의미하되 확장자 .py는 배고 파일명으로 부른다.
![모듈](https://user-images.githubusercontent.com/58713853/73340966-077c6100-42bf-11ea-866c-cefcbc7ea827.PNG)

### import
- 자주 사용하는 기능을 표존 모듈로 미리 만들어져 있다.
- 파이썬 설치 경로에 확장자가 .py 파일이 표준모듈 이다.
- 대표적으로 수학, 난수, 시간 관련 모듈이 있다.
- 모듈을 가져와 사용할 때는 import 명령을 사용한다.

```python
import 모듈이름
```

### math 모듈
- 수학 연산에 필요한 상수와 연산 함수를 제공한다.
- 삼각함수, 지수함수, 로그함수 등 수학시간에 배운 대부분의 계산 함수가 제공된다.

![math](https://user-images.githubusercontent.com/58713853/71962501-eb941b00-323c-11ea-9d9d-afeb16b0dfc0.PNG)


#### math 모듈 사용
```python
import math

print(math.sin(math.radians(45)))
print(math.sqrt(2))
print(math.factorial(5))
```
### 통계(statistics) 모듈
- statistics 모듈은 3.4 버전에 추가 되었다.
- 평균, 분산 등의 통계값을 계산한다.
- math 모듈보다 한번에 정확한 값을 효율적으로 계산한다.

![통계](https://user-images.githubusercontent.com/58713853/71962643-37df5b00-323d-11ea-9aaf-07701a878d7c.PNG)

#### statistics 모듈 사용
```python
import statistics

score = [30, 40, 60, 70, 80, 90]
print(statistics.mean(score)) 
print(statistics.harmonic_mean(score)) 
print(statistics.median(score)) 
print(statistics.median_low(score))
print(statistics.median_high(score))
```

### time 모듈
- time 모듈은 날짜와 시간 관련 기능을 제공한다.
- 대표적인 함수는 현재 시간을 조사하는 time 이다.
- ctime 함수를 사용하면 문자열 형태로 시간을 알려준다.
- 현지 시간을 구할 때는 localtime을 사용한다.

#### time 모듈 사용
```python
import time

print(time.time())
print(time.ctime())
```
#### time 함수를 사용해 실행 시간을 측정 해보자

```python
import time

start = time.time()
for a in range(1000):
  print(a)
end = time .time()
print(end - start)
```

### calendar 모듈
- calendar 모듈은 달력 기능을 제공한다.
- calendar 함수는 인수로 받은 년도의 달력 객체를 리턴한다.
- month 함수는 년도와 달을 받아 해당 달의 달력 객체를 리턴한다.
- weekday 함수는 특정 날짜가 무슨 요일인지 조사한다.

#### calendar 모듈 사용
- calendar, month 함수를 사용해 달력을 출력 해보자.
```python
import calendar

print(calendar.calendar(2019))
print(calendar.month(2019, 10))
```

#### 2019년 광복절은 무슨 요일인지 계산해보자.
```python
import calendar

yoil = ["월", "화", "수", "목", "금", "토", "일"]
day = calendar.weekday(2019, 8, 15)
print("광복절은 " + yoil[day] + "요일이다.")
```

### Random 모듈
- random 모듈은 난수를 생성하는 기능을 제공한다.
- 0에서 1미만의 실수 하나를 생성한다.
- 일정 범위를 지정하여 난수를 생성할 수 있다.

#### 로또 번호 생성기(1 ~ 45까지의 난수를 6개 만들어보기)
```pyton
import random

lotto = [n for n in range(1,46)]
random.shuffle(lotto) 
# random 모듈중 shuffle 이라는 list를 섞어주는 함수를 사용해서 간단하게 만들 수 있다.
print(lotto[0:6])
```
### sys 모듈
- 파이썬 해석기가 실행되는 환경과 해석기의 여라 가지 기능을 조회하고 관리하는 모듈
- 시스템에 관련된 정보를 조사한다.

#### sys 모듈 사용
```python
import sys

print("버전 :", sys.version)
print("플랫폼 :", sys.platform) 
print("바이트 순서 :", sys.byteorder)
print("모듈 경로 :", sys.path) 
sys.exit(0)
```
## 패키지
- 대규모 프로젝트를 수행하려면 이미 잘 만들어놓은 코드를 활용하는 것이 좋다.
- 처음부터 모든 코드를 다 작성할 수는 없고 그럴 필요도 없다.
- 잘 구축된 도구를 적극적으로 활용해야 하며 이런 목적으로 마련된 장치가 모듈이다.
- 모듈의 수가 많아지면 관리하기가 어렵다.
- 모듈을 관리하기 위해 패키지라는 개념이 필요하다.
- 모듈이 파일이라면 패키지는 폴더와 같다.
![패키지](https://user-images.githubusercontent.com/58713853/73341124-59bd8200-42bf-11ea-9fb8-5a8300f665d6.PNG)

### 패키지 사용하는 예제
```python
import calc.add
calc.add.outadd(1,2)

import report.table
report.table.printreport()
```
