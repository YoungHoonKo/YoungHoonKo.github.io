---
title: 01. C-Programming
Author: YoungHoon Ko
date: 2022-11-25 08:50:32 +0900
categories: [University(2022-Second-Semester), C-Programming]
tags: [c, c_programming]
---

[toc]

## C Programming 실습1

### 정사각형의 넓이 구하기

```c
#define _CRT_SECURE_NO_WARINGS
#include <stdio.h>

int main(void){
  int a;
  printf("정사각형의 변의 길이를 입력하세요.\n");
  scanf("%d", &a);
  printf("정사각형의 넓이는 %d입니다.\n", a*a);

  return 0;
}
```



### 삼각형 넓이 구하기

```c
#define _CRT_SECURE_NO_WARINGS
#include <stdio.h>

int main(void){
  double h, m;
  printf("삼각형의 높이를 입력하세요.\n");
  scanf("%lf", &h);
  printf("삼각형의 밑변을 입력하세요.\n");
  scanf("%lf", &m);
  printf("삼각형의 넓이는 %f입니다.\n", m*h/2);

  return 0;
}
```



### 부호반전

```c
#define _CRT_SECURE_NO_WARINGS
#include <stdio.h>

int main(void){
  int a;
  printf("정수를 입력하세요.\n");
  scanf("%d", &a);
  if (a>0)
  {
    printf("부호를 반전하면 %d입니다.\n", -1*a);
  }
  else if (a<0)
  {
    printf("부호를 반전하면 %d입니다.\n",-1*a);
  }

  return 0;
}
```



### 홀수 짝수 판별

```c
#define _CRT_SECURE_NO_WARINGS
#include <stdio.h>

int main(void){
  int a;
  printf("정수를 입력하세요.\n");
  scanf("%d", &a);
  if (a % 2 == 0)
  {
    printf("%d은(는) 짝수입니다.\n", a);
  }
  else if (a % 2 != 0)
  {
    printf("%d은(는) 홀수입니다.\n", a);
  }

  return 0;
}
```



### 여러가지 조건을 한 번에 걸기

```c
#define _CRT_SECURE_NO_WARINGS
#include <stdio.h>

int main(void){
  char a;
  printf("A~C까지의 문자를 입력하세요.\n");
  scanf("%c", &a);
  if (a == 'A' || a == 'B' || a == 'C')
  {
    printf("정답입니다.\n");
  }
  else
  {
    printf("틀렸습니다.\n");
  }

  return 0;
}
```



### switch문 

```c
#define _CRT_SECURE_NO_WARINGS
#include <stdio.h>

int main(void){
  int a;
  printf("성적을 입력하세요.\n");
  scanf("%d", &a);

  printf("성적은 %d입니다.\n", a);

  switch (a)
  {
    case 50:
      printf("노력이 필요합니다.\n");
      break;
    case 60:
      printf("조금 더 노력하세요.\n");
      break;
    case 70:
      printf("잘 했습니다.\n");
      break;
    case 80:
      printf("메우 잘 했습니다.\n");
      break;
    case 90:
      printf("메우 우수합니다.\n");
      break;
    default:
      printf("공부 좀 해라\n");
      break;
  }
  return 0;
}
```

