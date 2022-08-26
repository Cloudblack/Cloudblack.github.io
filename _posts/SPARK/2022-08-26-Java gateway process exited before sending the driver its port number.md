---
published: true
layout: single
title: Java gateway process exited before sending the driver its port number
categories: [SPARK]
tags:
  - error
toc: true
toc_sticky: true
date created: 금요일, 8월 26일 2022
date modified: 금요일, 8월 26일 2022
---

``` python
from pyspark import SparkConf, SparkContext

conf = SparkConf().setMaster("Local").setAppName('category-review-average')

sc = SparkContext(conf=conf)
```

위 코드를 실행시킬때 에러가 나게된다.  
구글에선 Java관련해서 문제를 해결하는데  
어제까지 되던데 안되서 유심히 살펴보니  
setMaster의 Local을 local로 바꾸니까 정상적으로 동작한다.  
아직 정확한 동작원리는 모르나 대소문자를 구분하지 않게 하는 기능이 없는 것으로 추정된다.  
