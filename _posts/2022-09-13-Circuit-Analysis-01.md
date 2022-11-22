---
title: 01. Circuit Analysis
author: YoungHoon Ko
date: 2022-09-13 16:33:00 +0900
categories: [University(2022-Second-Semester), Circuit Analysis]
tags: [circuit_analysis, python]
---

[toc]

## 2022-09-13 회로이론 첫 번째 과제

### 파이썬으로 학번, 이름, 입학년도, 휴학 여부 입력 받아서 한 문장으로 출력하기

```python
a = input('What is your name? ')
b = input('What is your Student ID? ')
c = input('When did you enroll the University? ')
d = input('Are you taking a break from school? ')
e = int(c) + 4

if c == '2022':
    c = '1st'
elif c == '2021':
    c = '2nd'
elif c == '2020':
    c = '3nd'
else:
    c = '4th'


if d == 'Y':
    f = int(input('How long do you want to take a break from the shcool ? '))
    print('%s, %s, you are %s year student in this year, aren’t you? You may graduate on February %s year.' % (a, b, c, e + f))


elif d == 'N':
    print('%s, %s, you are %s year student in this year, aren’t you? You may graduate on February %s year.' % (a, b, c, e))

```





