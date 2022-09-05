---
published: true
layout: single
title: Structured vs Unstructured Data
categories: [SPARK]
tags:
  - Structured
  - Unstructured
toc: true
toc_sticky: true
date created: 수요일, 8월 31일 2022
date modified: 월요일, 9월 5일 2022
---

# 데이터를 합치고 추출하기
![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220831220342.png)

미국의 2000불 이상의 주식만 가져오기  
가능한 방법은 몇가지일까??  
![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220831220409.png)  
성능은 2번이 더좋다.  
그런데 매번 이렇게 뭐가 더좋을지 고민하면서 코딩해야하나?  
데이터가 구조화되어있다면 자동으로 최적화 된다.

## Unstructured
<mark style="background: #FF5582A6;">Free form</mark>
- 로그파일
- 이미지

## Semi Structured
<mark style="background: #FF5582A6;">행과 열</mark>
- CSV
- JSON
- XML

## Structured
<mark style="background: #FF5582A6;">행과열 + 데이터 타입(스키마)</mark>
- 데이터베이스

## RDDs vs Structured Data

### RDD에서는
- 데이터의 구조를 모르기때문에 데이터를 다루는 것을 개발자에게 의존
- map, flatmap, filter등을 통해 유저가 만든 function을 수행

### Structured Data에선
- 데이터의 구조를 이미 알고있으므로 어떤 태스크를 수행할것인지만 정의하면된다.
- 최적화도 자동으로 할 수 있다.

#### Spark sql은 구조화된 데이터를 다룰 수 있게 해준다.
- 유저가 일일이 function을 정의하는 일 없이 작업을 수행 할 수 있다.(sql문을 사용)
- 자동으로 연산이 최적화된다.
