---
title: Git과 Github

date: "2020-02-12T19:21:34.169Z"
template: "post"
draft: false
slug: "2020_02_12"
category: "Daily"
tags:
  - "git"
  - "github"
  - "Web Development"
description: "깃과 깃허브, 브랜치 관련 개념 정리"
socialImage: ""
---
### Git과 Githhub

#### Git : Version Control System
- 코드의 변경사항 기록, 관리
- 필요시 이전 상태로 rollback 할 수 있음
- 팀단위 개발 시 체계적, 효과적 협업

#### Distributed Version Control System : 분산 버전 관리 시스템
- 중앙서버 뿐만 아니라 각 개발자의 컴퓨터에도 최신 버전의 코드, 수정사항 내역, meta 정보를 전부 가지고있는 방식.

#### Github : Git의 중앙서버
❗️모든 작업은 local(내 pc)에서 일어남.
<br>
❗️문제가 생겨도 내 pc에서 생김. conflict도 내 pc에서만 생김. (다른 개발자들에게 영향 X)

- clone : 처음 작업을 시작할 때 다운로드
- pull : 최신 코드를 다운로드
- push : 내 코드를 업로드

#### Local repository
![](https://images.velog.io/images/k904808/post/de304989-138e-44d1-b816-e0e38762a0d6/image.png)
이미지 출처 : https://neurathsboat.blog/post/git-intro/

⚠️ commit, push 하기 전에 파일을 제대로 올렸는지, 코드가 제대로 돌아가는지 반드시 확인 필요.
> ```$git diff``` / ```$git status``` 로 확인하고 커밋 해야함.


#### Git Brach의 종류
>Gitflow에서는 항상 유지되는 메인 브랜치(master, develop)과 일정기간 동안만 유지되는 보조 브랜치(feature, release, hotfix) 총 5가지가 있다.

![](https://images.velog.io/images/k904808/post/436df1ec-5dd5-4e88-b77d-5917fc18d898/image.png)

- master : 배포(release)이력을 관리하기 위해 사용. 배포가능한 상태만 관리.

- develop : 기능 개발을 위한 브랜치들을 병합하기 위해 사용. 모든기능이 추가되고 버그가 수정되어 배포가능한 안정적 상태라면 develop 브랜치를 master 브랜치에 병합. 평소에는 이 브랜치를 기반으로 개발을 진행한다.

- feature : 새로운 기능 개발, 버그 수정이 필요할 때마다 'develop' 브랜치로부터 분기. feature 브랜치의 작업은 기본적으로 공유 필요 없기 때문에 로컬 저장소에서 관리. 개발이 완료되면 'develop' 브랜치로 병합하여 다른 사람들과 공유.

- release : 이번 출시 버전을 준비하는 배포 전용 브랜치. 배포 준비가 완료되면 master 브랜치에 병합. 배포 완료 후 develop 브랜치에도 병합. (release-RB_* 또는 release-* 또는 release/* 처럼 이름 짓는 것이 일반적인 관례)

- hotfix : 배포한 버전에 긴급하게 수정을 해야할 필요가 있을 경우, master 브랜치에서 분기. 바로 배포가 가능한 mater 브랜치에서 직접 브랜치를 만들어 필요한 부분만 수정한 후 다시 master 브랜치에 병합하여 배포.

이미지 출처 및 참고 : https://gmlwjd9405.github.io/2018/05/11/types-of-git-branch.html
