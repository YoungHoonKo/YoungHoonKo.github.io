---
title: 07. Statistics
Author: YoungHoon Ko
date: 2022-11-28 15:07:00 +0900
categories: [University(2022-Second-Semester), Statistics]
tags: [r, statistics]
image: /assets/img/분산분석 보고서.png
---

[toc]

# 석회황이 벌에게 미치는 효과 연구 보고서

## 정보

```markdown
R의 OrchardSprays는 8가지 농도(A>B>...>H)의 석회황유화액(lime surphur emulsion)을 자당 용액(sucrose solution)에 섞은 후, 농도별로 8 개의 벌 방에 발랐다.<br>
여기에 100 마리 벌을 넣은 후 2시간 뒤에, 각 벌 방에서 줄어든 자당 용액의 양이 얼마인지 측정하였다.<br>
그림1은 농도별로 자 당 감소량의 상자도표이고, 표1은 농도별 자당 감소량의 평균, 표준편차 를 나타낸다.<br>
일원배치 분산분석법을 이용하여, 석회황 농도에 따라서 줄어든 자당 용액의 양의 양이 같은지 살펴보자.<br>
또한 던컨의 다중비교법을 이용하여, 어떤 농도에서 줄어든 자당 용액의 양이 다른지 살펴보자. 유의수준 0.0.5 를 사용한다.
```

<img src="/assets/img/분산분석 보고서.png" alt="분산분석 보고서" style="zoom:50%;" />

## 표1

- 표1. 석회황 농도별 자당 감소액의 기술통계

| 농도 |  평균  | 표준편차 | 반복수 | 최소 | 최대 |
| :--: | :----: | :------: | :----: | :--: | :--: |
|  A   | 4.625  |  3.204   |   8    |  2   |  12  |
|  B   | 7.625  |  3.292   |   8    |  4   |  14  |
|  C   | 25.250 |  24.429  |   8    |  9   |  84  |
|  D   | 35.000 |  13.438  |   8    |  20  |  57  |
|  E   | 63.125 |  26.910  |   8    |  39  | 114  |
|  F   | 69.000 |  29.189  |   8    |  20  | 114  |
|  G   | 68.500 |  20.142  |   8    |  24  |  92  |
|  H   | 90.250 |  24.224  |   8    |  69  | 130  |



## 표2

- 표2은 일원배치 분산분석을 실시하여 얻은 분산분석표이다.
- 표2. 일원배치 분산분석표

| 요인 | 제곱합 | 자유도 | 평균제곱합 | 검정통계량 |     P     |
| :--: | :----: | :----: | :--------: | :--------: | :-------: |
| 농도 | 56160  |   7    |    8023    |   19.06    | 9.499e-13 |
| 잔차 | 23570  |   56   |    421     |            |           |
| 총합 | 79730  |   63   |            |            |           |

-  유의확률 p=(9.499e-13 )이므로, 농도에 따른 자당 감소효과가 동일하다고 볼 수 (**있다**, 없다).



## 표3

- 표3는 던컨의 다중비교법을 실시한 결과이다.
- 농도 F, G, E의 자당 감소량은 동일하다.
- 농도 B, A의 자당 감소량은 동일하다.
- 농도 H의 자당 감소량은 나머지와 다르다.
- 농도 D의 자당 감소량은 농도 C의 자당 감소량을 제외한 나머지와다르다.
- 농도 C의 자당 감소량은 나머지와 다르다.
- 표3. 던컨의 다중비교법 결과. 던컨 집단이 같은 글자이면, 평균이 유의하게 다르지 않다.

| 농도 |  평균  | 던컨집단 |
| :--: | :----: | :------: |
|  H   | 90.250 |    a     |
|  F   | 69.000 |    b     |
|  G   | 68.500 |    b     |
|  E   | 63.125 |    b     |
|  D   | 35.000 |    c     |
|  C   | 25.250 |    cd    |
|  B   | 7.625  |    d     |
|  A   | 4.625  |    d     |



## 부록(코드)

```R
> boxplot(decrease~treatment, data=OrchardSprays)
```

```R
> fit <- lm(decrease ~ treatment, data = OrchardSprays)
```

```R
> anova(fit)
Analysis of Variance Table

Response: decrease
          Df Sum Sq Mean Sq F value    Pr(>F)    
treatment  7  56160  8022.9  19.062 9.499e-13 ***
Residuals 56  23570   420.9                      
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1
```

```R
install.packages("agricolae")
library(agricolae)
```

```R
> duncan.test(fit, "treatment", alpha = 0.05, console = TRUE)

Study: fit ~ "treatment"

Duncan''s new multiple range test # Duncan''s에서 ''를 적은 이유는 하나만 적으면 끝까지 작은 따옴표로 묶이기 때문
for decrease 

Mean Square Error:  420.8862 

treatment,  means

  decrease       std r Min Max
A    4.625  3.204350 8   2  12
B    7.625  3.292307 8   4  14
C   25.250 24.429198 8   9  84
D   35.000 13.437687 8  20  57
E   63.125 26.909571 8  39 114
F   69.000 29.189039 8  20 114
G   68.500 20.142351 8  24  92
H   90.250 24.223660 8  69 130

Alpha: 0.05 ; DF Error: 56 

Critical Range
       2        3        4        5        6        7        8 
20.54875 21.61527 22.31804 22.82864 23.22155 23.53556 23.79336 

Means with the same letter are not significantly different.

  decrease groups
H   90.250      a
F   69.000      b
G   68.500      b
E   63.125      b
D   35.000      c
C   25.250     cd
B    7.625      d
A    4.625      d
```

