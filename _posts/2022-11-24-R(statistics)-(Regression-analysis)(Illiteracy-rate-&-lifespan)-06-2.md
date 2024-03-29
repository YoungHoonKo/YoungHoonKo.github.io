---
title: 06-2. Statistics(Regression analysis)(Illiteracy rate & lifespan)
Author: YoungHoon Ko
date: 2022-11-24 13:07:00 +0900
categories: [University(2022-Second-Semester), Statistics]
tags: [r, statistics]
image: /assets/img/문맹률과 기대수명에 대한 회귀분석표.png
---

[toc]

# 2022-11-28 통계학 과제

## 문맹률이 수명에 미치는 영향에 관한 회귀분석 보고서와 문제 풀이

### 보고서

```markdown
(1)-(2) 문맹이 수명에 미치는 영향을 알아보기 위하여, 미국 50 개 주의 문맹률 % (1970년)과 기대수명 (세)(1969–71년)을 조사하 였다.
(자료: state.x77 in R, U.S. Department of Commerce, Bureau of the Census (1977)) 단순회귀분석을 실시하여 아래의 표2과 표3를 얻었다.
```



#### 표2. 분산분석: 종속변수 y는 기대수명 (세) , 독립변수 x는 문맹률 (%)

| 요인      | 제곱합(sum sq) | 자유도(df) | 평균제곱(mean sq) | F-value | 유의확률 pr(>\|t\|) |
| --------- | -------------- | ---------- | ----------------- | ------- | ------------------- |
| 회귀 모형 | 30.578(SSR)    | 1          | 30.5785           | 25.429  | 6.969e-06           |
| 잔차      | 57.721(SSE)    | 48         | 1.2025            |         |                     |
| 합계      | 88.299(SST)    | 49         |                   |         |                     |



#### 표3. 계수추정표

```R
								Estimate 			Std.Error    t value				Pr(>|t|)
(Intercept)     72.3949        0.3383      213.973			 < 2e-16 ***
x 							-1.2960        0.2570      -5.043        6.97e-06 ***   
```



#### 그림2. 미국 50개 주에 대한 문맹률(%)과 기대수명((세)의 산점도와 회귀직선

<img src="/assets/img/문맹률과 기대수명에 대한 회귀분석표.png" alt="이미지" style="zoom:50%;" />



#### 코드

```R
> mydata <- data.frame(state.x77)
> fit <- lm(mydata$Life.Exp ~ mydata$Illiteracy)
> anova(fit)
Analysis of Variance Table

Response: mydata$Life.Exp
                  Df Sum Sq Mean Sq F value    Pr(>F)    
mydata$Illiteracy  1 30.578 30.5785  25.429 6.969e-06 ***
Residuals         48 57.721  1.2025                      
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1
```

```R
> summary(fit)

Call:
lm(formula = mydata$Life.Exp ~ mydata$Illiteracy)

Residuals:
    Min      1Q  Median      3Q     Max 
-2.7169 -0.8063 -0.0349  0.7674  3.6675 

Coefficients:
                  Estimate Std. Error t value Pr(>|t|)    
(Intercept)        72.3949     0.3383 213.973  < 2e-16 ***
mydata$Illiteracy  -1.2960     0.2570  -5.043 6.97e-06 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 1.097 on 48 degrees of freedom
Multiple R-squared:  0.3463,	Adjusted R-squared:  0.3327 
F-statistic: 25.43 on 1 and 48 DF,  p-value: 6.969e-06
```

```R
> plot(mydata$Illiteracy, mydata$Life.Exp, xlab="illiteracy rate %", ylab="Life expectancy")
> abline(fit)
```





### 문제

```markdown
1. 표2에 대한 설명으로 틀린 것은 어느 것인가?

        1. 결정계수 𝑅2= 0.346 이므로 총변동 중 회귀모형이 설명하는 변동은 34.6%이다.(30.578/88.299)

        2. 𝐻0: β = 0에 대한 검정통계량은 F=25.4이다.

        3. 잔차의 평균제곱합은 57.721이다.

        4. 유의수준 0.05에서 귀무가설을 기각하므로 <그림1>의 직선 모형이 유의하다.(틀림)
        - 유의확률이 유의수준 보다 작기 때문에 귀무가설을 기각함, 그래프도 틀린 그래프가 됨
        5. 위 보기 중 답 없음
```



- 한 번 풀어봐

```markdown
2. 표3에 대한 설명으로 틀린 것은 어느 것인가?

        1. 𝐻0: α = 0에 대한 검정통계량은 t=213.973이고, 유의수준 0.05에서 y절편이 0이 아니다.

        2. 유의수준 0.05에서 𝐻0: β=0 에 대한 p 값이 0.05보다 작으므로, 문맹률이 수명에 유의하게 영향을 미친다고 볼 수 있다.

        3. 표2의 F-검정통계량과 표3에서 𝐻0: β = 0에 대한 t-검정통계량의 제곱은 동일하다.(틀림)
        - 다름

        4. 유의수준 0.05에서 문맹률이 1%감소할 때 수명이 1.296세 감소한다고 할 수 있다. 

        5. 위 보기 중 답 없음
```

- R^2 = 결정계수 = SSR/SST
