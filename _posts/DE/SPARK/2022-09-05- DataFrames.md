---
published: true
layout: single
title:  DataFrames
categories: [SPARK]
tags:
  - 
  -  DataFrames
toc: true
toc_sticky: true
date created: 월요일, 9월 5일 2022
date modified: 월요일, 9월 5일 2022
---

# DataFrames
- Dataframe은 관계형 데이터셋으로 RDD + Relation
- RDD가 함수형 API를 가졌다면 DataFrame은 선언형 API
- 자동으로 최적화가 가능
- 타입이없다.(df가 타입을 강제하지않는다)

## DataFrame의 특징
- RDD의 확장판
- 지연실행 (Lazy Execution)
- 분산 저장
- Immutable

- Row 객체가있다
- SQL 쿼리를 실행할 수 있다
- 스키마를 가질 수 있고 이를 통해 성능을 더욱 최적화 할 수 있다.
- CSV, JSON, Hive 등으로 읽어오거나 변환이 가능하다.

## 스키마를 확인하는 법
- dtypes  
  ![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220905165822.png)
- show()
  - 테이블 형태로 데이터를 출력
  - 첫 20개의 열만 보여줌  
  ![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220905165840.png)
- printSchema()
	- 스키마를 트리 형태로 보여줌  
	  ![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220905165933.png)

## DataFrame Operations
SQL과 비슷한 작업이 가능하다
- Select  
  ![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220905170146.png)
- Agg  
  Aggregate 그룹핑 후 데이터를 하나로 합치는 작업  
  ![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220905170227.png)

- Where
- Limit
- OrdeBy
- GroupBy  
  ![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220905170333.png)

- Join  
  ![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220905170358.png)
