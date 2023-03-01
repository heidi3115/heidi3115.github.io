---
layout: post
title:  "CORS"

[//]: # (date:   2023-01-02 21:34:36 +0900)

categories: IT
---

[//]: # (<h1>Introduction</h1>)

<h3>CORS란?</h3>
CORS는 Cross Origin Resource Sharing의 약자이다.   
출처가 다른 자원들을 공유한다는 뜻으로, 한 출처에 있는 자원에서 다른 출처에 있는 자원에 접근하도록 하는 개념이다.   
브라우저의 보안과 관련하여 아주 중요한 역할을 수행하기 때문에 존재하는데, 아래에서 자세히 알아보자.


## 1. 출처 (Origin)

CORS에 대해 이해하기 위해서는 먼저 출처라는 개념에 대해 알아야 한다.    
다음 이미지를 확인해보자.

![img_1.png](img_1.png)

위 구성요소 중 Protocol+Host+Port 세가지가 같으면 동일 출처(origin)라고 한다.


### 동일 출처 예시
    http://example.com:80
    http://exmaple.com

Port는 생략 가능하므로 동일 출처이다.


    http://example.com/test1/index.html
    http://example.com/test2/index.html

Protocol, Host, Port(생략)가 같고 Path부터 다르므로 동일 출처이다.

### 다른 출처 예시
    http://example.com/test1
    https://example.com/test2

Protocol이 다르므로 동일출처가 아니다.


    http://example.com
    http://test.com

Host가 다르다.


다른 출처 요청일 경우, CORS정책에 준수하여 요청해야만 정상적으로 응답을 받을 수 있다.



## 자유롭게 다른 출처로 요청을 보낼 수 있다면?
다른 블로그에서 자유롭게 다른 출처로 요청을 보내는 상황을 적어둔 것을 가져왔다.

    홈페이지를 서핑하고 있는데, <script>가 심어진 evil.com 페이지를 열었다고 생각해봅시다.   
    굉장히 유용한 정보를 담고 있는 사이트이지만, 페이지를 열면서 <script>가 실행되어 은행에 
    'Delete /account'를 요청하도록 되어 있습니다. 
    AJAX 호출로 은행 API를 호출하여 나의 은행 계좌를 삭제해버리는 사고가 발생합니다.

따라서, 다른 출처의 접근을 막기 위해서 동일 출처 정책이 등장하게 되었다.



## CORS의 동작 원리

1. 웹 어플리케이션에서 다른 출처의 리소스를 요청하는 경우 HTTP 프로토콜을 사용해서 요청을 보낸다.
2. 이 과정에서 브라우저는 요청 헤더 속 Origin 이라는 필드에 출처를 함께 담아보낸다.
3. 서버에선 요청에 대한 응답을 전달한다.
4. 이 때 response header에 Access-Control-Allow-Origin 이란 값을 보낸다.
5. 응답을 받은 브라우저에선 보낸 요청의 Origin과 서버의 response header 속 Access-Control-Allow-Origin을 비교해 본 다음 유효한 응답인지 아닌지를 결정한다.


## CORS의 요청 방식 세 가지


### 1. 단순 요청 (simple request)

- 서버에게 바로 본 요청을 전송하는 방식으로 요청에 대한 응답으로,   
서버가 헤더에 **Access-Control-Allow-Origin** 를 확인하여 브라우저가 CORS 동작을 수행을 검토한다.

- 조건 : 요청 메소드는 GET, HEAD, POST 중에서만 가능
- User Agent가 자동으로 설정한 헤더를 제외하면, 아래와 같은 헤더들만 사용할 수 있다.
    - Accept
    - Accept-Language
    - Content-Language
    - Content-Type
    - DPR
    - Downlink (en-US)
    - Save-Data
    - Viewport-Width
    - Width

- Content-Type 헤더에는 아래와 같은 값들만 설정할 수 있다.
  - application/x-www-form-urlencode
  - multipart/form-data
  - text/plain

### 2. 프리플라이트 요청 (preflight request)

- 단순 요청의 조건에 벗어나는 요청의 경우, 서버에 실제 요청을 보내기 전에 예비 요청에 해당하는 프리플라이트 요청을 먼저 보내서 실제 요청이 전송하기에 안전한지 확인한다.   
만약 안전한 요청이라고 확인이 된다면, 그때서야 실제 요청을 서버에게 보낸다. **총 두 번의 요청을 전송하는 것**.

- 브라우저에서 options 메서드를 통해 사전 요청을 보내고 서버에선 어떤 것을 허용/금지할지 정보를 헤더에 담아 보내주게 되는데,  
이러한 방식은 안정성을 조금 더 보장받을 수 있다.


### 3. 인증 정보를 포함한 요청 (credentialed request)
이 방식은 인증된 정보를 가지고 요청하는 방법으로 보안이 강화된 방법이다.  
여기서 말하는 인증 정보란 쿠키(Cookie) 혹은 Authorization 헤더에 설정하는 토큰 값 등을 일컫는다.   
만약 이러한 인증 정보를 포함한 요청(Credentialed Request)이라면, 별도로 따라줘야 하는 CORS 정책이 존재한다.

우선, 쿠키 등의 인증 정보를 보내기 위해서는 클라이언트 단에서 요청 시 별도의 설정이 필요하다.  
이는 Ajax 요청을 위해 어떠한 도구를 사용하느냐에 따라 달라진다. 만약 XMLHttpRequest, jQuery의 ajax, 또는 axios를 사용한다면 withCredentials 옵션을 true로 설정해줘야 한다.   
반면, fetch API를 사용한다면 credentials 옵션을 include로 설정해줘야 한다.   
이러한 별도의 설정을 해주지 않으면 쿠키 등의 인증 정보는 절대로 자동으로 서버에게 전송되지 않는다.