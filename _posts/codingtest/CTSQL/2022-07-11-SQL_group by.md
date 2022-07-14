---
layout: single
title: "SQL Group by"
categories:
  - CTSQL
tags:
  - [SQL, coding test, Group by]

toc: true
toc_sticky: true






---

# SQL coding test

### 입양 시각 구하기 1

`ANIMAL_OUTS` 테이블은 동물 보호소에서 입양 보낸 동물의 정보를 담은 테이블입니다. 

`ANIMAL_OUTS` 테이블 구조는 다음과 같으며, `ANIMAL_ID`, `ANIMAL_TYPE`, `DATETIME`, `NAME`, `SEX_UPON_OUTCOME`는 각각 동물의 아이디, 생물 종, 입양일, 이름, 성별 및 중성화 여부를 나타냅니다.

| NAME             | TYPE       | NULLABLE |
| ---------------- | ---------- | -------- |
| ANIMAL_ID        | VARCHAR(N) | FALSE    |
| ANIMAL_TYPE      | VARCHAR(N) | FALSE    |
| DATETIME         | DATETIME   | FALSE    |
| NAME             | VARCHAR(N) | TRUE     |
| SEX_UPON_OUTCOME | VARCHAR(N) | FALSE    |

보호소에서는 몇 시에 입양이 가장 활발하게 일어나는지 알아보려 합니다. 

09:00부터 19:59까지, 각 시간대별로 입양이 몇 건이나 발생했는지 조회하는 SQL문을 작성해주세요. 

이때 결과는 시간대 순으로 정렬해야 합니다.

##### 예시

SQL문을 실행하면 다음과 같이 나와야 합니다.

| HOUR | COUNT |
| ---- | ----- |
| 9    | 1     |
| 10   | 2     |
| 11   | 13    |
| 12   | 10    |
| 13   | 14    |
| 14   | 9     |
| 15   | 7     |
| 16   | 10    |
| 17   | 12    |
| 18   | 16    |
| 19   | 2     |

``` mysql
SELECT HOUR(datetime) as hr,count(datetime) from ANIMAL_OUTS  
group by HOUR(datetime) 
having hr between 9 and 20 
order by hr
```

1. 결과를 표시한 시간과 입양횟수를 표기
2. hour를 사용해서 datetime을 시간별로 groupby 한다
3. 조건에있는 9~20을 having 에서 넣어준다 
    - 이미 만들어둔 hr을 사용
4. 마지막으로 정렬을 사용해준다 



---

### **입양 시각 구하기 **2

보호소에서는 몇 시에 입양이 가장 활발하게 일어나는지 알아보려 합니다. 

0시부터 23시까지, 각 시간대별로 입양이 몇 건이나 발생했는지 조회하는 SQL문을 작성해주세요. 

이때 결과는 시간대 순으로 정렬해야 합니다.

##### 예시

SQL문을 실행하면 다음과 같이 나와야 합니다.

| HOUR | COUNT |
| ---- | ----- |
| 0    | 0     |
| 1    | 0     |
| 2    | 0     |
| 3    | 0     |
| 4    | 0     |
| 5    | 0     |
| 6    | 0     |
| 7    | 3     |
| 8    | 1     |
| 9    | 1     |
| 10   | 2     |
| 11   | 13    |
| 12   | 10    |
| 13   | 14    |
| 14   | 9     |
| 15   | 7     |
| 16   | 10    |
| 17   | 12    |
| 18   | 16    |
| 19   | 2     |
| 20   | 0     |
| 21   | 0     |
| 22   | 0     |
| 23   | 0     |

``` mysql
SET @hour := -1;
SELECT (@hour := @hour +1) as HOUR ,
        (SELECT COUNT(*) FROM ANIMAL_OUTS WHERE HOUR(DATETIME)=@hour) AS COUNT
FROM ANIMAL_OUTS
WHERE @hour < 23
```

입양 시각 1번까지는 실실 웃으면서 풀었는데 ifnull써서 0을 채우려다가 생각해보니 null이라서 집계를 안한게 아니고 행 자체가 존재하지않다는것을 깨달았다.. 

갑작스런 난이도 상승으로 결국 구글링을 하게되었다( 변수사용법을 몰랐다 )

결론적으로 변수를 추가해 비는 시각을 추가해주면 된다 

1. 변수 선언 -1 부터 +1시키며 22번돌리면 0~23이 생성
2. 해당 변수와 같은 시간일때 카운트한 숫자를 넣는다
3. 변수가 23전까지 반복