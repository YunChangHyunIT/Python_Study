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
# enumerate가 튜플을 리턴하므로 전에 공부 했었던 튜플 
  print(no, "번 학생의 성적 : ", s)
```
