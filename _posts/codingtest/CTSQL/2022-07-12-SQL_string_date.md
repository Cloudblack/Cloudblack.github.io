---
layout: single
title: "SQL String, Date"
categories:
  - CTSQL
tags:
  - [SQL, coding test, String, Date]

toc: true
toc_sticky: true






---

# SQL coding test

`ANIMAL_INS` 테이블은 동물 보호소에 들어온 동물의 정보를 담은 테이블입니다.

 `ANIMAL_INS` 테이블 구조는 다음과 같으며, `ANIMAL_ID`, `ANIMAL_TYPE`, `DATETIME`, `INTAKE_CONDITION`, `NAME`, `SEX_UPON_INTAKE`는 각각 동물의 아이디, 생물 종, 보호 시작일, 보호 시작 시 상태, 이름, 성별 및 중성화 여부를 나타냅니다.

| NAME             | TYPE       | NULLABLE |
| ---------------- | ---------- | -------- |
| ANIMAL_ID        | VARCHAR(N) | FALSE    |
| ANIMAL_TYPE      | VARCHAR(N) | FALSE    |
| DATETIME         | DATETIME   | FALSE    |
| INTAKE_CONDITION | VARCHAR(N) | FALSE    |
| NAME             | VARCHAR(N) | TRUE     |
| SEX_UPON_INTAKE  | VARCHAR(N) | FALSE    |

---

### 루시와 엘라 찾기

동물 보호소에 들어온 동물 중 이름이 Lucy, Ella, Pickle, Rogan, Sabrina, Mitty인 동물의 아이디와 이름, 성별 및 중성화 여부를 조회하는 SQL 문을 작성해주세요.

##### 예시

이때 결과는 아이디 순으로 조회해주세요. 예를 들어 `ANIMAL_INS` 테이블이 다음과 같다면

| ANIMAL_ID | ANIMAL_TYPE | DATETIME            | INTAKE_CONDITION | NAME  | SEX_UPON_INTAKE |
| --------- | ----------- | ------------------- | ---------------- | ----- | --------------- |
| A373219   | Cat         | 2014-07-29 11:43:00 | Normal           | Ella  | Spayed Female   |
| A377750   | Dog         | 2017-10-25 17:17:00 | Normal           | Lucy  | Spayed Female   |
| A353259   | Dog         | 2016-05-08 12:57:00 | Injured          | Bj    | Neutered Male   |
| A354540   | Cat         | 2014-12-11 11:48:00 | Normal           | Tux   | Neutered Male   |
| A354597   | Cat         | 2014-05-02 12:16:00 | Normal           | Ariel | Spayed Female   |

SQL문을 실행하면 다음과 같이 나와야 합니다.

| ANIMAL_ID | NAME | SEX_UPON_INTAKE |
| --------- | ---- | --------------- |
| A373219   | Ella | Spayed Female   |
| A377750   | Lucy | Spayed Female   |

```mysql
SELECT ANIMAL_ID,NAME ,SEX_UPON_INTAKE 
from ANIMAL_INS 
where name in ('Lucy', 'Ella', 'Pickle', 'Rogan', 'Sabrina', 'Mitty')
```

동물의 이름이  Lucy, Ella, Pickle, Rogan, Sabrina, Mitty

- name에 특정 문자열이있는지 체크
- from, where in

동물의 아이디와 이름, 성별 및 중성화 여부를 조회하는 SQL 문

- select

---

보호소에 돌아가신 할머니가 기르던 개를 찾는 사람이 찾아왔습니다. 이 사람이 말하길 할머니가 기르던 개는 이름에 'el'이 들어간다고 합니다. 동물 보호소에 들어온 동물 이름 중, 이름에 "EL"이 들어가는 개의 아이디와 이름을 조회하는 SQL문을 작성해주세요. 이때 결과는 이름 순으로 조회해주세요. 단, 이름의 대소문자는 구분하지 않습니다.

##### 예시

예를 들어 `ANIMAL_INS` 테이블이 다음과 같다면

