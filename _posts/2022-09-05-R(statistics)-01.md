---
title: 01. Statistics
Author: YoungHoon Ko
date: 2022-09-05 16:33:00 +0900
categories: [University(2022-Second-Semester), Statistics]
tags: [r, statistics]
---

[toc]

# 2022-09-05 통계학 첫 번째 과제

## 수업시간에 알려준 R 명령어 연습과 연습문제 2번 문제 풀이

### 명령어 연습

```R
# 계산기 처럼 사용하기
2+3
2^3
1/2
sqrt(2)
sin(pi)
exp(1)
log(exp(1))
log(10, base=10)
abs(-1)
factorial(5)
choose(5,2) # choose는 경우의 수를 찾는 것.
```

```R
# 변수
x <- 3
x+4
e <- exp(1)
e^2
```

```R
# 객체 관리
ls() #내부에 객체를 보여줌
rm(x) #x객체를 지움
rm(list = ls()) #모든 객체를 삭제
ls()
```

```R
# vector
z <- 3:13 #3부터 13까지 1간격으로 벡터 만들기
z
z <- seq(3,13,0.1) #3부터 13까지 0.1 간격으로 벡터 만들기
z
z <- 2.2*z #z에 2 곱하기.
z
# rm(a,b)
length(z) #z 벡터의 길이 구하기
z[2] #z벡터의 두 번째 성분
c(1,3,4) #1,3,4를 한 번에 붙여 벡터 하나 만들기
z[c(1,3,4)] #z 벡터 중 1,3,4번째 성분 가져오기
```

```R
# matrix
x <- c(1,2,3) #화면에는 행벡터로 보이지만 실제로는 열벡터
x
y <- c(4,5,6) #화면에는 행벡터로 보이지만 실제로는 열벡터
y
xy <- c(x,y) # 두 벡터를 하나로 붙이기
xy
A <- cbind(x,y) #c = 열, bind = 묶다 => 열붙이기를 한 것
A
B <- rbind(x,y) #r = 행, bind = 묶다 => 행붙이기를 한 것
B
A[1,2] #1행 2열의 값을 추출함
A[,2] #출력은 행으로 출력되지만 열이다.
B[1,]
# C(1,3,5,0) #벡터 만들기
A <- matrix(c(1,3,5,0),2,2) #행렬 만들기 
A
t(A) #행렬 교환하기
solve(A) #역행렬 구하기
```

```R
# data.frame
mtcars
help(mtcars) #도움말
head(mtcars) #첫 몇 줄 보기
names(mtcars) #열 이름 보기
summary(mtcars) #기본 기술 통계 보기 
mtcars$am # am 열(변수) 가져오기
mtcars$hp #hp 열(변수) 가져오기
#그냥 보면 직관적이지 않다
table(mtcars$am) #빈도표 만들기, 0과 1의 개수를 직관적으로 보여줌
boxplot(mtcars$hp) #상자(box)도표 구하기
summary(mtcars$hp) #기술 통계 구하기
boxplot(am~hp, data=mtcars) #am=0/1 집단 별로 hp(마력)에 대한 상자도표 그리기

#변수(열) 선택하기 또는 data.frame 쪼개기
head(mtcars)
mtcars[1:5,] #1,2,3,4,5 행 가져오기
mtcars[,2] #2열 가져오기 
table(mtcars[,2]) #직관적으로 보기
mtcars2 <- subset(mtcars,vs=1) #vs=1인 행(표본) 선택
mtcars2
mtcars3 <- subset(mtcars,vs==1&am==0)
#rm(mtcars)
mtcars3
mtcars4 <- mtcars[,c("mpg","hp")]
mtcars4
```

```R
# boxplot
boxplot(mtcars4)
```

```R
# hist
hist(mtcars$hp)
```

### 연습문제 2번 문제풀이

```R
# 0) 값 확인
x <- mtcars$cyl
x # 값 확인
```

```R
# 1) 빈도표와 상대빈도표를 작성하라
z <- table(x) #빈도표
z
prop.table(z) #상대빈도표
```

```R
# 2) 막대그래프를 그려라
barplot(z) #막대그래프 
```

```R
# 3) 원그래프를 그려라
pie(z) #원그래프
```

```R
# 4) 소형차, 중형차, 대형차의 비율은 얼마인가?
a <- prop.table(z)
a * 100
```

