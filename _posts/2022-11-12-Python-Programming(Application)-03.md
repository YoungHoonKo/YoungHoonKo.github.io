---
title: 03. Python-Programming(Application)
author: YoungHoon Ko
date: 2022-11-12 00:45:00 +0900
categories: [University(2022-Second-Semester), Python-Programming(Application)]
tags: [python, application]
image: /assets/img/wordcloud.png
image: /assets/img/CleanShot 2022-11-14 at 08.15.24@2x.png
---

[toc]

# 파이썬(응용) 과제3

## 9장 심화문제 1번 ~ 9번

### 9.1

```python
name = input("이름을 입력하시오. : ")
name = name.split(' ')
name[1]
```

```python
이름을 입력하시오. : 고 영 훈

# 결과
'영'
```



### 9.2

```python
import string

a = input("문자열을 입력하시오. : ")
b = string.ascii_uppercase
c = string.ascii_lowercase
ls = []
for i in range(len(a)):
    if a[i].isupper():
        ls.append(a[i])
    elif a[i].islower():
        print(a[i], end='')
for j in range(len(ls)):
    print(ls[j], end='')
```

```python
문자열을 입력하시오. : JoKenTive

# 결과
oeniveJKT
```



### 9.3

```python
import string

a = input("문자열을 입력하시오. : ")

def num(a):
    num_upper = num_lower = num_number = num_spc = 0
    for i in range(len(a)):
        if a[i] in list(string.ascii_uppercase):
            num_upper += 1
        elif a[i] in list(string.ascii_lowercase):
            num_lower += 1
        elif a[i].isdigit(): # isdigit()함수 : 어떤 문자열이 숫자의 형태이면 True를 반환함
            num_number += 1
        else:
            num_spc += 1
    return num_upper, num_lower, num_number, num_spc

b = list(num(a))
print("대문자, 소문자, 숫자, 특수문자의 개수")
print("대문자 = %d" % b[0])
print("소문자 = %d" % b[1])
print("숫자 = %d" % b[2])
print("특수문자 = %d" % b[3])
```

```python
문자열을 입력하시오. : 123!@#ASDasd

# 결과
대문자, 소문자, 숫자, 특수문자의 개수
대문자 = 3
소문자 = 3
숫자 = 3
특수문자 = 3
```



### 9.4

```python
a = list(input("a = "))
b = list(input("b = "))
new_str1 = []
new_str2 = []

if len(a) != len(b):
    raise
else:
    for i in range(len(a)):
        new_str1.append(a[i]+b[i])
        new_str2.append(a[i] + b[-i-1])
print("".join(new_str1))
print("".join(new_str2))
```

```python
a = ABCD
b = 1234

# 결과
A1B2C3D4
A4B3C2D1
```



### 9.5

```python
import re

s = "Korea is awesome! I REALLY LOVE KOREA."
s1 = re.sub(r"[.]", "", s)
# s1 = s1.split() 굳이 자를 필요 없음!!

a = s.count("KOREA")
b = s.count("Korea")
c = s.count("korea")
# print(a)
# print(b)
# print(c)

print(s)
print("Korea의 출현 횟수 : %d" % int(a + b + c))
```

```python
# 결과
Korea is awesome! I REALLY LOVE KOREA.
Korea의 출현 횟수 : 2
```



### 9.6

```python
s = {"English" : 89, "Science" : 90, "Math" : 92, "History" : 80}
a = s.values()
a = list(a)
# print(a)

count = 0
for i in range(len(a)):
    count += int(a[i])

sum_val = count
mean = sum_val/len(a)

print("문장 s : English = 89, Science = 90, Math = 92, History = 80")
print("총점 : %d" % sum_val)
print("평균점수 %.2f" % mean)
```

```python
# 결과
문장 s : English = 89, Science = 90, Math = 92, History = 80
총점 : 351
평균점수 87.75
```



### 9.7

```python
import string

src_str = string.ascii_uppercase + string.ascii_lowercase

def ciper(a):          # 암호화 코드를 만드는 함수
    idx = src_str.index(a)
    return dst_str[idx]

src = input('문장을 입력하시오: ')
d = int(input("이동시킬 칸 수를 입력하시오"))
dst_str = src_str[d:] + src_str[:d]
print('암호화된 문장 : ', end='')

for ch in src:
    if ch in src_str:
        print(ciper(ch), end='')
    else:
        print(ch, end='')
  
print()
```

```python
문장을 입력하시오: Veni, Vedi, veci
이동시킬 칸 수를 입력하시오3

# 결과
암호화된 문장 : Yhql, Yhgl, yhfl
```



### 9.8

