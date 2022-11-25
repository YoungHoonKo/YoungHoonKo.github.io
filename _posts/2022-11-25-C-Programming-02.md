---
title: 02. C Programming
Author: YoungHoon Ko
date: 2022-11-25 09:55:32 +0900
categories: [University(2022-Second-Semester), C Programming]
tags: [c, c_programming]
---

[toc]

## C Programming 실습2

### 반목문

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void){
   for (int i = 1; i <= 5; i++)
   {
     printf("반복하고 있습니다.\n");
   }

  printf("반복을 종료했습니다.\n");
  
  return 0;
}
```



### 정수를 입력하고 개수 만큼 별 출력하기

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void){
   for (int i = 1; i <= 5; i++)
   {
     printf("반복하고 있습니다.\n");
   }

  printf("반복을 종료했습니다.\n");
  
  return 0;
}
```



### 대각선 별 출력

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void){
  int num;

  printf("몇 개의 *을 출력할까요?\n");
  scanf("%d", &num);

  for (int i = 1; i <= num; i++)
  {
    for (int j = 1; j <= num; j++)
    {
      if (j == i)
      {
        printf("*");
      }
      else
      {
        printf(" ");
      }
    }
    printf("\n");
  }
  return 0;
}
```



### 입력한 숫자까지 합 구하기

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void){
  int num, sum = 0;

  printf("몇 까지의 합계를 계산할까요?\n");
  scanf("%d", &num);

  for (int i = 1; i <= num; i++)
  {
    sum += i;
  }
  printf("1부터 %d까지의 합은 %d입니다.\n", num, sum);
  
  return 0;
}
```



### 입력한 숫자자리 건너뛰기

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int main(void){
  int res;

  printf("몇 번째 자리를 건너뛸가요? (1-10)\n");
  scanf("%d", &res);

  for (int i = 1; i <= 10; i++)
  {
    if (i == res)
    {
      continue;
    }
    printf("%d번째 자리입니다.\n", i);
  }

  return 0;
}
```

