---
title: 05. C-Programming
Author: YoungHoon Ko
date: 2022-11-26 15:34:32 +0900
categories: [University(2022-Second-Semester), C-Programming]
tags: [c, c_programming]
---

[toc]

## C Programming 실습5 

### 헤더파일 생성 후 불러와서 사용하기

- 헤더파일을 만들어서 제곱함수를 저장하고 호출하여 사용하기

- myfunc C 파일

```c
#include "myfunc.h"

int power(int x, int y)
{
  int pow = 1;

  for (int i = 1; i <= y; i++)
  {
    pow = pow * x;
  }

  return pow;
}

```



- myfunc header 파일

```c
#ifndef myfunc_h
#define myfunc_h

#include <stdio.h>

#endif /* myfunc_h */

int power(int x, int y);
```



- main 파일

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include "myfunc.h"

int main(void)
{
  int num1, num2, res;

  printf("1번째 정수를 입력하세요. \n");
  scanf("%d", &num1);

  printf("2번째 정수를 입력하세요. \n");
  scanf("%d", &num2);

  res = power(num1, num2);

  printf("%d의 %d제곱은 %d입니다.\n", num1, num2, res);

  return 0;
}
```

