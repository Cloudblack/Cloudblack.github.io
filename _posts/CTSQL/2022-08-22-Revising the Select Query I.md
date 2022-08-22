---
published: true
layout: single
title: Revising the Select Query I
categories:
  - CTSQL
tags:
  - Select
  - 해커랭크

toc: true
toc_sticky: true

---
프로그래머스에있는 sql문제를 모두 풀었다.  
한글로된 sql 문제 사이트를 더 찾지는 못했고  
앞으로를 위해서라도 영어로된 sql문제를 풀어보기위해 해커랭크를 시작하기로했다.   

---

[출처](https://www.hackerrank.com/challenges/revising-the-select-query/problem?isFullScreen=true)  
# 문제

Query all columns for all American cities in the **CITY** table with populations larger than `100000`. The **CountryCode** for America is `USA`.

The **CITY** table is described as follows:

![CITY.jpg](https://s3.amazonaws.com/hr-challenge-images/8137/1449729804-f21d187d0f-CITY.jpg)

---
city라는 테이블에서 인구수(population) 100000이상인 모든 미국의 도시의 전체 컬럼을 보여줘라
countrycode에서 미국은 USA이다

``` mysql
select * from city where population > 100000 and countrycode ='USA'
```
