---
title: 04. HTML-typing the contents(Text)
Author: YoungHoon Ko
date: 2022-07-14 10:23:00 +0900
categories: [HTML, HTML-Study]
tags: [html]
---

# 4. 웹 문서에 내용 입력하기

[toc]

## 4-1. 텍스트 입력하기

#### 1. `<hn>` 태그

- h는 제목을 뜻하는 heading의 줄임말임
- 제목은 다른 텍스트 보다 굵고 진하게 표시함
- 자주 사용하는 제목 스타일을 미리 태그 형식으로 만든 것
- n의 값은 1~6까지의 크기가 있고, 1이 가장 크고 6이 가장 작음
- `<hn>title</hn>` 이런 식으로 뒤에 닫는 태그인  `</hn>`을 **반드시** 붙여줌

~~~html
<h1>이것은 제목1입니다.</h1>
<h2>이것은 제목2입니다.</h2>
(...생략...)
<h6>이것은 제목6입니다.</h6>
~~~



#### 2. `<p>` 태그, `<br>` 태그

##### 1. `<p>` 태그

- `<p>text</p>`의 기본 형태로 사용함
- 태그들 사이에 텍스트를 넣으면 텍스트 앞뒤고 빈 줄이 생기면서 단락이 만들어짐
- 그러나 편집기에서 p태그 사이에 줄을 바꾸더라도 웹에서는 한 줄로 표시됨
- 그러나 텍스트 단락이 웹에 한 줄로 표시할 수 없을 경우 자동으로 줄이 바뀜

~~~html
<p>
  안녕하세요
  고영훈입니다
  이렇게 P태그 안에서 줄을 바꿔도 한 줄로 표시됩니다.
  너무 길이가 길면 웹에서 자동으로 줄바꿈이 되는 것도 기억해두세요!!
</p>
~~~

##### 2. `<br>` 태그

- 텍스트 단락을 만들 때 원하는 위치에서 줄바꿈을 할 수 있음
- `<br>` 태그 단독으로 사용하기 때문에 닫는 태그는 필요 없음

~~~html
<p>
  이렇게 줄을 쓰다가 여기서 줄바꿈 하고 싶다면<br>이렇게 하면 '싶다면'에서 줄바꿈합니다!
</p>
~~~

##### 3. 차이점
~~~markdown
<br>태그를 두 번 사용하면 줄바꿈에 줄바꿈이여서 텍스트 단락이 나눠진 것처럼 화면에 표시할 수 있다.
그러나 후에 공부할 CSS를 사용해 텍스트 단락 스타일을 적용할 때 문제가 생깁니다. 왜냐하면 실제적으로 단락이 만들어진 것이 아니기 때문입니다.그래서 단락을 만들때는 반드시 <p>태그를 사용해야 합니다.

~~~



#### 3. `<blockqoute>` 태그

- 다른 사람의 말이나 책의 내용을 인용할 때 사용함
- 우리가 흔히 사용하는 ' "" '는 브라우저가 인식할 수 없음
- 인식할 수 있는 방법은 `<blockqoute>인용할 문장</blockqoute>` 이렇게 하면 됨
- **그리고 다른 텍스트들 보다 약간 들여씀**
- 화면 낭독기를 돌릴때 인용문은 다른 텍스트와 구분함

~~~html
<h1>이것은 제목1입니다.</h1>
<p>
  이렇게 줄을 쓰다가 여기서 줄바꿈 하고 싶다면<br>이렇게 하면 '싶다면'에서 줄바꿈합니다!
</p>
<blockqoute>
  이 문장을 인용문입니다. 다른 텍스트보다 안으로 들여씁니다.<br>이렇게 다른 태그들도 사용할 수 있습니다. 그리고 화면 낭독기를 돌리면 다른 텍스트들과 구분합니다.
</blockqoute>
~~~



#### 4. `<strong>` 태그, `<b>` 태그

##### 1. `<strong>` 태그

- `<strong>강조할 텍스트</strong>`의 형태로 사용함
- **경고나 주의 사항**처럼 중요한 **내용**을 강조할 때 사용함(**진짜 중요!!**)
- 화면 낭독기를 돌리면 `<strong>` 태그를 사용한 부분을 강조하여 읽음(**의미 중심**)

##### 2. `<b>` 태그

- 단순히 **글자만 굵게 표시**할 때 사용함
- 화면 낭독기를 돌릴 때 강조하지 않음(**보이는 것 중심**)

##### 3. 차이점

~~~ markdown
<strong>태그와 <b>태그는 눈으로 보기에 큰 차이점이 없다. 그래도 구분하는 이유는 화면 낭독기 기능 때문이다. <strong>태그는 낭독할 때 강조하여 읽지만 <b>태그는 그렇지 않다. 전자는 의미 중심이고, 후자는 글자 즉, 보이는 것에 중심을 둔 것이다.
~~~



#### 5. `<em>` 태그,  `<i>` 태그

##### 1.  `<em>` 태그

- em은 강조를 뜻하는 영단어 'emphasis'의 줄임말임
- 문장의 흐름상 **특정 부분을 강조**하고 싶을 때 사용함
- 즉, **문장 중에서 특별히 강조하고 싶은 부분에 사용함**

##### 2.  `<i>` 태그

- i는 이탤릭체(기울기체)를 뜻하는 영단어 'italic'의 줄임말임
- **마음속의 생각이나 용어, 관용구 등**을 표시할 때 사용함
- 즉, 단순히 **다른 텍스트와 구별하기 위해** 기울여서 표시하고 싶을 때 사용함



#### 6. 그 밖의 다양한 텍스트 관련 태그들

1.  `<abbr>` 태그 : 줄임말을 표시하고, 제목의 속성을 표시할 수 있음
2.  `<cite>` 태그 : 웹 문서나 포스트에서 참고내용을 표시함 
3.  `<code>` 태그 : 컴퓨터 인식을 위한 소스 코드임
4.  `<small>` 태그 : 부가 정보처럼 작게 표시할 수 있음
5.  `<sub>` 태그 : 아래 첨자를 표시함
6.  `<sup>` 태그 : 위 첨자를 표시함
7.  `<s>` 태그 : 취소선을 표시함

<hr />



