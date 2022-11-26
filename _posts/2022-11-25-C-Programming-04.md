---
title: 04. C-Programming
Author: YoungHoon Ko
date: 2022-11-26 15:34:32 +0900
categories: [University(2022-Second-Semester), C-Programming]
tags: [c, c_programming]
---

[toc]

## C Programming 실습4

- 함수에서 전달받는 인수를 parameter(매개변수) 또는 가인수라 하고, 출력하는 인수를 실인수(argument)라고 한다.

### 기본적인 함수사용

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

void buy(void){
  printf("차를 구입했습니다.\n");
}


int main(void){

  buy();

  printf("차를 한 대 더 구입합니다.\n");

  buy();

  return 0;
}
```



### 함수 변수를 넣어 사용하기1

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

void buy(int x){
  printf("%d만 원짜리 차를 구입했습니다.\n", x);
}


int main(void){

  buy(20);
  buy(30);

  return 0;
}
```



### 함수 변수를 넣어 사용하기2

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int buy(int x, int y){
  int z;

  printf("%d만원과 %d만 원짜리의 차를 구입했습니다.\n", x, y);

  z = x + y;

  return(z);
}

int main(void){

  int num1, num2, sum;

  printf("얼마짜리 차를 구입했습니까?\n");
  scanf("%d", &num1);

  printf("얼마짜리 차를 구입했습니까?\n");
  scanf("%d", &num2);

  sum = buy(num1, num2);

  printf("합계는 %d만 원 입니다.\n", sum);

  return 0;
}
```



### 전역변수와 지역변수

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int a = 0;

void func(void){

  int c = 2;

  printf("func함수에서는 a와 c를 사용할 수 있습니다.\n");
  printf("변수 a의 값은 %d입니다.\n", a);
  printf("변수 c의 값은 %d입니다.\n", c);
}

int main(void){
  int b = 1;

  printf("main함수에서는 a와 b를 사용할 수 있습니다.\n");
  printf("변수 a의 값은 %d입니다.\n", a);
  printf("변수 b의 값은 %d입니다.\n", b);

  func();

  return 0;
}
```



### static 사용

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int a = 0;

void func(void)
{
  int b = 0;        // b는 함수가 실행될 때 마다 초기화 됨
  static int c = 0; // static = 맨 처음만 초기화

  printf("변수 a는 %d, 변수 b는 %d, 변수 c는 %d입니다.\n", a, b, c);

  a++;
  b++;
  c++;
}

int main(void)
{

  for (int i = 0; i < 5; i++)
  {
    func();
  }

  return 0;
}
```

