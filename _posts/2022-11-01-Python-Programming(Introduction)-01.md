---
title: 01. Python-Programming(Introduction)
author: YoungHoon Ko
date: 2022-11-01 13:45:23 +0900
categories: [University(2022-First-Semester), Python-Programming(Introduction)]
tags: [python, introduction]
---

[toc]

# 파이썬(입문) 과제1

## 가위바위보 게임

### 비기는 것이 없는 버전

```python
import random  # 랜덤함수 불러오기

a = ["가위", "바위", "보"]  # 가위바위보 리스트

win = 0
lose = 0
draw = 0

while True:
    computer = random.choice(a)  # 컴퓨터가 랜덤으로 가위바위보 중 하나 선택
    print(["가위", "바위", "보"])
    me = str(input("하나를 선택하시오: "))

    if me == computer:  # 나와 컴퓨터가 동일한 것을 냈을 때
        print("비겼습니다.")
        print(" 승: %d , 패: %d , 비김: %d" % (win, lose, draw))

    elif computer == "가위":  # 컴퓨터가 가위를 냈을 때
        if me == "바위":
            print("이겼습니다")
            win = win + 1
            print(" 승: %d , 패: %d, 비김: %d" % (win, lose, draw))

        elif me == "보":
            print("졌습니다")
            lose = lose + 1
            print(" 승: %d, 패: %d, 비김: %d" % (win, lose, draw))

    elif computer == "바위":  # 컴퓨터가 바위를 냈을 때
        if me == "보":
            print("이겼습니다")
            win = win + 1
            print(" 승: %d , 패: %d, 비김: %d" % (win, lose, draw))

        elif me == "가위":
            print("졌습니다")
            lose = lose + 1
            print(" 승: %d, 패: %d, 비김: %d" % (win, lose, draw))

    elif computer == "보":  # 컴퓨터가 보를 냈을 때
        if me == "가위":
            print("이겼습니다")
            win = win + 1
            print(" 승: %d , 패: %d, 비김: %d" % (win, lose, draw))

        elif me == "바위":
            print("졌습니다")
            lose = lose + 1
            print(" 승: %d, 패: %d, 비김: %d" % (win, lose, draw))
```

### 비기는 것이 있는 버전

```python
import random  # 랜덤함수 불러오기

a = ["가위", "바위", "보"]  # 가위바위보 리스트

win = 0
lose = 0
draw = 0

while True:
    computer = random.choice(a)  # 컴퓨터가 랜덤으로 가위바위보 중 하나 선택
    print(["가위", "바위", "보"])
    me = str(input("하나를 선택하시오: "))

    if me == computer:  # 나와 컴퓨터가 동일한 것을 냈을 때
        print("비겼습니다.")
        draw += 1
        print(" 승: %d , 패: %d , 비김: %d" % (win, lose, draw))

    elif computer == "가위":  # 컴퓨터가 가위를 냈을 때
        if me == "바위":
            print("이겼습니다")
            win = win + 1
            print(" 승: %d , 패: %d, 비김: %d" % (win, lose, draw))

        elif me == "보":
            print("졌습니다")
            lose = lose + 1
            print(" 승: %d, 패: %d, 비김: %d" % (win, lose, draw))

    elif computer == "바위":  # 컴퓨터가 바위를 냈을 때
        if me == "보":
            print("이겼습니다")
            win = win + 1
            print(" 승: %d , 패: %d, 비김: %d" % (win, lose, draw))

        elif me == "가위":
            print("졌습니다")
            lose = lose + 1
            print(" 승: %d, 패: %d, 비김: %d" % (win, lose, draw))

    elif computer == "보":  # 컴퓨터가 보를 냈을 때
        if me == "가위":
            print("이겼습니다")
            win = win + 1
            print(" 승: %d , 패: %d, 비김: %d" % (win, lose, draw))

        elif me == "바위":
            print("졌습니다")
            lose = lose + 1
            print(" 승: %d, 패: %d, 비김: %d" % (win, lose, draw))
```



## Up-Down 게임

- 한 숫자를 랜덤하게 뽑아서 계속해서 추론하는 문제입니다.

```python
import random #random함수 불러오기
guess= random.randrange(1, 101) #숫자 제한

print("지금부터 게임을 시작합니다.하나의 숫자를 랜덤으로 정할테니 그 수를 맞춰주세요.")

while True:
  num = int(input("1과 100사이의 수를 입력하시오: ")) #무한루프
  
  if num == guess:
    print("정답입니다.")
    break
          
  elif num < guess:
    print("up")

  elif num > guess:
    print("down")
```

