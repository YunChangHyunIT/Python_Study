# 6일차 공부

## 사전
- 키와 값의 쌍을 저장하는 대용량의 자료구조이다.
- 해시 알고리즘을 사용해 일대일로 대응되는 특성이 있어 맵이라고 부르기도한다.
- 사전을 정의할 때는 {} 괄호 안에 키 : 값 형태로 나열한다.
  - ex) { "boy" : "소년", "school" : "학교"}
- 키는 값을 찾는 기준이 된다.
- 키는 중복이되지 않는 고유한 값이여야 한다.
- 키는 읽기 전용이라 변경할 수 없다.
- 키가 사전에 있는지 in, not in로 조사 할 수 있다.
- get메서드 함수로도 접근할 수 있다.

#### 사전 예제 코드
```python
dic = { "boy" : "소년", "school" : "학교"}
print(dic["boy"])
print(dic["student"])   # KeyError 없는 키이므로 접근 불가

print(dic.get("boy")) # 사전 내부에 있는 get 함수로도 접근할 수 있다.
print(dic.get("student", "사전에 없는 단어 입니다.")) # 키가 없을 시 출력될 내용을 지정해 줄 수 있다.

if "student" in dic : # in 을 사용해 사전안에 키가 있는지 확인한다.
  print("사전에 있는 단어입니다.")
else :
  print("사전에 없는 단어입니다.")
```

### 사전 관리
- 사전은 변경이 가능한 자료 형이다.
- 키의 중복을 허용하지 않아 기존에 있는 키의 값을 변경한다.
- 없는 키에 대해 값을 대입하면 새로운 키의 값의 쌍이 추가 된다.
- 키와 값을 얻으려면 keys, values 메서드를 사용한다.
- update 메서드를 사용해 두개의 사전을 병합한다.

#### 사전관리 예제
```python
dic = { "boy" : "소년", "school" : "학교", "book" : "책" }
dic["boy"] = "남자애"
dic["girl"] = "여자애"
print(dic)

del dic["book"]
print(dic)

print(dic.keys()) # 키값만 출력해준다.
print(dic.values()) # 값만 출력해준다.
print(dic.items()) # 키와 값을 모두 출력해준다.

dic2 = { "student" : "학생", "teacher" : "선생님", "book" : "서적" }
dic.update(dic2) # dic을 기준으로 dic과 dic2를 병합한다. 
# 이 때, 같은 키값이면 원래 있던 값이 update를 할 값으로 바꾼다. "book" : "서적" 이 된다.

```


#### 사전의 활용
- 팝송 가사에 등장하는 알파벳 문자의 출현 횟수를 정렬해서 세어 보자.
```python
song = """by the rivers of babylon, there we sat down
yeah we wept, when we remember zion.
when the wicked carried us away in captivity
required from us a song
new how shall we sing the lord's song in a strange land
"""

alphabet = dict() # 빈 사전을 정의

# 키가 소문자 알파벳, 값이 갯수인 alphabet 사전을 만든다.
for alpha in song :
  if alpha.isalpha() == False:  # 알파벳이 아니면 이 문장 밑에 반복문을 건너뛴다.
    continue
  
  c = c.lower()   # 모든 문자를 소문자로 바꾼다.
  
  if c in alphabet :    
  # alphabet 사전이 비어있기 때문에 c에 해당하는(알파벳 소문자) 키가 있으면 +1을 하고 없으면 1의 값을 가진 키와 값을 만든다.
    alphabet[c] += 1
  else :
    alphabet[c] = 1
    
print(alphabet)

key = list(alphabet.keys())   # 알파벳 소문자(사전의 키)로만 이루어진 리스트를 만든다.
key.sort()    # 키를 정렬한다.

for c in key :
  print(c, "=>", alphabet[c])  
  # '알파벳(key 리스트에 있는) => 갯수(alphabet[c]에 해당하는 값)' 형식으로 출력한다 
```
