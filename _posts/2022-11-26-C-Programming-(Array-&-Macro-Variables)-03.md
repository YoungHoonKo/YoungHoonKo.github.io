---
title: 03. C-Programming(Array & Macro Variables)
Author: YoungHoon Ko
date: 2022-11-26 10:34:32 +0900
categories: [University(2022-Second-Semester), C-Programming]
tags: [c, c_programming]
---

[toc]

## C Programming 실습3

### 배열기초

```c
#include <stdio.h>

int main(void)
{
  int test[5];

  test[0] = 80;
  test[1] = 60;
  test[2] = 22;
  test[3] = 50;
  test[4] = 75;

  for (int i = 0; i < 5; i++)
  {
    printf("%d번째 사람의 점수는 %d입니다.\n", i+1, test[i]);
  }

  return 0;
}
```



### 배열과 for

```c
#include <stdio.h>

int main(void)
{
  int test[5];

  printf("5명의 점수를 입력하세요.\n");
  for (int i = 0; i < 5; i++)
  {
    scanf_s("%d", &test[i]);
  }
  for (int j = 0; j < 5; j++)
  {
    printf("%d번째 사람의 점수는 %d점입니다.\n", j+1, test[j]);
  }

  return 0;
}
```



### 배열 Indexing

```c
#include <stdio.h>

int main(void)
{
  int test[5] = {80, 60, 22, 50, 75};

  for (int i = 0; i < 5; i++)
  {
    printf("%d번째 사람의 점수는 %d점입니다.\n", i+1, test[i]);
  }


  return 0;
}
```



### 매크로 변수1

```c
#include <stdio.h>
#define NUM 5 //매크로 변수, 자주 사용하는 변수에 값을 지정

int main(void)
{
  int test[NUM] = {80, 60, 22, 50, 75};

  for (int i = 0; i < NUM; i++)
  {
    printf("%d번째 사람의 점수는 %d입니다.\n", i + 1, test[i]);
  }

  return 0;
}
```



### 매크로 변수2

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#define NUM 5

int main(void)
{
  int test[NUM];
  int tmp;

  printf("%d명의 점수를 입력하세요.\n", NUM);

  for (int i = 0; i < NUM; i++)
  {
    scanf("%d", &test[i]);
  }

  for (int s = 0; s < NUM-1; s++)
  {
    for (int t = s + 1; t < NUM; t++)
    {
      if (test[t] > test[s])
      {
        tmp = test[t];
        test[t] = test[s];
        test[s] = tmp;
      }

    }

  }
  for (int j = 0; j < NUM; j++)
  {
    printf("%d등의 점수는 %d입니다.\n", j+1, test[j]);
  }

  return 0;
}
```



### 매크로 변수3

```c
#include <stdio.h>
#define _CRT_SECURE_NO_WARNINGS
#define NUM 5
#define SUB 2

int main(void)
{
  int test[SUB][NUM];

  test[0][0] = 80; //국어
  test[0][1] = 60; //산수
  test[0][2] = 22; //사회
  test[0][3] = 50; //과학
  test[0][4] = 75; //영어
  test[1][0] = 90;
  test[1][1] = 55;
  test[1][2] = 68;
  test[1][3] = 72;
  test[1][4] = 58;

  for (int i = 0; i < NUM; i++)
  {
    printf("%d번째 사람의 국어 점수는 %d입니다.\n", i+1, test[0][i]);
    printf("%d번째 사람의 산수 점수는 %d입니다.\n", i+1, test[1][i]);

  }

  return 0;
}
```