| ANIMAL_ID | ANIMAL_TYPE | DATETIME            | INTAKE_CONDITION | NAME         | SEX_UPON_INTAKE |
| --------- | ----------- | ------------------- | ---------------- | ------------ | --------------- |
| A355753   | Dog         | 2015-09-10 13:14:00 | Normal           | Elijah       | Neutered Male   |
| A352872   | Dog         | 2015-07-09 17:51:00 | Aged             | Peanutbutter | Neutered Male   |
| A353259   | Dog         | 2016-05-08 12:57:00 | Injured          | Bj           | Neutered Male   |
| A373219   | Cat         | 2014-07-29 11:43:00 | Normal           | Ella         | Spayed Female   |
| A382192   | Dog         | 2015-03-13 13:14:00 | Normal           | Maxwell 2    | Intact Male     |

- 이름에 'el'이 들어가는 동물은 Elijah, Ella, Maxwell 2입니다.
- 이 중, 개는 Elijah, Maxwell 2입니다.

따라서 SQL문을 실행하면 다음과 같이 나와야 합니다.

| ANIMAL_ID | NAME      |
| --------- | --------- |
| A355753   | Elijah    |
| A382192   | Maxwell 2 |

```mysql
SELECT ANIMAL_ID, NAME 
FROM ANIMAL_INS 
WHERE NAME like '%el%' and ANIMAL_TYPE = 'Dog'
ORDER BY NAME
```

테이블에서 이름에 'el'이 들어가는 '개'

- like를 사용해 이름 어딘가에 el이있다면 선택한다 
- Animal_type이 dog이면 선택
- From, where, like

아이디와 이름을 조회

- Select

이름순으로 조회

- Order by

---

### 중성화 여부 파악하기

보호소의 동물이 중성화되었는지 아닌지 파악하려 합니다. 중성화된 동물은 `SEX_UPON_INTAKE` 컬럼에 'Neutered' 또는 'Spayed'라는 단어가 들어있습니다. 동물의 아이디와 이름, 중성화 여부를 아이디 순으로 조회하는 SQL문을 작성해주세요. 이때 중성화가 되어있다면 'O', 아니라면 'X'라고 표시해주세요.

##### 예시

예를 들어 `ANIMAL_INS` 테이블이 다음과 같다면

| ANIMAL_ID | ANIMAL_TYPE | DATETIME            | INTAKE_CONDITION | NAME      | SEX_UPON_INTAKE |
| --------- | ----------- | ------------------- | ---------------- | --------- | --------------- |
| A355753   | Dog         | 2015-09-10 13:14:00 | Normal           | Elijah    | Neutered Male   |
| A373219   | Cat         | 2014-07-29 11:43:00 | Normal           | Ella      | Spayed Female   |
| A382192   | Dog         | 2015-03-13 13:14:00 | Normal           | Maxwell 2 | Intact Male     |

- 중성화한 동물: Elijah, Ella
- 중성화하지 않은 동물: Maxwell 2

따라서 SQL문을 실행하면 다음과 같이 나와야 합니다.

| ANIMAL_ID | NAME      | 중성화 |
| --------- | --------- | ------ |
| A355753   | Elijah    | O      |
| A373219   | Ella      | O      |
| A382192   | Maxwell 2 | X      |

※ 컬럼 이름은 일치하지 않아도 됩니다.

```mysql
SELECT ANIMAL_ID, NAME, 
IF(SEX_UPON_INTAKE like '%Neutered%' OR 
   SEX_UPON_INTAKE like '%Spayed%','O','X') as '중성화' 
From ANIMAL_INS 
ORDER BY ANIMAL_ID
```

테이블에서 중성화된 ( 'Neutered' 또는 'Spayed')가 포함된 단어가 있으면 O 없으면 X

- IF를 사용해 특정 단어가있으면 O 없으면 X를 표시
- IF, LIKE, FROM

아이디와 이름 중성화 여부를 아이디 순으로 쿼리

- SELECT, ORDER BY

---

### 오랜 기간 보호한 동물(2)

보호 테이블 외에 입양 테이블이 추가됨

