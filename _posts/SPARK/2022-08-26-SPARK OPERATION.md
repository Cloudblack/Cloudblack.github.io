---
published: true
layout: single
title: SPARK OPERATION
categories: [SPARK]
tags:
  - SPARK OPERATION
  - Transformations
  - Actions
toc: true
toc_sticky: true
date created: 금요일, 8월 26일 2022
date modified: 금요일, 8월 26일 2022
---

<head>
  <style>
    table.dataframe {
      white-space: normal;
      width: 100%;
      height: 240px;
      display: block;
      overflow: auto;
      font-family: Arial, sans-serif;
      font-size: 0.9rem;
      line-height: 20px;
      text-align: center;
      border: 0px !important;
    }

    table.dataframe th {
      text-align: center;
      font-weight: bold;
      padding: 8px;
    }

    table.dataframe td {
      text-align: center;
      padding: 8px;
    }

    table.dataframe tr:hover {
      background: #b8d1f3; 
    }

    .output_prompt {
      overflow: auto;
      font-size: 0.9rem;
      line-height: 1.45;
      border-radius: 0.3rem;
      -webkit-overflow-scrolling: touch;
      padding: 0.8rem;
      margin-top: 0;
      margin-bottom: 15px;
      font: 1rem Consolas, "Liberation Mono", Menlo, Courier, monospace;
      color: $code-text-color;
      border: solid 1px $border-color;
      border-radius: 0.3rem;
      word-break: normal;
      white-space: pre;
    }

  .dataframe tbody tr th:only-of-type {  
      vertical-align: middle;  
  }

  .dataframe tbody tr th {  
      vertical-align: top;  
  }

  .dataframe thead th {  
      text-align: center !important;  
      padding: 8px;  
  }

  .page__content p {  
      margin: 0 0 0px !important;  
  }

  .page__content p > strong {  
    font-size: 0.8rem !important;  
  }

  </style>
</head>

## ipynb에서 spark연결  
그냥 ipynb에서 돌리게되면 spark를 찾지못해 에러가 나게된다.  

findspark를 이용해 spark를 맞춰주자

```python
import findspark
findspark.init()
```

### sparkcontext 설정  
spark를 사용하라면 sparkcontext 객체를 만들어야하는데 그전에 먼저 conf를 통해 설정을하자.  

setMaster('local')로 local환경에서 실행할거라는것과  

setAppname으로 이름을 지정한다.

```python
import pyspark
conf = pyspark.SparkConf().setMaster('local').setAppName("transformation_actions")
sc = pyspark.SparkContext(conf = conf)
```

현재 사용하는 설정들을 볼 수 있다.

```python
sc.getConf().getAll() 
```

<pre>
[('spark.master', 'local'),
 ('spark.driver.host', 'host.docker.internal'),
 ('spark.app.id', 'local-1661518189407'),
 ('spark.rdd.compress', 'True'),
 ('spark.serializer.objectStreamReset', '100'),
 ('spark.submit.pyFiles', ''),
 ('spark.driver.port', '6655'),
 ('spark.executor.id', 'driver'),
 ('spark.app.name', 'transformation_actions'),
 ('spark.submit.deployMode', 'client'),
 ('spark.ui.showConsoleProgress', 'true'),
 ('spark.app.startTime', '1661518189304')]
</pre>
sparkcontext는 하나밖에 만들 수 없기 때문에 필요에따라 종료한다.

```python
sc.stop()
```

종료했기때문에 다시 sc를 만든다.

```python
sc = pyspark.SparkContext(conf = conf)
```

## spark operation은 action과 transformation으로 왜 나누어졌을까?  
지연되는 연산이 유용한 경우가 있기 때문이다.  

메모리를 최대한 활용 할 수 있다.  

데이터를 다루는 task는 반복되는 경우가 많다.  

![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220826221514.png)  

만약 그냥 반복을 하게된다면 disk로 한번씩 들어가기떄문에 속도가 저하되게된다.  

그래서 조금 더 좋은 방식은  

![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220826221628.png)  

인메모리에 남겨서 태스크에서 태스크로 바로 넘어가는것인데  

어떤 데이터를 메모리에 남겨야 할지 알아야지 가능하다  

그래서 transformations은 지연 실행되게 때문에 어떤 데이터를 메모리에 저장해야하는지 알 수 있다.  

### Cache & Persist  
데이터를 메모리에 저장하고 싶을떄 사용이 가능하다

```python
categoryReviws = filtered_lines.map(parse).persist()
result1 = categoryReviws.take(10)
result2 = categoryRevies.mapValues(lambda x: (x,1)).collect()
```

categoryReviws라는 RDD가 두번 사용되는데 persist()로 메모리에 남겨두고 사용할 수 있다.

#### storage level  
메모리에 저장을 할때 여러 종류의 storage level이 존재한다  

