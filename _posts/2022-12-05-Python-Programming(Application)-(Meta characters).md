---
title: 04. Python-Programming(Application)(Meta characters)
Author: YoungHoon Ko
date: 2022-12-05 00:45:00 +0900
categories: [University(2022-Second-Semester), Python-Programming(Application)]
tags: [python, application]
---

[toc]

# 메타 문자 정리

- 텍스트를 잘 다루기 위해서는 우선적으로 메타 문자에 대해 알아야한다.
- 헷갈리는 것이 많겠지만 실습을 통해 반복적으로 사용법을 익혀야함을 느낀다.

|   식   |         기능         |                       설명                       |
| :----: | :------------------: | :----------------------------------------------: |
|   ^    |         시작         | ^Apple => 문장의 첫 단어가 Apple로 시작하는 문장 |
|   $    |          끝          |  pie$ => 문장의 마지막 단어가 pie로 끝나는 문장  |
|   .    |         문자         |           .하나당 한 개의 문자로 취급            |
|   \d   |         숫자         |         [0-9]와 같은 의미, 한 개의 숫자          |
|   \w   |     숫자와 문자      |            한 개의 문자나 숫자로 취급            |
|   \s   |       공백문자       |             스페이스, 탭, 줄바꿈 등              |
|   \S   | 공백문자 제외한 문자 |     공백문자를 제외한 모든 문자가 될 수 있음     |
|   *    |    0회 이상 반복     |          AB* => A, AA, AAB, CAB, ABBBB,          |
|   +    |    1회 이상 반복     |               AB+ => AB, ABB, ABBB               |
|   ?    |  0회 또는 1회 반복   |                   AB? => A, AB                   |
|   \|   |         또는         |         Apple\|apple => Apple 또는 apple         |
| [abc]  |    문자 선택 범위    |            a, b, c 가운데 하나의 문자            |
| [^abc] |    문자 제외 범위    |             a, b, c가 아닌 어떤 문자             |

