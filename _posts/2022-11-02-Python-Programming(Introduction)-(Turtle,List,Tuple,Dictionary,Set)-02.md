---
title: 02. Python-Programming(Introduction)(Turtle, List, Tuple, Dictionary, Set)
Author: YoungHoon Ko
date: 2022-11-02 13:50:09 +0900
categories: [University(2022-First-Semester), Python-Programming(Introduction)]
tags: [python, introduction]
image: /assets/img/t-pic.png
---

[toc]

# 파이썬(입문) 과제2

## Turtle

### 거북이로 무작위 방향으로 그림을 그리는 UI 구현

```python
#프로그램1
import turtle
import random

## 전역 변수 선언 ##
myTurtle, tX, tY, tColor, tSize, tShape = [None] * 6
shapeList = []
playerTurtles = []
swidth, sheight = 500, 500


## 메인 코드 부분 ##
if __name__ == "__main__":
    turtle.title('거북 리스트 활용')
    turtle.setup(width = swidth + 50, height = sheight + 50)
    turtle.screensize(swidth, sheight)
    turtle.bgcolor('pink')
    
    shapeList = turtle.getshapes()
    for i in range(0, 100):
        random.shuffle(shapeList)
        myTurtle = turtle.Turtle(shapeList[0])
        tX = random.randrange(-swidth / 2, swidth / 2)
        tY = random.randrange(-sheight / 2, sheight / 2)
        r = random.random();g = random.random();b = random.random()
        tSize = random.randrange(1, 3)
        playerTurtles.append([myTurtle, tX, tY, tSize, r, g, b])
        
    for tList in playerTurtles:
        myTurtle = tList[0]
        myTurtle.color((tList[4], tList[5], tList[6]))
        myTurtle.pencolor((tList[4], tList[5], tList[6]))
        myTurtle.turtlesize(tList[3])
        myTurtle.goto((tList[1], tList[2]))
        
    turtle.done()
```

<img src="/assets/img/t-pic.png" alt="이미지" style="zoom:30%;" />



## 리스트

### 리스트 내포

```python
# 코드
# num을 0~5까지 리스트에 넣어라
numList = [num for num in range(0, 6)]
print(numList)

# num이 짝수이면 num^2을 리스트에 넣어라
numList2 = [num * num for num in range(0, 7) if num % 2 == 0]
print(numList2)
```

```python
# 결과
[0, 1, 2, 3, 4, 5]
[0, 4, 16, 36]
```



### zip함수

- 동시에 여러 리스트에 접근하는 함수이다.
- 여러 리스트 중 개수가 작은 것까지만 접근한다.
- `타입은 리스트 타입이 아님!!!`  zip 타입이다.
- 두 리스트를 튜플, 딕셔너리로 짝지을 때도 사용한다.

```python
# 코드
myList1 = ['a', 'b', 'c', 'd', 'e', 'f', 'g']
myList2 = ['A', 'B', 'C', 'D', 'E', 'F', 'G']
for small, big in zip(myList1, myList2):
    print(small, '-->', big)

myTup = tuple(zip(myList1, myList2)) # 튜플 변환
myDic = dict(zip(myList1, myList2)) # 딕셔너리 변환
print(myTup)
print(myDic)
```

```python
# 결과
# 리스트 zip으로 묶기
a --> A
b --> B
c --> C
d --> D
e --> E
f --> F
g --> G

# 리스트를 튜플로 변환
(('a', 'A'), ('b', 'B'), ('c', 'C'), ('d', 'D'), ('e', 'E'), ('f', 'F'), ('g', 'G'))

# 리스트를 딕셔너리로 변환
{'a': 'A', 'b': 'B', 'c': 'C', 'd': 'D', 'e': 'E', 'f': 'F', 'g': 'G'}
```



## 튜플

### 2차원 듀플을 생성한 후 모든 값을 출력하는 코드

```py
# 코드
tt = ((1, 2, 3),
      (4, 5, 6),
      (7, 8, 9))

for i in range(0, 3):
    print("\n")
    for k in range(0, 3):
        print("%3d " % tt[i][k], end='')
```

```python
# 결과
  1   2   3 

  4   5   6 

  7   8   9
```



### 튜플을 리스트로 받아서 항목 변경하는 코드

```python
# 코드
myTuple = (1, 2, 3, 4)
myList = list(myTuple) #튜플을 리스트로 받음
myList.append(5) #리스트 항목을 변경함 
myTuple = tuple(myList) #다시 리스트를 튜플로 받음
print(myTuple)
```

```python
# 결과
(1, 2, 3, 4, 5)
```



