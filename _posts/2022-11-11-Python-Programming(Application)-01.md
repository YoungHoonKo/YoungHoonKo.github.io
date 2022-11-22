---
title: 01. Python-Programming(Application)
author: YoungHoon Ko
date: 2022-11-11 02:20:00 +0900
categories: [University(2022-Second-Semester), Python-Programming(Application)]
tags: [python, application]
---

[toc]

# 파이썬(응용) 과제1

## 문제

**1)** 정수 2개를 입력 받아 평균을 구하는 함수를 완성하라.

```python
def add2():
    a = int(input("첫 번째 숫자를 입력하세요: "))
    b = int(input("두 번재 숫자를 입력하세요: "))
    
    print("평균 = ", (a+b)/2)
add2()

# 결과
첫 번째 숫자를 입력하세요: 15
두 번재 숫자를 입력하세요: 22
평균 =  18.5
```

```python
# 결과 검증
add2()

첫 번째 숫자를 입력하세요: 15
두 번재 숫자를 입력하세요: 22
평균 =  18.5
```



**2)** 섭씨 온도를 입력받아 화씨온도로 환산하는 함수를 완성하라.

𝐹 = 9/5𝐶 + 32

```python
def c2f(temp):
    F = (9/5)*temp + 32
    return F
temp = 30.5
print(f'섭씨 {temp:0.1f}도는 화씨 {c2f(temp):0.1f} 도 입니다.')

# 결과
섭씨 30.5도는 화씨 86.9 도 입니다.
```

```python
# 결과 검증
temp = 30.5
print(f'섭씨 {temp:0.1f}도는 화씨 {c2f(temp):0.1f} 도 입니다.')

섭씨 30.5도는 화씨 86.9 도 입니다.
```



**3)** 반지름을 입력 받아 원의 둘레와 면적을 구하는 프로그램을 완성하라

```python
# code
def circle(r):
    pi = 3.14
    area = pi*r*r #제곱은 곱하기로 하자
    circ = 2*pi*r
    return area, circ #return은 차례대로 1개 이상 출력 가능
area, circ = circle(3.5)
print("면적 = %0.2f"%area)
print("둘레 = %0.2f"%circ)

# 결과
면적 = 38.47
둘레 = 21.98
```

```python
# 결과 검증
area, circ = circle(3.5)
print("면적 = %0.2f"%area)
print("둘레 = %0.2f"%circ)

면적 = 38.47
둘레 = 21.98
```



**4)** while문을 사용해 1부터 1000까지의 자연수 중 3의 배수의 중 12의 배수가 아닌 수의 합을 구하는 프로그램 작성하라

```python
# code
total = []
i = 1
while i < 1000:
    i += 1 #1000 보다 작을 때 항상 1을 더해야 하기 때문에 i += 1을 맨 위에 적는게 좋다.
    if i % 3 == 0:
        if i % 12 != 0:
            total.append(i)
result = sum(total)
print(result)

# 결과
125001
```

```python
# 결과 검증
print(result)

125001
```



**5)** For문을 사용해 1부터 1000까지의 자연수 중 3의 배수의 중 12의 배수가 아닌 수의 합을 구하는 프로그램 작성하라

```python
result = 0
for i in range(1, 1001):
    if i % 3 == 0:
        if i % 12 != 0:
            result += i
    
print(result)

# 결과
125001
```

```python
# 결과 검증
print(result)

125001
```



**6)** 리스트 numbers 중 70점 이상되는 요소의 평균을 구하는 프로그램을 작성하라

```python
numbers = [70, 60, 55, 75, 95, 90, 80, 80, 85, 100]

list = []
for i in range(len(numbers)):
    if numbers[i] >= 70:
        list.append(numbers[i])
    else:
        continue

#print(list)
average = sum(list)/len(list)
print(average)

# 결과

84.375
```

```python
# 결과 검증
print(average)

84.375
```



**7)** 리스트 numbers 중 홀수와 짝수를 각각 저장하는 리스트 변수를 만들라

```python
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
odd_result = []
even_result = []

for i in range(len(numbers)):
    if numbers[i] % 2 != 0:
        odd_result.append(numbers[i])
    elif numbers[i] % 2 == 0:
        even_result.append(numbers[i])

print(odd_result)
print(even_result)

# 결과
[1, 3, 5, 7, 9]
[2, 4, 6, 8, 10]
```

```python
# 결과 검증
print(odd_result)
print(even_result)

[1, 3, 5, 7, 9]
[2, 4, 6, 8, 10]
```

