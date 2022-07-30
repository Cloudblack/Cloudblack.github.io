---
published: true
layout: single
title: "제약조건"
categories:
  - SQL
tags:
  - [SQL]

toc: true
toc_sticky: true

---
# 제약 조건(constraint)

제약 조건(constraint)이란 데이터의 무결성을 지키기 위해, 데이터를 입력받을 때 실행되는 검사 규칙을 의미합니다.

이러한 제약 조건은 CREATE 문으로 테이블을 생성할 때나 ALTER 문으로 필드를 추가할 때도 설정할 수도 있습니다.
1. NOT NULL
2. UNIQUE
3. PRIMARY KEY
4. FOREIGN KEY
5. DEFAULT

## NOT NULL

NOT NULL 제약 조건을 설정하면, 해당 필드는 NULL 값을 저장할 수 없습니다.

즉, 이 제약 조건이 설정된 필드는 무조건 데이터를 가지고 있어야 합니다.

### CREATE 문으로 NOT NULL 설정
``` mysql
CREATE TABLE 테이블이름(
    필드이름 필드타입 NOT NULL,
    ...
    )
```
``` mysql
CREATE TABLE Test(
    ID INT NOT NULL,
    Name VARCHAR(30),
    ReserveDate DATE,
    RoomNum INT
    );
```
![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220725123339.png)

NOT NULL 제약 조건이란 해당 필드에 NULL 값을 저장할 수 없도록 설정하는 것으로, 해당 필드를 생략하지 못하도록 하는 제약 조건은 아닙니다.

따라서 INSERT 문으로 레코드를 저장할 때 NOT NULL 제약 조건이 설정된 필드의 값을 생략할 수도 있습니다.
``` mysql
  
INSERT INTO Test (Name, ReserveDate, RoomNum)

VALUES('이순신', '2016-02-16', 1108);
```
![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220725123553.png)

### ALTER 문으로 NOT NULL 설정

ALTER 문으로 테이블에 새로운 필드를 추가하거나 수정할 때도 NOT NULL 제약 조건을 설정할 수 있습니다.

테이블에 새로운 필드를 추가할 때 NOT NULL 제약 조건을 설정
``` mysql
ALTER TABLE 테이블이름

ADD 필드이름 필드타입 NOT NULL
```

기존 필드에 NOT NULL 제약 조건을 설정
``` mysql
ALTER TABLE 테이블이름

MODIFY COLUMN 필드이름 필드타입 NOT NULL
```

``` mysql
ALTER TABLE Reservation
MODIFY COLUMN name VARCHAR(30) NOT NULL;
```
![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220725123906.png)
## UNIQUE

UNIQUE 제약 조건을 설정하면, 해당 필드는 서로 다른 값을 가져야 합니다.

즉, 이 제약 조건이 설정된 필드는 중복된 값을 저장할 수 없습니다.

### CREATE 문으로 UNIQUE 설정

CREATE 문에서 테이블을 생성할 때 다음과 같이 UNIQUE 제약 조건을 설정할 수 있습니다.

CREATE 문으로 테이블을 생성할 때 해당 필드의 타입 뒤에 UNIQUE를 명시하면, 해당 필드에는 더는 중복된 값을 저장할 수 없습니다.

``` mysql
1.CREATE TABLE 테이블이름(
    필드명 필드타입 UNIQUE,
    ...
    )

2.CREATE TABLE 테이블이름(
    필드이름 필드타입,
    ...,
    [CONSTRAINT 제약조건이름] UNIQUE (필드이름)
)
```
위의 두 문법은 모두 해당 필드에 UNIQUE 제약 조건을 설정합니다.
이때 두 번째 문법을 사용하면, 해당 제약 조건에 이름을 설정할 수 있습니다.

``` mysql
CREATE TABLE Test (
    ID INT UNIQUE,
    Name VARCHAR(30),
    ReserveDate DATE,
    RoomNum INT
    );
```
![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220725124153.png)
### ALTER 문으로 UNIQUE 설정

ALTER 문으로 테이블에 새로운 필드를 추가하거나 수정할 때도 UNIQUE 제약 조건을 설정할 수 있습니다.
``` mysql
1. ALTER TABLE 테이블이름
   ADD 필드이름 필드타입 UNIQUE

2. ALTER TABLE 테이블이름
   ADD [CONSTRAINT 제약조건이름] UNIQUE (필드이름)
```

``` mysql
1. ALTER TABLE 테이블이름
   MODIFY COLUMN 필드이름 필드타입 UNIQUE

2. ALTER TABLE 테이블이름
   MODIFY COLUMN [CONSTRAINT 제약조건이] 
   UNIQUE (필드이름)
```


``` mysql
ALTER TABLE Reservation
ADD CONSTRAINT reservedRoom UNIQUE (RoomNum);
#ALTER TABLE 문을 사용하여 Reservation 테이블의 RoomNum 필드에 reservedRoom이라는 이름을 가지는 UNIQUE 제약 조건을 설정
```
![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220725124433.png)

