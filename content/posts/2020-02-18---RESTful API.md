---
title: RESTful API

date: "2020-02-18T18:30:10.169Z"
template: "post"
draft: false
slug: "2020_02_18"
category: "Daily"
tags:
  - "REST"
  - "RESTful API"
  - "Web Development"
description: "RESTful API"
socialImage: ""
---
지난 2월에 [RESTful API에 대해 정리](https://velog.io/@k904808/RESTful-API)해 보았었는데, 다시 읽어보니 RESTful API에 대한 이해없이 개념만 나열해둔 정리였다. 😭
[좋은 자료](https://evan-moon.github.io/2020/04/07/about-restful-api/?fbclid=IwAR3sbk8REMXfwP8UpNCiSfk91LZxL4dWwL3c72OW_umetAPM90A9aObmYfI)가 있어 차분하게 읽어보고 나름대로 정리해보았다.


>
**좋은 API란? **
어떠한 정보도 없는 누군가가, 구구절절 설명없이 엔드포인트만 봐도 어떤 동작을 하는 API인지 바로 이해할 수 있을 정도로 **정의가 직관적이고 명확한 API**.



이를 위한 **API 아키텍쳐 가이드라인이 REST**이며, 2000년에 로이 필딩(Roy Fielding)이 소개한 이후 20년이 지난 현재도 널리 사용되고 있다.

### REST란?
**RE**presentaional **S**tate **T**ransfer의 약자.
즉, REST는 통신을 통해 자원의 표현된 상태를 주고받는 것에 대한 아키텍쳐 가이드 라인이다.

REpresentaional State 란?
= 대표적인 상태
= 표현된 상태
= 서버가 가지고 있는 리소스의 상태

**원본 리소스는 데이터베이스에 저장된 하나의 로우로 존재한다.
이를 그대로 넘겨줄 수 없으니 서버가 원본 리소스를 읽어와 클라이언트가 요청하는 '상태로 표현해주는 것'**


### RESTful API란?
프론트엔드와 백엔드가 소통하는 엔드포인트

리소스의 표현 상태만으로는 서버에서 어떤 일이 발생하는지 알기 어렵다.
때문에, RESTful API에서는 **REST 아키텍쳐를 통해 표현된 리소스와 더불어 어떠한 행위인지 명시할 수 있는 HTTP 메소드와 URI를 활용한다.** 


### RESTful API의 세가지 요소

>**REST** : 리소스가 어떻게 표현되는지? 
ex) Accept: application/json

>**URI**  : 어떤 리소스인지?
ex) /api/users/1

>**HTTP 메소드** : 어떤 행위인지?
ex) GET

아래와 같이 클라이언트가 서버에게 요청을 보내고 응답을 받았다고 해보자.
-> **1번 유저의 정보를 가져오는 API겠구나 하고 추측할 수 있다.**

```
GET http://localhost:8000/api/users/1
Host : localhost:8000
Accept: application/json
```

```
HTTP/1.1 200 OK
Content-Length: 18
Content-Type: application/json

{
	id   : 1,
    	name : 'Kay'

}

```

### ✔️**여기에서, user 가 아닌 users 이유는?**
유저라는 리소스가 특정한 하나의 객체가 아니기 때문

' / 고유한 ID' 를 이용해 리소스의 계층을 표현하며 특정 유저를 표현할 수 있다.


### ❗️**URI에는 행위가 표현되면 안된다**
ex) POST /users/2/delete
가이드라인에 어긋남

권장사항은, **URI가 가지는 의미는 철저히 어떤 리소스인지, 그리고 리소스의 계층 구조에 대한 것 뿐이어야함** 
ex) DELETE /users/2


참고 :
https://evan-moon.github.io/2020/04/07/about-restful-api/?fbclid=IwAR3sbk8REMXfwP8UpNCiSfk91LZxL4dWwL3c72OW_umetAPM90A9aObmYfI
