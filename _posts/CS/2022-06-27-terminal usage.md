---
published: true
layout: single
title: "linux 터미널 명령어 모음"
categories: [CS]
tags:
  - [linux]
toc: true
toc_sticky: true
date created: 월요일, 6월 27일 2022
date modified: 목요일, 9월 1일 2022
---

# linux 터미널 명령어 모음

# 디렉토리 관련 명령어

## 디렉토리 목록 확인
```
$ ls`
`$ ls -al` : 감춰진 파일은 .이 붙는다. a 옵션을 사용하면 해당 파일을 확인할 수 있다.
`$ ls -l
```

## 새 디렉토리 생성
`$ mkdir [디렉토리명]`  
`$ mkdir -p [디렉토리명/디렉토리명/디렉토리명…]` : 여러 디렉토리 생성

## 디렉토리 이동
`$ cd [디렉토리명]`  
`$ cd ..` : 부모 디렉토리로 이동

tip) 디렉토리명이 너무 길 때, 조금만 쓰고 tab키 누르면 자동완성

## 디렉토리 삭제
- `$ rm -r [디렉토리명]`

    -r (remove directories and their contents recursively; 해당 디렉토리 아래 있는 내용들도 삭제한다.)

# 파일 관련 명령어

## 비어있는 파일 생성
```
$ touch [파일명]
```

## 파일 삭제
```
$ rm [파일명]
```

## 파일 복사
```
$ cp [파일위치 및 파일이름] [목적지 파일위치 및 파일 이름]
```

## 파일 이동 (파일 이름을 바꿀 때에도 사용)
```
$ mv [파일위치 및 파일이름] [목적지 파일위치 및 파일 이름]
$ mv [원래 파일 이름] [바꾸고 싶은 파일 이름]
```

## 파일 만들고 편집 (nano 에디터)
`$ nano [파일명]` : 새 파일 작성 or 존재하는 파일 수정

## 파일 내용 보기
```
$ cat [파일명]
```

## 파일 위치 검색
- `$ locate *.log` : (확장자가 .log인 파일 찾기)

    디렉토리를 뒤지는게 아니라 데이터베이스(mlocate)를 뒤져서 찾는다.

`$ find . *.log` : 디렉토리 뒤짐

- `$ whereis ls`

- `$ whereis rm`

    실행파일 위치 찾기

# 현재 위치 확인
```
$ pwd
```

# 명령창 내용 삭제
```
$ clear
```

# 명령어 도움말 확인
`$ [명령어] --help` `$ man [명령어]` : /[찾고싶은단어] 사용해서 단어찾기 가능, 그 상태로 n을 누르면 다음 단어 찾기

# 패키지 매니저 (Package Manager)
- 기본으로 내장되어 있는 패키지(프로그램)가 아닌 새로운 패키지(프로그램)를 설치하려고 할 때 도와주는 소프트웨어 (안드로이드의 구글플레이, iOS의 앱스토어 같은 ..)
- apt, yum 등이 있음.

## 패키지 목록 업데이트
```
$ apt-get update
```

- 패키지 매니저를 통해 설치할 수 있는 패키지 목록들을 업데이트한다. (설치하기전에)
- 패키지가 설치되는게 아니라 패키지 목록들이 업데이트 되는 것.

## 패키지 찾기
```
$ apt-cache search [패키지명]
```

- 저장된 패키지 목록 중에 해당 패키지 찾기..?
- 관련된 패키지 목록까지 나온다.

## 패키지 설치
```
$ apt-get install [패키지명]
```

## 패키지 업그레이드
```
$ apt-get upgrade` `$ apt-get upgrade [패키지명]
```

## 패키지 삭제
```
$ apt-get remove [패키지명]
```

# 패키지를 설치하는 순서 (항상 이 순서를 따르는게 좋음.)
1. 패키지 목록 업데이트 (apt-get update)
2. 패키지 설치 (apt-get install)

# 다운로드

## 파일을 다운로드 (wget 사용)
```
$ wget -O [저장할 파일명] [다운로드 url]
```

## 소스코드 다운로드 (git 사용)
\1. git 설치  
`$ apt-get install git` 2. 소스코드 다운  
`$ git clone [소스코드 url] [디렉토리명] : 명시한 디렉토리에 소스코드 다운받는다.`
