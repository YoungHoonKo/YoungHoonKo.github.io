---
title: 02. Circuit Analysis(Ohm's Law, P = VI)
Author: YoungHoon Ko
date: 2022-09-28 16:55:00 +0900
categories: [University(2022-Second-Semester), Circuit Analysis]
tags: [circuit_analysis, python]
---

[toc]

## 2022-09-27 회로이론 과제

### 파이썬으로 P = VI 공식을 이용하여 0이 입력된 값을 구하기

#### 코드

- I, V, P, Direction of I 를 입력하면 됨

```python
# P = IV (전력 = 전압 * 전류)
# V = P / I (전압 = 전력 / 전류)
# I = P / V (전류 = 전력 / 전압)
i, v, p, di = map(str, input("Type I, V, P, Direction of I ? ").split())
i = int(i)
v = int(v)
p = int(p)
if i == 0:
    if di == '+':
        i = (p / v)
        print("The unknown Intensity of current of the node is %0.1f A" % i)
    elif di == '-':
        i = (p / v) * -1
        print("The unknown Intensity of current of the node is %0.1f A" % i)
if v == 0:
    if di == '+':
        v = (p / i)
        print("The unknown Voltage of the node is %0.1f V" % v)
    elif di == '-':
        v = (p / i) * -1
        print("The unknown Voltage of the node is %0.1f V" % v)
if p == 0:
    if di == '+':
        p = i*v
        print("The unknown Power of the node is %0.1f W" % p)
    elif di == '-':
        p = i * v * -1
        print("The unknown Power of the node is %0.1f W" % p)

```



#### 결과

```python
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Type I, V, P, Direction of I ? 5 0 -20 +
The unknown Voltage of the node is -4.0 V
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
```

