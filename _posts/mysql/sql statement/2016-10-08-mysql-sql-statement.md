---
layout: post
title: sql积累
description: sql积累
keywords: sql
category : sql 语句
tags : [sql , sql语句]
---


1.显示某个库中所有表的名字和表的comment说明.

```
select table_name, table_comment from information_schema.tables where table_schema = 'dbname'; 
```

