---
layout: post
title:  "Todo App 만들기"

[//]: # (date:   2023-01-02 21:34:36 +0900)

categories: Notes
---

[//]: # (<h1>Introduction</h1>)

## 목차

### 1. 서론
   - 1.1. 나는 왜 Todo app을 제작하게 되었을까?
   - 1.2. Todo app을 뭘로 만들까?

### 2. 제작 과정
   - 2.1. Node.js + express로 서버 구성하기
   - 2.2. mongoDB 세팅하기
   - 2.3. 간단한 레이아웃 적용 및 Todo App 구현

### 3. 후기

---



### 1. 서론

#### 1.1. 나는 왜 Todo app을 제작하게 되었을까?

나는 프론트앤드 개발자들이 토이 프로젝트로 Todo app을 주로 만든다는 것을 익히 들어 알고 있었다.   
하지만 기본적인 Todo App이 아닌 조금 더 멋진 프로젝트를 만들 수 있지 않을까 하는 알 수 없는 자신감 때문에 생각만하고 미뤄온 지 어느 덧 반 년...   
함께 멋진 업그레이드 버전 Todo App을 만들기로 한 동료는 퇴사하여 나를 떠났고 결국 나는 아무것도 만들지 않은 채 시간만 보내고 있는 사람이 되었다!   

<img src="/assets/study/todoApp/todoapp_1.png" width="400" height="300">


 사실 예전부터 만들고 싶던 프로그램이 있는데, 그건 바로 과자 추천 프로그램이다.   

<img src="/assets/study/todoApp/todoapp_2.png" width="700" height="300">


현재 사무실에서는 주기적으로 담당 과장님께서 과자나 음료수를 주문한다. 그런데 다들 입맛도 다르고 인원이 많아 먹는 속도도 꽤 빠르다보니 주문을 담당하는 사람 입장에서는 꽤 고민거리일 것이라고 생각되었다.(절대 내가 먹고 싶은 과자가 따로 있어서 그런 것은 아니다!)   
엄청 거창한 프로그램은 아니지만, 직원들이 원하는 과자를 검색해서 추천 버튼을 눌러놓으면 관리자가 들어가서 추천이 많은 순서대로 확인할 수 있는 프로그램이다. 확인하고 나면 초기화 버튼을 눌러 추천 수를 0으로 돌릴 수 있다...는 것 까지 생각해 두었다.

이 기능들을 구현하기 위해서는 서버와 DB, 각종 오픈 API(쇼핑몰 상품 조회 등)가 필요했는데 당시 내 지식과 능력으로는 서버나 DB에 대한 지식도 부족했고, 어떤식으로 프로젝트를 구성하면 좋을 지 생각하는 능력도 부족했다.   
그래서 미루고 미뤄왔던 서버 DB 연동, CRUD 등의 기능을 자바스크립트로 모두 구현할 기본기를 다지기 위해 간단한 todo App을 먼저 만들어 보기로 했다.


#### 1.2. Todo App을 뭘로 만들까?

- Node.js   
  Node.js란 자바스크립트의 런타임 환경(플랫폼)으로, 웹브라우저 외의 영역인 서버 측에서 자바스크립트 언어를 사용할 수 있게 해준다.   
  자바스크립트는 원래 브라우저에서만 돌아갈 수 있다고 한다.
- V8   
각 브라우저 별 엔진이 존재하는데, 구글 크롬 브라우저의 V8 엔진이 Node.js에 들어가 있다.   
엔진은 자바스크립트 언어를 기계어로 해석하는 역할을 한다.
- express   
Node.js의 프레임워크로, Node.js의 원칙과 방법을 이용하여 서버를 쉽게 구현할 수 있게 해준다.




### 2. 제작 과정

#### <a href='/notes/2023/08/28/classNotes-todoApp2.html'>2.1. Node.js + express로 서버 구성하기</a>
#### 2.2. mongoDB 세팅하기
#### 2.3. 간단한 레이아웃 적용 및 Todo App 구현


### 3. 후기
