---
title: 08. C-Programming(Convert the pointer of a common code)
Author: YoungHoon Ko
date: 2022-11-27 01:34:32 +0900
categories: [University(2022-Second-Semester), C-Programming]
tags: [c, c_programming]
---

[toc]

## C Programming 실습8

### 1번 문제

```markdown
문자열의 길이를 검사하는 함수 int length(char str[])을 작성하시오.
```

```c
#define _CRT_SECURE_NO_WARINGS
#include <stdio.h>

int length(char str[]);

int main(void)
{
  char str[100];
  int ans;

  printf("문자열을 입력하세요.\n");
  scanf("%s", str);

  ans = length(str);

  printf("문자열의 길이는 %d입니다.\n", ans);

  return 0;
}

int length(char str[])
{
  int c = 0; // 변수 초기화 해줘야함

  for (int i = 0; str[i] != '\0';i++) // \0은 문자열의 끝을 의미함
  {
    c++;
  }
  return c;
}
```



### 2번 문제

```markdown
문자열 안에 포함되어 있는 'a'의 개수를 검사하는 함수 int search(char str[])을 작성하시오.
```

```c
#define _CRT_SECURE_NO_WARINGS
#include <stdio.h>

int search(char str[]);

int main(void)
{
  char str[100];
  int ans;

  printf("문자열을 입력하세요.\n");
  scanf("%s", str);

  ans = search(str);

  printf("%s 안에 a는 %d개가 있습니다.\n", str, ans);

  return 0;
}

int search(char str[])
{
  int c = 0;

  for (int i = 0; str[i] != '\0'; i++) {
    if (str[i] == 'a')
    {
      c++;
    }
    else
      continue;
  }
  return c;
}
```



### 3번 문제

```markdown
문자열을 비교하는 함수 int compare(char str1[], char str2[])을 작성하시오.<br>
문자열 str1과 str2를 비교해서 일치하면 1, 그렇지 않으면 -1을 반환한다.
```

```c
#define _CRT_SECURE_NO_WARINGS
#include <stdio.h>

int compare(char str1[], char str2[]);

int main(void)
{
  char str1[100];
  char str2[100];
  int ans;

  printf("1번째 문자열을 입려하세요.\n");
  scanf("%s", str1);

  printf("2번째 문자열을 입려하세요.\n");
  scanf("%s", str2);

  ans = compare(str1, str2);

  if (ans == 1)
  {
    printf("2개의 문자열은 같습니다.\n");
  }
  else if (ans == -1)
  {
    printf("2개의 문자열을 다릅니다.\n");
  }

  return 0;
}

int compare(char str1[], char str2[])
{
  for (int i = 0; str1[i] == str2[i]; i++)
  {
    if (str1[i] == '\0')
    {
      return 1;
    }
  }
  return -1;
}
```



### 4번 문제

```markdown
1 ~ 3번 문제 포인터 연산으로 바꿔라
```

#### 1번 포인터 변환

```c
#define _CRT_SECURE_NO_WARINGS
#include <stdio.h>

int length(char *str);

int main(void)
{
  char str[100];
  int ans;

  printf("문자열을 입력하세요.\n");
  scanf("%s", str);

  ans = length(str);

  printf("문자열의 길이는 %d입니다.\n", ans);

  return 0;
}

int length(char *str)
{
  int c = 0; // 변수 초기화 해줘야함

  while (*str){
    c++;
    str++;
  }
  return c;
}
```



#### 2번 포인터 변환

```c
#define _CRT_SECURE_NO_WARINGS
#include <stdio.h>

int search(char *str);

int main(void)
{
  char str[100];
  int ans;

  printf("문자열을 입력하세요.\n");
  scanf("%s", str);

  ans = search(str);

  printf("%s 안에 a는 %d개가 있습니다.\n", str, ans);

  return 0;
}

int search(char *str)
{
  int c = 0;

  while (*str) {
    if (*str == 'a')
    {
      c++;
    }
    str++;
  }
  return c;
}
```



#### 3번 포인터 변환

```c
#define _CRT_SECURE_NO_WARINGS
#include <stdio.h>

int compare(char *str1, char *str2);

int main(void)
{
  char str1[100];
  char str2[100];
  int ans;

  printf("1번째 문자열을 입려하세요.\n");
  scanf("%s", str1);

  printf("2번째 문자열을 입려하세요.\n");
  scanf("%s", str2);

  ans = compare(str1, str2);

  if (ans == 1)
  {
    printf("2개의 문자열은 같습니다.\n");
  }
  else if (ans == -1)
  {
    printf("2개의 문자열을 다릅니다.\n");
  }

  return 0;
}

int compare(char *str1, char *str2)
{
  while (*str1 == *str2) {
    if (*str1 == '\0')
    {
      return 1;
    }
    str1++;
    str2++;
  }
  return -1;
}
```



### 5번 문제

```markdown
표준 라이브러리 <ctype>의 영문자를 대문자로 변환하는 toupper() 함수,<br>
소문자로 변환하는 tolower() 함수를 검사해서 변환하는 코드를 작성하시오.
```

```c
#define _CRT_SECURE_NO_WARINGS
#include <stdio.h>
#include <ctype.h>

int main(void)
{
  char str[100];
  int ans;

  printf("문자열을 입력하세요.\n");
  scanf("%s", str);

  for (int i = 0; str[i] != '\0'; i++)
  {
    str[i] = toupper(str[i]);
  }
  printf("대문자로 변환하면 %s입니다.\n", str);

  for (int j = 0; str[j] != '\0'; j++)
  {
    str[j] = tolower(str[j]);
  }
  printf("소문자로 변환하면 %s입니다.\n", str);

  return 0;
}
```

