---
title: Django X MySQL

date: "2020-02-17T23:49:10.169Z"
template: "post"
draft: false
slug: "2020_02_17"
category: "Daily"
tags:
  - "Django"
  - "MySQL"
  - "Web Development"
description: "Django X MySQL"
socialImage: ""
---
## Django DB sqlite3 -> MySQL 바꾸기
#### 가상환경 활성화, django 설치 후 mysqlclient 설치
Django DB에 MySQL을 바로 붙이면 안 붙기 때문에, mysqlclient를 먼저 설치
```$pip install mysqlclient```

#### MySQL 설치 후 DB 생성
설치 및 기본 설정은 구글링으로 자료를 찾아보기
아래 명령어로 name 이라는 데이터베이스(스키마) 생성
```create database name character set utf8mb4 collate utf8mb4_general_ci;```
❗️utf8 은 emoji 지원 안함. utf8mb4 사용 권장

잘 생성되었는지 데이터베이스 목록을 보려면,
```show databases;```

name 이라는 데이터베이스를 사용하려면,
```use name;```

❗️맨 끝에 ;(세미콜론)을 잊지 말고 붙이기.


#### my_settings.py 파일생성 및 정보입력
![](https://images.velog.io/images/k904808/post/d512118c-4bb8-492a-801f-b0240284f719/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202020-02-17%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%2010.40.00.png)
위의 tree 이미지와 같이 django 프로젝트 디렉토리 안에서 manage.py가 있는 디렉토리에 my_settings.py 파일을 생성. (네이밍은 my_settings.py 등으로 변경해도 무관)

my_setting.py에 아래와 같이 DB 정보 입력
```
DATABASES = {
    'default' : {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': '#데이터베이스 이름',
        'USER': '#유저(root)',
        'PASSWORD': '#패스워드',     
        'HOST': 'localhost',
        'PORT': '3306',
    }
}
#mysql 초기설정에서 비밀번호를 입력 안하도록 설정해두었으면 패스워드 부분을 비워두어야 에러없이 진행된다.
```

#### settings.py 수정
my_setting를 import,
```import my_settings```

기존 database 부분을 삭제한 뒤 my_settings.py 파일 안에 있는 DATABASE 설정을 참조하도록,
```DATABASES = my_settings.DATABASES```

입력 후 저장하면 끝.

migrate 와 runserver가 정상적으로 이루어지고, sql 안에 데이터 테이블이 잘 생성되면 성공쓰.

➕DEBUG = FALSE/ ALLOWED_HOST = [*] 혹은 한국 IP만..

### 실제 배포하기 전 프로젝트 설정
.gitignore 를 이용해서 유저의 DB정보와 password 등이 들어있는 my_settings.py를 git에 업로드 되지 않도록 관리해주어야 한다.
진짜 끝.
