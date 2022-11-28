---
title: 03. HTML-Semantic tags
Author: YoungHoon Ko
date: 2022-07-13 11:00:00 +0900
categories: [HTML, HTML-Study]
tags: [html]
---

# 3. 웹 문서 구조를 만드는 시맨틱 태그

[toc]

## 1. 시맨틱 태그란?

- 시맨틱이란 '의미론적인', '의미가 통하는'이라는 뜻을 가진 영단어
- 즉, 태그의 이름만 봐도 무슨 의미인지 알 수 있음
- EX) `<p>`, `<a>`, `<nav>` 등의 태그가 있음

## 2. 시맨틱 태그는 왜 필요할까?

1. 웹 브라우저가 HTML의 소스 코드만 보고도 어느 부분이 제목이고 메뉴이고 본문인지 알 수 있기 때문
2. 문서 구조가 정확히 나눠지기 때문에 다양한 화면에서 웹 문서를 표현하기 쉽기 때문
3. 웹 사이트를 검색할 때 필요한 내용을 정확히 찾을 수 있음

## 3. 웹 문서 구조를 만드는 주요 시맨틱 태그

#### 1. `<header>` 태그

- 말 그대로 헤더 영역을 의미함
- 웹 사이트의 헤더도 있지만, 특정 영역의 헤더도 있음
- 사이트의 헤더는 주로 맨 위쪽이나 왼쪽에 있음
- **주로 검색 창이나 사이트 메뉴를 삽입함**

#### 2. `<nav>` 태그

- 같은 웹 문서 안에서 다른 위치로 연결하거나 다른 웹 문서로 연결하는 링크를 만듬
- 웹 문서의 위치에 영향을 받지 않으므로 **헤더**나 **푸터**, **사이드 바** 안에 포함할 수도 있고 독립해서 사용할 수도 있음
- 여러개의 `<nav>` 태그를 사용할 때는 **id** 속성을 지정하면 내비게이션마다 **다른 스타일**을 지정할 수 있음

#### 3. `<main>` 태그

- 웹 문서의 중심 주제 또는 주요 기능과 **직접적으로** 관련되어 있거나 확장되는 콘텐츠로 구성
- **하나의 웹 문서에 하나만 사용할 수 있음**
- 문서 전반에 걸쳐 반복되는 내용을 포함해서는 안 됨

#### 4. `<article>` 태그

- 사전적 의미로 '신문', '잡지' 등의 의미를 가지고 있음
- 실제로 웹에서 보여주고 싶은 내용을 넣음
- 블로그나 포스트 처럼 **독립된 컨텐츠**로 사용함
- `<article>` 태그를 여러개 사용할 수도 있고, `<section>` 태그를 넣을 수도 있음

#### 5. `<section>` 태그

- 웹 문서에서 콘텐츠 영역을 나타냄
- **몇개의 콘텐츠를 묶는 용도로 사용함**

#### 6. `<aside>` 태그

- 본문 내용 외에 왼쪽이나 오른쪽, 혹은 아래쪽에 사이드 바를 만듬
- 필수 요소는 아니므로 필요할 경우에만 사용함

#### 7. `<footer>` 태그

- 웹 문서의 맨 아래쪽에 있는 푸터 영역을 만듬
- 사이트 제작 정보, 저작권 정보, 연락처 등을 넣음
- `<header>`, `<section>`, `<article>` 태그들을 모두 사용할 수 있음

#### 8. `<div>` 태그

- `<div>`는 영단어 division의 줄임말임

- `<header>`, `<section>` 태그가 나오기 전에는 `<div>` 태그로 문서 구조를 구분했음

- id나 class 속성을 사용해서 문서 구조를 만들거나 스타일을  적용할 때 사용함

- 즉, 영역을 구별하거나 스타일로 문서를 꾸미는 것임

  ##### 1. id

  - id를 불러올 때는 '#'을 클래스명 앞에 붙여서 사용함

  - **id는 중복으로 사용할 수 없음 즉, 한 개의 아이디 페이지에서 한 번만 사용해야함**

  - 한 요소에 하나의 아이디만 적용 가능

    ~~~ html
    <!-- 하나의 <p> 태그에 하나의 아이디만 사용 가능 -->
    <p id="attendance">고영훈</p>
    
    <!-- 여러개 아이디를 사용할 수 없음, 아이디의 잘못된 사용 -->
    <p id="attendance education">고영훈</p>
    ~~~

    

  ##### 2. class

  - class를 불러올 때는 '.'을 클래스명 앞에 붙여서 사용함

  - **중복 사용이 가능함**

  - **페이지 여러곳에 동일한 클래스명을 사용해도 무방함**

  - 한 요소에 여러개의 클래스명이 지정될 수 있음

    ~~~ html
    <!-- 하나의 <p> 태그에 여러 클래스 사용, 클래스를 추가할 때는 띄어쓰기로 구분 -->
    <p class="school name friend">고영훈</p>
    
    <!-- 한 요소가 여러개의 클래스, 한개의 아이디를 동시에 가지는 것은 가능 -->
    <p class="school name" id="attendance">고영훈</p>
    ~~~

    

  <hr />

  

  

  