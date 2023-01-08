---
layout: post
title:  "React의 라이프 사이클 메서드"

[//]: # (date:   2023-01-02 21:34:36 +0900)

[//]: # (categories: React)
---

[//]: # (<h1>Introduction</h1>)

<h4>React의 Hooks 1. useEffect</h4>

모든 리액트 컴포넌트에는 라이프사이클이 존재한다.
라이프 사이클(life-cycle)이란 직역하자면 **생명 주기**라는 뜻이다.<br /><br /><br />
컴포넌트의 수명은 페이지 준비 과정에서 시작되어 페이지에서 사라질때 끝난다.


첫 렌더링에 특정 작업이 함께 이루어져야 하는 경우 혹은 컴포넌트를 업데이트 하기 전과 하고 나서 처리해야 하는 경우에 이러한 라이프사이클 메서드를 사용하는데,
라이프 사이클 메서드는 클래스형 컴포넌트에서만 사용 가능하다.
함수형 컴포넌트에서는 Hooks 기능을 사용하여 비슷한 작업을 처리할 수 있다.


이번 글에서는 React Hooks 중에서 함수형 컴포넌트에서도 렌더링 직후 작업을 설정하는 **useEffect**에 대해서 작성해보도록 하겠다.


Hooks는 리액트 16.8 버전에 새로 도입된 기능이다.


그 중 useEffect는 리액트 컴포넌트가 렌더링 될 때마다 특정 작업을 수행하도록 설정할 수 있는 Hook이다.


<br />

```javascript
import { createApp } from 'vue'

createApp({
  data() {
    return {
      count: 0
    }
  }
}).mount('#app')
```

```
<div id="app">
  <button @click="count++">
    Count is: {{ count }}
  </button>
</div>
```