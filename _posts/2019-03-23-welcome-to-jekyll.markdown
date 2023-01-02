---
layout: post
title:  "Vue.js 소개"
date:   2023-01-02 21:34:36 +0900
categories: Vue
---
<h1>Introduction</h1>

<h4>당신은 지금 Vue 3 문서를 읽고있습니다!<br/></h4>
1) Vue 2 지원은 2023년 12월 31일에 종료될 예정입니다.
<a href="https://v2.vuejs.org/lts/">링크</a>에서 자세한 내용을 확인하세요.<br/>
2) Vue 2 문서는 <a href="https://v2.vuejs.org/">v2.vuejs.org</a>로 이동하였습니다.<br/>
3) Vue 2에서 3로 업그레이드 하는 방법은 <a href="https://v3-migration.vuejs.org/">Migration Guide</a>를 확인하세요


<h2>Vue는 무엇일까요?</h2>

vue(뷰)는 사용자 인터페이스를 구축하기 위한 Javascript의 프레임워크입니다. 
표준 HTML, CSS 및 JavaScript를 기반으로 구축되며 간단하거나 복잡한 사용자 인터페이스를 
효율적으로 개발하는 데 도움이 되는 선언적 구성 요소 기반 프로그래밍 모델을 제공합니다.

간단한 샘플코드를 확인해보세요 :

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

해당 예제는 클릭할때마다 숫자가 1씩 더해지는 버튼을 만들어냅니다.
이 예제는 Vue의 두 가지 핵심 기능을 보여줍니다.

<span style="font-weight:700; font-size:16px">선언적 렌더링</span> : Vue는 Javascript 상태를 기반으로 HTML 출력을 선언적으로 설명할 수 있는 템플릿 구문으로, 표준 HTML을 확장합니다. <br />
<span style="font-weight:700; font-size:16px">반응성</span> : Vue는 JavaScript 상태 변경을 자동으로 추적하고 변경이 발생할 때 DOM을 효율적으로 업데이트합니다.

이쯤되면 당신은 질문이 있을 수 있습니다. 하지만 걱정하지 마세요. 남은 문서들에서 세부 내용을 다룰것입니다.
