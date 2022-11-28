---
title: 09. C-Programming(Structure)
Author: YoungHoon Ko
date: 2022-11-28 20:24:32 +0900
categories: [University(2022-Second-Semester), C-Programming]
tags: [c, c_programming]
---

[toc]

## C Programming 실습9

### 구조체 기본

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

struct Car{
  int num;
  double gas;
};
int main(void)
{
  struct Car car1;

  car1.num = 10;
  car1.gas = 20;

  printf("자동차 번호는 %d : 연료량은 %lf입니다.\n", car1.num, car1.gas);

  return 0;
}
```



### 함수와 구조체

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

typedef struct Car{
  int num;
  double gas;
};

// 매개변수에 구조체를 넘겨줄 수 있음
void show(struct Car c);

int main(void)
{
  struct Car car1 = {0, 0.0};

  printf("번호를 입력하세요.\n");
  scanf("%d", &car1.num);

  printf("연료량을 입력하세요.\n");
  scanf("%lf", &car1.gas);

  show(car1);

  return 0;
}

void show(struct Car c)
{
  printf("자동차 번호는 %d : 연료량은 %lf입니다.\n", c.num, c.gas);
}
```



### 포인터와 구조체

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

typedef struct Car{
  int num;
  double gas;
};

void show(struct Car *pC);

int main(void)
{
  struct Car car1 = {10, 20.5};

  car1.num = 30;
  car1.gas = 40.1;

  show(&car1);

  return 0;
}

// 포인터를 사용할 때 ->를 사용한다.
void show(struct Car *pC)
{
  // 중요
  printf("자동차 번호는 %d : 연료량은 %lf입니다.\n", pC->num, pC->gas);
}
```



### 배열과 구조체

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

// 배열과 구조체 같이 사용
typedef struct Car{
  int num;
  double gas;
};

int main(void)
{
  struct Car cars[3];

  // 중요
  cars[0].num = 1234; cars[0].gas = 25.5;
  cars[1].num = 4567; cars[1].gas = 52.2;
  cars[2].num = 7890; cars[2].gas = 20.5;


  for (int i = 0; i < 3; i++) {
    printf("자동차 번호는 %d : 연료량은 %lf입니다.\n", cars[i].num, cars[i].gas);
  }

  return 0;
}
```



### 구조체의 포인터

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

typedef struct Car{
  int num;
  double gas;
  struct Car *next;  // 구조체의 주소
};

int main(void)
{
  struct Car car0;
  struct Car car1;
  struct Car car2;
  struct Car *pcar;

  car0.num = 1234; car0.gas = 25.5;
  car1.num = 4567; car1.gas = 52.2;
  car2.num = 7890; car2.gas = 20.5;

  car0.next = &car1;
  car1.next = &car2;
  car2.next = NULL;


  for (pcar = &car0; pcar != NULL; pcar = pcar -> next) {
    printf("자동차 번호는 %d : 연료량은 %lf입니다.\n", pcar -> num, pcar ->  gas);
  }

  return 0;
}
```

