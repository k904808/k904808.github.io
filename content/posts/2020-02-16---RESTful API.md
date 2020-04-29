---
title: RESTful API

date: "2020-02-16T20:49:10.169Z"
template: "post"
draft: false
slug: "2020_02_16"
category: "Daily"
tags:
  - "RESTfulAPI"
  - "Web Development"
description: "RESTful API"
socialImage: ""
---
### RESTful HTTP API 구조 및 핵심 개념

- URI(Uniform Resource Identifier)
해당 사이트의 특정 리소스의 위치를 나타내는 **유일한 주소**

- HTTP Method
HTTP request가 의도하는 action을 정의한 것 (POST, GET)

- Payload
HTTP request에서 보내는 데이터(body)


### REpresentational State Transfer
- 웹상에서 사용되는 여러 리소스를 HTTP URI로 표현하고 그 리소스에 대한 action을 HTTP Method로 정의하는 방식.

- "리소스(HTTP URI로 정의된)를 어떻게 한다(HTTP Method + Payload)"를 구조적으로 깔끔하게 표현하는 것.

- Method는 주로 GET과 POST를 사용

### RESTful API의 장점
- 그 자체만으로도 API의 목적이 쉽게 이해 됨. (self-descriptiveness)

### RESTful API를 개발할 때 유의할 점
- /(슬래시)는 계층관계를 나타낼 때 사용
- URI에 _(underscore)는 주로 포함하지 않고 영어 대문자보다 소문자를 사용.

참고 및 출처 : 위코드 은우님 세션
