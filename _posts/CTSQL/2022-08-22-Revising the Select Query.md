---
published: true
layout: single
title: Revising the Select Query
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

---
[출처](https://www.hackerrank.com/challenges/revising-the-select-query-2/problem?isFullScreen=true&h_r=next-challenge&h_v=zen)
Query the **NAME** field for all American cities in the **CITY** table with populations larger than `120000`. The _CountryCode_ for America is `USA`.

The **CITY** table is described as follows:  

![CITY.jpg](https://s3.amazonaws.com/hr-challenge-images/8137/1449729804-f21d187d0f-CITY.jpg)

시티 테이블에서 모든 미국 도시들에대한 네임 필드를 쿼리해라.  
미국의 코드는 USA이다

``` mysql
select name from city where population > 120000 and countrycode = "USA"
```

쿼리 난이도가 많이 낮다.  
영어를 공부한다는 마음가짐으로 해보자 