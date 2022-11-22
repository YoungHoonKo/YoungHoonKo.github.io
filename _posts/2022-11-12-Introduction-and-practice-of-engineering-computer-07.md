---
title: 07. Introduction and practice of engineering computer
author: YoungHoon Ko
date: 2022-11-12 06:50:32 +0900
categories: [University(2022-First-Semester), Introduction and practice of engineering computer]
tags: [c, computer_engineering]
---

[toc]

# 공학컴퓨터입문및실습 과제7

## 사용자로부터 변수를 입력 받아서 다항식을 계산하는 프로그램

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void)
{
    double x;
    double res;

    printf("X의 값을 입력하시오. :");
    scanf("%lf", &x);

    res = 3*(x*x*x) - 7*(x*x) + 9;

    printf("다항식의 값은 %lf입니다.\n", res);

    return 0;
}
```



## 사용자로 문자를 받아서 아스키 코드를 출력하는 프로그램

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void)
{
    char ch;

    printf("문자를 입력하시오. :");
    scanf("%c", &ch);

    printf("아스키 코드: %d\n", ch);
  	//getchar()함수를 사용하지 않고 문자를 정수형으로 받아서 출력하면 된다.

    return 0;
}
```



## 자동판매기 프로그램

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void)
{
    int money, price, change;

    printf("투입한 돈 :");
    scanf("%d", &money);

    printf("물건 값 :");
    scanf("%d", &price);

    change = money - price;
    printf("거스름돈 :%d\n", change);

    int coin100s = change / 100;  //거스름돈에서 100원 짜리 개수를 계산
    change = change % 100;  //거스름돈에서 100원 짜리를 내주고 남은 돈

    int coin10s = change / 10;  //거스름돈에서 10원 짜리 개수를 계산
    change = change % 10;  //거스름돈에서 10원 짜리를 네주고 남은 돈

    printf("100원 동전의 개수 :%d\n", coin100s);
    printf("10원 동전의 개수 :%d\n", coin10s);

    return 0;
}
```



## a 부터 z까지 출력하는 프로그램을 배열을 사용해서 만듬

```c
#include <stdio.h>
#define SIZE 26

int main(void)
{
    int i;
    char codes[SIZE];

    for (i = 0;i < SIZE;i++)
        codes[i] = 'a' + i;  //'a'에 1을 더하면 'b'가 된다.

    for (i = 0;i < SIZE;i++)
        printf("%c ", codes[i]);
    printf("\n");

    return 0;
}
```



## 학생들의 성적을 입력받아서 평균을 구하는 프로그램입니다.

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#define STUDENT 5  //기호 상수를 지정함

int main(void)
{
    int scores[STUDENT]; //배열을 기호 상수로 정의 함
    int i, average, sum;

    for (i = 0;i < STUDENT;i++) //정수 i를 기호 상수 - 1 까지 1을 더하면서 반복함, 성적 5개을 입력 받음.
    {
        printf("학생들의 성적을 입력해주세요. :");
        scanf("%d", &scores[i]);
    }
    for (i = 0;i < STUDENT;i++)   //입력 받은 5가지의 성적의 합계를 구합니다.
        sum += scores[i];

    average = sum / STUDENT;  //성적의 합계를 기호 상수로 나눠서 평균을 구합니다.
    printf("성적 평균 :%d\n", average);
  	//적절한 형식 지정자를 사용하고 가독성을 높이기 위해 이스케이프 문자(\n)을 사용해서 줄을 바꿈

    return 0;
}
```



## 화씨온도를 섭씨온도로 바꾸는 함수

```c
#include <stdio.h>
#define CRT_SECURE_NO_WARINGS
double FtoC(double temp_f);

int main(void){
    double c, f;
    printf("F값을 입력해주세요. : ");
    scanf("%lf", &f);
    c = FtoC(f);
    printf("화씨온도 %lf은 섭씨온도 %lf입니다. \n", f, c);
    return 0;
}

double FtoC(double temp_f){
    double temp_c;
    temp_c = (5.0 * (temp_f - 32.0)) / 9.0;
    return temp_c;
}
```



## 소수를 찾는 함수

```c
#include <stdio.h>
#define _CRT_SECURE_NO_WARNINGS
int check_prime(int);

int main(void)
{
    int k;
    printf("정수를 입력해주새요. : ");
    scanf("%d", &k);
    if (check_prime(k) == 1 ) printf("소수입니다.\n");
    else printf("소수가 아닙니다. \n");
    return 0;
}

int check_prime(int n)
{
    int is_prime = 1;
    for (int i = 2;i < n; ++i)
    {
        if (n % i == 0)
        {
            is_prime = 0;
            break;
        }
    }
    return is_prime;
}
```



## 팩토리얼을 순환호출을 사용해서 작성했습니다.

```c
#define _CRT_SECURE_NO_WARINGS
#include <stdio.h>

int factorial(int n);

int main(void)
{
    int x = 0, result;
    printf("정수를 입력하세요. :");
    scanf("%d", &x);
    
    result = factorial(x);
    printf("%d!은 %d입니다. \n", x, result);
    
    return 0;
}

int factorial(int n)
{
    printf("factorial(%d)\n", n);
    
    if (n <= 1) return 1;
    else return n * factorial(n - 1);
}
```



## 정수의 합을 소수의 합으로 구하는 함수

```c
#include <stdio.h>
#define _CRT_SECURE_NO_WARNINGS
int check_prime(int k);

int main(void)
{
    int k, flag = 0;
    printf("양의 정수를 입력해주새요. : ");
    scanf("%d", &k);
    
    for (int i = 2;i < k;++i)
    {
        if ( check_prime(i) == 1)
        {
            if (check_prime(k - i) == 1)
            {
                printf("%d = %d + %d\n", k, i, k - i);
                flag = 1;
            }
        }
    }
    if (flag == 0)
    {
        printf("%d은 소수들의 합으로 표현할 수 없습니다.\n", k);
        return 0;
    }
}
int check_prime(int n)
{
    int is_prime = 1;
    for (int i = 2;i < n; ++i)
    {
        if (n % i == 0)
        {
            is_prime == 0;
            break;
        }
    }
    return is_prime;
}
```

