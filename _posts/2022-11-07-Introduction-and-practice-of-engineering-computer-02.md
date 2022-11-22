---
title: 02. Introduction and practice of engineering computer
author: YoungHoon Ko
date: 2022-11-07 03:12:00 +0900
categories: [University(2022-First-Semester), Introduction and practice of engineering computer]
tags: [c, introduction_and_practice_of_engineering computer]
---

[toc]

# 공학컴퓨터입문및실습 과제2

## 문자를 입력 받아 아스키코드 찾기

```c
#include <stdio.h>

int main(void)
{
    char ch;

    printf("문자를 입력하시오: ");
    ch = getchar();

    printf("아스키 코드: %d\n", ch); //문자를 정수로 받으면 아스키코드 출력

    return 0;
}
```





## 2차 함수 계산

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void)
{
    double x = 2.0;
    double y;

    y = 3.0*x*x + 7.0*x + 9.0;
    printf("y = 3.0*x*x + 7.0*x + 9.0 = %f \n", y);

    return 0;
}
```



## 몫과 나머지를 계산

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void)
{
    int a;
    int b;
    int result1;
    int result2;

    printf("첫 번째 정수를 입력해주세요. :");
    scanf("%d", &a);


    printf("두 번째 정수를 입력해주세요. :");
    scanf("%d", &b);

    result1 = a / b;
    result2 = a % b;

    printf("목은 %d이고 나머지는 %d입니다. \n", result1, result2);

    return 0;
}
```



## 세 개의 정수를 입력받아 최대값 찾기

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void)
{
   int a, b, c, largest;

   printf("3개의 정수를 입력해주세요. :");
   scanf("%d %d %d", &a, &b, &c);

   largest = a;
   if (largest < b) largest = b;
   if (largest < c) largest = c;
   printf("가장 큰 정수는 %d이다. \n", largest);

   return 0;
}
```



## 점수를 입력해 가입여부 결정

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void)
{
   int math, chemi, physic;

   printf("수학, 화학, 물리 점수를 한 줄에 입력하세요. :");
   scanf("%d %d %d", &math, &chemi, &physic);

   if (math >= 50, chemi >= 50, physic >= 50) {
      if ((physic + math) >= 150 || (math + chemi) >= 150)
         printf("가입할 수 있습니다.\n");
      else
         printf("가입할 수 없습니다.\n");
   }
   else
   {
      printf("가입할 수 없습니다. \n");
   }
   return 0;
}
```



## 가위바위보 게임(1번만 실행)

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main(void)
{
   int computer;
   int user;
   int 가위 = 0;
   int 바위 = 1;
   int 보 = 2;

   srand(time(NULL));     // rand, srand, time is set!!

   printf("가위 바위 보 게임에 오신 것을 환영합니다.");

   printf("하나를 선택하세요(가위-0, 바위-1, 보-2):");

   computer = rand() % 3;

   scanf("%d", &user);

   if ((user + 1) % 3 == computer)
      printf("컴퓨터: %d\n사용자: %d \n컴퓨터승!\n", computer, user);

   else if ((user + 2) % 3 == computer)
      printf("컴퓨터: %d\n사용자: %d \n사용자승!\n", computer, user);

   else if (user == computer)
      printf("컴퓨터: %d\n사용자 : %d \n비겼습니다!\n", computer, user);

   return 0;
}
```



## 과세의 표준을 입력하여 소득세 계산하기

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void)
{
   int money, tax;

   printf("과세 표준을 입력하시오(만원) :");
   scanf("%d", &money);

   if (money <= 1000)
      tax = money * 0.08;
   else if (money <= 4000)
      tax = (1000 * 0.08) + (money - 1000) * 0.17;
   else if (money <= 8000)
      tax = (1000 * 0.08) + (3000 * 0.17) + (money - 4000) * 0.26;
   else
      tax = (1000 * 0.08) + (3000 * 0.17) + (4000 * 0.26) + (money - 8000) * 0.35;

   printf("소득세는 %d만원 입니다. \n", tax);

   return 0;
}
```