`ANIMAL_OUTS` 테이블은 동물 보호소에서 입양 보낸 동물의 정보를 담은 테이블입니다. `ANIMAL_OUTS` 테이블 구조는 다음과 같으며, `ANIMAL_ID`, `ANIMAL_TYPE`, `DATETIME`, `NAME`, `SEX_UPON_OUTCOME`는 각각 동물의 아이디, 생물 종, 입양일, 이름, 성별 및 중성화 여부를 나타냅니다. `ANIMAL_OUTS` 테이블의 `ANIMAL_ID`는 `ANIMAL_INS`의 `ANIMAL_ID`의 외래 키입니다.

| NAME             | TYPE       | NULLABLE |
| ---------------- | ---------- | -------- |
| ANIMAL_ID        | VARCHAR(N) | FALSE    |
| ANIMAL_TYPE      | VARCHAR(N) | FALSE    |
| DATETIME         | DATETIME   | FALSE    |
| NAME             | VARCHAR(N) | TRUE     |
| SEX_UPON_OUTCOME | VARCHAR(N) | FALSE    |

입양을 간 동물 중, 보호 기간이 가장 길었던 동물 두 마리의 아이디와 이름을 조회하는 SQL문을 작성해주세요. 이때 결과는 보호 기간이 긴 순으로 조회해야 합니다.

##### 예시

예를 들어, `ANIMAL_INS` 테이블과 `ANIMAL_OUTS` 테이블이 다음과 같다면

```
ANIMAL_INS
```

| ANIMAL_ID | ANIMAL_TYPE | DATETIME            | INTAKE_CONDITION | NAME       | SEX_UPON_INTAKE |
| --------- | ----------- | ------------------- | ---------------- | ---------- | --------------- |
| A354597   | Cat         | 2014-05-02 12:16:00 | Normal           | Ariel      | Spayed Female   |
| A362707   | Dog         | 2016-01-27 12:27:00 | Sick             | Girly Girl | Spayed Female   |
| A370507   | Cat         | 2014-10-27 14:43:00 | Normal           | Emily      | Spayed Female   |
| A414513   | Dog         | 2016-06-07 09:17:00 | Normal           | Rocky      | Neutered Male   |

```
ANIMAL_OUTS
```

| ANIMAL_ID | ANIMAL_TYPE | DATETIME            | NAME       | SEX_UPON_OUTCOME |
| --------- | ----------- | ------------------- | ---------- | ---------------- |
| A354597   | Cat         | 2014-06-03 12:30:00 | Ariel      | Spayed Female    |
| A362707   | Dog         | 2017-01-10 10:44:00 | Girly Girl | Spayed Female    |
| A370507   | Cat         | 2015-08-15 09:24:00 | Emily      | Spayed Female    |

SQL문을 실행하면 다음과 같이 나와야 합니다.

| ANIMAL_ID | NAME       |
| --------- | ---------- |
| A362707   | Girly Girl |
| A370507   | Emily      |

※ 입양을 간 동물이 2마리 이상인 경우만 입력으로 주어집니다.

```mysql
SELECT ins.ANIMAL_ID, ins.NAME 
FROM ANIMAL_INS as ins 
INNER JOIN ANIMAL_OUTS as outs
ON ins.ANIMAL_ID = outs.ANIMAL_ID
ORDER BY DATEDIFF(outs.DATETIME,ins.DATETIME) desc
limit 2
```

입양을 간 동물 중

- 입양을 갔다는건  outs - ins로 outs에 기록이 있어야하기때문에 inner join을 사용
- inner join

보호기간이 가장 길었던 동물 두마리

- outs와 ins의 차이를 비교해야해 datediff를 사용했다
- datediff는 앞에서 뒤의 날짜를 비교한다
- 가장 길었던 동물을 찾기위해 datediff 기준으로 order by로 정렬
- 두마리를 선택하기위해 limit을 줬다

아이디와 이름을 조회

- select

---

### DATETIME에서 DATE로 형 변환

