---
published: true
layout: single
title: Spark cluster
categories: [SPARK]
tags:
  - Spark cluster
toc: true
toc_sticky: true
date created: 토요일, 8월 27일 2022
date modified: 월요일, 8월 29일 2022
---

## 스파크의 구조
spark는 master와 worker toplogy로 구성되어있다.

스파크를 쓰면서 잊지 말아야 할 점
- 항상 데이터가 여러곳에 분산되어 있다는 것
- 같은 연산이어도 여러 노드에 걸쳐서 실행된다는점  
![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220827155746.png)

마스터로는 드라이버 프로그램이있고 워커로 워커 노드들이 있다.  
드라이버 프로그램으로 sparkcontext가있고 RDD를 생성한다.  
개발할때 드라이버 프로그램을 주로사용하게되고  
워커 노드들에게 연산해야 할 작업을 보내게된다

즉, 드라이버 프로그램이 명령해 워커 노드에서 연산이 이루어진다.

드라이버 프로그램은 워커노드와 클러스터 매니저를 통해 소통한다  
클러스터 매니저는 수행되는 작업에 대한 스케줄링과 클러스터 전반에 대한 자원관리를 담당한다  
유명한 클러스터 매니저로 yarn과 mesos가있다

### 드라이버 프로그램
- 메인 프로세스를수행한다
- sparkcontext로 RDD를 생성한다
- transformation과 action을 저장해두거나 워커 노드들에게 전송한다.

### 워커노드
- Excutor에서 task를 수행한다
- 연산결과를 드라이버 프로그램으로 전송한다
- 연산에 필요한 cache를 갖고있다

### 동작방식
드라이버 프로그램에서 RDD를 생성하게되고 클러스터 매니저에서 워커 노드들을 준비시킨다  
드라이버 프로그램에서 필요한 작업들을 워커 노드들에게 보내게되고 결과물들을 다시 드라이버 프로그램으로 가져오게된다
