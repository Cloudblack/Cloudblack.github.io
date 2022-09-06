---
published: true
layout: single
title: error Python worker exited unexpectedly
categories:
  - SPARK
tags:
  - Error

toc: true
toc_sticky: true

---

``` python
ERROR PythonRunner: Python worker exited unexpectedly (crashed) java.net.SocketException: Connection reset by peer: socket write error
```
이런 에러와 함께 스파크가 강제로 꺼져버린다.  
어제까지 잘 돌아가던게 안돌아가니까 몇시간째 헤매고있었다.  

[해결출처](https://programmerah.com/solved-error-pythonrunner-python-worker-exited-unexpectedly-crashed-40820/)

메모리도 늘려보고 분산도 늘려보고 다 시도했지만 결국 실패 그런데 해결은 정말 황당했다.. 그냥 켜진 창들을 껐다가 다시키니까 잘된다.  
그냥 켜진게 너무많아 메모리 문제였던 것으로 추정된다.