1. MEMORY_ONLY - 메모리에만 저장

2. MEMORY_AND_DISK -메모리와 디스크 동시, 메모리에 데이터가없을경우 디스크까지 보겠다

3. MEMORY_ONLY_SER - SERIALIZER를 거쳐 용량을 아낀다 하지만 불러올때 다시 deserializer를 거치기때문에 연산이 추가된다.

4. MEMORY_AND_DISK_SER - 위와 마찬가지

5. DISK_ONLY - 디스크에만 저장

#### Cache  
- 디폴트 Storage level을 사용

- RDD : MEMORY_ONLY

- DF : MEMORY_AND_DISK

#### Persist  
- Storage level을 사용자가 원하는대로 지정 가능

## Actions  
- 결과값을 연산하여 출력하거나 저장

- Eager Execution 즉시 실행



> collect() 전부 가져와서 보여준다

> count() 갯수를 세준다

> first() 첫번째 데이터만 보여준다

> distinct() 중복을 제거한다

> countByValue() 값을 기준으로 세어준다

> take(n) n개만큼 보여준다

> top(n) 내림차순으로 정렬하고 상위 n개를 보여준다

> reduce  

> fold  

> foreach 요소를 하나하나 꺼내서 적용시킴 (워커에서 동작하고 드라이브에서는 볼 수 없음)



Actions를 알기에 앞서 RDD객체를 만들어준다.  

### parallelize
parallelize는 list를 가지고 객체를 생성한다.

```python
foods = sc.parallelize(['짜장면','마라탕','짬뽕','떡볶이','쌀국수','짬뽕','짜장면','짜장면','짜장면','라면','우동','라면'])
```

### collect  
RDD 객체안에 있는 데이터를 볼 수있다.  

개발 단계에서는 사용하지만 프로덕션 단계에서는 사용해선 안된다.  

왜냐면 전부를 가져오기 때문에 비용이 어마어마하고 스파크를 사용하는 이유가없어진다.

```python
foods.collect()
```

<pre>
['짜장면', '마라탕', '짬뽕', '떡볶이', '쌀국수', '짬뽕', '짜장면', '짜장면', '짜장면', '라면', '우동', '라면']
</pre>

### countByValue  
value 기준으로 숫자를 센다

```python
foods.countByValue()
```

<pre>
defaultdict(int,
            {'짜장면': 4,
             '마라탕': 1,
             '짬뽕': 2,
             '떡볶이': 1,
             '쌀국수': 1,
             '라면': 2,
             '우동': 1})
</pre>

### take  
take(숫자)로 원하는 만큼의 데이터를 반환한다.

```python
foods.take(4)
```

<pre>
['짜장면', '마라탕', '짬뽕', '떡볶이']
</pre>

### first  
첫번째 값을 반환한다.

```python
foods.first()
```

<pre>
'짜장면'
</pre>

### count  
데이터의 갯수를 센다.

```python
foods.count()
```

<pre>
</pre>

### distinct  
중복제거

```python
foods.distinct().collect()
```

<pre>
['짜장면', '마라탕', '짬뽕', '떡볶이', '쌀국수', '라면', '우동']
</pre>

```python
foods.distinct().count()
```

<pre>
7
</pre>

### foreach  
요소를 하나하나 꺼내서 적용시킴

```python
foods.foreach(lambda x:print(x))
#워커 노드에서만 실행되어 드라이브 프로그램에서는 볼 수 없다.
```

### top(숫자)  
내림차순으로 정렬후 정해진 숫자만큼 반환

```python
foods.top(4)
```

<pre>
['짬뽕', '짬뽕', '짜장면', '짜장면']
</pre>

## Transformations  
- 결과값으로 새로운 RDD를 반환

- Lazy execution 지연실행

- Narrow + Wide 두개로 나뉜다  



> map(f) 하나하나함수를 적용

> flatMap(f) 하나하나 함수를 적용하고 중첩리스트를 제거

> filter(f) 필터로 걸러낸다  

> distinct 중복을 제거

> reduceByKey  

> groupByKey(f) 그룹화한다

> mapValues  

> flatMapValues  

> sortByKey

### Narrow Transformations  
- 1:1 변환  

- filter,map,flatMap,sample.union  

- 1열을 조작하기 위해 다른 열/파티션의 데이터를 쓸 필요가없다 예를들어 정렬을 할 경우 다른 파티션을 참고해야한다

- 정렬이 필요하지 않은 경우

#### map(f)  
map은 하나하나 꺼내 함수를 하나하나 적용한다.

```python
sc.parallelize([1,2,3]).map(lambda x:x +2).collect()
```

<pre>
[3, 4, 5]
</pre>

#### flatMap(f)  
리스트의 요소를 펼쳐볼떄 사용한다 ( 이중리스트를 제거한다)

