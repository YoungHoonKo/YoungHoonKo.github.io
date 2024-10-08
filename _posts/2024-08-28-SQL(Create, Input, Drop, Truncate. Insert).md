---
title: 03. SQL(Create, Input, Drop, Truncate. Insert)
Author: YoungHoon Ko
date: 2024-08-28 11:45:00 +0900
categories: [SQL, Practice_SQL]
tags: [sql, basic]
image: /assets/img/create_table.jpg
image: /assets/img/input_data.jpg
image: /assets/img/test_table2.jpg
image: /assets/img/test_table3.jpg
image: /assets/img/drop.jpg
image: /assets/img/create_table.jpg
image: /assets/img/insert.jpg
---
[toc]

# 스키마와 테이블의 정의

## 스키마란 무엇인가?

- 테이블이나 뷰 또는 프로시저와 펑션 등 업무나 데이터의 **<u>영역별로 구분되는 개념</u>**
- 테이블들과 다양한 객체를 가진 집합

## 테이블이란 무엇인가?

- 데이터가 물리적으로 저장되는 **<u>단위</u>**
- 테이블이 모여서 하나의 스키마, 또는 데이터베이스가 되며 다른 오브젝트들의 원천이 됨
- 모든 객체나 오브젝트는 테이블을 기반으로 관리 됨

---

# Creat, Insert

- Create : 테이블 혹은 스키마를 생성하는 명령어
- Insert : 테이블에 데이터를 입력하는 명령어

```sql
-- Create 실습;
create schema test_schema;

create table test_schema.test_table(
id int ,
name varchar(100), -- 최대 name의 길이를 입력함;
input_data date
);

-- test_table 생성 확인;
select *
from test_schema.test_table tt;
-- 단일 테이블 조회 시 tt{알리아스(별칭)}는 있어도 ,없어도 상관 없음;

insert into test_schema.test_table values
(1, '홍길동','2024-08-28');

insert into test_schema.test_table values
(2, '고길동','2024-08-29');

insert into test_schema.test_table values
(3, '김길동','2024-08-30');
```

- **<u>test_table</u>**을 생성함

![](/assets/img/create_table.jpg)

- test_table에 insert를 사용해 데이터를 입력함

![](/assets/img/input_data.jpg)



## as와 like

- as

```sql
-- as는 복제하고자 하는 테이블의 칼럼과 데이터 모두 다 복제하는 것;
create table test_schema.test_table2
as select * from test_schema.test_table;

select *
from test_schema.test_table2;
```

![](/assets/img/test_table2.jpg)



- Like

```sql
-- like는 데이터를 제외한 칼럼을 복제하는 것;
create table test_schema.test_table3
like test_schema.test_table;

select *
from test_schema.test_table3;
```

![](/assets/img/test_table3.jpg)

---

# Drop, Truncate

- drop : **<u>테이블 자체를 삭제하는 명령어</u>**(데이터도 물론 같이 삭제 됨)
- truncate : 테이블은 그대로 두고 데이터만 삭제하는 명령어(**<u>drop & create와 같음</u>**)

```sql
-- Drop 실습;
drop table test_schema.test_table3;
```

- 테이블 test_table3 삭제

![](/assets/img/drop.jpg)

```sql
-- Truncate 실습;
truncate table test_schema.test_table2;
select *
from test_schema.test_table2;
```

- 테이블은 유지한 상태로 **<u>데이터만 삭제</u>**

![](/assets/img/create_table.jpg)



---

# Insert

- Insert문 사용법

```sql
-- insert 실습;

-- test_table 조회
select * 
from test_schema.test_table;

-- 데이터 추가 방법 1 : 칼럼 만든 순서대로 데이터 입력
insert into test_schema.test_table values
(1, '홍길동','2024-08-28');

-- 데이터 추가 방법 2 : test_table() 안에 칼럼 순서를 자유롭게 적고 순서에 맞게 values에 입력
insert into test_schema.test_table(name, id, input_data) values
('박길동', 2, '2024-09-01');

-- 데이터 추가 방법 3 : 입력 안 하는 데이터는 마찬가지로 칼럼에서 빼고 순서에 맞게 입력
insert into test_schema.test_table (id, input_data) values
(1,'2024-08-28');
```

![](/assets/img/insert.jpg)

---

# Summary

- 스키마는 뷰나 데이터의 **<u>영역별로 구분되는 개념</u>**
- 테이블은 데이터가 물리적으로 저장되는 **<u>단위</u>**
- create : 테이블 혹은 스키마를 생성하는 명령어
- input : 테이블에 데이터를 입력하는 명령어
- drop : **<u>테이블 자체를 삭제하는 명령어</u>**(데이터도 물론 같이 삭제 됨)
- truncate : 테이블은 그대로 두고 데이터만 삭제하는 명령어(**<u>drop & create와 같음</u>**)

