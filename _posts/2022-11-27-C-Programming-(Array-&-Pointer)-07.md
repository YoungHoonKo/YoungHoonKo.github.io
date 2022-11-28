---
title: 07. C-Programming(Array & Pointer)
Author: YoungHoon Ko
date: 2022-11-27 15:34:32 +0900
categories: [University(2022-Second-Semester), C-Programming]
tags: [c, c_programming]
---

[toc]

## C Programming 실습7

### 배열과 포인터

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <stdlib.h>

int main(void)
{
  int test[5] = {80, 60, 55, 22, 75};

  printf("test[0]의 값은 %d입니다.\n", test[0]);
  printf("test[0]의 어드레스는 %p입니다.\n", &test[0]);
  printf("test[1]의 값은 %d입니다.\n", test[1]);
  printf("test[1]의 어드레스는 %p입니다.\n", &test[1]);

  return 0;
}
```



### 배열과 함수(평균을 구하는 함수)

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <stdlib.h>

double avg(int t[]);

int main(void)
{
  int test[5];
  int i;
  double ans;

  printf("5명의 시험 점수를 입력하세요.\n");

  for (int i = 0; i <= 4; i++) {
    scanf("%d", &test[i]);
  }

  ans = avg(test);

  printf("평균점수는 %lf입니다.\n", ans);

  return 0;
}


double avg(int t[])
{
  double sum = 0;

  for (int i = 0; i <= 4; i++) {
    sum += t[i];
  }

  return sum/5;
}
```



### 포인터와 함수(평균을 구하는 함수)

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <stdlib.h>

double avg(int *pT);

int main(void)
{
  int test[5];
  int i;
  double ans;

  printf("5명의 시험 점수를 입력하세요.\n");

  for (int i = 0; i <= 4; i++) {
    scanf("%d", &test[i]);
  }

  ans = avg(test);

  printf("평균점수는 %lf입니다.\n", ans);

  return 0;
}

double avg(int *pT)
{
  double sum = 0.0;

  for (int i = 0; i <= 4; i++) {
    sum += *(pT + 1);
  }

  return sum/5;
}
```



### 매모리 할당(malloc)

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <stdlib.h>

int main(void)
{
  char *str;
  int num;
  printf("몇개의 a를 준비할까요?\n");
  scanf("%d", &num);

  str = (char *) malloc (sizeof(char) * (num + 1));
  if (!str){
    printf("메모리를 확보할 수 없습니다.\n");
    return 0;
  }
  for (int i = 0; i < num; i++) {
    *(str+i) = 'a';
  }
  *(str+num) = '\0';

  printf("%s를 준비했습니다.\n", str);

  free(str);

  return 0;
}
```



