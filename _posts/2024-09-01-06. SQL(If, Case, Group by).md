---

title: 06. SQL(If, Case, Group by)
Author: YoungHoon Ko
date: 2024-09-01 10:50:00 +0900
categories: [SQL, Practice_SQL]
tags: [sql, basic, sql_p]
image: /assets/img/if_1.jpg
image: /assets/img/if_2.jpg
image: /assets/img/null_0.jpg
image: /assets/img/if_3.jpg
image: /assets/img/group_1.jpg
image: /assets/img/group_2.jpg
image: /assets/img/group_3.jpg
---
[toc]

# 분기문

## 내장 함수의 정의

- 데이터를 특정 조건에 맞게 변형하여 처리하는 문법

## 분기문의 종류

- If - 조건이 하나일 때
- Case - 조건이 하나 이상일 때
- Group by - **<u>여러 개의 rows를 하나의 row로 만들 수 있음</u>**
  - **<u>Group by문은 꼭 집계 함수와 함께 사용함</u>**


---

# If, Case

```sql
CREATE table class.exam (
id int auto_increment primary key
, name varchar(100)
, math int
, english int
);

INSERT INTO class.exam values (null, 'Mike', 100, 100);
INSERT INTO class.exam values (null, 'John', 96, 84);
INSERT INTO class.exam values (null, 'Cole', 83, 66);
INSERT INTO class.exam values (null, 'Jordan', 100, 100);
INSERT INTO class.exam values (null, 'Curry', 76, 93);
INSERT INTO class.exam values (null, 'Lebron', 58, 89);

SELECT *
FROM class.exam;
```

![](/assets/img/if_1.jpg)

```sql
SELECT name, math
, IF(math>=80, 'good', 'try') as Feedback
, english
, CASE when english >= 90 then '수'
	     when english >= 80 then '우'
	     when english >= 70 then '미'
	     when english >= 60 then '양'
  ELSE '가' end as english
FROM class.exam;
```

![](/assets/img/if_2.jpg)

- math가 80점 이상인 사람은 피드백 컬럼에 good 아니면 try를 보여주는 조건을 걸었음
- english는 여러가지 조건을 걸기 위해 case문을 사용
- case 조건에 부합하지 않을 경우 else문로 처리함
  - **<u>마지막에 'end'는 꼭 적어야 함</u>**

- case문은 위에서 아래로 실행하기 때문에 **<u>조건의 범위를 큰 것에서 작은 것으로 좁혀야 함</u>**
- case문의 마지막에는 꼭 end로 마무리~

## Ifnull

- null과 0의 차이

![](/assets/img/null_0.jpg)

```sql
INSERT INTO class.exam values (null, 'Kim', null, null);

SELECT name
, math
, IFNULL(math, 0) as in_ -- 만약 math = null 이면 0을 출력함
FROM class.exam;
```

![](/assets/img/if_3.jpg)

- **null은 0이 아님**

- 알 수 없는 값으로 연산을 하더라도 **<u>모든 값이 null로 출력</u>** 

  ```sql
  SELECT 100 + null; -- null 출력
  ```

---

# Group by

- group by는 하나의 조건으로 여러 개의 rows를 하나로 묶어줌 

```sql
SELECT STATE, COUNT(*) as cnt 
FROM class.c_customer
group by state;
```

![](/assets/img/group_1.jpg)

- 이 데이터 중 STATE를 Group by로 묶어서 각 주마다 몇명이 살고있는지 확인

![](/assets/img/group_2.jpg)

```sql
SELECT BIGCATEGORY, COUNT(*) as cnt, PRICE 
FROM class.c_product
group by BIGCATEGORY;
```

- 위의 코드는 오류가 발생한다 왜?
  - **<u>Price를 집계 함수를 사용하지 않을 시 중복 데이터를 처리할 수 없어서 오류가 발생</u>**
  - **<u>group by절로 묶는 컬럼 이외에는 모두 집계함수로 사용해야 함</u>**

```sql
SELECT BIGCATEGORY, SUBCAREGORY,  COUNT(*) as cnt, sum(price) as sum
, max(PRICE) as max_
, min(PRICE) as min_
FROM class.c_product
group by BIGCATEGORY, SUBCAREGORY;
```

![](/assets/img/group_3.jpg)

- price를 sum 함수로 묶어서 사용하면 문제 없이 사용할 수 있음

---

# Summary

- 분기문은 특정 데이터를 조건에 맞게 변형하여 처리하는 문법
- 조건이 하나면 if문, 여러 개면 case문 사용
  - case문 사용시 end 입력 중요
- group by문은 하나의 조건으로 여러 개의 row를 하나의 row로 묶어줌
- **<u>group by절로 묶는 컬럼 이외에는 모두 집계함수로 사용해야 함</u>**

