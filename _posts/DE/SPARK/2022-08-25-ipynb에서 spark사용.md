---
published: true
layout: single
title: ipynb에서 spark사용 + vsc ipynb
categories:
  - SPARK
tags:
  - error

toc: true
toc_sticky: true

---
[출처](https://changhsinlee.com/install-pyspark-windows-jupyter/)

.py에서는 잘돌아가는 코드가  
ipynb에서는 돌아가지않는다는 큰 문제가생겼다.  
오류메세지는 pyspark에 T라는 기능이없다는데 검색해도 찾을 수 없었고  
ipynb를 jupyter에서 사용하는법을 찾아 프로필도 추가해보고 여러가질 해봤지만 아무것도 되지않았다.  
위에 걸은 링크도 별 효과가없어 지나쳤었는데 문득 갑자기  
순서의 문제가 아닐까 싶어졌다.  

결론적으로  
``` python
import pyspark
from pyspark import SparkConf,SparkContext

import pandas as pd

import findspark
findspark.init()
```

이던 코드를 

``` python
import findspark
findspark.init()

import pyspark
from pyspark import SparkConf,SparkContext

import pandas as pd
```

이렇게 바꿨더니 잘 돌아간다.  
findspark는 스파크 위치를 잡아주는건데 당연하게도 아래에있으면 안될 수 밖에없다.  
스파크 공부를 시작한지 이틀정도되었는데 환경 셋팅에서 엄청나게 걸리고있다.  
주피터 노트북에서 되는걸 확인했으니 이제 vsc에서 돌아가게 만들어보려고한다.

---

콘다의 환경으로 돌려도 vsc에서는 돌아가지않았는데  
커널을 변경했다가 다시 돌아오니 잘 돌아간다.  
커널을 껐다 키지 않아 계속 이전 설정값이들어갔던 것으로 추측된다.