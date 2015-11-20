---
layout: post
category: 技术
title: rethinkdb开源数据库
tags: web
---

###[rethinkdb官网](http://www.rethinkdb.com/)

- db 命令选择数据库 test(默认数据库名称为test)
- table_create 命令创建数据表
- 最后 run 命令将查询发送到了服务端
- 运行 r.table('authors') 查询就可以得到表 authors 中的所有数据项：
- 通过 filter 方法可以根据条件进行数据过滤

		 r.table("authors").filter(r.row["name"] == "William Adama").run()
- RethinkDB 帮助我们生成了，可以通过generated_keys 得到
- 通过主键查询数据项：

		r.db('test').table('authors').get('7644aaf2-9928-4231-aa68-4e65e31bf219').run()
- 更新 authors 表，添加新字段 type 并设置为 fictional，注意到所有数据项的 type 字段的值都变成了 "fuctional"：8/24/2015 11:22:43 AM 

		r.table("authors").update({"type": "fictional"}).run()
		r.table("authors").filter(r.row['name'] == "William Adama").update({"rank": "Admiral"}).run()
- Jean-Luc Picard 新发表了一篇文章：
		
		r.table('authors').filter(r.row["name"] == "Jean-Luc Picard").update({"posts": r.row["posts"].append({
        "title": "Shakespeare",
        "content": "What a piece of work is man..."})
   		 }).run()
- 删除文章数小于3的数据项

		r.table("authors").
   			 filter( r.row["posts"].count() < 3 ).
    		 delete().run()