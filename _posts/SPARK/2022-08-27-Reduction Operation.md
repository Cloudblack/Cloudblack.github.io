---
published: true
layout: single
title: Reduction Operation
categories:
  - SPARK
tags:
  - Reduction Operation

toc: true
toc_sticky: true

---

# Reduction 
- 절약? 감소시킨다는 뜻
- <mark style="background: #FF5582A6;">요소들을 모아서 하나로 합치는 작업</mark> 
- 많은 spark의 연산들이 reduction

## 대부분의 <mark style="background: #FF5582A6;">action은 Reduction이다</mark> 

근접하는 요소들을 모아서 하나의 결과로 만드는 일을한다
- 물론 파일저장이나 collect()등과 같이 reduction이 아닌 액션도있다.

## Parallel Reduction
### <mark style="background: #ADCCFFA6;">병렬처리가 가능한 경우</mark> 
![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220827162034.png)
각 파티션의 태스크는 독립적이어야한다
### 병렬처리가 힘든 경우
![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220827162134.png)
태스크가 이전태스크의 결과값에 의존하는 경우 
이전태스크를 기다려야하기때문에 굳이 병렬처리를 할 필요도없다

### 대표적인 Reduction Actoins
#### Reduce
- RDD.reduce(f)
``` python
from operator import add
sc.parallelize([1,2,3,4,5]).reduce(add)
```
15

하지만 파티션이 들어가는 경우 헷갈리게된다.
![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220827162529.png)

- [1,2,3,4]의 값이 하나의파티션에 있는 경우
	- `((1*2+2)*2+3)*2+4=26`
- [1,2],[3,4]로 파티션이 나뉜경우
	- `((1*2+2)*2+(3*2)+4 = 18`

이렇게 파티션이 어떻게 나뉠지 프로그래머가 정확하게 알기 어렵다.
그래서 연산의 순서와 상관없이 결과값을 보장하려면
- 교환법칙(`a*b = b*a`)
- 결합법칙`(a*b)*c = a*(b*c)
교환법칙과 결합법칙이 성립되게 신경써서 코딩을 해야한다

#### Fold
Reduce와 비슷하나 zerovalue(초기값)가 들어간다
- RDD.fold(zerovalue,f)
``` python
from operator import add
sc.parallelize([1,2,3,4,5]).fold(0,add)
```
15

그런데 실제 코드를 돌려보면 reduce와 비슷하면서도 다른 결과를 갖고오게되는데

``` python
rdd = sc.parallelize([2,3,4],4)
rdd.reduce(lambda x,y: x*y)
# (2*3*4) = 24
rdd.fold(1,lambda x,y: x*y)
# (1*2*3*4) = 24
```
reduce의 초기값은 0
fold의 초기값은 1인데 둘다 같은 24가 나오게된다
만약 fold의 초기값이 0이라면 0을 출력하게된다

``` python
rdd.reduce(lambda x,y: x+y)
# 0+2+3+4 = 9
rdd.fold(1,lambda x,y: x+y)
# (1+1) + (1+2) + (1+3) + (1+4) = 14
```
각 파티션의 시작값이 1이기때문에 이런 문제가 발생한다.

이런 부분을 잘 생각하면서 코딩을 해야겠다

#### GroupBy
함수를 기준으로 그룹화해준다
- RDD.groupBy(f)
``` python
rdd = sc.parallelize([1,1,2,3,5,8])
result = rdd.groupBy(lambda x: x%2).collect()
sorted([(x,sorted(y)) for (x,y) in result])
```
[(0,[2,8]), (1, [1,1,3,5])]

#### Aggregate
- RDD데이터 타입과 Action결과 타입이 다를 경우 사용
- 파티션 단위의 연산 결과를 합치는 과정을 거친다.
- RDD.aggregate(<mark style="background: #FF5582A6;">zeroValue</mark> ,<mark style="background: #FFB86CA6;">seqOp</mark> ,<mark style="background: #FFF3A3A6;">combOp</mark> )
	- <mark style="background: #FF5582A6;">zerovalue</mark>  각 파티션에서 누적할 시작 값
	- <mark style="background: #FFB86CA6;">seqOp</mark>  타입 변경 함수
	- <mark style="background: #FFF3A3A6;">combOp</mark> 합치는 함수

``` python
seqOp = (lambda x, y: (x[0] + y,x[1] +1))
combOp = (lambda x,y: (x[0] + y[0],x[1]+y[1]))
sc.parallelize([1,2,3,4]).aggregate((0,0),seqOp,combOp)
```
(10,4)
![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220827165523.png)
![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220827165533.png)

많이 쓰이는 reduction action이다
대부분의 데이터 작업은 크고 복잡한 데이터 타입 => 정제된 데이터하기 떄문
