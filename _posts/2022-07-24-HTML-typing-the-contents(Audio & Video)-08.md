---
title: 08. HTML-typing the contents(Audio & Video)
Author: YoungHoon Ko
date: 2022-07-24 13:14:38 +0900
categories: [HTML, HTML-Study]
tags: [html]
image: /assets/img/CleanShot 2022-08-10 at 14.14.36@2x.png
image: /assets/img/CleanShot 2022-08-10 at 14.14.36@2x.png
image: /assets/img/CleanShot 2022-08-10 at 14.23.19@2x.png
image: /assets/img/CleanShot 2022-08-10 at 14.40.55@2x.png
image: /assets/img/CleanShot 2022-08-10 at 14.40.16@2x.png
---

[toc]

# 4. 웹 문서에 내용 입력하기

## 4-5. 오디오와 비디오 삽입하기

### 1. 다양한 멀티미디어 파일을 삽입할 때 쓰는`<object>`, `<embed` 태그

#### 1. `<object>` 태그

- `<object>` 태그는 오디오 파일뿐만 아니라 비디오, 자바 애플릿, PDF 등 **다양한 멀디미디어 파일**을 삽입할 때 사용한다.
- 기본 형식은 다음과 같다.

~~~html
<object width="너비" height="높이" data="파일"></object>
~~~

- `width`,  `height`,  `data` 등의 속성을 지정할 수 있다.

- Ex) PDF 파일 삽입하기

~~~html
<object width="900" height="800" data="math.pdf"></object>
~~~

![이미지](/assets/img/CleanShot 2022-08-10 at 13.30.20@2x.png)



#### 2. `<embed>` 태그

- HTML 초기 버전부터 사용해서 **대부분의 브라우저에서 사용할 수 있다.**
- 기본 형식은 다음과 같다.

~~~html
<embed src="파일 경로" width="너비" height="높이">
~~~

- `src`, `width`,  `height` 등의 속성을 지정할 수 있다.
  - `<object>` 태그와 <u>**다른 점**</u>
    1. `data` 속성이 아닌 `src` 속성을 가진다는 것
    2. **닫는 태그**가 없다는 것
- `<embed>` 태그는 오디오, 비디오, 이미지 등 다향한 멀티 미디어 파일을 삽입할 수 있다.
- **HTML의 `<audio`,  `video`, `<object>` 태그를 지원하지 않는 웹 브라우저를 고려해야할 때 `<embed>` 태그를 사용한다.**(중요)
- Ex) 오디오 파일 삽입하기

~~~html
<embed src="musics/pop.mp3">
~~~



#### 3. `<audio>`, `<video>` 태그

- 두 태그는 사용법과 속성이 거의 비슷하다
- HTML에서 **배경 음악이나 효과음 등 오디오 효과**를 넣으려면 `<audio>` 태그를 사용하고, **비디오 파일**을 삽입할 때는 `<video>` 태그를 사용한다.
- 이때 오디오나 비디오의 재생을 조절할 수 있는 **컨트롤 바 속성**을 함께 표시한다.

##### 1. `<audio>` 태그

- 기본 형식은 다음과 같다

~~~html
<audio src="오디오 파일 경로"></audio>
~~~

- Ex) 오디오 파일 삽입하기

~~~html
<audio src="musics/pop.mp3" controls></audio>
~~~

![이미지](/assets/img/CleanShot 2022-08-10 at 14.14.36@2x.png)



##### 2. `<video>` 태그

- 기본 형식은 다음과 같다

~~~html
<video src="비디오 파일 경로"></video>
~~~

- 컨트롤 바를 사용할 때 너비를 지정하지 않으면 웹 브라우저에 가득 차게 나타나므로 너비를 적절히 지정하는게 좋다.
- Ex)

~~~html
<video src="videos/field.mp4" controls width="700"></video>
~~~

![이미지](/assets/img/CleanShot 2022-08-10 at 14.23.19@2x.png)



##### 3. `<audio>`, `<video>` 태그의 속성

|        종류        |                             설명                             |
| :----------------: | :----------------------------------------------------------: |
|      controls      |                    화면에 컨트롤 바 표시                     |
|      autoplay      |                   오디오, 비디오 자동 재생                   |
|        loop        |                   오디오, 비디오 반복 재생                   |
|       muted        |                   오디오, 비디오 소리 제거                   |
|      preload       | 페이지를 불러올 때 오디오나 비디오 파일을 어떻게 로딩할건지 지정 |
|   width, height    | 비디오 플레이어의 너비와 높이를 지정함, 하나면 지정하면 나머지는 자동 계산됨 |
| poster="파일 이름" | `<video>` 태그에서 사용하는 속성으로 비디오 재생 전에 표시될 포스터 지정 |



### 2. 웹 브라우저에서 지원하는 멀티미디어 파일의 종류

|  종류  |  확장자  | 설명                                                         |
| :----: | :------: | :----------------------------------------------------------- |
| 비디오 |   mp4    | 많이 사용하는 비디오 형식으로 라이선스가 있지만 웹에서는 무료로 사용할 수 있다. |
|        |   webm   | 화질이 우수하고 무료라서 mp4와 함께 사용된다.                |
| 오디오 |   mp3    | 대부분의 음원에서 사용하는 형식이다.2017년 이후 라이선스가 종료되면서 무료로 사용할 수 있다. |
|        | mp4, m4a | mp3의 문제점을 개선한 AAC(Advanced Audio Coding) 코덱을 사용한 파일 형식이다.확장자는 mp4, mpa이다. |



- 웹 브라우저별 오디오, 비디오 파일의 지원 여부를 나타낸 것으로, 괄호 안의 내용은 지원하는 웹 브라우저 버전이다.

|     웹 브라우저     | 오디오  | 비디오  | 비디오 |
| :-----------------: | :-----: | :-----: | :----: |
|                     |   mp3   |   mp4   |  webm  |
|  인터넷 익스플로러  |  o(9+)  |  o(9+)  |   x    |
|        크롬         | o(all)  | o(all)  | o(25+) |
|     파이어폭스      | o(22+)  | o(35+)  | o(28+) |
|       사파리        |  o(4+)  | o(3.2+) |   x    |
|       오페라        | o(15+)  | o(25+)  | o(16+) |
|     iOS 사파리      | o(4.1+) | o(all)  |   x    |
| 안드로이드 브라우저 | o(2.3+) | o(4.4+) |   x    |

### 3. 실습

- 비디오 파일 삽입하고 자동 재생시키기

![이미지](/assets/img/CleanShot 2022-08-10 at 14.40.55@2x.png)

![이미지](/assets/img/CleanShot 2022-08-10 at 14.40.16@2x.png)

