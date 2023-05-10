---
layout: post
title:  "강의 정리 - HTML / CSS 소개"

[//]: # (date:   2023-01-02 21:34:36 +0900)

categories: Notes
---

[//]: # (<h1>Introduction</h1>)

## HTML이란?

HTML은 Hyper Text Markup Language의 약자로 웹 페이지를 만들 때 사용하는 **자료 구조 표현 언어**를 뜻한다.   
자료는 마음대로 표현하는 것이 아니라 HTML의 정해진 태그로 나눠두어 자료의 구조를 표현할 수 있어야 한다.

HTML에서 사용하는 태그들은 다음과 같다.

* `<p></p>` : paragraph의 약자로, 문단을 나타낼 때 사용
* `<a></a>` : anchor의 약자로, 하이퍼링크를 걸어주는 태그
* `<ul></ul>`, `<ol></ol>` : unordered/ordered list의 약자로, 보통 `li` 태그와 같이 쓴다.
* `<li></li>` : list item의 약자로, 보통 ul, ol 태그와 같이 쓴다.

이외에도 많은 태그들이 존재하는데, 모두 외울 순 없으니 필요할 때 검색해서 사용법을 익혀보는 것을 추천한다.



## CSS란?

CSS는 cascading style sheet의 약자로, 이름에서도 알 수 있듯 사용자에게 스타일, 레이아웃 등 문서를 표시하는 방법을 지정하는 언어를 뜻한다.   
제목 및 링크의 색상과 크기 변경 혹은 레이아웃을 만드는 데 사용할 수 있다.

위에 설명한 HTML의 태그에 스타일을 설정하여 깔끔하고 가독성 있는 웹 페이지를 구현할 수 있다.

사용 예시 

```javascript
p { // 모든 p 태그에
    width: 30px; // 너비를 30px을 주고
    height: 50px; // 높이를 50px 주고
    background: tomato; // 배경색을 tomato로 지정해주세요!
}
```



## HTML에 CSS 적용하기

일반적으로 HTML에 CSS를 적용하는 방법은 세가지가 있다.
* Inline style sheet
    - HTML 태그에 style 속성을 주어 css를 적용하는 방법
* Internal style sheet
    - `<style></style>`를 추가하여 그 안에 css를 적용하는 방법
* Linking style sheet 
    - 별도의 CSS 파일을 만들어 HTML 문서와 연결하는 방법


<div style="border: 3px solid #dcdcdc; padding:10px; border-radius: 10px">
📍 Linking Style Sheet를 기본으로 사용하고, 특정 문서에만 적용되는 스타일을 Internal Style Sheet/Inline Style Sheet로 만든다.
</div>


### Linking Style Sheet

Linking Style Sheet로 CSS 파일을 연결하기 위해서는 HTML 파일에 다음과 같은 코드를 추가 해야한다.

    <link href="css파일 경로.css" rel="stylesheet" />

이 방법은 여러 HTML 문서에 사용할 수 있기 때문에 적용시키고 싶은 문서에 `<link>` 태그로 연결만 해주면 된다.


### Inline/Internal Style Sheet

이 방법들은 HTML 문서 내에서 CSS를 적용할 수 있는 방법들이다.   
특히 Inline 방식은 해당 코드에 직접 style 속성을 주어 css 적용이 가능하고, Internal 방식은 문서 안에 
`<style></style>` 코드를 넣어주어 css 적용이 가능하다.

#### Inline 방식

    <p style="background:red; font-size:15px;">히히히</p>

#### Internal 방식

```javascript
<p>히히히</p>


<style>
  p {
    background: red;
    font-size: 15px;
  }
</style>
```


## class 이름 짓기

위에서는 HTML에 CSS를 적용할 수 있는 방법들에 대해 알아보았다.
모든 방법들은 각 태그 별로, 혹은 특정 태그만 지정하여 스타일을 지정할 수 있는데 이를 위해서는 원하는 태그에 class를 부여하여야 한다.

```javascript
<p class="test">히히히</p>
<style>
  .test {
    background: black;
    font-size: 50px;
  }
</style>
```

이 때 class 이름 앞에 점(.)을 찍어야 한다는 것. 그리고 이름 중복을 피해야 한다는 것을 주의하고 작성한다.
위에서 계속 예시를 들었던 것처럼 태그 명 자체로도 스타일 적용이 가능하다.


## Id 부여하기

각 태그에는 class명을 지정하지 않고도 스타일을 적용할 수 있다. Id 선택자라는 것이 바로 그 방법인데, 사용법은 class와 동일하다.
다만 Id는 이름에서 알 수 있듯이 고유한 이름으로서, 하나의 문서에 하나밖에 사용할 수 없다.

```javascript
<p id="title">
  히히히
</p>
<style>
  #title {
    background: green;
    font-size: 100px;
  }
</style>
```



여기까지 태그에 스타일을 주는 법에 대해 알아보았다. 그런데 여기서 한 가지 주의해야할 점이 있다.   
눈치 빠른 사람들은 이미 알아챘겠지만, 나는 일부러 계속해서 같은 속성(background, font-size)을 반복해서 예시로 들었다.
이는 같은 스타일을 동시에 적용했을 때, 어떤 방식이 가장 최 상위 권한을 가지는 지 작성하기 위함이었다.


우리가 작성했던 코드를 다시 한 번 살펴보자.   


```javascript
p {  // tag selector
  background: red;
  font-size: 15px;
}
.test { // class selector
  background: black;
  font-size: 50px;
}
#title { // id selector
   background: green;
    font-size: 100px;
}
```


우선 태그 자체로 스타일을 적용하는 방법은 `tag selector`라고 부르며, 가장 최하위의 권한을 가지고 있다.


다음으로 class로 스타일을 적용하는 방법인 `class selector`, id로 스타일을 적용하는 방법인 `id selector`가 존재하는데,   
고유 권한인 `id selector`가 가장 높은 권한을 가지고 있다.

따라서 세 방법을 한 줄로 나타내면 다음과 같다.

**`tag < class < id`**