---
layout: post
title:  "http의 구조 / 요소"

[//]: # (date:   2023-01-02 21:34:36 +0900)

categories: IT
---

[//]: # (<h1>Introduction</h1>)

<h3>HTTP의 구조</h3>

HTTP는 HTML 문서와 같은 텍스트로 되어있는 리소스(데이터)들을 가져올 수 있도록 해주는 프로토콜(통신규약)이다.   
프로토콜이란 컴퓨터들끼리 HTML 파일을 주고받을 수 있게 도와주는 소통방식 또는 약속이다.

클라이언트와 서버 간의 통신을 효율적으로 하기 위한 HTTP의 특징에 대해 적어보겠다.


### Connectionless

HTTP의 첫번째 특징은 Connectionless(비연결성)다.   
클라이언트와 서버가 연결되어 있지 않다는 뜻으로, 계속해서 연결이 되어 있을 때 필요한 리소스들을 비연결성을 통해 아낌과 동시에 더 많은 연결을 할 수 있다는 장점이 있다.
클라이언트가 어떠한 데이터를 요청하면 서버는 응답을 하고 한번 맺었던 연결을 끊어버린다.


### Stateless

HTTP는 Stateless(무상태)다. 클라이언트와 서버 관계에서 서버가 클라이언트의 상태를 보존하지 않는다는 뜻이다.   
각각의 HTTP 통신(요청/응답)은 이러한 특성 떄문에 이전 및 과거의 통신(요청/응답)에 대한 내용을 전혀 알지 못 한다. 따라서, 매 통신마다 필요한 모든 정보를 담아서 요청을 보내야 한다.
따라서 서버는 세션과 같은 별도의 추가 정보를 관리하지 않아도 되고, 다수의 요청 처리 및 서버의 부하를 줄일 수 있는 장점을 갖게된다.
다만 이 전의 기록이 필요한 경우(좋아요 버튼 등) 로그인 토큰 또는 쿠키, 세션 같은 기술이 등장하게 된다.


### URL

URL(Uniform Resource Locators)은 서버에 자원을 요청하기 위해 입력하는 영문 주소이다.
URL의 구조는 아래와 같다.

[//]: # (<img src="/assets/javascript-01/1.png">)

* Protocol
* Domain
* Path
    - 파일의 경로를 가리키며, /(슬래시) 뒤에 나온다.   
      예 : https://heidi3115.github.io/itPost
* Parameter
    - 파라미터는 쿼리 스트링이라고도 부르며, key(파라미터의 이름)=value(파라미터의 값) 형태로 이루어진다.    
      ?(물음표) 뒤에 나열되고, & 기호로 구분되어 여러 개가 존재할 수 있다.   
      예 : https://search.naver.com/search.naver?where=image&sm=tab_jum&query=미피+고화질


### Response / Request

[//]: # (<img src="/assets/javascript-01/1.png">)

HTTP 메시지는 서버와 클라이언트 간에 데이터가 교환되는 방식으로, 이때 메시지 타입은 Response와 Request로 나뉜다.  
그림과 같이 Request는 클라이언트 -> 서버로 전달하는 메시지고, Response는 Request에 대한 서버의 응답이다.

메세지는 세 부분으로 이루어져 있다.

[//]: # (<img src="/assets/javascript-01/1.png">)

#### Request
* Start Line
    - HTTP 메소드, Request target, HTTP version 등
        - HTTP 메소드 : `GET`, `POST`, `PUT`, `DELETE`
        - Request target : HTTP Request가 전송되는 목표 주소
        - HTTP version : version에 따른 Request 메세지 구조 및 데이터 식별을 위함
* Header
    - HTTP Request 그 자체에 대한 정보. `key : value` 형태로 이루어져 있음.
        - Host : 요청하려는 서버 호스트명 및 포트 번호
        - User-agent : 클라이언트 프로그램 정보
        - Referer : 직전 웹 링크 주소
        - Accept : 클라이언트가 처리 가능한 미디어 타입 종류
        - If-Modified-Since : 쓰여진 이후 변경된 리소스 취득, 페이지 수정 시 최신 페이지로 교체함.
        - Authorization : 인증 토큰을 서버로 보낼 때 쓰는 header
        - Cookie : 쿠키 값은 `key-value`로 표현된다.

* Body
    - Request가 전송하는 데이터로, POST 요청일 경우 HTML 폼 데이터가 포함되어 있음.


#### Response
* Start Line
    - HTTP version, Status Code, Status Text 등
        - Status Code : Response 상태를 나타내는 코드. (200, 403, 404, 500 등)
        - Status Text : Response 상태를 간략하게 text로 설명
* Header
    - Location : 301, 302 상태코드일 때만 볼 수 있는 Header
    - Server : 웹 서버의 종류
    - Age : max-age 시간내에서 얼마나 흘렀는지 초 단위로 알려주는 값
    - Referrer-policy : 서버 referrer 정책을 알려주는 값
    - WWW-Authenticate : 사용자 인증이 필요할 시 서버가 제공하는 인증 방식
    - Proxy-Authenticate : 요청한 서버가 프록시 서버인 경우 유저 인증을 위한 값

* Body
    - Request의 Body와 동일.
