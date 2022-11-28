---
title: 03. Statistics(Central limit theorem)
Author: YoungHoon Ko
date: 2022-10-24 11:33:00 +0900
categories: [University(2022-Second-Semester), Statistics]
tags: [r, statistics]
image: /assets/img/limt3.png
image: /assets/img/limit10.png
image: /assets/img/limit30.png
---

[toc]

# 2022-10-24 통계학 과제

## 중심극한정리 B(3, 1/6)의 표본평균의 분포

### n = 3개

```R
# 3개
set.seed(20221024)
par(mfrow=c(2,2))
x <- rbinom(3000, 3, 1/6) # B(3, 1/6)에서 난수를 3000개 생성함

x <- matrix(x, 1000, 3) # 1000x3 행렬로 변환

x.mean <- apply(x, 1, mean) # 각 행에서 3개 난수의 평균 계산

hist(x.mean, main=" ", freq=F, xlab=" ", xlim=c(0,2.0), ylim=c(0,6))
```

![이미지](/assets/img/limt3.png)



### n = 10개

```R
# 10개
set.seed(20221024)
par(mfrow=c(2,2))
x <- rbinom(10000, 3, 1/6) # B(3, 1/6)에서 난수를 3000개 생성함

x <- matrix(x, 1000, 10) # 1000x3 행렬로 변환

x.mean <- apply(x, 1, mean) # 각 행에서 3개 난수의 평균 계산

hist(x.mean, main=" ", freq=F, xlab=" ", xlim=c(0,2.0), ylim=c(0,6))
```

![이미지](/assets/img/limit10.png)



### n = 30개

```R
# 30개
set.seed(20221024)
par(mfrow=c(2,2))
x <- rbinom(30000, 3, 1/6) # B(3, 1/6)에서 난수를 3000개 생성함

x <- matrix(x, 1000, 30) # 1000x3 행렬로 변환

x.mean <- apply(x, 1, mean) # 각 행에서 3개 난수의 평균 계산

hist(x.mean, main=" ", freq=F, xlab=" ", xlim=c(0,2.0), ylim=c(0,6))
```

![이미지](/assets/img/limit30.png)