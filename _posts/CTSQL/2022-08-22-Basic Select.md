---
published: true
layout: single
title: Basic Select
categories: [CTSQL]
tags:
  - Basic Select
toc: true
toc_sticky: true
date created: 월요일, 8월 22일 2022
date modified: 월요일, 8월 29일 2022
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

---
<https://www.hackerrank.com/challenges/select-all-sql/problem?isFullScreen=true>

Query all columns (attributes) for every row in the **CITY** table.  
The **CITY** table is described as follows:  
![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220827204933.png)  
city table의 모든 row에 대한 모든 cloumn을 쿼리하라

``` mysql
select * from city
```

아직 쉽다…

---
<https://www.hackerrank.com/challenges/select-by-id/problem?isFullScreen=true&h_r=next-challenge&h_v=zen>
Query all columns for a city in **CITY** with the _ID_ `1661`.
The **CITY** table is described as follows
![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220829193916.png)

city테이블에서 ID가 1661인 것에서 모든 컬럼을 쿼리하라
``` mysql
select * from city where id = 1661
```

---
https://www.hackerrank.com/challenges/japanese-cities-attributes/problem?isFullScreen=true

Query all attributes of every Japanese city in the **CITY** table. The **COUNTRYCODE** for Japan is `JPN`.

시티 테이블에서 일본의 모든 특성을 쿼리해라
``` mysql
select * from city where countrycode = 'JPN'
```

---
