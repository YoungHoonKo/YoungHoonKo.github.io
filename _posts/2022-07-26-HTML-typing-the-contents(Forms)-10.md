---
title: 10. HTML-typing the contents(Forms)
Author: YoungHoon Ko
date: 2022-07-26 16:04:38 +0900
categories: [HTML, HTML-Study]
tags: [html]
image: /assets/img/CleanShot 2022-08-18 at 15.07.57@2x.png
image: /assets/img/form-intro.png
image: /assets/img/CleanShot 2022-08-18 at 15.32.27@2x.png
image: /assets/img/CleanShot 2022-08-18 at 15.46.31@2x.png
image: /assets/img/CleanShot 2022-08-18 at 15.59.06@2x.png
image: /assets/img/CleanShot 2022-08-18 at 15.59.06@2x.png)
---

[toc]

# 5. 입력 양식 작성하기

## 5-1. 폼 삽입하기

### 1. Intro

#### 1. What is form?

- 우리가 흔히 쇼핑몰, 설문 조사 등에 참여할 때 아이디, 비밀번호, 주소 등의 정보를 입력하란 페이지를 본 적이 있을 것이다.
- **웹 사이트로 정보를 보낼 수 있는 요소는 모두 form이라고 할 수 있다.**

![이미지](/assets/img/CleanShot 2022-08-18 at 15.07.57@2x.png)

#### 2. How does it work?

![](/assets/img/form-intro.png)

1. 사용자가 아이디와 비밀번호를 입력하고 로그인 버튼을 누른다.
2. 입력한 정보는 웹 서버로 전송 된다.
3. 데이터베이스에서 입력받은 아이디와 비밀번호가 일치하는지 확인한다.
4. 확인한 결과를 웹 브라우저에 보낸다.

- 폼과 관련된 작업은 정보를 저장하거나 검색, 수정하는 것이 대부분인데 모두 **데이터 베이스**를 기반으로 작동한다.
- 따라서 틀은 HTML로 만들고, 입력한 정보는 APS, PHP,  JSP 같은 서버 프로그래밍을 이용해 처리한다.

### 2. Text

#### 1. 폼을 만드는 `<form>` 태그

```html
<form[속성="속성값">여러 폼 요소</form>
```

- `<form>`과 `</form>` 사이에 여러 가지 폼 요소를 넣는다.
- 몇 가지 속성을 사용해서 입력받은 자료를 어떤 방식으로 서버로 넘길 것인지, 서버에서 어떤 프로그램을 이용해 처리할 것인지를 지정한다.

|    종류    |                             설명                             |
| :--------: | :----------------------------------------------------------: |
| **method** | 입력받은 정보를 서버 쪽 프로그램으로 어떻게 넘겨줄 것인지 지정<br />사용할 수 있는 속성 값은 **get**과 **post**이다.<br />1. **get** : 데이터를 256 ~ 4,096 Byte까지만 서버로 넘길 수 있음.사용자가 입력한 내용이 그대로 드러난다는 단점이 있음<br />2.**post** : 입력 내용의 길이에 제한 받지 않음.내용도 드러나지 않음 |
|  **name**  |  자바스크립트로 폼을 제어할 때 사용할 **폼의 이름**을 지정   |
| **action** | `<form>` 태그 안에 내용을 처리해 줄 **서버 프로그램**을 지정 |
| **target** | **action** 속성에서 지정한 파일을 **다른 창**에서 열도록 함  |

#### 2. 자동 완성 기능을 나타내는 **autocomplete** 기능

![](/assets/img/CleanShot 2022-08-18 at 15.32.27@2x.png)

- 위의 사진 처럼 아이디를 입력하려고 하는데 밑에 작게 자동으로 내용을 보여준다.
- 사용자가 입력했던 내용을 기억하고 비슷한 글자가 입력되면 이전에 입력한 내용을 힌트로 보여준다.
- 자동 완성 기능은 **autocomplete** 속성을 사용하며 속성값은 "on"이다.
- 하지만 인증 번호, 중요한 개인 정보 등은 사용하지 않는 것이 좋다.
- 이때는 속성값을 "off"로 바꿔주면 된다.

```html
<form action="" autocomplete="off">
  /* 폼 요소들 */
</form>
```

#### 3. 폼 요소를 그룹으로 묶는 `<fieldset>`, `<legend>` 태그

- 하나의 폼에서 구역을 나눌 때  `<fieldset>` 태그를 사용한다.

```html
<fieldset [속성="속성값"></fieldset>
```

- `<legend>` 태그는 `<fieldset>` 태그로 묶은 그룹에 **제목**을 붙일 수 있다.

```html
<fieldset>
  <legend>
    그룹 이름
  </legend>
</fieldset>
```

#### 4. 폼 요소에 레이블을 붙이는  `<label>` 태그

- `<label>` 태그는 `<imput>` 태그와 같은 폼 요소에 레이블을 붙일 때 사용한다.
- 레이블이란 아이디 입력 창 옆에 붙어있는 텍스트를 말한다.

![](/assets/img/CleanShot 2022-08-18 at 15.46.31@2x.png)

- **아이디(6자 이상)**이라는 텍스트와 입력란을 묶는 예제이다

  1. 태그 안에 폼 요소 넣기(`<label>` 태그 안에 `<input>` 태그 넣기)

  ```html
  <label>레이블명<input></label>
  ```

  ``` html
  <label>아이디(6자 이상)<input></label>
  ```

  ![](/assets/img/CleanShot 2022-08-18 at 15.59.06@2x.png)

  2. `<label>` 태그의 for 속성과 폼 요소의 id 속성을 연결(`<label>` 태그와 폼 요소를 따로 쓰고 연결하기)

  ```html
  <label for="id">레이블명<input id="id"></label>
  ```

  ```html
  <label for="my-id">아디디(6자 이상)</label>
  <input type="text" id="my-id">
  ```

  ![](/assets/img/CleanShot 2022-08-18 at 15.59.06@2x.png)

  

  - 이 방법은 첫 번째 방법 보다 복잡하지만, `<label>` 태그를 사용한 레이블과 정보를 입력받는 `<input>` 태그가 떨어져 있더라도 서로 쉽게 연결할 수 있다는 장점이 있다.







로그인 폼 작동 과정 사진 출처: <https://seulbinim.github.io/WSA/form.html>