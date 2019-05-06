---
title: mongoose使用
date: 2018-10-22 15:15:00
tags: nodeJS
---

> mongoose.model.find()

Model.find(query, fields, options, callback)
query: 查询参数
fields: 返回字段
options: 限制条件
callback: 回调函数

如：
```
// 查询 _id=5bcd732344309e24369c2266 的数据记录，只返回以下字段：_id,sysPlat,createTime，{ skip: 1 }是跳过第一条数据开始查询
PojoModel.find({'_id': '5bcd732344309e24369c2266'}, ['_id','sysPlat','createTime'], { skip: 1 }).exec(function(err, pojos) {
        console.log(pojos);
        success(pojos);
      });
```
