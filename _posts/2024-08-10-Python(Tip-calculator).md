---
title: 01. Python(Tip-calculator)
Author: YoungHoon Ko
date: 2024-08-09 00:45:00 +0900
categories: [Python, Practice]
tags: [python, python_p]
---

[toc]

# Tip-calculator

- Split the bill includuing tips!!

```python
# Tip_calculator
Total_bill = float(input("What was the total bill? $"))
Tip_per = int(input("What percentage tip would you like to give? 10, 12 or 15? "))
Head = int(input("How many people to split the bill?"))
result = Total_bill/Head * (100 + Tip_p)/100 # 무조건 소수 둘째자리까지 반올림 하기
result = "{:.2f}".format(result) # format 형식을 취하면 확실하게 표현할 수 있음
print(f"Each person should pay: ${result}")
```

## Explanation

- 지불해야할 총 금액을 입력함

- 팁은 총 금액의 몇 퍼센트를 지불할 것인지 선택함

- 나눠 낼 인원 수 작성

- 간단한 수식 작성

  - $$
    toatalbill(totalbill + Tip/100) * 1/Head
    $$

  - $$
    toatalbill(1 + Tip/100) * 1/Head
    $$

  - $$
    toatalbill/Head * (1 + Tip/100)
    $$

- 소수점 2째자리까지 반올림 해서 보여야하기 때문에 **"round(a, n)"**을 생각했음

  - 그러나 round 함수는 끝자리가 0이면 출력하지 않아서 **"format()"** 함수로 아이디어를 바꿈
