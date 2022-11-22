---
title: 04. Introduction and practice of engineering computer
author: YoungHoon Ko
date: 2022-11-09 13:30:00 +0900
categories: [University(2022-First-Semester), Introduction and practice of engineering computer]
tags: [c, computer engineering]
---

[toc]

# 공학컴퓨터입문및실습 과제4

## 배열 실습1

```c
#include <stdio.h>
#define SIZE 5

int main(void)
{
    int i;
    int score[SIZE]; //배열 지정
    
    score[0] = 10;
    score[1] = 20;
    score[2] = 30;
    score[3] = 40;
    score[4] = 50;
    //배열의 각 요소에 값을 대입한다.
    for (i = 0; i < SIZE; i++) //i를 0~SIZE-1까지 반복한다.
    {
        printf("scores[%d]=%d\n", i, score[i]);
    }
    return 0;
}
```



## 배열 실습2

```c
#include <stdio.h>
#define SIZE 10

int main(void)
{
    int price[SIZE] = { 12, 3, 19, 6, 18, 8, 12, 4, 1, 19};
    //배열에 미리 값을 지정했습니다.
    int i, minimum;
    
    printf("[");
    for (i = 0;i < SIZE;i++) //i는 0~ SIZE - 1까지 반복을 합니다.
    {
        printf("%d ", price[i]); //price[i]를 정수형을 받습니다.
    }
    printf("]\n");
    
    minimum = price[0];  //최소값을 배열 price의 0번째 요소로 지정합니다.
    
    for (i = 1;i < SIZE;i++) 
    {
        if (price[i] < minimum)
            minimum = price[i];
      			//만약에 배열 안의 요소가 지정해 놓은 최소값 보다 작으면 최소값이 바뀝니다.
    }
    printf("최소값은 %d입니다.", minimum);  //바뀐 최소값을 출력합니다.
    
    return 0;
}
```



## 베열 실습3

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#define SIZE 5

int main(void)
{
    int i, k;
    int list[SIZE] = {16, 7, 9, 1, 3};
    
    for (k = 0;k < SIZE;k++)
    {
        for (i = 0;i < SIZE-1;i++)
        {
            if (list[i] > list[i + 1])
            {
                int tmp = list[i];
                list[i] = list[i + 1];
                list[i + 1] = tmp;
            }
        }
    }
    for (i = 0;i < SIZE;i++)
    {
        printf("%d ", list[i]);
    }
    return 0;
}
```



## 2차원 배열 실습

```c
#include<stdio.h>
#define Xcor 3
#define Ycor 3
int main() {
   int a, b;
   int A[Xcor][Ycor];
   int B[Xcor][Ycor];
   int C[Xcor][Ycor];
   for (a = 0; a < 3; a++) {
      for (b = 0; b < 3; b++) {
         scanf("%d", &A[a][b]);

      }
   }
   for (a = 0; a < 3; a++) {
      for (int b = 0; b < 3; b++) {
         scanf("%d", &B[a][b]);

      }
   }
   for (a = 0; a < 3; a++) {
      for (int b = 0; b < 3; b++) {
         C[a][b] = A[a][0] * B[0][a] + A[a][1] * B[1][a] + A[a][2] * B[2][a];

      }
   }
    
   for (a = 0; a < 3; a++) {
      printf("\n");
      for (int b = 0; b < 3; b++) {
         printf("%d",C[a][b]);
         printf(",");
      }
   }
    return 0;
}
```



## 난수를 생성 후 10으로 나눈 나머지가 가장 많이 생성된 수를 찾기

```c
#include<stdio.h>
#include <stdlib.h>
int main(void) {
    int num[10] = {0, };
    int temp;
    for (int i = 0; i < 100; i++) {
        temp = rand() % 10;
        num[temp]+=1;
    }
    int max = 0;
    for (int i = 0; i < 9; i++) {
        if (num[i] > max) {
            max = num[i];
            temp = i;
        }
    }
    printf("가장 많이 생성된 수 = %d\n", temp);
    
    return 0;
}
```



## 포인터 실습

```c
#include <stdio.h>

int main(void){
    int number = 10;
    int *p;
    
    p = &number;
    printf("변수 number의 값 = %d\n", number);
    
    *p = 20;
    printf("변수 number의 값 = %d\n", number);
    
    return 0;
}
```



## swap함수 실습

```c
#include <stdio.h>
void swap(int *px, int *py);

int main(void){
    
    int a = 100, b = 200;
    
    printf("swap() 호출전 a=%d b=%d\n", a, b);
    swap(&a, &b);
    printf("swap() 호출전 a=%d b=%d\n", a, b);
    
    return 0;
}

void swap(int *px, int *py)
{
    int tmp;
    
    tmp = *px;
    *px = *py;
    *py = tmp;
}
```

