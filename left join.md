# mysql
MySql的join（连接）查询 （三表 left join 写法）
----
### 1、内连接：将两个表中存在连结关系的字段符合连接条件的记录形成记录集

Select A.name,B.name from A inner join B on A.id=B.id和

Select A.name,B.name from A,B where A.id=B.id结果是一样的（内连接的inner关键字可省略）；

### 2、外连接：分为左外连接和右外连接

左连接A、B表结果包括A的全部记录和符合条件的B的记录。

右联结A、B表的结果和左联结B、A的结果是一样的，也就是说：

Select A.name,B.name from A Left Join B on A.id=B.id和

Select A.name,B.name from B Right Join A on B.id-A.id执行后的结果是一样的。

### 3、全联结

### 4、无联结

### 5、三表联结查询

select username,psw,gname,tel from (t1 left join t2 on t1.t1_id=t2.t1_id) left join t3 on t1.t1_id=t3.t1_id

### 6、终极的三表联结查询

items：商品表，item_visit_stats：商品访问表，item_trade_stats：商品销售表

SELECT i.num_iid, i.title, i.price, SUM(iv.user_visits) AS uv,it.buyer_num,it.item_num,it.item_num*i.price AS turnover
FROM (items AS i RIGHT JOIN item_visit_stats AS iv ON i.num_iid=iv.num_iid)
LEFT JOIN (SELECT num_iid,SUM(buyer_num) AS buyer_num,SUM(item_num) AS item_num FROM item_trade_stats
WHERE seller_nick="XXXX" AND business_day BETWEEN '2010-08-14' AND '2010-08-15' GROUP BY num_iid)
AS it ON it.num_iid=iv.num_iid 
WHERE i.nick="XXXX" AND iv.business_day BETWEEN '2010-08-14' AND '2010-08-15'
GROUP BY i.num_iid ORDER BY uv DESC
