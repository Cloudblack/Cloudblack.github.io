---
layout: single
title: "Apache Hadoop이란?"
categories:
  - ETC
tags:
  - [ETC]

toc: true
toc_sticky: true



---

# Apache Hadoop이란?

### Apache Hadoop이란?

빅데이터를 저장, 처리, 분석할 수 있는 소프트웨어 프레임워크

- Distributed
- Scalable
- Fault-tolerant
- Open Source



다양한 에코 시스템

- 하둡이 동작하는데 같이 사용할 수 있는 여러 생태계를 구성하는 환경



하둡의 핵심 구성은

![image-20220708114216904](https://raw.githubusercontent.com/Cloudblack/Forpicture/image/img/image-20220708114216904.png)

- Hadoop Distributed File System
    - 클러스터에 데이터를 저장
    - 데이터는 block으로 분할되고, 클러스터의 여러 노드에 분산되어 저장된다
        - 각 block은 기본적으로  64mb 또는 128mb의 크기
    - 각 block은 여러 개의 replication을 생성하여 사용한다
        - 기본적으로 3개의 replication block을 생성하고
        - replication block은 서로 다른 노드에 저장된다
            - 이를통해 reliability 와 availability를 향상시켰다
- MapReduce  
    - 클러스터의 데이터를 처리
    - 두개의 pahse로 구성 : Map Reduce
        - Map과 Reduce 사이에는 shuffle과 sort라는 스테이지가 이있음
    - 각 Map task는 전체 데이터 셋에 대해서 별개의 부분에 대한 작업을 수행
        - 기본적으로 하나의 HDFS block을 대상으로 수행
        - 모든 Map task가 종료되면, MapReduce 시스템은 intermediate 데이터를 Reduce phases를 수행할 노드로 분산하여 전송

그리고 그위에 에코시스템을 얹어서 사용