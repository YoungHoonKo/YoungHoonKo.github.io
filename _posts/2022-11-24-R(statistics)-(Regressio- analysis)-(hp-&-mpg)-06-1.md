---
title: 06-1. Statistics(Regression analysis)(hp & mpg)
Author: YoungHoon Ko
date: 2022-11-24 12:33:00 +0900
categories: [University(2022-Second-Semester), Statistics]
tags: [r, statistics]
image: /assets/img/마력과 연비에 대한 회귀분석 표.png
image: /assets/img/mfrow.png
---

[toc]

# 2022-11-24 통계학 과제

## 마력과 연비에 대한 회귀분석

### 문제

```markdown
R의 mtcars 중 자동 트랜스미션 차 19대를 이용하여, 단순회귀모형을 이용하여, 마력(x), 연비(y)를 어떻게 설명할 수 있는지 살펴보자.이때 `유의수준 0.05`를 사용한다. 표 1의 분산분석표에서 검정통계량 F=38.088에 대한 유의확률 $p=1.025 x 10^-5$이 유의수준 0.05보다 작으므로, 𝘏0 : 𝛃 = 0 또는 𝘏0 : 단순회귀모형이 유의하지 않다를 기각한다. 즉, 추정된 단순회귀모형이 적합하여 유의하다.모형의 결정계수가 `R^2 = 189.923/264.588 = 0.6914`이므로, 마력은 연비의 총변동 중 69.14를 설명한다.
```



### 표1. 분산분석표

| 요인           | 제곱합(SS)   | 자유도(df) | 평균제곱합(MS = ss/df) | 검정통계량(F) | 유의확률(P) |
| -------------- | ------------ | ---------- | ---------------------- | ------------- | ----------- |
| 회귀(마력 hp)  | 182.937(SSR) | 1          | 182.937                | F=38.088      | 1.025e-05   |
| 잔차(residual) | 81.651(SSE)  | 17         | 4.803                  |               |             |
| 총합           | 264.588(SST) | 18         |                        |               |             |



### 표2. 계수추정표

|                 | 추정값(Estimate) | 표준오차(Std. Error) | 검정통계량(t value) | 유의확률(Pr(>\|t\|)) |
| --------------- | ---------------- | -------------------- | ------------------- | -------------------- |
| 절편(Intercept) | 26.624848        | 1.615883             | 16.477              | 6.92e-12 ***         |
| 마력            | -0.059137        | 0.009682             | -6.172              | 1.02e-05 ***         |



### 그림1. 계수추정표로부터 구한 추정된 회귀직선식

<img src="/assets/img/마력과 연비에 대한 회귀분석 표.png" alt="이미지" style="zoom:50%;" />

```markdown
여기서, 절편에 대한 유의확률 p = 6.92 X 10^-12이 유의수준 0.05보다 작으므로, 절편은 유의하다.기울기에 대한 유의확률 p = 1.02 x 10^-5이 유의수준 0.05보다 작으므로, 기울기가 유의하다. 즉, 마력이 연비에 유의하게 영향을 미치며, 마력이 1 증가하면, 연비가 0.05912(마일/갤런) 감소한다. 잔차의 표준오차는 `𝞭(hat) = √MSE = 2.192`이다.
```



```markdown
그림2에서 잔차의 QQ-plot을 보면, 잔차가 대부분 정규분포를 벗어나지 않음을 볼 수 있다. 잔차에 대한 샤피로의 정규성검정에서 유의확률 p = 0.1044이므로, 단순회귀모형의 정규성 가정이 성립함을 알 수 있다.
```

### 그림2. 잔차식

<img src="/assets/img/mfrow.png" alt="이미지" style="zoom:50%;" />



### 코드

```R
> x <- mtcars[mtcars$am == 0, "hp"]
> y <- mtcars[mtcars$am == 0, "mpg"]
> fit <- lm(y ~ x)
> anova(fit)
Analysis of Variance Table

Response: y
          Df  Sum Sq Mean Sq F value    Pr(>F)    
x          1 182.937 182.937  38.088 1.025e-05 ***
Residuals 17  81.651   4.803                      
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1
```

```R
> summary(fit)

Call:
lm(formula = y ~ x)

Residuals:
    Min      1Q  Median      3Q     Max 
-4.1018 -1.9026  0.6114  1.5592  2.9241 

Coefficients:
             Estimate Std. Error t value Pr(>|t|)    
(Intercept) 26.624848   1.615883  16.477 6.92e-12 ***
x           -0.059137   0.009582  -6.172 1.02e-05 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 2.192 on 17 degrees of freedom
Multiple R-squared:  0.6914,	Adjusted R-squared:  0.6733 
F-statistic: 38.09 on 1 and 17 DF,  p-value: 1.025e-05
```

```R
> plot(x, y, main = "Simple regression analysis", xlab = "hp", ylab = "mpg", text(130, 14, "mpg = 26.624848 - 0.059137*hp"))
> abline(fit)
> par(mfrow=c(2, 2))
> plot(fit)
```

```R
> shapiro.test(fit$residuals)

	Shapiro-Wilk normality test

data:  fit$residuals
W = 0.92307, p-value = 0.129
```

* R^2 = 결정계수 = SSR/SST
