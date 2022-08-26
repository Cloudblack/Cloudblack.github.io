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

# Spark Operation

## Transformations
- 결과값으로 새로운 RDD를 반환
- Lazy execution 지연실행
> map  
> flatMap  
> filter  
> distinct  
> reduceByKey  
> groupByKey  
> mapValues  
> flatMapValues  
> sortByKey
>

## Actions
- 결과값을 연산하여 출력하거나 저장
- Eager Execution 즉시 실행
> collect  
> count  
> first
> distinct
> countByValue  
> take  
> top  
> reduce  
> fold  
> foreach
