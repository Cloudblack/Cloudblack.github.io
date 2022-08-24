---
published: true
layout: single
title: parquet to csv
categories:
  - DA
tags:
  - parquet to csv

toc: true
toc_sticky: true

---
## parquet은 무엇인가??
보통 행을 기반으로 데이터를 저장하는데비해 parquet은 열 기반으로 데이터를 저장한다

![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220824195129.png)

parquet의 장점으로는
- 높은 압축률, 칼럼 단위로 구성하면 데이터가 더 균일하므로 압축률이 높아진다.
- 데이터를 전체 칼럼중에서 일부 칼럼을 선택해서 가져오는 형식으로 선택하지 않은 칼럼의 데이터에서 I/O가 발생하지 않는다.
- 칼럼에 동일한 데이터타입이 저장되기 때문에 칼럼별로 적합한 인코딩을 사용 가능

그렇지만 소량의 데이터에 굳이 parquet를 쓸 필요까진 없다.  
애초에 parquet은 하둡처럼 빅데이터 분산에서 효율적으로 쓰고자 만들어진 파일 형식이다.  

이제 parquet 형식의 파일을 csv로 변경해보자

``` python
import pandas as pd
df = pd.read_parquet('data/fhvhv_tripdata_2020-03.parquet')
df.to_csv('data/fhvhv_tripdata_2020-03.parquet',index=False)
```

pandas로 parquet을 읽은후에 csv로 내보낸다.