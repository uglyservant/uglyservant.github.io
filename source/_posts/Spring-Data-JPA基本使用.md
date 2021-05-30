---
title: Spring Data JPA基本使用
date: 2020-03-12 10:10:02
tags:
- Spring Data JPA
- Java
- SQL
categories:
- 教程
---

<div style="text-align: center;">有时候Java开发用用JPA还不错</div>
<!-- more -->

## Spring Boot项目下Spring Data JPA的常用配置

```yaml
server:
  port: 8081
  
spring:
  datasource:
    url: jdbc:mysql:///jap?serverTimezone=GMT%2B8&useSSL=false
    driver-class-name: com.mysql.cj.jdbc.Driver
    username: root
    password: root
    hikar:
      idle-timeout: 30000
      connection-timeout: 10000
      maximum-pool-size: 15
      minimum-idel: 5
      auto-commit: true
  jpa:
    hibernate:
      ddl-auto: update
    show-sql: true
    properties:
      hibernate:
        dialect: org.hibernate.dialect.MySQL5InnoDBDialect
```

