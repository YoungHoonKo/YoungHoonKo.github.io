---
title: 03. Introduction and practice of engineering computer(Factorial & Stars)
Author: YoungHoon Ko
date: 2022-11-08 09:00:00 +0900
categories: [University(2022-First-Semester), Introduction and practice of engineering computer]
tags: [c, computer_engineering]
---

[toc]

# 공학컴퓨터입문및실습 과제3

## 5!을 구해보자

```c
#include <stdio.h>

int main(void)
{
   int i = 5;
   int factorial = 1;

   while (i >= 1)
   {
      factorial *= i;
      i--;
   }
   printf("%d \n", factorial);

   return 0;
}
```



## 정수를 입력 받아 factorial을 구해보자

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void)
{
   int fact = 1;
   int i, n;

   printf("정수를 입력하시요. :");
   scanf("%d", &n);

   for (i = 1; i <= n; i++)
      fact = fact * i;

   printf("%d!은 %d입니다.", n, fact);

   return 0;
}
```



## 정수를 입력 받아 입력한 범위까지 소수 찾기

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void)
{
   int n, is_prime;

   printf("어디까지 찾을까요? : ");
   scanf("%d", &n);

   for (int i = 2; i <= n; i++)
   {
      is_prime = 1;
      for (int k = 2; k < i; k++)
      {
         if (i % k == 0)
         {
            is_prime = 0;
            break;
         }
      }
      if (is_prime == 1)
         printf("%d, ", i);
   }
   printf("\n\n");
   return 0;
}
```



## 정수를 입력하여 그 수 많큼 별 출력하기

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void)
{
   int a;
   int b;

   for (a = 1; a < 51; a++)
   {
      printf("데이터를 입력하세요. :");
      scanf("%d", &a);

      for (b=0;b < a; b++)
      printf("*");
      printf("\n");
   }
}
```

