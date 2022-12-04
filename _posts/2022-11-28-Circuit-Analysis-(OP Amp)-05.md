---
title: 05. Circuit Analysis(OP Amp)
Author: YoungHoon Ko
date: 2022-11-28 20:00:00 +0900
categories: [University(2022-Second-Semester), Circuit Analysis]
tags: [circuit_analysis, python]
---

[toc]

## 2022-11-28 회로이론 과제

### 파이썬으로 OP Amp 가중치 덧셈 프로그램

#### 코드

```python
# 가중치 덧셈 프로그램

Rf = 1000

def Register():
    Regs_num = int(input("how many Input Registers In a circuit "))
    Regs_val = list(map(int, input("Type the values of the input Registers? ").split(' ')))

    if len(Regs_val) > Regs_num or len(Regs_val) < Regs_num:
        raise('저항값의 개수가 다릅니다.')

    return Regs_val, Regs_num

def Voltage(Rnum):
    Volt_val = list(map(int, input("Type the values of the input Voltages? ").split(' ')))

    if len(Volt_val) > Rnum or len(Volt_val) < Rnum:
         raise('전압값의 개수가 다릅니다.')

    Volt_src = int(input("Type the value of the voltage source ? "))

    return Volt_val, Volt_src

def res(Rnum, Rval, Vval, Vsrc):
    res_val = 0
    for i in range(Rnum):
        if Rval[i] == 0:
            raise("0으로 나눴습니다.")
        else:
            res_val += (Rf*(Vval[i] - Vsrc)/Rval[i])
    return -res_val + Vsrc

# main
print("~"*36)
Rval, Rnum = Register()
Vval, Vsrc = Voltage(Rnum)
print("The output voltage is %.1f" %res(Rnum, Rval, Vval, Vsrc))
print("~"*54)
```



#### 출력

```python
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
how many Input Registers In a circuit 3
Type the values of the input Registers? 1000 1000 1000
Type the values of the input Voltages? 2 2 2
Type the value of the voltage source ? 0
The output voltage is -6.0
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
```

```python
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
how many Input Registers In a circuit 3
Type the values of the input Registers? 100 200 300
Type the values of the input Voltages? 1 2 3
Type the value of the voltage source ? 1
The output voltage is -10.7
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
```