제약 조건에 이름을 설정하면, 다음과 같이 이름을 사용하여 해당 제약 조건을 삭제할 수 있습니다.

``` mysql
ALTER TABLE 테이블이름

DROP INDEX 제약조건이름
```
UNIQUE 제약 조건을 설정하면, 해당 필드는 자동으로 인덱스(INDEX)로 만들어집니다.

``` mysql
ALTER TABLE Reservation

DROP INDEX reservedRoom;
```
![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220725124628.png)

## PRIMARY KEY

PRIMARY KEY 제약 조건을 설정하면, 해당 필드는 NOT NULL과 UNIQUE 제약 조건의 특징을 모두 가집니다.

따라서 이 제약 조건이 설정된 필드는 NULL 값을 가질 수 없으며, 또한 중복된 값을 가져서도 안 됩니다.

이러한 PRIMARY KEY 제약 조건을 기본 키라고 합니다.

UNIQUE는 한 테이블의 여러 필드에 설정할 수 있지만, PRIMARY KEY는 테이블당 오직 하나의 필드에만 설정할 수 있습니다.

이러한 PRIMARY KEY 제약 조건은 테이블의 데이터를 쉽고 빠르게 찾도록 도와주는 역할을 합니다.

### CREATE 문으로 PRIMARY KEY 설정

CREATE 문에서 테이블을 생성할 때 다음과 같이 PRIMARY KEY 제약 조건을 설정할 수 있습니다.

CREATE 문으로 테이블을 생성할 때 해당 필드의 타입 뒤에 PRIMARY KEY를 명시하면, 해당 필드가 기본 키로 설정됩니다.

``` mysql
1. CREATE TABLE 테이블이름(
    필드이름 필드타입 PRIMARY KEY,
    ...
    )  
    
2. CREATE TABLE 테이블이름(
    필드이름 필드타입,
    ...,
    [CONSTRAINT 제약조건이름] PRIMARY KEY (필드이름)
    )
```

위의 두 문법은 모두 해당 필드에 PRIMARY KEY 제약 조건을 설정합니다.

이때 두 번째 문법을 사용하면, 해당 제약 조건에 이름을 설정할 수 있습니다.

``` mysql
CREATE TABLE Test (
    ID INT PRIMARY KEY,
    Name VARCHAR(30),
    ReserveDate DATE,
    RoomNum INT
    );
```
![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220725124825.png)

### ALTER 문으로 PRIMARY KEY 설정

ALTER 문으로 테이블에 새로운 필드를 추가하거나 수정할 때도 PRIMARY KEY 제약 조건을 설정할 수 있습니다.

테이블에 새로운 필드를 추가할 때 해당 필드를 기본 키로 설정

``` mysql

1. ALTER TABLE 테이블이름
   ADD 필드이름 필드타입 PRIMARY KEY

2. ALTER TABLE 테이블이름
   ADD [CONSTRAINT 제약조건이름] 
   PRIMARY KEY (필드이름)
```

또한, 기존에 존재하는 필드를 기본 키로 설정
``` mysql


1. ALTER TABLE 테이블이름
   MODIFY COLUMN 필드이름 필드타입 PRIMARY KEY

2. ALTER TABLE 테이블이름
   MODIFY COLUMN [CONSTRAINT 제약조건이름] 
   PRIMARY KEY (필드이름)
```

PRIMARY KEY 제약 조건을 추가할 기존 필드는 NULL 값을 갖지 않도록 먼저 선언되어 있어야 합니다.

``` mysql
  
ALTER TABLE Reservation
CONSTRAINT CustomerID ADD PRIMARY KEY (ID);
```
![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220725125057.png)

다음과 같은 방법을 사용하여 설정된 PRIMARY KEY 제약 조건을 삭제할 수 있습니다.
``` mysql
ALTER TABLE 테이블이름

DROP PRIMARY KEY
```

``` mysql
ALTER TABLE Reservation

DROP PRIMARY KEY;
```

## FOREIGN KEY

FOREIGN KEY 제약 조건을 설정한 필드는 외래 키라고 부르며, 한 테이블을 다른 테이블과 연결해주는 역할을 합니다.

외래 키가 설정된 테이블에 레코드를 입력하면, 기준이 되는 테이블의 내용을 참조해서 레코드가 입력됩니다.

즉, FOREIGN KEY 제약 조건은 하나의 테이블을 다른 테이블에 의존하게 만듭니다.

FOREIGN KEY 제약 조건을 설정할 때 참조되는 테이블의 필드는 반드시 UNIQUE나 PRIMARY KEY 제약 조건이 설정되어 있어야 합니다.

### CREATE 문으로 FOREIGN KEY 설정

CREATE 문에서 테이블을 생성할 때 다음과 같이 FOREIGN KEY 제약 조건을 설정할 수 있습니다.
``` mysql
CREATE TABLE 테이블이름(
    필드이름 필드타입,
    ...,
    [CONSTRAINT 제약조건이름]
    FOREIGN KEY (필드이름)
    REFERENCES 테이블이름 (필드이름)
    )
```
위의 문법을 사용하면 해당 필드에 FOREIGN KEY 제약 조건을 설정합니다.
이때 참조되는 테이블의 이름은 REFERENCES 키워드 다음에 명시됩니다.