`ANIMAL_INS` 테이블에 등록된 모든 레코드에 대해, 각 동물의 아이디와 이름, 들어온 날짜[1](https://school.programmers.co.kr/learn/courses/30/lessons/59414#fn1)를 조회하는 SQL문을 작성해주세요. 이때 결과는 아이디 순으로 조회해야 합니다.

##### 예시

예를 들어, `ANIMAL_INS` 테이블이 다음과 같다면

```
ANIMAL_INS
```

| ANIMAL_ID | ANIMAL_TYPE | DATETIME            | INTAKE_CONDITION | NAME   | SEX_UPON_INTAKE |
| --------- | ----------- | ------------------- | ---------------- | ------ | --------------- |
| A349996   | Cat         | 2018-01-22 14:32:00 | Normal           | Sugar  | Neutered Male   |
| A350276   | Cat         | 2017-08-13 13:50:00 | Normal           | Jewel  | Spayed Female   |
| A350375   | Cat         | 2017-03-06 15:01:00 | Normal           | Meo    | Neutered Male   |
| A352555   | Dog         | 2014-08-08 04:20:00 | Normal           | Harley | Spayed Female   |
| A352713   | Cat         | 2017-04-13 16:29:00 | Normal           | Gia    | Spayed Female   |

SQL문을 실행하면 다음과 같이 나와야 합니다.

| ANIMAL_ID | NAME   | 날짜       |
| --------- | ------ | ---------- |
| A349996   | Sugar  | 2018-01-22 |
| A350276   | Jewel  | 2017-08-13 |
| A350375   | Meo    | 2017-03-06 |
| A352555   | Harley | 2014-08-08 |
| A352713   | Gia    | 2017-04-13 |

```mysql
SELECT ANIMAL_ID,NAME,date_format(DATETIME,'%Y-%m-%d') as '날짜' 
FROM ANIMAL_INS
ORDER BY ANIMAL_ID
```

모든 레코드에 대해 각 동물의 아이디와 이름 들어온 날짜를 조회하는 SQL문

- 들어온 날짜를 초까지 표시하는 datetime에서 연월일만 표시하게끔 변경
- date_format(날짜,'변경할 포맷 형식'')으로 변경
- select, date_format, from

아이디 순으로 조회

- order by



포맷 표시 형식 

| FORMAT          | 설명                                      |
| --------------- | ----------------------------------------- |
| %M              | Month 월(Janeary, February ...)           |
| %m              | Month 월(01, 02, 03 ...)                  |
| %W              | Day of Week 요일(Sunday, Monday ...)      |
| %D              | Month 월(1st, 2dn, 3rd ...)               |
| %Y              | Year 연도(1999, 2000, 2020)               |
| %y              | Year 연도(99, 00, 20)                     |
| %X              | Year 연도(1999, 2000, 2020) %V와 같이쓰임 |
| %x              | Year 연도(1999, 2000, 2020) %v와 같이쓰임 |
| %a              | Day of Week요일(Sun, Mon, Tue ...)        |
| %d              | Day 일(00, 01, 02 ...)                    |
| %e              | Day 일(0, 1, 2 ..)                        |
| %c              | Month(1, 2, 3 ..)                         |
| %b              | Month(Jen Feb ...)                        |
| %j              | n번째 일(100, 365)                        |
| %H              | Hour 시(00, 01, 24) 24시간 형태           |
| %h              | Hour 시(01, 02, 12) 12시간 형태           |
| %I(대문자 아이) | Hour 시(01, 02 12) 12시간 형태            |
| %l(소문자 엘)   | Hour 시(1, 2, 12) 12 시간 형태            |
| %i              | Minute 분(00, 01 59)                      |
| %r              | hh:mm:ss AP                               |
| %T              | hh:mm:ss                                  |
| %S, %s          | Second 초                                 |
| %p              | AP, PM                                    |
| %w              | Day Of Week (0, 1, 2) 0부터 일요일        |
| %U              | Week 주(시작: 일요일)                     |
| %u              | Week 주(시작 월요일)                      |
| %V              | Week 주(시작: 일요일)                     |
| %v              | Week 주(시작:월요일)                      |

---

