### what is search 
input keyword then return all of the msgs which about your keyword

### type of search
- internet search
	- biggest datas
	- PB level

- site search (vertical search)
	- lesser datas 
	- easy to do
	- can use database

### full-text searching [全文检索] + [倒排索引] + [Lucene]
针对一个关键字 "笔记本电脑" 如果用户不小心输入成 "笔记电脑", 那么就会出现检索不到的现象
假设我们有一个product这个表来存储了所有可能的关键字，那么这个表里面只有 "笔记本电脑" 这个数据
当我们进行sql语句查询 "笔记电脑" 的时候，就会发现找不到相关数据
```select * from product where content like "%笔记电脑%";```

为了解决这个问题，可以采用分词 分表的思想
将原本的关键字"笔记本电脑" 分成 “笔记本” 和 “电脑” 两个关键字 (亦或者笔记， 笔记本， 电脑）
然后将对应的关键字存入一个新的表product_term表中
term  ids
笔记本 1
电脑 2

类似于这种的表，然后再去查询的话就是
``` select * from product_term where term = '电脑'; ```
``` select * from product_term where term = '笔记'; ```
然后将两条语句的搜索结果进行汇总，最终返回

上述
- 分词分表的表就是【倒排索引表】，里面的数据就是【倒排索引】
- 在倒排索引表中查询数据进行返回的这个过程就是【全文检索】
- Lucene 是一个jar包，里面封装了全文检索的相关算法




