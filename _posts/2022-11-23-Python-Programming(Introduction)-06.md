---
title: 06. Python-Programming(Introduction)
Author: YoungHoon Ko
date: 2022-11-23 16:31:45 +0900
categories: [University(2022-First-Semester), Python-Programming(Introduction)]
tags: [python, introduction]
image: /assets/img/drink_muchine.png
---

[toc]

# 파이썬(입문) 자판기 프로그래밍

- 클래스를 활용해서 만들어봤다.

## 코드

```python
class drink_muchine:
 
    def __init__(self):
        self.p = {'사과 주스' : 900, '오렌지 주스' : 1000,'라떼' : 1000,'사이다' : 1300, '우유' : 1600,'콜라' : 2500 }
        self.n = {1:'사과 주스', 2:'오렌지 주스', 3:'라떼', 4:'사이다', 5:'우유', 6:'콜라'}
        self.money = 0
 
    def showmenu(self):
        print('[종류]')
        i = 1
        for k, v in self.p.items():
            print(str(i)+'.', k, v, '원')
            i+=1
        print()
 
 
    def inputmoney(self):
        while True:
            try:
                self.money += int( input('현금을 투입해 주세요 : ') )
            except Exception as e:
                print(e)
                continue
            else:
                print('잔액:', self.money)
                print()
                break
 
 
    def buy(self):
        try:
            n = int(input('번호를 선택해주세요(종료:0):'))
        except Exception as e:
            print(e)
        else:
            if n == 0:
                return False       
 
            if n>=1 and n<=6:
                if self.money >= self.p[ self.n[n] ]:
                    print( self.n[n], '구입완료' )
                    self.money = self.money - self.p[ self.n[n] ]
                    print('잔액:', self.money)
                else:
                    print('잔액이 부족합니다.')
                    self.inputmoney()
        
            else:
                print('잘못된 번호입니다.')
 
        return True
 
 
d = drink_muchine()
d.showmenu()
d.inputmoney()
 
while d.buy():    
    print()
 
print('자판기 종료합니다.')
print('거스름돈 : ', d.money, '원')
```



## 결과

<img src="/assets/img/drink_muchine.png" alt="이미지" style="zoom:50%;" />



## 소감

- 여러번 실행했을 때 어떤 항목을 몇개 구입했는지 카운트하는 코드를 적었으면 더 좋았을 것 같다.