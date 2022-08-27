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
date modified: 토요일, 8월 27일 2022
---

# Key Value RDD

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

- groupByKey(numPartitions = None, partitionFunc = )  
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
- reduceByKey
- mapValues
- keys
- join(+ leftOuterJoin , rightOuterJoin)

대부분의 key value rdd에 적용되는 operation이 transformations인 경우가 많다  
key value rdd로 처리되는 값들이 파티션이 유지가 안되더라도 굉장히 값이 큰경우 가 많기때문이다.

## Actions
- countByKey
