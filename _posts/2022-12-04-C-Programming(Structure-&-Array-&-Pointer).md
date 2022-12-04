---
title: 10. C-Programming(Structure & Array & Pointer)
Author: YoungHoon Ko
date: 2022-12-04 12:24:32 +0900
categories: [University(2022-Second-Semester), C-Programming]
tags: [c, c_programming]
image: /assets/img/structure.png
image: /assets/img/structure array.png
image: /assets/img/structure pointer.png
---

[toc]

## 구조체 과제

### 구조체를 이용해 사람의 나이, 몸무게, 키를 입력받은 뒤 출력하시오.

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

struct Person{
  int age1;
  int age2;
  double weight1;
  double weight2;
  double height1;
  double height2;
};

int main(void)
{
  struct Person P;

  printf("나이를 입력하세요.\n");
  scanf("%d", &P.age1);

  printf("몸무게를 입력하세요.\n");
  scanf("%lf", &P.weight1);

  printf("키를 입력하세요.\n");
  scanf("%lf", &P.height1);

  printf("나이를 입력하세요.\n");
  scanf("%d", &P.age2);

  printf("몸무게를 입력하세요.\n");
  scanf("%lf", &P.weight2);

  printf("키를 입력하세요.\n");
  scanf("%lf", &P.height2);

  printf("나이 %d 몸무게 %lf 키 %lf입니다.\n", P.age1, P.weight1, P.height1);
  printf("나이 %d 몸무게 %lf 키 %lf입니다.\n", P.age2, P.weight2, P.height2);

  return 0;
}
```



<img src="/assets/img/structure.png" alt="이미지" style="zoom:50%;" />



### 구조체 배열을 사용해 1번과 같은 결과를 출력하시오

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

typedef struct Person{
  int age;
  double weight;
  double height;
}Person;

int main(void)
{
  Person prs[2];

  for (int i = 0; i < 2; i++) {
    printf("나이를 입력하세요.\n");
    scanf("%d", &prs[i].age);

    printf("몸무게를 입력하세요.\n");
    scanf("%lf", &prs[i].weight);

    printf("키를 입력하세요.\n");
    scanf("%lf", &prs[i].height);
  }

  for (int j = 0; j < 2; j++) {
    printf("나이 %d 몸무게 %lf 키 %lf입니다.\n", prs[j].age, prs[j].weight, prs[j].height);
  }

  return 0;
}
```



<img src="/assets/img/structure array.png" alt="이미지" style="zoom:50%;" />



### 구조체 포인터를 사용해 void aging(Person *p)를 정의하고 나이를 1살 증가시켜 출력하시오.

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

typedef struct Person{
  int age;
  double weight;
  double height;
}Person;

void aging(Person *p);

int main(void)
{
  Person prs;

  printf("나이를 입력하세요.\n");
  scanf("%d", &prs.age);

  printf("몸무게를 입력하세요.\n");
  scanf("%lf", &prs.weight);

  printf("키를 입력하세요.\n");
  scanf("%lf", &prs.height);

  printf("나이 %d 몸무게 %lf 키 %lf입니다.\n", prs.age, prs.weight, prs.height);

  aging(&prs);

  printf("1년이 경과했습니다.\n");

  printf("나이 %d 몸무게 %lf 키 %lf입니다.\n", prs.age, prs.weight, prs.height);

  return 0;
}

void aging(Person *p)
{
  p->age++;
}
```



<img src="/assets/img/structure pointer.png" alt="이미지" style="zoom:50%;" />