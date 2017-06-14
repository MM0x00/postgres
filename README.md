# Postgres 在线实验环境

## 软件简介

PostgreSQL通常是简单的“Postgres”，是一种对象关系数据库管理系统（ORDBMS），重点是可扩展性和标准合规性。作为数据库服务器，其主要功能是存储数据，安全地并支持最佳实践，并根据其他软件应用程序的要求，随时检索数据，无论是在同一台计算机上还是在网络上的另一台计算机上运行（包括互联网）。它可以处理从小型单机应用程序到具有许多并发用户的大型面向Internet的应用程序的工作负载。最近的版本还提供数据库本身的复制以实现安全性和可扩展性

所属类别是数据库

特点：

1.丰富的数据类型支持

2.支持大部分类型的数据库客户端接口

## 软件官网

https://www.postgresql.org/

## Dockerfile 使用方法

### 如何使用
### 启动postgres实例
```
$ docker run --name some-postgres -e POSTGRES_PASSWORD=mysecretpassword -d postgres
```
此包括EXPOSE 5432（postgres端口），因此标准容器链接将使其自动可用于链接的容器。默认postgres用户和数据库是在entrypoint中创建的initdb。
```
postgres数据库是用于用户，实用程序和第三方应用程序使用的默认数据库。
postgresql.org/docs
```
### 从应用程序连接到它
```
$ docker run --name some-app --link some-postgres:postgres -d application-that-uses-postgres
```
### 或通过 psql
```
$ docker run -it --rm --link some-postgres:postgres postgres psql -h postgres -U postgres
psql (9.5.0)
Type "help" for help.

postgres=# SELECT 1;
 ?column? 
----------
        1
(1 row)
```
## 资源链接

- https://en.wikipedia.org/wiki/PostgreSQL
