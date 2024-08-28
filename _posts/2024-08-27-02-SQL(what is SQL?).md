---
title: 02. SQL(What is SQL?)
Author: YoungHoon Ko
date: 2024-08-27 09:50:00 +0900
categories: [SQL, Practice_SQL]
tags: [sql, basic]
---
[toc]

# SQL의 정의와 역할

## SQL이란 무엇인가?

- SQL은 데이터베이스를 관리하는 언어이다

## 데이터베이스에서 SQL의 역할은 무엇인가?

- SQL을 통헤 데이터베이스 내 **객체를 생성, 변경, 삭제 할 수 있음**
- SQL을 통헤서 데이터베이스 내 **사용자를 관리할 수 있음**
- SLQ을 통해서 원하는 **데이터를 원하는 형태로 출력할 수 있음**

# SQL의 분류

## 1. DDL

- creat : 데이터베이스, 테이블 등을 생성
- alter : 테이블 수정
- drop : 데이터베이스, 테이블 삭제
- truncate : 테이블 초기화

## 2. DML

- select : 데이터 조회
- insert : 데이터 삽입
- update : 데이터 수정
- delete : 데이터 삭제(테이블 내 모든 데이터를 삭제할 수 있지만, truncate와는 다름)

## 3. DCL

- grant : 권한 부여
- revoke : 권환 회수
- commit : 트랜잭션의 작업을 **저장**
- rollback : 트랜잭션의 작업을 **취소, 복구**

# 정리

- 데이터베이스와 데이터베이스 툴을 헷갈리지 말자!!