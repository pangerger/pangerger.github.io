---
title: mybatis
date: 2020-05-28 19:39:30
tags: mybatis
---

使用 mybatis 常改的地方  

<!-- more -->

# 常用法

## 集合 foreach

``` xml
xml 为：普通in用法
<if test="record.typeList != null and record.typeList.size()>0 ">
    AND type in
    <foreach collection="record.typeList" open="(" close=")" item="type" separator=",">
        #{type}
    </foreach>
</if>

sql：
and type in(1,2,3)

==============================
like foreach:
<if test="record.typeList != null and record.typeList.size()>0 ">
    AND 
    <foreach collection="record.typeList" open="(" close=")" item="type" separator="or">
      type like concat('%',#{type},'%') 
    </foreach>
</if>
sql:
and (type like concat('%',1,'%') or type like concat('%',2,'%') or type like concat('%',3,'%') )
```



# 疑问

> 参数 父类 子类

``` java

》Food 为 父类 , Apple 为子类，子类多了一个属性叫 type

// mapper 接口里 
/**
 * 查询记录列表
 *
 * @param record
 * @return
 */
List<Food> selectByType(@Param("record") Food record,
                        @Param("pageBegin") int pageBegin,
                        @Param("pageSize") int pageSize);

// Service 层: 显然这是没问题的 接口要一个父类，使用时给子类
Apple apple = new Apple;
apple.setType(1);
List<Food> foods = selectByType(apple,-1,-1);
    
问题来了：：：：：=============》》》》》》》》》
// xml 里 record.type 为啥可以呢? 当然 我们知道 此时 record 是一个 Apple! 但它的原理是啥？？？
<if test="record.type != null and record.type!='' ">
    id = #{record.type}
</if>
```

