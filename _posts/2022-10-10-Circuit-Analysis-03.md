---
title: 03. Circuit Analysis
Author: YoungHoon Ko
date: 2022-10-10 17:45:00 +0900
categories: [University(2022-Second-Semester), Circuit Analysis]
tags: [circuit_analysis, python]
---

[toc]

## 2022-10-10 회로이론 세 번째 과제

### 파이썬으로 직렬-병렬 저항의 합 구하는 코드 구현

```python
print("~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~")
ID = input("What is your Student ID? ")

#A and B
AtoB = input(
    "Are Registers between Node A and B connected Series or Parallel (S/P)? ")
if AtoB == 'S':
    Ssum1 = int(input("How many registers are connected in Series? "))
    if Ssum1 == 0:
        ValofS1 = []
        ValofS1.append(0)
        AtoB_Sum = sum(ValofS1)
    else:
        ValofS1 = list(
            map(int, input("Please, type the values of registers: ").split(", ")))
        # print(ValofS1)
        AtoB_Sum = 0
        if Ssum1 == len(ValofS1):
            AtoB_Sum = sum(ValofS1)
        else:
            raise
    # print(AtoB_Sum)

elif AtoB == 'P':
    Psum1 = int(input("How many registers are connected in Parallel? "))
    if Psum1 == 0:
        ValofP1 = []
        ValofP1.append(0)
        AtoB_Sum = sum(ValofP1)
    else:
        ValofP1 = list(
            map(int, input("Please, type the val8ues of registers: ").split(", ")))
        # print(ValofP1)
        i = 0
        AtoB_Sum = 0
        while i < Psum1:
            if Psum1 == len(ValofP1):
                if ValofP1[i] == 0:
                    AtoB_Sum += 0
                    i += 1
                else:
                    AtoB_Sum += 1/ValofP1[i]
                    i += 1
            else:
                raise

        if AtoB_Sum == 0:
            AtoB_Sum = 0
        else:
            AtoB_Sum = 1/AtoB_Sum
        # print(AtoB_Sum)

else:
    raise

#B and C
BtoC = input(
    "Are Registers between Node B and C connected Series or Parallel (S/P)? ")

if BtoC == 'S':
    Ssum2 = int(input("How many registers are connected in Series? "))
    if Ssum2 == 0:
        ValofS2 = []
        ValofS2.append(0)
        BtoC_Sum = sum(ValofS2)
    else:
        ValofS2 = list(
            map(int, input("Please, type the values of registers: ").split(", ")))
        # print(ValofS2)
        BtoC_Sum = 0
        if Ssum2 == len(ValofS2):
            BtoC_Sum = sum(ValofS2)
        else:
            raise
    # print(BtoC_Sum)

elif BtoC == 'P':
    Psum2 = int(input("How many registers are connected in Parallel? "))
    if Psum2 == 0:
        ValofP2 = []
        ValofP2.append(0)
        BtoC_Sum = sum(ValofP2)
    else:
        ValofP2 = list(
            map(int, input("Please, type the values of registers: ").split(", ")))
        # print(ValofP2)
        i = 0
        BtoC_Sum = 0
        while i < Psum2:
            if Psum2 == len(ValofP2):
                if ValofP2[i] == 0:
                    BtoC_Sum += 0
                    i += 1
                else:
                    BtoC_Sum += 1/ValofP2[i]
                    i += 1
            else:
                raise
        if BtoC_Sum == 0:
            BtoC_Sum = 0
        else:
            BtoC_Sum = 1/BtoC_Sum
        # print(BtoC_Sum)

else:
    raise

#C and D
CtoD = input(
    "Are Registers between Node C and D connected Series or Parallel (S/P)? ")
if CtoD == 'S':
    Ssum3 = int(input("How many registers are connected in Series? "))
    if Ssum3 == 0:
        ValofS3 = []
        ValofS3.append(0)
        CtoD_Sum = sum(ValofS3)
    else:
        ValofS3 = list(
            map(int, input("Please, type the values of registers: ").split(", ")))
        # print(ValofS3)
        CtoD_Sum = 0
        if Ssum3 == len(ValofS3):
            CtoD_Sum = sum(ValofS3)
        else:
            raise
    # print(CtoD_Sum)

elif CtoD == 'P':
    Psum3 = int(input("How many registers are connected in Parallel? "))
    if Psum3 == 0:
        ValofP3 = []
        ValofP3.append(0)
        CtoD_Sum = sum(ValofP3)
    else:
        ValofP3 = list(
            map(int, input("Please, type the values of registers: ").split(", ")))
        # print(ValofP3)
        i = 0
        CtoD_Sum = 0
        while i < Psum3:
            if Psum3 == len(ValofP3):
                if ValofP3[i] == 0:
                    CtoD_Sum += 0
                    i += 1
                else:
                    CtoD_Sum += 1/ValofP3[i]
                    i += 1
            else:
                raise
        if CtoD_Sum == 0:
            CtoD_Sum = 0
        else:
            CtoD_Sum = 1/CtoD_Sum
        # print(CtoD_Sum)

else:
    raise

Rsum = AtoB_Sum + BtoC_Sum + CtoD_Sum
print("\n")
print("%s, the equivalent register value of the circuit is %0.1f Ω" % (ID, Rsum))

print("~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~")

```



- 함수를 썼으면 더 간단하게 할 수 있는 것을 구현하지 못함