```python
import re

a = input("문장을 입력하시오 : ")
a = re.sub(r"[.]", "", a) # 특수문자 제거 코드. []안에 제거하고 싶은 특수문자를 넣으면 된다.
a = a.split()
# print(a)
ls_E = []
ls_N = []
ls_E_N = []
for i in range(len(a)):
    if a[i].isalpha():
        ls_E.append(a[i])
    elif a[i].isdigit():
        ls_N.append(a[i])
    else:
        ls_E_N.append(a[i])


print("영문 단어 : %s" % ' '.join(ls_E))
print("숫자 : %s" % ' '.join(ls_N))
print("영문자+숫자 : %s" % ' '.join(ls_E_N))
```

```python
# 입력
문장을 입력하시오 : Jian777 is very famous Data scientist. He is only 26 years old but published 19 papers.

# 결과
영문 단어 : is very famous Data scientist He is only years old but published papers
숫자 : 26 19
영문자+숫자 : Jian777
```



### 9.9(텍스트에서 제거)

```python
pip install wikipedia
```

```
# 결과
Requirement already satisfied: wikipedia in /Users/goyeonghun/opt/anaconda3/lib/python3.9/site-packages (1.4.0)
Requirement already satisfied: requests<3.0.0,>=2.0.0 in /Users/goyeonghun/opt/anaconda3/lib/python3.9/site-packages (from wikipedia) (2.27.1)
Requirement already satisfied: beautifulsoup4 in /Users/goyeonghun/opt/anaconda3/lib/python3.9/site-packages (from wikipedia) (4.11.1)
Requirement already satisfied: charset-normalizer~=2.0.0 in /Users/goyeonghun/opt/anaconda3/lib/python3.9/site-packages (from requests<3.0.0,>=2.0.0->wikipedia) (2.0.4)
Requirement already satisfied: urllib3<1.27,>=1.21.1 in /Users/goyeonghun/opt/anaconda3/lib/python3.9/site-packages (from requests<3.0.0,>=2.0.0->wikipedia) (1.26.9)
Requirement already satisfied: certifi>=2017.4.17 in /Users/goyeonghun/opt/anaconda3/lib/python3.9/site-packages (from requests<3.0.0,>=2.0.0->wikipedia) (2021.10.8)
Requirement already satisfied: idna<4,>=2.5 in /Users/goyeonghun/opt/anaconda3/lib/python3.9/site-packages (from requests<3.0.0,>=2.0.0->wikipedia) (3.3)
Requirement already satisfied: soupsieve>1.2 in /Users/goyeonghun/opt/anaconda3/lib/python3.9/site-packages (from beautifulsoup4->wikipedia) (2.3.1)
Note: you may need to restart the kernel to use updated packages.
```



- 특정 문자 제거하기

```python
import wikipedia
import re

wiki = wikipedia.page('Korea')
text = wiki.content
text = re.sub("Korean","", text)
text = re.sub("korean","", text)
text = re.sub("south","", text)
text = re.sub("South","", text)
text = re.sub("North","", text)
text = re.sub("north","", text)
text = re.sub("world","", text)
text = re.sub("World","", text)
text = re.sub("country","", text)
text = re.sub("Country","", text)
print(text)
```

```
# 텍스트가 너무 길어서 생략
```



- 제거한 문자 확인

```python
# 텍스트에서 제거한 문자 확인
# -1이 반환되면 제거 완료
a=text.find('Korean')
b=text.find('korean')
c=text.find('south')
d=text.find('South')
e=text.find('north')
f=text.find('North')
g=text.find('country')
h=text.find('Country')
print(a)
print(b)
print(c)
print(d)
print(e)
print(f)
print(g)
print(h)
```

```python
# 결과
-1
-1
-1
-1
-1
-1
-1
-1
```



- 그림 그리기

```python
from wordcloud import WordCloud

wordcloud = WordCloud(width = 2000, height = 1500).generate(text)
```

```python
import matplotlib.pyplot as plt
plt.figure(figsize=(14, 8))
# 이미지 보여줌
plt.imshow(wordcloud) 
plt.show()
```

<img src="/assets/img/wordcloud.png" alt="이미지" style="zoom:50%;" />



### 9.9(STOPWORD 사용)

```python
import wikipedia
from wordcloud import WordCloud, STOPWORDS
import matplotlib.pyplot as plt
```

```python
# 부산에 관한 텍스트를 불러옴
wiki = wikipedia.page('Busan Metropolitan City')
text = wiki.content
s_word = STOPWORDS.union({'Japan', 'japanese', 'China', 'Seoul', 'Daegu', 'North Korea', 'country', 'Country'})

wordcloud = WordCloud(width = 2000, height = 1500, stopwords = s_word).generate(text)
plt.figure(figsize=(14, 8))
plt.imshow(wordcloud) 
plt.show()
```

<img src="/assets/img/CleanShot 2022-11-14 at 08.15.24@2x.png" alt="이미지" style="zoom:50%;" />

