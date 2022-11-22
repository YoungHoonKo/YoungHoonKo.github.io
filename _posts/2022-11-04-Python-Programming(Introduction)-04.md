---
title: 04. Python-Programming(Introduction)
Author: YoungHoon Ko
date: 2022-11-04 14:40:11 +0900
categories: [University(2022-First-Semester), Python-Programming(Introduction)]
tags: [python, introduction]
image: /assets/img/Object-oriented-draw.png
image: /assets/img/multi1.png
image: /assets/img/multi2.png
---

[toc]

# 파이썬(입문) 과제4

## 객체 지향(Object oriented) 그림판

- 객체 지향 프로그래밍이란?
  - **프로그래밍에서 필요한 데이터를 추상화시켜 상태와 행위를 가진 객체를 만들고 그 객체들 간의 유기적인 상호작용을 통해 로직을 구성하는 프로그래밍 방법**

```python
# 코드
from tkinter import *
import math
import random

class Shape:
    color, width = '', 0
    shX1, shY1, shX2, shY2 = [0] * 4
    def drawShape(self):
        raise NotImplementedError()

class Rectangle(Shape):
    objects = None
    def __init__(self, x1, y1, x2, y2, c, w):
        self.shX1 = x1
        self.shY1 = y1
        self.shX2 = x2
        self.shY2 = y2
        self.color = c
        self.width = w
        self.drawShape()
       
    def __del__(self) :
        for obj  in self.objects :
            canvas.delete(obj)
               
    def drawShape(self) :
        sx1 = self.shX1; sy1 = self.shY1; sx2 = self.shX2; sy2 =self.shY2
        squreList = []        
        squreList.append(canvas.create_line(sx1, sy1, sx1, sy2, fill = self.color, width = self.width))
        squreList.append(canvas.create_line(sx1, sy2, sx2, sy2, fill = self.color, width = self.width))
        squreList.append(canvas.create_line(sx2, sy2, sx2, sy1, fill = self.color, width = self.width))
        squreList.append(canvas.create_line(sx2, sy1, sx1, sy1, fill = self.color, width = self.width))
        self.objects=squreList
       
class Circle(Shape) :
    objects = None
    def __init__(self,  x1, y1, x2, y2, c, w):
        self.shX1 = x1
        self.shY1 = y1
        self.shX2 = x2
        self.shY2 = y2
        self.color = c
        self.width = w
        self.drawShape()

    def __del__(self) :
        canvas.delete(self.objects)
 
    def drawShape(self) :
        sx1= self.shX1;   sy1= self.shY1;  sx2 = self.shX2;   sy2 = self.shY2
        self.objects = canvas.create_oval(sx1, sy1, sx2, sy2,
                                          outline = self.color,
                                          width = self.width)

def  getColor() :
    r = random.randrange(16, 256)
    g = random.randrange(16, 256)
    b = random.randrange(16, 256)
    return "#" + hex(r)[2:] + hex(g)[2:] + hex(b)[2:]

def getWidth() :
    return random.randrange(1, 9)

def  startDrawRect(event):
    global x1, y1, x2, y2, rectshape,cirshape
    x1 = event.x
    y1 = event.y

def endDrawRect(event):
    global x1, y1, x2, y2, rectshape,cirshape
    x2 = event.x
    y2 = event.y
    rect = Rectangle(x1, y1, x2, y2, getColor(), getWidth())
    rectshape.append(rect)

def  startDrawCircle(event):
    global x1, y1, x2, y2, rectshape,cirshape
    x1=event.x
    y1=event.y

def endDrawCircle(event):
    global x1, y1, x2, y2, rectshape,cirshape
    x2=event.x
    y2=event.y
    cir = Circle(x1, y1, x2, y2, getColor(), getWidth())
    cirshape.append(cir)

def deleteRectShape(event):
    global rectshape
    if len(rectshape) != 0 :
        dRS = rectshape.pop()
        del(dRS)

def deleteCirShape(event):
    global cirshape
    if len(cirshape) != 0 :
        dCS = cirshape.pop()
        del(dCS)

rectshape,cirshape = [],[]
window = None
canvas = None
x1, y1, x2, y2 = None, None, None, None

if __name__ == "__main__" :
    window=Tk()
    window.title("객체지향 그림판")
    canvas = Canvas(window, height = 300, width = 300)
    canvas.bind("<Button-1>", startDrawRect)
    canvas.bind("<ButtonRelease-1>", endDrawRect)
    canvas.bind("<Button-3>", startDrawCircle)
    canvas.bind("<ButtonRelease-3>", endDrawCircle)
    canvas.bind("<Double-Button-1>",deleteCirShape)
    canvas.bind("<Double-Button-2>",deleteRectShape)

    canvas.pack()
    window.mainloop()
```

<img src="/assets/img/Object-oriented-draw.png" alt="이미지" style="zoom:50%;" />



## 멀티 스레드(Multi Thread) 실습

- 스레드란?
  - 프로세스 내에서 일을 처리하는 세부실행 단위를 말함

- 멀티 스레드란?
  - 하나의 프로세스를 다수의 실행 단위로 구분하여 자원을 공유하고, 자원의 생성과 관리의 중복성을 최소화하여 수행 능력을 향상시키는 것을 **Multi Thread**라고 한다.
  - 하나의 프로그램에 동시에 여러개의 일을 수행할수 있도록 해주는 것

```python
# 코드
from tkinter import *
from tkinter.ttk import *  # progressbar를 위해 필요함
import random
import time
import threading

class ThreadProgressBar():
    thread = None
    progress = None

    def __init__(self, parent):
        self.progress = Progressbar(parent, orient=HORIZONTAL, length=500)
        self.progress.pack(side=TOP, fill=X, ipadx=10, ipady=10, padx=10, pady=10)
        self.thread = threading.Thread(target=self.runProgress, args=(self.progress,))
        self.thread.start()

    def runProgress(self, progress):
        hop = 0
        while True:
            hop = random.randrange(0,10)
            if progress['value'] >= 100:
                break
            progress['value'] += hop
            time.sleep(0.5)
    
def runThreadProgress():
    thBar1 = ThreadProgressBar(w)
    thBar2 = ThreadProgressBar(w)
    thBar3 = ThreadProgressBar(w)

if __name__ == "__main__":
    w = Tk()
    w.geometry("300x250")
    w.title("멀티 스레드")
    threadButton = Button(w, text='멀티스레드 시작', command=runThreadProgress)
    threadButton.pack(side=TOP, fill=X, ipadx=10, ipady=10, padx=10, pady=10)
    w.mainloop()
```

<img src="/assets/img/multi1.png" alt="이미지" style="zoom:50%;" />

<img src="/assets/img/multi2.png" alt="이미지" style="zoom:50%;" />