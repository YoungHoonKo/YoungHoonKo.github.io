---
title: 02. HTML-Basic structure
Author: YoungHoon Ko
date: 2022-07-12 12:45:00 +0900
categories: [HTML, HTML-Study]
tags: [html]
---

# HTML 구조 파악하기

[toc]

## HTML 기본 구조 살펴보기

~~~html
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <title>HTML 기본 구조 살펴보기</title>
</head>
<body>
  <h1>프런트엔드 웹 개발</h1>
  <hr>
  <p>HTML</p>
  <p>CSS</p>
  <p>JavaScript</p>
</body>
</html>
~~~

- 일반 문서와는 다르게 정해진 형식에 맞춰서 내용을 입력해야함

- 위의 코트는 짧지만 HTML에서 **반드시** 필요한 모든 구조가 담겨있음

  - 보통 웹 문서는 `<!DOCTYPE html>`로 시작해서 `<html` `<head>` `<body>`라는 3가지 영역으로 구분됨
    - `<!DOCTYPE html>` : 웹이 HTML5 언어로 작성 됐음을 알려줌
    - `<html>`  : 웹 문서의 시작과 끝을 나타내는 태그임
    - `<head>`  : 웹 브라우저가 웹 문서를 해석하는데 필요한 정보를 입력하는 부분임
    - `<body>` : 실제로 화면에 나타나는 내용으로, HTML 태그의 대부분은 `<head>` 태그 안에 들어있음
  - `<html>` 
    - `<html lang="ko"` : `<html>` 태그에서는 문서에서 사용할 언어를 지정할 수 있음
      - 언어는 왜 표시할까?
        - 검색 사이트에서 특정 언어로 제한해 검색할 때 필요하기 때문임
        - EX) '한국어로 된 문서'로 범위를 지정하면 `<html lang="ko">`를  우선 검색함
        - 또한 화면 낭독기에서 웹 문서를 소리 내어 읽을 때 해당 언어에 맞추어 발음, 억양, 목소리를 다르게 할 수 있음

  - `<head>` 

    - `<meta>` 

      - 웹 브라우저에는 보이지 않지만 웹 문서와 관련된 정보를 지정할 때 사용함
      - **화면에 글자를 표시할 때 어떤 인코딩을 사용할지 지정하는 것**이  가장 중요함
      - 웹 서버는 영어가 기본임, 한글을 표시하려면 **UTF-8**이라는 **문자 세트**를 사용함
      - 간단한 설명, 제작자 등의 정보를 지정할 수 있음

      ~~~html
      <meta charset="UTF-8">
      
      <meta name="keyword" content="html 구조"> //웹 문서의 키워드에 대한 설명
      <meta name="description" content="html 구조를 설명드리겠습니다."> // 웹 문서 설명 
      <meta name="author" content="YoungHoon Ko"> //제작자 설명
      ~~~

      

    - `<title>`

      - `<head>` 안에서 가장 중요한 태그

        ~~~html
        <tite>이것은 제목입니다.</tite>
        ~~~

  - `<body>` 

    - `<h1>` : 글자의 크기를 조절할 수 있음(1~6까지 가능)(숫자가 커질수록 글자 작아짐)
    - `<p>` : 문장 입력을 가능하게 해줌
    - `<hr>` : horizo의 약어로 수평선을 그어줌

<hr />

