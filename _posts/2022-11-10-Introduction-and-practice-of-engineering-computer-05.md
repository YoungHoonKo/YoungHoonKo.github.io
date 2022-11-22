---
title: 05. Introduction and practice of engineering computer
author: YoungHoon Ko
date: 2022-11-10 12:45:00 +0900
categories: [University(2022-First-Semester), Introduction and practice of engineering computer]
tags: [c, introduction_and_practice_of_engineering computer]
---

[toc]

# 공학컴퓨터입문및실습 과제5

## 문제1

```markdown
수입이 있을 때마다 저축을 하는 사람이 있다.
저축을 하는 함수 int save()를 만들고, 저축하고자 하는 수입이 다음과 같을 때,
차례로 저축을 하고, 이때의 저축된 금액을 출력하는 프로그램을 작성하라.

//int save(int 저축된금액, int 저축액) { ....; };
//int 저축액[] = { 300, 1100, 450, 600, 75, 120, 850, 25, 250, 100 };
```

```c
#include <stdio.h>

int bankbook;

int save(int money){
   bankbook += money;
   printf("저축된 금액은%d입니다.\n", bankbook);
   return bankbook;
}

int main() {
   int al_save;
   int fu_save[] = { 300, 1100, 450, 600, 75, 120, 850, 25, 250, 100 };
   for (int a = 0; a <= 9; a++) {
      printf("저축하고자 하는 금액은%d\n", fu_save[a]);
      al_save = save(fu_save[a]);
   }
   return 0;
}
```



## 문제2

```markdown
다음 데이터에서, 가장 큰 값과, 그 값의 위치[index]를 구하는 프로그램을 작성하라.
int data[ ] =  {30, 11, 45, 60, 75, 12, 85, 25, 20, 10}; 
```

```c
#include <stdio.h>
int main(void) {
    int range[10] = { 30,11,45,60,75,12,85,25,20,10 };
    int a;
    int length = 0;
    length = sizeof(range) / sizeof(range[0]);

    int max = range[0];

    for (int i = 0; i < length; i++) {
        if (max < range[i]) {
            max = range[i];
            a = i;
        }
    }
    printf("최대값은 %d입니다.\n", max);
    printf("위치는 %d번째입니다\n", a);

    return 0;
}
```