```python
movies = [
    '그린 북',
    '매트릭스',
    '토이 스토리',
    '캐스트 어웨이',
    '포드',
    '보헤미안 랩소디',
    '빽 투 더 퓨처',
    '반지의 제왕',
    '죽은 시인의 사회'
]
```

```python
moviesRDD = sc.parallelize(movies)
```

```python
flatMoives = moviesRDD.flatMap(lambda x:x.split(" "))
flatMoives.collect()
```

<pre>
['그린',
 '북',
 '매트릭스',
 '토이',
 '스토리',
 '캐스트',
 '어웨이',
 '포드',
 '보헤미안',
 '랩소디',
 '빽',
 '투',
 '더',
 '퓨처',
 '반지의',
 '제왕',
 '죽은',
 '시인의',
 '사회']
</pre>
그런데 map이랑 뭐가 다른걸까? 똑같은 코드를 map으로 돌려보자

```python
mapMoives = moviesRDD.map(lambda x:x.split(" "))
mapMoives.collect()
```

<pre>
[['그린', '북'],
 ['매트릭스'],
 ['토이', '스토리'],
 ['캐스트', '어웨이'],
 ['포드'],
 ['보헤미안', '랩소디'],
 ['빽', '투', '더', '퓨처'],
 ['반지의', '제왕'],
 ['죽은', '시인의', '사회']]
</pre>
map에서 split을 사용하면 이중 리스트가 되는데 flatmap은 이중리스트를 제거하면서 출력한다

#### filter(f)  
필터링을 할떄 사용한다

```python
filterMovies = flatMoives.filter(lambda x: x!='매트릭스')
filterMovies.collect()
```

<pre>
['그린',
 '북',
 '토이',
 '스토리',
 '캐스트',
 '어웨이',
 '포드',
 '보헤미안',
 '랩소디',
 '빽',
 '투',
 '더',
 '퓨처',
 '반지의',
 '제왕',
 '죽은',
 '시인의',
 '사회']
</pre>

#### intersection  
교집합

```python
num1 = sc.parallelize([1,2,3,4])
num2 = sc.parallelize([4,5,6,7,8,9,10])
```

```python
num1.intersection(num2).collect()
```

<pre>
[4]
</pre>

#### union  
합집합

```python
numUnion = num1.union(num2)
numUnion.collect()
```

<pre>
[1, 2, 3, 4, 4, 5, 6, 7, 8, 9, 10]
</pre>

#### subtract  
차집합

```python
num1.subtract(num2).collect()
```

<pre>
[2, 1, 3]
</pre>

#### sample  
랜덤으로 샘플을 뽑음

첫번째 인자는 한번 뽑은 값을 다시 넣을지 결정한다 (True시 다시넣음)  

두번째 인자는 얼마나 뽑을것인가이다  

그리고 랜덤 시드값을 넣을 수 있다.

```python
numUnion.sample(True,.5, seed = 2).collect()
```

<pre>
[1, 2, 4, 5]
</pre>

### Wide Transformations  
- Shuffling 하는 특징

- interection and join, distince, cartesian, reduceByKey,groupByKey

- 아웃풋 RDD의 파티션에 다른파티션의 데이터가 들어갈 수 있다.  

![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220826210811.png)

#### groupBy  
그룹화한다

```python
foodsGroup = foods.groupBy(lambda x:x[0])
```

```python
res = foodsGroup.collect()
res
```

<pre>
[('짜', <pyspark.resultiterable.ResultIterable at 0x23c6db74d60>),
 ('마', <pyspark.resultiterable.ResultIterable at 0x23c6dca1c40>),
 ('짬', <pyspark.resultiterable.ResultIterable at 0x23c6e5bda60>),
 ('떡', <pyspark.resultiterable.ResultIterable at 0x23c6d9025e0>),
 ('쌀', <pyspark.resultiterable.ResultIterable at 0x23c6d8186a0>),
 ('라', <pyspark.resultiterable.ResultIterable at 0x23c6d818a30>),
 ('우', <pyspark.resultiterable.ResultIterable at 0x23c6e58c190>)]
</pre>

```python
for (k,v) in res:
    print(k , list(v))
```

<pre>
짜 ['짜장면', '짜장면', '짜장면', '짜장면']
마 ['마라탕']
짬 ['짬뽕', '짬뽕']
떡 ['떡볶이']
쌀 ['쌀국수']
라 ['라면', '라면']
우 ['우동']
</pre>

```python
nums = sc.parallelize([1,2,3,4,5,6,7,8,9,10])
nums_res = nums.groupBy(lambda x: x%2).collect()
nums_res
```

<pre>
[(1, <pyspark.resultiterable.ResultIterable at 0x23c6e5e6340>),
 (0, <pyspark.resultiterable.ResultIterable at 0x23c6e5e9d30>)]
</pre>

```python
list(nums_res[0][1])
```

<pre>
[1, 3, 5, 7, 9]
</pre>
