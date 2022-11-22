---
title: 06. Introduction and practice of engineering computer
author: YoungHoon Ko
date: 2022-11-11 02:45:00 +0900
categories: [University(2022-First-Semester), Introduction and practice of engineering computer]
tags: [c, computer_engineering]
---

[toc]

# 공학컴퓨터입문및실습 과제6

## 가위바위보 게임(여러번 실행)

```c
#define _CRT_SECURE_NO_WARNINGS
#include <time.h>
#include <stdio.h>
#include <stdlib.h>

int main(void)
{
    int user = 0;
    int win = 0;
    int lose = 0;

    while (1)
    {
        srand((unsigned int)time(NULL));
        int computer = rand() % 3;

        printf("\n가위 바위 보 게임을 시작합니다.\n");
        printf("\n가위, 바위, 보 중에서 하나를 선택하세요(가위-0, 바위-1, 보-2) : ");
        scanf("%d", &user);
        if (user <= 3)
        {
            if ((user + 1) % 3 == computer)
            {
                printf("졌습니다.\n");
                printf("사용자 : %d\n컴퓨터 : %d\n", user, computer);
                lose += 1;
                printf("승 : %d 패 : %d\n", win, lose);
            }

            else if (user == computer)
            {
                printf("비겼습니다.\n");
                printf("사용자 : %d\n컴퓨터 : %d\n", user, computer);
                printf("승 : %d 패 : %d\n", win, lose);
            }

            else
            {
                printf("이겼습니다.\n");
                printf("사용자 : %d \n컴퓨터 : %d\n", user, computer);
                win += 1;
                printf("승 : %d 패 : %d\n", win, lose);
            }
        }

        else if (user > 3)
        {
            printf("~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~\n");
            printf("잘못된 수를 입력했습니다.\n");
            printf("~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~\n");
        }
    }

    return 0;
}

```



## 숫자를 입력받아서 구구단 출력

```c
#include <stdio.h>

int main(void)
{
    int a;
    int b;

    printf("구구단을 출력합니다. : ");
    scanf("%d", &b);

    for (a = 1;a < 10;a++)
        printf("%d X %d = %d\n", b, a, b * a);

    return 0;
}
```



## 상품의 가격과 수량을 입력 받아서 총가격을 출력하자

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void)
{
    int a;
    int b;
    int res;

    printf("상품 가격을 입력하시오. :");
    scanf("%d", &a);

    printf("상품의 개수를 입력하시오. :");
    scanf("%d", &b);

    res = a * b;

    printf("총 가격은 %d입니다.\n", res);

    return 0;
}
```



## 내년 나이를 맞추는 프로그램

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void)
{
    int a;
    int b;

    printf("나이를 입력하시오. : ");
    scanf("%d", &a);
    b = a + 1;

    printf("내년 나이는 %d살이 되시는군요.\n", b);

    return 0;
}
```



## 세 수를 입력 받아서 평균을 구하는 프로그램

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void)
{
    int a;
    int b;
    int c;
    float res;  //평균의 값은 실수형으로 받습니다.

    printf("정수를 입력하시오. :");
    scanf("%d", &a);

    printf("정수를 입력하시오. :");
    scanf("%d", &b);

    printf("정수를 입력하시오. :");
    scanf("%d", &c);

    res = (a + b + c) / 3;

    printf("평균은 %f입니다.\n", res);
	  //실수형으로 받기 위해 알맞은 형식 지정자를 사용한다.

    return 0;
}
```



## 삼각형의 두 각을 입력하면 나머지 한 각을 찾는 프로그램

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void)
{
    float a;
    float b;
    int res;

    printf("첫 번째 각을 입력하세요. :");
    scanf("%f", &a);

    printf("두 번째 각을 입력하세요. :");
    scanf("%f", &b);

    res = 180 - (a + b);

    printf("나머지 한 각의 크기는 %d입니다.\n", res);

    return 0;
}
```



## 10진수를 16진수, 8진수로 바꾸는 프로그램

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void)
{
    int a;

    printf("변환할 10진수를 입력해주세요. :");
    scanf("%d", &a);

    printf("%d %#x %#o\n", a, a, a);

    return 0;
}
```



## 변수의 값을 교환하는 프로그램

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void)
{
    int a;
    int b;
    int tmp;

    printf("a값을 입력해주세요. :");
    scanf("%d", &a);

    printf("b값을 입력해주세요. :");
    scanf("%d", &b);

    printf("%d %d\n", a ,b); //a, b를 순차적으로 출력함

    tmp = a;
    a = b;
    b = tmp;

    printf("%d %d\n",a, b);  //a, b의 순서를 바꿔서 출력함

    return 0;
}
```



## 부동소수점은 부정확할 수 있다?(yes)

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void)
{
    float value = 0.1;

    printf("%.20f", value);
    return 0;
}
```



## 구의 표면적과 부피를 구하는 프로그램

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#define PI 3.141592

int main(void)
{
    int radius;
    double b;
    double c;

    printf("반지름을 입력하시오. :");
    scanf("%d", &radius);

    b = 4.0 * PI * (radius * radius);
    c = 4.0/3.0 * PI * (radius * radius * radius);

    printf("구의 표면적 = %lf\n", b);
    printf("구의 부피 = %lf\n", c);

    return 0;
}
```

