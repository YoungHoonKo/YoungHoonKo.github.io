---
title: 01. HTML-Introduction
Author: YoungHoon Ko
date: 2022-07-11 16:33:00 +0900
categories: [HTML, HTML-Study]
tags: [html]
image: /assets/img/screenshot/개발자 툴.png
---

# 1. HTML 시작하기

[toc]

## HTML이란?

- 다양한 인터넷 정보를 웹 브라우저에 보여줄 때 사용하는 언어(웹 문서를 만드는 언어)
- HTML = ***HyperText Markup Language***의 줄임말
  - **HyperText**는 문서를 서로 연결해주는 링크를 의미함
  - __Markup__은 '표시한다'라는 뜻
- 즉, 웹 브라우저에 내용을 보여 주는 텍스트, 이미지 영상 등의 위치를 표시하는 것을 의미함

## HTML과 일반 문서의 차이점

### 일반 문서

- 엑셀, 워드 파일 등의 문서는 입력 프로그램과 내용 확인 프로그램이 같음
- EX) 워드 파일로 표를 만들고 워드가 제공하는 프로그램을 활용해 표를 입력함.그리고 나중에 이 파일을 워드 프로그램에서 불러와서 사용할 수 있음

### HTML

- 입력 프로그램과 내용 확인 프로그램이 다름
- 웹 편집기(vscode)에서 마크업 형식으로 표를 작성해야 함
- 그리고 웹 브라우저가 마크업 형식의 표를 읽고 화면에 나타냄
- 이때 웹 브라우저가 어느 부분이 제목, 텍스트, 표인지 구분하기 위해서 **태그**를 사용함

~~~html
<h1>title</h1>
<p>text</p>
<table>
    <tr>
        <td>셀1</td>
        <td>셀2</td>
    </tr>
    <tr>
        <td>셀3</td>
        <td>셀4</td>
    </tr>
</table>
~~~

![이미지](/assets/img/screenshot/개발자 툴.png)

- 위의 코드처럼 **태그**를 사용해 웹 브라우저(크롬, 사파리)가 뭐가 뭔지 알 수 있게 함
