---
title: 06. HTML-typing the contents(Table)
Author: YoungHoon Ko
date: 2022-07-16 18:49:20 +0900
categories: [HTML, HTML-Study]
tags: [html]
image: assets/img/html/html-logo.png
---

# 4. 웹 문서에 내용 입력하기

[toc]

## 4-3. 표 만들기

#### 1. 표의 구성 요소

- 표(table)은 행(row)과 열(col) 그리고 셀(cell)로 이루어짐
  - 셀은 행과 열이 만나 이루어진 곳으로 내용이 들어가는 자리

#### 2. `<table>` 태그,  `<caption>` 태그

- 표의 시작과 끝을 알려줌(`<table></table>`의 형식으로 사용함)
-  `<caption>` 태그는 표의 제목을 넣을 때 사용함
  -  `<table>` 태그 바로 아랫줄에  `<caption>` 태그를 사용하면 됨( `<caption>제목</caption>`)

~~~html
<table>
  <caption>title</caption>
</table>
~~~



#### 3.  `<tr>` 태그,  `<td>` 태그,  `<th>` 태그

-  `<tr>` 태그는 전체 행을 만듬
-  `<td>` 태그는 행 안에 셀을 만듬
-   `<table>` 태그 안에 `<tr>` 태그,  `<td>` 태그가 모두 모여야 하나의 셀을 만들 수 있음
-  `<th>` 태그는  표의 제목 행에 셀을 만들때 사용함
  - 글자가 진하게 표시됨
  - 셀 안에 중앙에 배치됨

~~~html
<table>
  <tr>
    <th>진하게 표시됨</th>
    <th>중앙에 배치됨</th>
  </tr>
  <tr>
    <td>일반 셀에 내용입력</td>
    <td>일반 셀에 내용입력</td>
  </tr>
</table>
~~~



#### 4.   `<thead>` 태그,   `<tbody>` 태그,   `<tfooter>` 태그

- 일부 표에서는 제목, 본문, 요약 등으로 표의 내용을 나눔
- 이때 표의 구조를 나누어 주는 것이 좋음
- 구조를 지정하면 화면 낭독기를 돌릴 때 이용자가 편리하게 이용할 수 있음
-  `<thead>` 태그는 **제목**을 표시함
  - 자바스크립트를 사용해서 고정 가능
-  `<tbody>` 태그는 **본문**을 표시함
  - 본문이 길 경우 본문 내용만 스크롤할 수 있음(자바스크립트 사용)
-  `<tfooter>` 태그는 요약을 표시함

~~~html
<table>
  <caption>title</caption>
  <thead>
    <th>진한 글씨</th>
    <th>중앙에 배치됨</th>
  </thead>
  <tbody>
    <td>내용</td>
    <td>내용</td>
  </tbody>
  <tfooter>
    <td>요약</td>
    <td>요약</td>
  </tfooter>
</table>
~~~



#### 5.  `<rowspan>` 태그,  `<colspan>` 태그

- 표는  `<tr>` 태그와  `<th>` 태그,  `<td>` 태그를 이용해서 여러 셀로 구성함
- 이때 여러 셀을 합치거나 나누어서 다양한 형태로 바꿀 수 있음
- **행이나 열을 실제로 합치거나 나누는 것으로  `<td>` 태그와  `<th>` 태그에서 이루어짐**
-  `<rowspan>` 태그는 행(row)을 합치는 태그임
  - `<td rowspan="2">행을 합쳤습니다</td>` 의 형태로 사용함
-  `<colspan>` 태그는 열(col)을 합치는 태그임
  - `<th colspan="2">열을 합쳤습니다</th>` 의 형태로 사용함

~~~html
<table>
  <caption>title</caption>
  <thead>
    <th rowspan="2">진한 글씨</th>
    <th>중앙에 배치됨</th>
  </thead>
  <tbody>
    <td>내용</td>
    <td>내용</td>
  </tbody>
  <tfooter>
    <td colspan="2">요약</td>
    <td>요약</td>
  </tfooter>
</table>
//위의 코드는 rowspan과 colspan을 보여주기 위한 예시입니다.
~~~



#### 6. `<col>` 태그,  `<colgroup>` 태그

- 단순히 표를 만드는 것이 아니라 특정 열에 배경색을 넣거나 너비를 바꾸려면 특정 열을 선택해야함
- 그때 사용하는 태그가  `<col>` 태그,  `<colgroup>` 태그임
- `<col>` 태그는 열을 1개만 지정할 때 사용함
-  `<colgroup>` 태그는 2개 이상의 열을 지정할 때 사용함
- **반드시** `<caption>` 태그 다음에 써야함(**중요**)
  - 표의 내용이 시작되기 전에 열의 상태를 알려주는 것
- `<col>` 태그를 사용할 때는  `<colgroup>` 태그 안에 포함하여 사용하는데,  **표 전체 열의 개수만큼  `<col>` 태그를 넣어야함**
  - 스타일을 지정하지 않은 열이 있으면 그냥  `<col>` 태그를 넣음

<hr />

