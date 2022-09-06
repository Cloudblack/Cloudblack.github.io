---
published: true
layout: single
title: Key Value RDD
categories: [SPARK]
tags:
  - Key Value RDD
toc: true
toc_sticky: true
date created: 토요일, 8월 27일 2022
date modified: 월요일, 8월 29일 2022
---

# Key Value RDD Operations
- groupByKey
- reduceByKey
- mapValues
- keys
- countByValue
- Joins
	- inner join
	- outer join
- 등등

## Transformations

### GroupByKey
- groupBy(f,numPartitions = None, partitionFunc = )  
  주어진 함수를 기준으로 Group화 한다

``` python
rdd = sc.parallelize([1,1,2,3,5,8])
result = rdd.groupBy(lambda x: x%2).collect()
sorted([(x,sorted(y)) for (x,y) in result])
```

[(0,[2,8]), (1, [1,1,3,5])]

- <mark style="background: #FF5582A6;">groupByKey</mark> (numPartitions = None, partitionFunc = )  
  주어지는 Key를 기준으로 Group화 한다

``` python
rdd = sc.parallelize([("a",1),("b",1),("a",1)])
sroted(rdd.groupByKey().mapValues(len).collect())
```

[('a',2), ('b',1)]

``` python
rdd = sc.parallelize([("a",1),("b",1),("a",1)])
sroted(rdd.groupByKey().mapValues(list).collect())
```

[('a',[1,1]),('b',[1])]

### reduceByKey
- reduce(f)  
  주어지는 함수를 기준으로 요소들을 합침 (<mark style="background: #FF5582A6;">action</mark> )
  
  ``` python
  
  
  
  
  
  
sc.parallelize([1,2,3,4,5]).reduce(add)

```
15

- <mark style="background: #FF5582A6;">reduceByKey</mark> (f,numPartitions=None, partitionFunc = )
  Key를 기준으로 그룹을 만들고 합침(<mark style="background: #FF5582A6;">Trans</mark> )
  ``` python
rdd = sc.parallelize([("a",1),("b",1),("a",1)])
sorted(rdd.reduceByKey(add).collect())
```

[('a',2),('b',1)]

개념적으로 groupByKey +reduction  
하지만 GroupByKey보다 훨씬 빠르다

### mapValues
- 함수를 밸류에만 적용한다, 파티션과 키는 그대로

``` python
x = sc.parallelize([("a",["apple","bana","lemon"]), ("b",["grapes"])])
def f(x): return len(x)
x.mapValues(f).collect()
```

[('a',3),('b',1)]

### keys
- 모든 키를 가진 RDD를 생성

``` python
m = sc.parallelize([(1,2),(3,4)]).keys()
m.collect()
```

[1,3]

### join(+ leftOuterJoin , rightOuterJoin)
- 여러개의 RDD를 합치는데 사용  
![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220829153730.png)

- innerjoin  
  교집합
- outerjoin  
  기준쪽 데이터는 전부 출력하고 반대쪽에 데이터가 없는 경우 None을 출력  
  ![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220829155554.png)
- full outer join = union  
![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220829155735.png)


대부분의 key value rdd에 적용되는 operation이 transformations인 경우가 많다  
key value rdd로 처리되는 값들이 파티션이 유지가 안되더라도 굉장히 값이 큰경우 가 많기때문이다.

## Actions

### countByKey
- 각 키가 가진 요소들을 센다

``` python
rdd = sc.parallelize([("a",1),("b",1),("a",1)])
sorted(rdd.countByKey().items())
[('a',2),('b',1)]

```
