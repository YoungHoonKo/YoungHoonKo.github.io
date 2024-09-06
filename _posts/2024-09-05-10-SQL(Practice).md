---

title: 10. SQL(Practice)
Author: YoungHoon Ko
date: 2024-09-05 12:50:00 +0900
categories: [SQL, Practice_SQL]
tags: [sql, basic, sql_p]
image: /assets/img/p_1.jpg
image: /assets/img/p_2.jpg
image: /assets/img/p_3.jpg
image: /assets/img/p_4.jpg
image: /assets/img/p_5.jpg
image: /assets/img/p_6.jpg
image: /assets/img/p_7.jpg
---
[toc]

# Practice

## 테이블 생성 및 데이터 입력

```sql
CREATE schema final_test ;
```

### RESERVATION 테이블

```sql
CREATE table final_test.RESERVATION (
R_ID  int auto_increment primary key,
FROM_DATE date ,
TO_DATE date ,
HOTEL_ID varchar(5) ,
GUSET_ID int ,
PERIOD int
);
```

```sql
INSERT INTO final_test.RESERVATION values
(null , '2023-01-01', '2023-01-05', 'p001', 1, 4) ;

INSERT INTO final_test.RESERVATION values
(null , '2023-01-02','2023-01-04', 'p003', 2, 2) ;

INSERT INTO final_test.RESERVATION value
(null , '2023-01-04', '2023-01-08', 'p003', 3, 4) ;

INSERT INTO final_test.RESERVATION values
(null , '2023-01-02', '2023-01-03', 'p002', 4, 1) ;

INSERT INTO final_test.RESERVATION values
(null , '2023-01-04', '2023-01-21', 'p002', 5, 17) ;

INSERT INTO final_test.RESERVATION values
(null , '2023-01-04', '2023-01-15', 'p004', 2, 11) ;

INSERT INTO final_test.RESERVATION values
(null , '2023-01-05', '2023-01-07', 'p003', 1, 2) ;

INSERT INTO final_test.RESERVATION values
(null , '2023-01-02', '2023-01-04', 'p004', 3, 2) ;

```



### HOTEL 테이블

```sql
CREATE table final_test.HOTEL (
HOTEL_ID varchar(5) primary key,
HOTEL_NAME varchar(50) ,
PRICE int
);
```

```sql
INSERT INTO final_test.HOTEL values
('p001', '써니호텔', 100000);

INSERT INTO final_test.HOTEL values
('p002', '레니얼호텔', 85000);

INSERT INTO final_test.HOTEL values
('p003', '청평호텔', 150000);

INSERT INTO final_test.HOTEL values
('p004', '국민호텔', 1280000);
```



### GUEST 테이블

```sql
CREATE table final_test.GUEST (
GUEST_ID int auto_increment primary key,
GUEST_NAME varchar(5)
);
```

```sql
INSERT INTO final_test.GUEST values
(null, '공아랑') ;

INSERT INTO final_test.GUEST values
(null, '산윤수') ;

INSERT INTO final_test.GUEST values
(null, '한수지') ;

INSERT INTO final_test.GUEST values
(null, '송영진') ;

INSERT INTO final_test.GUEST values
(null, '조승우') ;
```

### 테이블 확인

```sql
SELECT *
FROM final_test.RESERVATION r ;

SELECT *
FROM final_test.HOTEL h ;

SELECT *
FROM final_test.GUEST g ;
```

- RESERVATION

  ![](/assets/img/p_1.jpg)

- HOTEL

  ![](/assets/img/p_2.jpg)

- GUEST

  ![](/assets/img/p_3.jpg)

---

## 코드 작성

### <처리3>

```markdown
Database에서 아래 조건에 맞는 SQL문을 작성하세요.
(1) RESERVATION테이블에서 다음과 같은 순서로 컬럼이 출력되어야 합니다.
 - R_ID, HOTEL_ID, FROM_DATE, TO_DATE
(2) HOTEL_ID가 p003인 RESERVATION만 조회하세요.
```

### <쿼리>

```sql
SELECT R_ID , HOTEL_ID , FROM_DATE , TO_DATE 
FROM final_test.RESERVATION r 
WHERE HOTEL_ID = 'p003'
```

![](/assets/img/p_4.jpg)

---

### <처리4>

```markdown
Database에서 아래 조건에 맞는 SQL문을 작성하세요.
(1) RESERVATION 테이블에서 HOTEL_ID별 예약 손님의 수를 구하세요.
- 다음과 같은 순서로 컬럼이 출력되도록 합니다. (컬럼 이름이 다르다면 컬럼 alias로 사용할 것, 홑따옴표를 사용할 수 있음)
HOTEL_ID, 예약자수
```

### <쿼리>

```sql
SELECT r.HOTEL_ID , COUNT(*) as '예약자 수' 
FROM final_test.RESERVATION r join final_test.HOTEL h 
on r.HOTEL_ID = h.HOTEL_ID
JOIN final_test.GUEST g 
on r.GUSET_ID = g.GUEST_ID 
group by r.HOTEL_ID ;
```

![](/assets/img/p_5.jpg)

---

### <처리5>

```markdown
Database에서 아래 조건에 맞는 SQL문을 작성하세요.
(1) 다음과 같은 순서로 컬럼이 출력되도록 합니다.
 - R_ID, FROM_DATE, TO_DATE, HOTEL_NAME, PRICE, GUEST_NAME
(2) RESERVATION, HOTEL, GUEST를 JOIN하여 위 컬럼 순서로 조회하세요.
(3) GUEST_NAME을 오름차순으로 정렬하여 조회하세요.
```

### <쿼리>

```sql
SELECT r.R_ID , r.FROM_DATE , r.TO_DATE , h.HOTEL_NAME , h.PRICE , g.GUEST_NAME 
FROM final_test.RESERVATION r join final_test.HOTEL h 
on r.HOTEL_ID = h.HOTEL_ID
JOIN final_test.GUEST g 
on r.GUSET_ID = g.GUEST_ID
ORDER BY g.GUEST_NAME ASC ;
```

![](/assets/img/p_6.jpg)

---

### <처리6>

```markdown
Database에서 아래 조건대로 데이터가 출력되도록 SQL을 작성하세요.
(1) RESERVATION테이블에서 GUEST_ID별 PERIOD의 합계를 조회하세요.
(2) 컬럼순서는 다음과 같습니다. (alias 시 홑따옴표를 사용할 수 있음)
 - GUEST_ID, 총숙박일수
```

### <쿼리>

```sql
SELECT r.GUSET_ID , sum(r.PERIOD) as '총 숙박일 수' 
FROM final_test.RESERVATION r join final_test.GUEST g 
on r.GUSET_ID = g.GUEST_ID 
GROUP BY r.GUSET_ID 
```

![](/assets/img/p_7.jpg)

---

# Summary

- 쿼리를 작성할 때 요청 사항을 한국어로 작성해 보자
