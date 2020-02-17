---
title: 인증(Authentication) & 인가(Authorization)-2

date: "2020-02-14T20:43:51.169Z"
template: "post"
draft: false
slug: "2020_02_14"
category: "Daily"
tags:
  - "Authorization"
  - "Authentication"
  - "Web Development"
description: "인증(Authentication) & 인가(Authorization)-2"
socialImage: ""
---
JWT(JSON Web Tokens)
유저가 로그인에 성공하면 access token 이라는 암호화된 유저 정보를 첨부해서 request를 보낸다.

```
HTTP/1.1 200 OK
Content-Type: application/json

{
    "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZGVudGl0eSI6MSwiaWF0IjoxNDQ0OTE3NjQwLCJuYmYiOjE0NDQ5MTc2NDAsImV4cCI6MTQ0NDkxNzk0MH0.KPmI6WSjRjlpzecPvs3q_T3cJQvAgJvaQAPtk1abC_E"
}
```
서버에서는 access token을 복호화해서 해당 유저정보를 얻게된다.<br>
이러한 절차의 목적은 해당 유저가 요청할 때마다 로그인하지 않아도 되도록 하는 것.<br>
access token을 생성하는 방법은 여러가지가 있는데, 그중 이번에 다루는 것은 JWT이다.

```
>>> import jwt
>>> jwt.encode({'user_id': 1}, 'wecode', algorithm = 'HS256')
b'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyX2lkIjoxfQ.DHk2kqJnk-mJg-7xcN4NwkaFJRUh01K3vY2V6g8o3bE'
>>> token = jwt.encode({'user_id': 1}, 'wecode', algorithm = 'HS256')
>>> jwt.decode(token, 'wecode', algorithm = 'HS256')
{'user_id': 1}
>>> token = jwt.encode({'user_id': 1}, 'wecode', algorithm = 'HS512')
>>> print(token)
b'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzUxMiJ9.eyJ1c2VyX2lkIjoxfQ.ZacrrpzNICXDuHinVYF6aPT5QjaH_zAbH7ihSSUDrMwCUBd1FdxLql5CFWSXt5BNC6P4APTUn-0BrDUowoSqjw'
```
