---
title: 02. Statistics
author: YoungHoon Ko
date: 2022-09-25 16:33:00 +0900
categories: [University(2022-Second-Semester), Statistics]
tags: [r, statistics]
---

[toc]

# 2022-09-25 통계학 두 번째 과제

## 2장 3번, 3장 8, 9, 10번 문제 풀이

### 2장 3번

```R
# 2장 3번 문제 풀이
iris
x <- iris[1:50,1]
x

#평균
mean(x)
#분산
var(x)
#표준편차
sd(x)

#중앙값
median(x)
#최대값
max(x)
#최소값
min(x)
#범위
range(x)
#Q1, Q2, Q3
quantile(x)
#IQR
IQR(x)

#상자도표
boxplot(x)
#히스토그램
hist(x)

#이상치 찾기
max(x)
quantile(x)
5.2 + 1.5 * IQR(x)
#Q3 + 1.5 * IQR을 벗어나는 이상치는 없다(max = Q3 + 1.5 * IQR)

min(x)
quantile(x)
4.8 - 1.5 * IQR(x)
#Q1 - 1.5 * IQR을 벗어나는 이상치는 없다(min > Q1 - 1.5 * IQR)
```



### 3장 8번

```R
# 8
# mtcars에서 mpg를 y축, wt를 x축 변수로 두자. 산점도를 그려라. mpg=a+b*wt를 만족하는 최적직선식에서 a와 b를 구하라.
# 1.산점도와 최적직선식을 한 그래프에 그려라.
wt <- mtcars$wt
mpg <- mtcars$mpg
par(mar=c(1,1,1,1)) # Error in plot.new() : figure margins too large 오류 발생시 실행
cor(wt, mpg) # 상관 계수 출력
plot(wt, mpg)
fit <- lm(mpg~wt)
abline(fit, col="red")
# 2.wt와 mpg의 상관계수 계산하라.
fit
# wt = -5.344, mpg = 37.285
```



### 3장 9번

```R
# 9
# iris에서 Species별로 Sepal.Length의 통계량을 계산하자.
# 1.Species 집단 별로 평균과 표준편차를 계산하여, 표를 만들어라.
iris
a <- aggregate(Sepal.Length~Species, data = iris, mean)
b <- aggregate(Sepal.Length~Species, data = iris, sd)
a
b
# 2.Species 집단 별로 Sepal.Length의 상자도표를 그려라.
boxplot(Sepal.Length~Species, data = iris, xlab = "Species", ylab = "Sepal.Length")
```



### 3장 10번

```R
#10
# Titanic에서 객실 1,2,3 등급 별, 여성, 어른 자료를 이용하자
# 1.객실과 생존여부에 대한 교차표를 구하라(전체%, 행%, 열%)
Titanic
mytable3 <- Titanic[1:3, "Female","Adult",]
mytable3
library(gmodels)
CrossTable(mytable3)
# 2.모자이크 도표와 막대그래프를 그려라
plot(mytable3)
pt <- prop.table(mytable3, 1)*100
barplot(pt, beside=T, legend=c("1","2","3"))
```

