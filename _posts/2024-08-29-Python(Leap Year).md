---
title: 03. Python(Leap Year)
Author: YoungHoon Ko
date: 2024-08-29 19:45:00 +0900
categories: [Python, Practice_Python]
tags: [python, python_p]
---

[toc]

# 윤년(Leap Year)

## 윤년의 개념

- **<u>윤년은 태양의 공전 주기와 달력상의 연도 간의 차이를 조정하기 위해 도입된 개념</u>**
- 윤년에는 평소보다 하루가 추가되어 1년이 366일 됨

## 윤년의 조건

1. 연도가 4의 배수이면서 100의 배수가 아닐 때
2. 연도가 4의 배수이면서 100의 배수이지만 400의 배수일 때

```python
year = int(input())

if year % 4 == 0:
    if year % 100 == 0:
        if year % 400 == 0:
            print(f"{year}년은 윤년입니다.")
        else:
            print(f"{year}년은 평년입니다.")
    else:
        print(f"{year}년은 윤년입니다.")
else:
    print(f"{year}년은 평년입니다.")
```

