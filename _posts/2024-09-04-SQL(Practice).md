---

title: 09. SQL(Practice)
Author: YoungHoon Ko
date: 2024-09-04 16:45:00 +0900
categories: [SQL, Practice_SQL]
tags: [sql, basic, sql_p]
image: /assets/img/sql_실습.jpg
---
[toc]

# Practice

## [문제]

```markdown
2014년에 이루어진 주문들 가운데 State별 평균 주문금액이 큰 순서대로 State명과 주문 금액을 출력하라 
```

---

## [생각]

### 1. 우선 한글로 적어보기

- 2014년도 주문 테이터 필요
- State별 평균 주문금액 데이터 필요
- 큰 순서대로 출력
- State명과 주문 금액을 **<u>최종적으로 출력</u>**

### 2. 테이블에 있는 데이터를 잘 살펴보자

```sql
SELECT *
FROM class.c_order co ;

SELECT *
FROM class.c_customer cc ;

SELECT *
FROM class.c_product cp ;
```

- State는 c_customer 테이블에 존재
- 주문금액을 알기 위해선 **'제품 가격 X 주문 수량'**을 알아야 함
- 제품 가격은 c_product 테이블에 존재
- 주문 수량은 c_order 테이블에 존재

### 3. PK를 위주로 Join을 이용

- **<u>각 테이블 마다 컬럼에 열쇠 모양이 PK(Primary Key)</u>**
- c_order의 PK는 **ORDERID**
- c_customer의 PK는 **CUSTOMERID**
- c_product의 PK는 **PRODUCTID**

### 메인 테이블 설정

-  Join키를 기준으로 한 쪽이 유일한 테이블을 설정해야 함
- **<u>c_order 테이블의 컬럼을 보면 ORDERID, CUSTOMERID, PRODUCTID 모두 가지고 있음</u>**

### 4. 가로(컬럼)는 SELECT, 세로(로우)는 WHERE

### 5. WHERE절에 들어갈 조건 찾기

- 2014년도 주문 데이터
- **<u>c_order의 ORDERDAE가 '2014-01-01'과 '2014-12-31' 사이의 데이터</u>**

```sql
WHERE co.ORDERDATE >= '2014-01-01'
AND co.ORDERDATE <= '2014-12-31'
```

- **'2014-01-02'가 '2014-01-01'보다 크다**
- **'2014-01-01'가 '2014-01-02'보다 작다**

---

## [풀이]

- PK 확인

```sql
SELECT *
FROM class.c_order co -- ORDERID(PK), CUSTOMERID, PRODUCTID 가지고 있음

SELECT *
FROM class.c_customer cc -- CUSTOMERID(PK)

SELECT *
FROM class.c_product cp -- PRODUCTID(PK)
```

- 테이블 확인 후 **<u>메인 테이블 결정</u>**

```sql
SELECT *
FROM class.c_order co join class.c_customer cc 
on co.CUSTOMERID = cc.CUSTOMERID 
```

- c_order와 c_customer를 CUSTOMERID 컬럼을 이용하여 Join

```sql
SELECT *
FROM class.c_order co JOIN class.c_customer cc 
on co.CUSTOMERID = cc.CUSTOMERID 
JOIN class.c_product cp 
on co.PRODUCTID = cp.PRODUCTID 
```

- c_order와 c_product를 PRODUCTID 컬럼을 이용하여 Join

```sql
SELECT *
FROM class.c_order co join class.c_customer cc 
on co.CUSTOMERID = cc.CUSTOMERID 
JOIN class.c_product cp 
on co.PRODUCTID = cp.PRODUCTID
WHERE co.ORDERDATE >= '2014-01-01'
AND co.ORDERDATE <= '2014-12-31'
```

- 2014년도 데이터를 **<u>WHERE</u>**을 이용해 **<u>세로(row</u>**) 지정

```sql
SELECT cc.STATE , AVG(cp.PRICE * co.QUANTITY) as AVG_Amount
FROM class.c_order co join class.c_customer cc 
on co.CUSTOMERID = cc.CUSTOMERID 
JOIN class.c_product cp 
on co.PRODUCTID = cp.PRODUCTID
WHERE co.ORDERDATE >= '2014-01-01'
AND co.ORDERDATE <= '2014-12-31'
GROUP BY cc.STATE 
```

- State별 평균 주문금액 출력
  - GROUP BY를 사용하기 위해 컬럼에 집계함수(AVG - 평균) 사용

```sql
SELECT cc.STATE , AVG(cp.PRICE * co.QUANTITY) as AVG_Amount
FROM class.c_order co join class.c_customer cc 
on co.CUSTOMERID = cc.CUSTOMERID 
JOIN class.c_product cp 
on co.PRODUCTID = cp.PRODUCTID
WHERE co.ORDERDATE >= '2014-01-01'
AND co.ORDERDATE <= '2014-12-31'
GROUP BY cc.STATE 
ORDER BY AVG(cp.PRICE * co.QUANTITY) DESC 
```

- 평균 주문금액이 큰 순서대로 State명과 주문 금액 출력

## [결과]

![](/assets/img/sql_실습.jpg)

---

# Summary

- 한글로 적는 것 부터 시작
- **SELECT는 컬럼(가로), WHERE은 로우(세로) 관리**
- **<u>늘 시작하기 전 테이블을 확인하고 PK와 메인 테이블을 설정하는 것 부터 시작</u>**
