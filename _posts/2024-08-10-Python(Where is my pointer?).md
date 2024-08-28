---
title: 02. Python(Wher is my pointer?)
Author: YoungHoon Ko
date: 2024-08-10 22:45:00 +0900
categories: [Python, Practice_Python]
tags: [python, python_p]
image: /assets/img/before_click.jpg
image: /assets/img/after_click.jpg
---

[toc]

# Do you know whre pointer is?

- **Use this!**

```python
from pickle import SHORT_BINBYTES
from math import ceil
from tkinter import *
def clickMouse(event):
    txt = ''
    if event.num == 1:
        txt += "마우스 왼쪽 버튼이 ("
    elif event.num == 2:
        txt += "마우스 오른쪽 버튼이 ("
    elif event.num == 3:
        txt += "마우스 중간 버튼이 ("

    txt += str(event.y)+","+str(event.x)+")에서 클릭됨"
    label1.configure(text=txt)

window = Tk()
window.geometry("400x400")
label1 = Label(window, text="이곳이 바뀜")

window.bind("<Button>", clickMouse)

label1.pack(expand=1, anchor=CENTER)
window.mainloop()
```

## Explanation

- 마우스가 위치를 가져오기 위해 math 라이브러리를 사용
- 딕셔너리, 리스트, 클래스 등의 자료형을 변환 없이 그대로 파일로 저장하고 이를 불러오는 pickle 모듈을 사용
- 화면으로 확인하기 위해 tkinter 사용
- 확인할 화면의 크기는 **400x400**을 사용
- 실행 시 나오는 페이지

![](/assets/img/before_click.png)

![](/assets/img/after_click.png)
