---

title: 04. SQL(select절의 활용, 표현식과 별칭, 연결 연산자(concat()))
Author: YoungHoon Ko
date: 2024-08-29 12:50:00 +0900
categories: [SQL, Practice]
tags: [sql, basic, sql_p]
image: /assets/img/select_1.jpg
image: /assets/img/select_2.jpg
image: /assets/img/select_3.jpg
image: /assets/img/select_4.jpg
image: /assets/img/select_5.jpg
image: /assets/img/select_6.jpg
---
[toc]

# SELECT문의 구성

## SELECT문의 구성

- 각 구성을 말할 땐, select절, from절 등으로 말 함

1. SELECT - 기본적으로 **컬럼명**과 **<u>*(모든 것)</u>**이 자주 들어감
2. FROM - **table명과 다른 select문**과 **다른 결과의 대명사**들이 들어올 수 있음
3. WHERE - 조건
4. GROUP BY - SELECT절과 같음
5. HAVING - SELECT절과 같음
6. ORDER BY - SELECT절과 같음

---

## SELECT문의 실행순서

- 1번 부터 차례로 우선순위를 가짐

1. FROM
2. WHERE
3. GROUP BY
4. HAVING
5. SELECT
6. ORDER BY

# SELECT문 실습

```sql
use class;	
```

- class를 사용할 때 'class.'을 생략하고 적을 수 있음

---

- 모든 칼럼 중  **<u>STATE = 'Arizona'</u>**이고  **<u>CUSTOMERTYPE = 'Home Office'</u>**인 튜플만 출력함
- **두 번째 조건 부터는  AND로 조건을 적음**
- 모든 출력은 WHERE절이 관리

```sql
SELECT *
FROM class.c_customer
WHERE STATE = 'Arizona'
AND CUSTOMERTYPE = 'Home Office';
```

![](/assets/img/select_1.jpg)

---

- 칼럼 중 **<u>CUSTOMERID, CUSTOMERNAME , CUSTOMERTYPE , COUNTRY , STATE</u>** 출력

```sql
SELECT CUSTOMERID, CUSTOMERNAME, CUSTOMERTYPE , COUNTRY , STATE 
FROM class.c_customer
WHERE STATE = 'Arizona'
AND CUSTOMERTYPE = 'Home Office';
```

![](/assets/img/select_2.jpg)

---

- A로 시작하는 사람을 찾고 싶을 땐 **<u>'A%'</u>**를 사용
- A가 들어가는 사람을 찾을 땐 **<u>'%A%'</u>**을 사용

```sql
SELECT CUSTOMERID, CUSTOMERNAME, CUSTOMERTYPE , COUNTRY , STATE 
FROM class.c_customer
WHERE STATE = 'Arizona'
AND CUSTOMERNAME LIKE 'A%';
```

![](/assets/img/select_3.jpg)

# 표현식과 별칭

- **<u>데이터베이스에 없는 숫자나 문자를 표현하는 것</u>**
- 데이터베이스에 없는 100과 'Korea'를 추가

```sql
SELECT CUSTOMERID, CUSTOMERNAME, CUSTOMERTYPE , COUNTRY , STATE, 100, 'Korea'
FROM class.c_customer
WHERE STATE = 'Arizona'
AND CUSTOMERNAME LIKE 'A%';
```

- WHERE 조건에 맞는 데이터에 100과 Korea 데이터를 추가함

![](/assets/img/select_4.jpg)

---

```sql
SELECT CUSTOMERID, CUSTOMERNAME, CUSTOMERTYPE , COUNTRY , STATE, 100 as num, 'Korea' as nation
FROM class.c_customer
WHERE STATE = 'Arizona'
AND CUSTOMERNAME LIKE 'A%';
```

- 표현식에 각각 **<u>num, nation</u>**이라는 별칭을 붙임

![](/assets/img/select_5.jpg)

# 연결 연산자(CONCAT())

- 연결연산자 concat함수로 **<u>문자열을 결합</u>**할 수 있다
- CUSTOMERID와 STATE가 결합된 형태로 text_라는 이름으로 출력됨

```sql
SELECT CUSTOMERID, CUSTOMERNAME, CUSTOMERTYPE , COUNTRY , STATE, 100 as num, 'Korea' as nation,CONCAT(CUSTOMERID , STATE) as text_ 
FROM class.c_customer
WHERE STATE = 'Arizona'
AND CUSTOMERNAME LIKE 'A%';
```

![](/assets/img/select_6.jpg)

# Summary

- select절은 출력하는 데이터의 컬럼을 컨트롤 한다
- 출력되는 rows(옆에 있는 거 )는 where절을 통해서 컨트롤할 수 있음
- 표현식을 통해 저장되어 있는 않은 데이터를 활용할 수 있으며, 별칭으로 원하는 컬럼명으 부여 할 수 있음
- 연결 연산자를 이용해서 데이터를 붙여서 출력할 수 있음
