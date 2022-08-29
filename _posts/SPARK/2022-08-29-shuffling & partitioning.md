---
published: true
layout: single
title: shuffling & partitioning
categories: [SPARK]
tags:
  - shuffling
  - partitioning
toc: true
toc_sticky: true
date created: 월요일, 8월 29일 2022
date modified: 월요일, 8월 29일 2022
---

# Shuffling
- 그룹핑시 데이터를 한 노드에서 다른 노드로 옮길때
- 성능으 많이 저하시킨다
- 결과로 나오는 RDD가 원본 RDD의 다른 요소를 참조하거나  
  다른 RDD를 참조할때 발생한다

ex) groupByKey를 할때  
![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220829160350.png)

## Shuffle을 일으킬 수 있는 작업들
- joins
- groupbykey
- reducebykey
- comebinebykey
- distinct
- intersection
- repartition
- coalesce

### GroupByKeys + Reduce
![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220829160714.png)

groupbykey로 먼저 키를 모으기 때문에 셔플링이 많이 일어나게된다

### Reducebykey
![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220829160929.png)

파티션별로 먼저 리듀스를 해주고 키를 기준으로 셔플링을 하기때문에 groupby를 먼저 하던 것 보다 셔플링이 덜 일어나게된다.

### 셔플링을 최소화 하려면??
- 미리 파티션을 만들어 두고 캐싱 후 reduceBykey를 실행
- 미리 파티션을 만들어 두고 캐싱 후 join실행
- 둘다 파티션과 캐싱을 조합해서 최대한 로컬 환경에서 연산이 실행되도록 하는 방식

셔플을 최소화 해서 10배의 성능 향상이 가능하다

# Partition
- 데이터를 최대한 균일하게 퍼트리고  
  쿼리가 같이 되는 데이터를 최대한 옆에 두어  
  검색 성능을 향상시키는 것

### 특징
- RDD는 쪼개져서 여러 파티션에 저장됨
- 하나의 파티션은 하나의 노드(서버)에
- 하나의 노드는 여러개의 파티션을 가질 수 있음
- 파티션의 크기와 배치는 자유롭게 설정 가능하며 성능에 큰 영향을 미침
- Key-Value RDD를 사용할때만 의미가 있다.

<mark style="background: #FF5582A6;">스파크의 파티셔닝 == 일반 프로그래밍에서 자료구조를 선택하는 것</mark>

### 종류

#### Hash Partithioning
- 데이터를 여러 파티션에 균일하게 분배하는 방식  
![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220829162501.png)

- hash partitioning의 잘못된 예  
![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220829162543.png)

#### Range Partitioning
- 순서가 있는, 정렬된 파티셔닝
	- 키의 순서에 따라
	- 키의 집합의 순서에 따라

서비스의 쿼리 패턴이 날짜 위주면  
일별 Range Partition 고려  
![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220829162653.png)

### Memory & Disk Partition

#### 디스크에서 파티션하기
- <mark style="background: #FF5582A6;">partitionBy()</mark> 자주사용하게될듯
- 파티션을 만든 후에 persist()를 하지않으면
	- 다음 연산에 불릴떄마다 반복하게된다 (셔플링이 반복됨)

``` python
pairs = sc.parallelize([1,2,3,4,2,4,1]).map(lambda x: (x, x))
pairs.collect()
```

[(1,1),(2,2),(3,3),(4,4),(2,2),(4,4),(1,1)]

``` python
pairs.partitionBy(2).glom().collect() #glom은 파티션까지 보여주는 함수
```

[ [(2,2),(4,4),(2,2),(4,4) ],[(1,1),(3,3),(1,1)] ]  
파티션을 두개로 지정해서 나눈다

``` python
pairs.partitionBy(2, lambda x: x%2).glom().collect()
```

[ [(2,2),(4,4), (2,2), (4,4)], [(1,1), (3,3), (1,1 )]]  
파티션을 나눌때 어떻게 나눌지 함수를 통해 나눈다

#### 메모리에 파티션하기
둘다 shuffling을 동반하여 매우 비싼 작업
- repartition()
	- 파티션의 크기를 줄이거나 늘리는 사용
- coalesce()
	- 파티션의 크기를 줄이는데 사용

### 연산중에 파티션을 만드는 작업들
- groupByKey
- reduceByKey
- foldByKey
- PartitionBy
- Sort
- mapValues(parent)
- flatMapValues(parent)
	- map과 flatmap은 key의 변형이 가능하기때문에 파티션이 잘 정의되어있다면 ~values 를 쓰는게 도움이 된다.
- filter(parent)
- Joins
	- inner join
	- outer join
- 등등
