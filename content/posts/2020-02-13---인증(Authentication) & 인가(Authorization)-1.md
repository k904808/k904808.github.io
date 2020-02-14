---
title: 인증(Authentication) & 인가(Authorization)-1

date: "2020-02-13T23:51:33.169Z"
template: "post"
draft: false
slug: "2020_02_13"
category: "Daily"
tags:
  - "Authorization"
  - "Authentication"
  - "Web Development"
description: "인증(Authentication) & 인가(Authorization)-1"
socialImage: ""
---
인증(Authentication)
유저의 아이디와 패스워드를 확인하는 절차.

-회원가입
유저 아이디와 패스워드 생성
유저 패스워드 암호화해서 DB 저장

-로그인
아이디와 패스워드를 입력
유저가 입력한 패스워드와 DB에 저장된 암호화한 패스워드 비교
일치하면 로그인 성공

-access token
로그인에 성공하면 access token을 클라이언트에게 전송
유저는 로그인 성공 후부터 request에 access token을 첨부해서 서버에 전송
<br>(매번 로그인 하지 않기 위함.)

패스워드 암호화
DB 해킹이나, 내부 인력이 유저의 패스워드이 있을 수 있으므로 패스워드는 반드시 암호화해서 저장해야함.

단방향 암호화 : 복호화가 어려움
양방향 암호화 : 대칭키 알고리즘 적용, 복호화 (다시 풀어서 보기)는 편함.  ex. 주민등록번호

암호화는 오픈소스 라이브러리 bcrypt 사용

<암호화 한 뒤 DB 저장>
str - 인코딩- bytes - 해싱 - salting - (해싱 12번 반복) - 디코딩 -str 상태로 DB에 저장

```
>>> password = '1234'
>>> a = password.encode()
>>> print(a)
b'1234'
>>> b = bcrypt.hashpw(a, bcrypt.gensalt())
>>> print(b)
b'$2b$12$cX1nZKeM2prdi5mAs8pzzu6BJshHinfOypMmrbrWoY9N8RnmVTjmW'
>>> c = b.decode()
>>> print(c)
$2b$12$cX1nZKeM2prdi5mAs8pzzu6BJshHinfOypMmrbrWoY9N8RnmVTjmW
```
<DB에 저장된 데이터와 유저가 입력한 패스워드 비교>
```
>>> d = '1234' #유저가 입력한 패스워드
>>> bcrypt.checkpw(d.encode('utf-8'),c) #둘다 bytes 상태가 아니면 오류 발생하므로 주의!
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/Users/kay/miniconda3/envs/auth/lib/python3.8/site-packages/bcrypt/__init__.py", line 100, in checkpw
    raise TypeError("Unicode-objects must be encoded before checking")
TypeError: Unicode-objects must be encoded before checking
>>> bcrypt.checkpw(d.encode('utf-8'),c.encode())
True #DB에 저장된 패스워드와 유저가 입력한 패스워드가 같으면 True 반환
>>> print(c.encode())
b'$2b$12$cX1nZKeM2prdi5mAs8pzzu6BJshHinfOypMmrbrWoY9N8RnmVTjmW'
>>> print(d.encode())
b'1234'
>>> c
```
