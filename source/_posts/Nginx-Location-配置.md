---
title: Nginx Location 配置
date: 2020-01-20 11:03:36
tags:
- Nginx
categories:
- 教程
---

<center>一些nginx中location的匹配规则</center>
<!-- more -->

## 「=」 修饰符：要求路径完全匹配

```sh
server {
	server_name localhost;
	location = /test-url {
		......
	}
}
```

## 「^~」修饰符：前缀匹配路径

```shell
server {
    server_name website.com;
    location ^~ /abcd {
    […]
    }
}
```

## 「~」修饰符：区分大小写的正则匹配

```shell
server {
    server_name website.com;
    location ~ ^/abcd$ {
    […]
    }
}
```

## 「~*」修饰符：不区分大小写的正则匹配

```shell
server {
    server_name website.com;
    location ~* ^/abcd$ {
    […]
    }
}
```

当有多条location规则是，Nginx有相应的优先级：

1. 精确匹配 `=`
2. 前缀匹配 `^~`
3. 按文件中的顺序正则匹配 `~` 和 `~*`
4. 匹配不带任何修饰的前缀匹配

## 案例分析

### 案例 1

```shell
server {
    server_name website.com;
    location /doc {
        return 701; # 用这样的方式，可以方便的知道请求到了哪里
    }
    location ~* ^/document$ {
        return 702; # 用这样的方式，可以方便的知道请求到了哪里
    }
} 
```

`curl -I  website.com:8080/document` 返回 `HTTP/1.1 702`

按照上述的规则，第二个会有更高的优先级

### 案例2

```sehll
server {
    server_name website.com;
    location /document {
        return 701;
    }
    location ~* ^/document$ {
        return 702;
    }
}
```

`curl -I  website.com:8080/document` 返回 `HTTP/1.1 702`

第二个匹配了正则表达式，优先级高于第一个普通前缀匹配

### 案例 3

```
server {
    server_name website.com;
    location ^~ /doc {
        return 701;
    }
    location ~* ^/document$ {
        return 702;
    }
}
```

`curl http://website.com/document`  返回 `HTTP/1.1 701`

第一个前缀匹配`^~`命中以后不会再搜寻正则匹配，所以会第一个命中

### 案例 4

```shell
server {
    server_name website.com;
    location /docu {
        return 701;
    }
    location /doc {
        return 702;
    }
}
```

`curl -I website.com:8080/document` 返回 `HTTP/1.1 701`，

```shell
server {
    server_name website.com;
    location /doc {
        return 702;
    }
    location /docu {
        return 701;
    }
}


```

`curl -I website.com:8080/document` 依然返回 `HTTP/1.1 701`

前缀匹配下，返回最长匹配的 location，与 location 所在位置顺序无关

### 案例 5

```shell
server {
	listen 8080;
	server_name website.com;

    location ~ ^/doc[a-z]+ {
        return 701;
    }

    location ~ ^/docu[a-z]+ {
        return 702;
    }
}


```

`curl -I website.com:8080/document` 返回 `HTTP/1.1 701`

把顺序换一下

```sehll
server {
	listen 8080;
	server_name website.com;

    location ~ ^/docu[a-z]+ {
        return 702;
    }
    
    location ~ ^/doc[a-z]+ {
        return 701;
    }
}


```

`curl -I website.com:8080/document` 返回 `HTTP/1.1 702`

正则匹配是使用文件中的顺序，找到返回

