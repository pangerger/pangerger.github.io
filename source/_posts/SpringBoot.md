---
title: SpringBoot
date: 2019-07-21 15:26:57
tags: spring
categories:
---

SpringBoot in learning

<!-- more -->





# 教程

<https://github.com/pangerger/springboot-learning-example>



# error

## idea 中所有注解无效

classpath有问题，创建项目时出错。

# 每日搜索

## hashmap为何查找那么快

O(1)???

<http://www.51gjie.com/java/679.html>

看图：<http://www.51gjie.com/Images/image1/lo5salay.lco.jpg>



# idea

## idea 中导入已有项目

直到点击pom.xml文件为止

<https://blog.csdn.net/Happy_wu/article/details/80423150>

## 取消对某文件的索引

<https://zhuanlan.zhihu.com/p/36305203>

> project struct中 model里设置。

# 登陆

## 权限管理

> token + redis + 网关
>
> > token本身是一个字符串，服务器生成发给客户端
> >
> > 客户端每次请求都带上这个token，服务端校验它。



### 初步了解

<https://www.jianshu.com/p/5b914dd6a4ef>

> 一个tokenController
>
> ITokenService及其实现类TokenService
>
> 拦截器

====



<https://www.zhihu.com/question/274566992>

jwt及redis+token

<https://www.jianshu.com/p/5b914dd6a4ef>



># [服务网关 Zuul 与 Redis 结合实现 Token 权限校验](https://segmentfault.com/a/1190000017058010)s
>
><https://segmentfault.com/a/1190000017058010>



## 什么是token

> 英文：代价卷，礼卷
>
> 计算机术语：令牌	

<https://blog.csdn.net/daimengs/article/details/81088172>

> token的意思是“令牌”，是服务端生成的一串字符串，作为客户端进行请求的一个标识。
>
> token的使用的是https???
>
> 在网络层面上token使用明文传输的话是非常危险的，所以一定要使用HTTPS协议。

## Base64加密

<https://www.zhihu.com/question/38036594/answer/74917716>

> 用64个可读字符进行编码，来表示二进制。
>
> ``` java
> 数字：0,1,2,3,4,5,6,7,8,9，共10个小写字母：a,b,c,d,e,f,g,h,i,j,k,l,m,n,o,p,q,r,s,t,u,v,w,x,y,z，共26个大写字母：A,B,C,D,E,F,G,H,I,J,K,L,M,N,O,P,Q,R,S,T,U,V,W,X,Y,Z，共26个
> +以及斜杠/
> ```
>
> **常用于在互联网中传输字节**
>
> >https://blog.csdn.net/qq_20545367/article/details/79538530
> >
> >Base64一般用于在HTTP协议下传输二进制数据，由于HTTP协议是文本协议，所以在HTTP协议下传输二进制数据需要将二进制数据转换为字符数据。然而直接转换是不行的。因为网络传输只能传输可打印字符。什么是可打印字符？在ASCII码中规定，0~31、127这33个字符属于控制字符，32~126这95个字符属于可打印字符，也就是说网络传输只能传输这95个字符，不在这个范围内的字符无法传输。那么该怎么才能传输其他字符呢？其中一种方式就是使用Base64。
> ---------------------
> 问题？  
>
> > http 可传输字符？？
> >
> > 怎么编码？？？ 什么是用=补零。
>
> <http://linuxsogood.org/1227.html>
>
> > Base64编码仅用于一个可打印ASCII字符就可以安全转换任何进进制数据，它常用于对电子邮件附件进行编码，使其通过SMTP安全传输。它还可以用在基本HTTP验证机制中对用户证书进行编码
> >
> > 许多Web应用程序利用Base64编码在cookie与其他参数中传递二进制数据，甚至用它打乱敏感数据以防止即使是细微的修改。应该总是留意并解码发送到客户端的任何Base64数据，由于这些数据使用特殊的字符集，而且有时会在字符串末尾添加补足字符，因此可以轻易辨别出Base64编码的字符串

``` java

//使用java自带的base64编码
==============================================
  import java.util.Base64;
  // 编码
        String encode = Base64.getEncoder().encodeToString("So".getBytes("UTF-8"));
        System.out.println(encode);
        // 解码
        byte[] decode = Base64.getDecoder().decode(encode);
        System.out.println(new String(decode, "UTF-8"));

 --------------------- 
 版权声明：本文为CSDN博主「艾华生」的原创文章，遵循CC 4.0 by-sa版权协议，转载请附上原文出处链接及本声明。
 原文链接：https://blog.csdn.net/qq_20545367/article/details/79538530
 
====================
    
    
```


## 参考资料

>  API 接口设计中Token设计讨论<https://www.jianshu.com/p/9fdcfd950292>
> <http://linuxsogood.org/1227.html>




# 数据库

## mysql优化

> <https://dbaplus.cn/news-155-1531-1.html>
>
> ``` mysql
> mysql> select * from t_message limit 10;
> 
> ...省略结果集
> 
>  
> 
> mysql> show status like 'last_query_cost';
> 
> +-----------------+-------------+
> 
> | Variable_name   | Value       |
> 
> +-----------------+-------------+
> 
> | Last_query_cost | 6391.799000 |
> 
> +-----------------+-------------+
> ```
>
>

### mysql mvcc

> <https://blog.csdn.net/whoamiyang/article/details/51901888>
>
>

# java se

## 循环

> 使用 List.foreach()方法或foreach方法来操作add  remove是会出异常的。
>
> 所以应该使用迭代器的方式来做。
>
> <https://zacard.net/2016/01/07/list-remove/>



## 正则表达式，判断是否含有中文

><https://blog.csdn.net/z69183787/article/details/53162015>
>
><http://www.micmiu.com/lang/java/java-check-chinese/>



# Spring 拦截器

**HandlerInterceptor**

> <https://www.jianshu.com/p/dc5cc2e25ab2>
>
> 三个重载方法



