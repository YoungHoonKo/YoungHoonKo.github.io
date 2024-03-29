---
title: 06. C Language(ASCII)
Author: YoungHoon Ko
date: 2022-07-23 19:49:00 +0900
categories: [C, C-Study]
tags: [c]
image: /assets/img/ASCII.png
Image: /assets/img/Extexed ASCII.jpeg
---

[toc]

# A promise to express letters in numbers, ASCII

## Origin of ASCII

- 분리되어 있는 두 장치가 통신을 할 때, a라는 문자를 전송하는 방법은 두 가지가 있다
  1. **스캔(Scan)**
     - 팩스(Fax)처럼 a라는 문자를 그대로 스캔(Scan)하여 전송하는 방법
  2. **변수지정(Specify variables)**
     - 만약에 두 장치가 97을 a라고 미리 약속하고 97이 전송되면 a가 전송되었다고 처리하는 것
- 첫 번째 방법은 이미지의 크기에 따라 전송할 데이터도 달라지고 점(Pixel)들의 최소 수만큼 전송해야 하기 때문에 데이터가 커질 수 밖에 없다.
- 따라서 효율성이라는 면에서 볼 때, `문자를 숫자로 바꿔서 전송`하면 크기도 일정해질 뿐만 아니라 문자 한 개를 보낼 때 1 ~ 2 Byte로도 가능하기 때문에 효율적이다.
- 따라서 컴퓨터는 대부분의 문자를 숫자로 변환해서 전송하는 방법을 사용한다.
- 그러나 이러한 변환 장치를 만든 회사가 여러 곳이여서 서로 약속한 정보가 달라 제대로 전송할 수 없었다.
- 이러한 이유에서 문자를 숫자로 표기하기 위한 표준이 필요했다.
- 이 필요성 때문에 등장한 여러 가지 표준이 있는데 그 중 개인용 컴퓨터(PC)에서 가장 많이 사용하는 **ASCII**이다.

## What is ASCII?

#### **ASCII**

-  **American Standard Code for Information Interchange(미국 정보 교환 표준 코드)**의 약어이다.

- ASCII는 1967에 표준으로 제정되어 1986에 마지막으로 개정되었다.
- ASCII는 초창기에 7 Bit 방식의 인코딩(Encoding)되었기 때문에 출력 불가능한 제어 문자 33개(0 ~ 32번)와 공백을 비롯한 출력 가능한 문자 95개로 이루어져 있다.
- 따라서 ASCII는 **128개(8비트 중 7비트(존 비트 3개, 디지트 비트 4개)**의 코드로 구성된다.

![ASCII](/assets/img/ASCII.png)

#### **Extended ASCII**

- 컴퓨터의 발달로 더 다양한 표현이 필요해짐에 따라 **8 Bit 인코딩(Encoding)**을 사용하도록 **확장**되었다.(기존 128개 -> 256개)

![Extexded ASCII](/assets/img/Extended ASCII.jpeg)

- 위의 표를 보면 알 수 있듯이, 총 256개의 숫자로 문자를 표현하기 때문에 **0 ~ 255**범위를 가지며 이 범위는 **부호를 고려하지 않는 1 Byte 메모리**에 저장할 수 있다.
- 따라서 컴퓨터에 문자가 아스키코드로 작성되었다면 **1 Byte 메모리에 저장하는 것이 가장 효율적**이다.









아스키코드 출처: <https://wondangcom.com/1780>

확장 아스키코드 이미지 출처 : <https://www.keepandshare.com/doc/947949/how-to-enter-ascii-codes-on-windows?ifr=y>