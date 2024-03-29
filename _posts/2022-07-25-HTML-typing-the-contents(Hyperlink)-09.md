---
title: 09. HTML-typing the contents(Hyperlink)
Author: YoungHoon Ko
date: 2022-07-25 16:14:38 +0900
categories: [HTML, HTML-Study]
tags: [html]
image: /assets/img/CleanShot 2022-08-17 at 16.24.23@2x.png
image: /assets/img/CleanShot 2022-08-17 at 16.24.55@2x.png
image: /assets/img/CleanShot 2022-08-17 at 16.37.41@2x.png
image: /assets/img/CleanShot 2022-08-17 at 16.37.58@2x.png
image: /assets/img/CleanShot 2022-08-17 at 16.37.41@2x.png
image: /assets/img/CleanShot 2022-08-17 at 16.59.35@2x.png
---

[toc]

# 웹 문서에 내용 입력하기

## 4-6. 하이퍼링크 삽입하기

### 1. 링크를 삽입하는 `<a>` 태그와 **href** 속성

- 링크를 삽입할 때는 `<a>` 태그를 사용하는데, 이때 텍스트를 사용하면 텍스트가, 이미지를 사용하면 이미지가 링크가 된다.
- 링크의 주소는 **href** 속성을 통해 지정한다.

```html
<a href="링크 주소">텍스트, 이미지</a>
```

- 위의 코드는 기본형이다.

#### 1. 텍스트 링크 만들기

- `<a>` 태그에 링크로 만들 텍스트를 입력하고, **href** 속성을 이용해 텍스트와 연결할 문서의 경로를 지정한다.

```html
<div>
  <a href="/Users/goyeonghun/Desktop/hoon/01.html">여기를 클릭하세요</a>
</div>
```

- 실습

![이미지](/assets/img/CleanShot 2022-08-17 at 16.24.23@2x.png)

![이미지](/assets/img/CleanShot 2022-08-17 at 16.24.55@2x.png)

- 텍스트에 링크를 추가하면 글자색이 바뀐다.
- 이 현상은 css를 통해 색을 지정해줘야한다.(뒤에 다룰 것)

#### 2. 이미지 링크 만들기

- 텍스트 링크와는 다르게 `<img>` 태그를 사용한다.
- `<a>` 태그의 사용은 텍스트 링크를 지정할 때와 같다.
- 차이점은 텍스트가 들어갈 자리에 `<img>` 태그가 들어간다.

```html
<a href="02.html"><img src="./gyh.png" alt="고영훈"></a>
```

- 실습

![이미지](/assets/img/CleanShot 2022-08-17 at 16.37.41@2x.png)

![이미지](/assets/img/CleanShot 2022-08-17 at 16.37.58@2x.png)

- 이미지를 클릭하면 연결된 문서로 이동한다.

### 2. **target** 속성

- 위의 두 링크들의 공통점은 바로 같은 페이지에서 열린다는 것이다.

> "그게 그렇게 중요한가요??"

- 일반적으로 사용할 때는 큰 불편함은 없을 수 있다. 그러나, 앞 페이지에 있는 내용을 가져와야 한다거나, 복사가 안 되는 텍스트일 경우는 매우 힘들 수 있다.
- 그래서 **target** 속성에` **_blank**` 를 사용하면 **새로운 창에서 연결된 문서가 열린다.**

```html
<div>
  <p>
    <a href="02.html" target="_blank"><img src="./gyh.png" alt="고영훈"></a>
  </p>
</div>
```

- 실습

![이미지](/assets/img/CleanShot 2022-08-17 at 16.37.41@2x.png)

![이미지](/assets/img/CleanShot 2022-08-17 at 16.59.35@2x.png)

- 새 창에서 연결된 파일이 열린 것을 확인할 수 있다.