``` mysql
CREATE TABLE Test2(
    ID INT,
    ParentID INT,
    FOREIGN KEY (ParentID)
    REFERENCES Test1(ID) ON UPDATE CASCADE
    );
```
![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220725131604.png)

위의 예제에서 Test2 테이블의 ParentID 필드는 Test1 테이블의 ID 필드를 참조하도록 설정됩니다.
따라서 Test1 테이블의 ID 필드가 변경되면, 같은 값의 Test2 테이블의 ParentID 필드도 같이 변경됩니다.

### ALTER 문으로 FOREIGN KEY 설정

ALTER 문으로 테이블에 새로운 필드를 추가하거나 수정할 때도 FOREIGN KEY 제약 조건을 설정할 수 있습니다.
``` mysql
ALTER TABLE 테이블이름
ADD [CONSTRAINT 제약조건이름]
FOREIGN KEY (필드이름)
REFERENCES 테이블이름 (필드이름)
```

``` mysql
ALTER TABLE Reservation
ADD CONSTRAINT CustomerID
FOREIGN KEY (ID)
REFERENCES Customer (ID);
```
![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220725131742.png)


FOREIGN KEY 제약 조건을 삭제
``` mysql
ALTER TABLE 테이블이름
DROP FOREIGN KEY 제약조건이름

ALTER TABLE Reservation
DROP FOREIGN KEY CustomerID;
```
## ON DELETE, ON UPDATE
FOREIGN KEY 제약 조건에 의해 참조되는 테이블에서 데이터의 수정이나 삭제가 발생하면, 참조하고 있는 테이블의 데이터도 같이 영향을 받습니다.

이때 참조하고 있는 테이블의 동작은 다음 키워드를 사용하여 FOREIGN KEY 제약 조건에서 미리 설정할 수 있습니다.
1. ON DELETE
2. ON UPDATE
참조되는 테이블의 값이 삭제될 경우의 동작은 ON DELETE 구문으로 설정할 수 있습니다.

또한, 참조되는 테이블의 값이 수정될 경우의 동작은 ON UPDATE 구문으로 설정할 수 있습니다.
이때 설정할 수 있는 동작은 다음과 같습니다.

1. CASCADE : 참조되는 테이블에서 데이터를 삭제하거나 수정하면, 참조하는 테이블에서도 삭제와 수정이 같이 이루어집니다.
2. SET NULL : 참조되는 테이블에서 데이터를 삭제하거나 수정하면, 참조하는 테이블의 데이터는 NULL로 변경됩니다.
3. NO ACTION : 참조되는 테이블에서 데이터를 삭제하거나 수정해도, 참조하는 테이블의 데이터는 변경되지 않습니다.
4. SET DEFAULT : 참조되는 테이블에서 데이터를 삭제하거나 수정하면, 참조하는 테이블의 데이터는 필드의 기본값으로 설정됩니다.
5. RESTRICT : 참조하는 테이블에 데이터가 남아 있으면, 참조되는 테이블의 데이터를 삭제하거나 수정할 수 없습니다.
``` mysql
CREATE TABLE Test2(
    ID INT,
    ParentID INT, 
    FOREIGN KEY (ParentID)
    REFERENCES Test1(ID) ON UPDATE CASCADE ON DELETE RESTRICT
    );

#참조되는 필드의 데이터가 수정될 때는 CASCADE 방식으로, 삭제될 때는 RESTRICT 방식으로 동작
```
![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220725201132.png)

## DEFAULT


DEFAULT 제약 조건은 해당 필드의 기본값을 설정할 수 있게 해줍니다.

만약 레코드를 입력할 때 해당 필드 값을 전달하지 않으면, 자동으로 설정된 기본값을 저장합니다.
#### CREATE 문으로 DEFAULT 설정

CREATE 문에서 테이블을 생성할 때 다음과 같이 제약 조건을 설정할 수 있습니다.
``` mysql
CREATE TABLE 테이블이름(
    필드이름 필드타입 DEFAULT 기본값,
    ...
    )

CREATE TABLE Test(
    ID INT,
    Name VARCHAR(30) DEFAULT 'Anonymous',
    ReserveDate DATE,
    RoomNum INT
    );
```
#### ALTER 문으로 DEFAULT 설정

ALTER 문으로 테이블에 새로운 필드를 추가하거나 수정할 때도 DEFAULT 제약 조건을 설정할 수 있습니다.
``` mysql
ALTER TABLE 테이블이름
ADD 필드이름 필드타입 DEFAULT 기본값

```
``` mysql
1. ALTER TABLE 테이블이름
   MODIFY COLUMN 필드이름 필드타입 DEFAULT 기본값

2. ALTER TABLE 테이블이름
   ALTER 필드이름 SET DEFAULT 기본값
```