## 딕셔너리

### 딕셔너리 사용법

```python
# 코드
dic = {'학번' : '20221234', '이름' : '홍길동', '학과' : '소프트웨어융합학과'}
print(dic.keys()) #모든 키들을 출력한다
print(list(dic.keys())) #리스트를 사용하여 dict_keys를 안 보여준다

print(dic.items()) #키와 값을 튜플 형태로 출력한다

print(dic.values()) #모든 값들을 출력한다 
print(list(dic.values())) #리스트를 사용하여 dict_keys를 안 보여준다

print('학과' in dic) #키가 딕셔너리에 있는지 확인할 때 사용한다 
```

```python
# 결과
dict_keys(['학번', '이름', '학과'])
['학번', '이름', '학과']

dict_items([('학번', '20221234'), ('이름', '홍길동'), ('학과', '소프트웨어융합학과')])

dict_values(['20221234', '홍길동', '소프트웨어융합학과'])
['20221234', '홍길동', '소프트웨어융합학과']

True
```



### 딕셔너리의 모든 값을 출력하는 코드

```python
# 코드
singer = {}

singer['a'] = 1
singer['b'] = 2
singer['c'] = 3
singer['d'] = 4

for i in singer.keys():
    print("%s --> %d" % (i, singer[i]))
```

```python
# 결과
a --> 1
b --> 2
c --> 3
d --> 4
```



### 딕셔너리를 정렬하는 코드

```python
# 코드
import operator
aDict, aList = {}, []

aDict = {'홍길동': 1, '류민지': 2, '최태준': 4, '김현준': 3}
# operator.itemgetter()에서 ()안에 0을 넣으면 키 정렬, 1을 넣으면 값 정렬암
aList = sorted(aDict.items(), key=operator.itemgetter(1))

print(aList)
```

```python
# 결과
[('홍길동', 1), ('류민지', 2), ('김현준', 3), ('최태준', 4)]
```



## 세트

### 세트 사용법

```python
# 코드
s = set() #빈 세트 생성
mySet1 = {1, 2, 2, 2, 2, 3, 3, 4} #중복되는 키는 자동으로 하나만 남는다 
print(mySet1)

mySet2 ={1, 5, 3, 4, 7, 8, 9}

print(mySet1 & mySet2) #교집합(두 세트에 공통을 들어있는 것)
print(mySet1 | mySet2) #합집합(두 세트를 합친 것)
print(mySet1 - mySet2) #차집합(첫 번째 세트에만 있고 두 번째 세트에는 없는 것)
print
```

```python
# 결과
{1, 2, 3, 4}
{1, 3, 4}
{1, 2, 3, 4, 5, 7, 8, 9}
{2}
{2, 5, 7, 8, 9}
```



##  예제

- 기차 수송량에 따라 순위 매기기

```python
# 코드
import operator
 
trainTupleList = [('토마스', 5), ('헨리', 8), ('에드워드', 9), ('에밀리', 5),
                  ('토마스', 4), ('헨리', 7), ('토마스', 3), ('에밀리', 8),
                  ('퍼시', 5), ('고든', 13)]
trainDic, trainList = {}, []
tmpTup = None
totalRank, currentRank = 1, 1
 
if __name__ == "__main__" :
    for tmpTup in trainTupleList :
        tName = tmpTup[0]
        tWeight = tmpTup[1]
        if tName in trainDic :
            trainDic[tName] += tWeight
        else :
            trainDic[tName] = tWeight
 
    print('기차 수송량 목록 => ', trainTupleList)
    print('------------------------')
    trainList = sorted(trainDic.items(), key = operator.itemgetter(1),
                reverse = True)
    
    print('기차\t총 수송량 순위')
    print('------------------------')
    print(trainList[0][0], '\t', trainList[0][1], '\t', currentRank)
    for i in range(1, len(trainList)) :
        totalRank += 1
        if trainList[i][1] == trainList[i-1][1] :
            pass
        else :
            currentRank = totalRank
        print(trainList[i][0], '\t', trainList[i][1], '\t', currentRank)
```

```python
# 결과
기차 수송량 목록 =>  [('토마스', 5), ('헨리', 8), ('에드워드', 9), ('에밀리', 5), ('토마스', 4), ('헨리', 7), ('토마스', 3), ('에밀리', 8), ('퍼시', 5), ('고든', 13)]

------------------------
기차    총 수송량 순위
------------------------
헨리     15      1
에밀리   13      2
고든     13      2
토마스   12      4
에드워드  9       5
퍼시     5       6
```

