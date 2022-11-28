---
title: 01. Introduction and practice of engineering computer(Basic Coding Test)(1)
Author: YoungHoon Ko
date: 2022-11-06 00:45:00 +0900
categories: [University(2022-First-Semester), Introduction and practice of engineering computer]
tags: [c, computer_engineering]
---

[toc]

# 공학컴퓨터입문및실습 과제1

## 4칙연산

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void)
{
   int x;
   int y;
   int result;

   printf("첫 번째 숫자를 입력해주세요. :"); // 첫 번째 숫자를 지정합니다.
   scanf("%d", &x);

   printf("두 번째 숫자를 입력해주세요. :"); // 두 번째 숫자를 지정합니다.
   scanf("%d", &y);

   result = x + y; // 덧셈
   printf("두 수의 합 = %d \n", result);

   result = x - y; //뺄셈
   printf("두 수의 차 = %d \n", result);

   result = x * y; //곱셈
   printf("두 수의 곱= %d \n", result);

   result = x / y; //나눗셈
   printf("두 수의 몫= %d \n", result);

   return 0;
}
```



## 여행비용 계산

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void)
{
   int air, hotel, pocket, day;
   int cost;
   
   printf("여행은 몇박인가요? :");
   scanf("%d", &day);
   
   printf("항공권 가격 :");
   scanf("%d", &air);

   printf("호텔 1박 가격 :");
   scanf("%d", &hotel);

   printf("하루에 필요한 용돈 :");
   scanf("%d", &pocket);

   cost = air + (hotel)*day + (day) * pocket;

   printf("총 여행 비용 :");

   printf("%d", cost);

   return 0;
}
```



## 순서를 바꿔서 출력

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void)
{
   int x;
   int y;

   scanf("%d %d", &x, &y);
   printf("%d %d\n", y, x); // 순서를 바꾸어서 출력하는 함수

   return 0;
 }
```



## 두 변수의 값을 바꾸어 출력

```c
#include <stdio.h>

int main(void)
{
   int x, y, temp;

   x = 3;
   y = 5;

   printf("x = %d, y = %d \n", x, y);

   temp = x;
   x = y;
   y = temp;

   printf("x = %d, y = %d \n", x, y);

   return 0;
}
```



## float형과 double형의 차이

```c
#include <stdio.h>

int main(void)
{
   float fvalue = 1234567890.12345678901234567890;
   //float형은 6개의 유효 숫자를 가질 수 있으므로 8번째 자릿수는 정확한 값이 나오지 않는다.
   double dvalue = 1234567890.12345678901234567890;
   //double형은 15자리 정도의 유효 숫자를 가질 수 있다.
   printf("float형 변수=%35.25f\n", fvalue);
   printf("double형 변수=%35.25f\n", dvalue);

   return 0;
}
```



## 언더플로우, 오버플로우

```c
#include <stdio.h>

int main(void)
{
   float x = 1e39;
   float y = 1.23456e-46;

   printf("x=%e\n", x);
   printf("y=%e\n", y);

   return 0;
}
```



## 	부동소수점

```c
#include <stdio.h>

int main(void)
{
   float value = 0.1;
   printf("%.20f \n", value);  //%.20는 소수점 이하 20자리를 표현하라는 것이다.
   return 0;
}
```



## 원의 표면적과 부피 구하기

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#define PI  3.141592

int main(void)
{
   double radius;
   double a;
   double b;

   printf("반지름을 입력하십시요.:");
   scanf("%lf", &radius);

   a = 4.0 * PI* (radius * radius);
   printf("구의 표면적: %lf \n", a);

   b = 4.0 / 3.0 * PI * (radius * radius * radius);
   printf("구의 부피: %lf \n", b);

   return 0;
}
```



## 다항식(3x^3 - 7x^2)의 값 구하기

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
int main(void)
{
   double x;
   double result;

   printf("x값을 입력하시오.: ");
   scanf("%lf", &x);

   result = (3*x * x * x) - (7*x * x) + 9;


   printf("다항식의 값은 %lf입니다.\n", result);

   return 0;
}
```

