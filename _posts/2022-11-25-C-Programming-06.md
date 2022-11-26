---
title: 06. C-Programming
Author: YoungHoon Ko
date: 2022-11-26 15:34:32 +0900
categories: [University(2022-Second-Semester), C-Programming]
tags: [c, c_programming]
---

[toc]

## C Programming 실습6

- Pointer

### 포인터 기초

```c
#define _CRT_SECURE_NO_WARINGS
#include <stdio.h>

int main(void) {
  int a;
  a = 5;

  printf("변수 a의 값은 %d입니다.\n", a);
  printf("변수 a의 어드레스는 %p입니다.\n", &a);

  return 0;
}
```



### 포인터와 그 주소

```c
#define _CRT_SECURE_NO_WARINGS
#include <stdio.h>

int main(void)
{
  int a;
  int *pA;
  a = 5;
  pA = &a;

  printf("변수 a의 값은 %d입니다.\n", a);
  printf("변수 a의 어드레스는 %p입니다.\n", &a);
  printf("포인터 pA의 값은 %p입니다.\n", pA);

  return 0;
}
```



### int *pA = &a ---> *pA = a

```c
#define _CRT_SECURE_NO_WARINGS
#include <stdio.h>

int main(void)
{
  int a;
  int *pA;

  a = 5;
  pA = &a;

  printf("변수 a의 값은 %d입니다.\n", a);
  printf("변수 a의 어드레스는 %p입니다.\n", &a);
  printf("포인터 pA는 %p입니다.\n", pA);
  printf("pA의 값은 %d입니다.\n", *pA); //포인터에 *을 붙이면 값이 된다

  return 0;
}
```



### 포인터값과 어드레스값

```c
#define _CRT_SECURE_NO_WARINGS
#include <stdio.h>

int main(void)
{
  int a, b;
  int *pA;
  a = 5;
  b = 10;
  pA = &a;

  printf("변수 a의 값은 %d입니다.\n", a);
  printf("변수 a의 어드레스는 %p입니다.\n", &a);
  printf("포인터 pA의 값은 %d입니다.\n", *pA);

  pA = &b;

  printf("변수 a의 값은 %d입니다.\n", b);
  printf("변수 a의 어드레스는 %p입니다.\n", &b);
  printf("포인터 pA의 값은 %d입니다.\n", *pA);

  return 0;
}
```



### swap함수

- swap함수는 두 변수의 값을 교환하는 것으로 파이썬과 다르게 포인터로 어드레스값을 바꿔줘야한다.



#### 잘못된 코드

```c
#define _CRT_SECURE_NO_WARINGS
#include <stdio.h>

void swap(int x, int y);

int main(void)
{
  int num1 = 5;
  int num2 = 10;

  printf("변수 num1의 값은 %d입니다.\n", num1);
  printf("변수 num2의 값은 %d입니다.\n", num2);
  printf("변수 num1과 num2의 값을 교환합니다.\n");

  swap(num1, num2);

  printf("변수 num1의 값은 %d입니다.\n", num1);
  printf("변수 num2의 값은 %d입니다.\n", num2);

  return 0;

}

//잘못된 swap함수(포인터 사용X)
void swap(int x, int y)
{
  int tmp;

  tmp = x;
  x = y;
  y = tmp;
}
```



#### 정확한 코드

```c
#define _CRT_SECURE_NO_WARINGS
#include <stdio.h>

void swap(int *x, int *y);

int main(void)
{
  int num1 = 5;
  int num2 = 10;

  printf("변수 num1의 값은 %d입니다.\n", num1);
  printf("변수 num2의 값은 %d입니다.\n", num2);
  printf("변수 num1과 num2의 값을 교환합니다.\n");

  swap(&num1, &num2);

  printf("변수 num1의 값은 %d입니다.\n", num1);
  printf("변수 num2의 값은 %d입니다.\n", num2);

  return 0;

}

//정확한 swap함수
void swap(int *x, int *y)
{
  int tmp;

  tmp = *x;
  *x = *y;
  *y = tmp;
}
```

