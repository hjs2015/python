# Day 11: day11 协程 安装认识数据库 数据库表数据的增删改查 数据库类型 外键 单表多表

> 对应原课程：day11_协程_安装认识数据库_数据库表数据的增删改查_数据库类型_外键_单表多表

---

## 1. 1.协程.py

### 📋 运行结果

```

0
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29

```

### 💻 完整代码

```python

# ### 协程
"""安装gevent的模块"""

# (1) 用协程改写生产者消费者模型
def producer():
	for i in range(1000):
		yield i

def consumer(gen):
	for i in range(10):
		print(next(gen))

# 初始化生成器函数
gen = producer()
consumer(gen)
consumer(gen)
consumer(gen)

# (2) 协程的具体实现
"""不能自动识别阻塞,必须手动写,switch是协程任务之间的来回切换."""
"""
from greenlet import greenlet
import time
def eat():
	print("eat1")
	g2.switch()
	time.sleep(2)
	print("eat2")
	
def play():
	print("play1")
	time.sleep(2)
	print("play2")
	g1.switch()
	
g1 = greenlet(eat)
g2 = greenlet(play)
g1.switch()
"""
# (3) gevent
"""gevent 是可以自动切换的,只不过不能自动识别阻塞"""
"""
import gevent
import time
def eat():
	print("eat1")
	time.sleep(2)
	print("eat2")
	
def play():
	print("play1")
	time.sleep(2)
	print("play2")

#
g1 = gevent.spawn(eat)
g2 = gevent.spawn(play)

g1.join()
g2.join()

print("程序结束")
"""

# (4) gevent (解决方法一,用gevent.time来取代time模块,以识别阻塞))
"""
import gevent
def eat():
	print("eat1")
	gevent.sleep(2)
	print("eat2")
	
def play():
	print("play1")
	gevent.sleep(2)
	print("play2")

# 利用gevent 创建协程对象g1
g1 = gevent.spawn(eat)
# 利用gevent 创建协程对象g2
g2 = gevent.spawn(play)

# 阻塞,必须等到g1任务执行完毕之后在放行
g1.join()
# 阻塞,必须等到g2任务执行完毕之后在放行
g2.join()

# 默认主线程不会等待协程任务就会终止程序.
print("程序结束")
"""
# (5) 终极版本 (彻底解决不认识阻塞的情况)
from gevent import monkey
monkey.patch_all() # 把下面所有引入的模块中的阻塞识别一下

import time
import gevent

import gevent
def eat():
	print("eat1")
	time.sleep(2)
	print("eat2")
	
def play():
	print("play1")
	time.sleep(2)
	print("play2")

# 利用gevent 创建协程对象g1
g1 = gevent.spawn(eat)
# 利用gevent 创建协程对象g2
g2 = gevent.spawn(play)

# 阻塞,必须等到g1任务执行完毕之后在放行
g1.join()
# 阻塞,必须等到g2任务执行完毕之后在放行
g2.join()

# 默认主线程不会等待协程任务就会终止程序.
print("程序结束")

```

### 📖 要点讲解

- (4) gevent (解决方法一,用gevent.time来取代time模块,以识别阻塞))

- (5) 终极版本 (彻底解决不认识阻塞的情况)

---

## 2. 1.笔记.py

### 📋 运行结果

```

错误：  File "/tmp/python3_course/day11_协程_安装认识数据库_数据库表数据的增删改查_数据库类型_外键_单表多表/代码/1.笔记.py", line 3
    d:  -> 切换到d盘
        ^^
SyntaxError: invalid syntax

```

### 💻 完整代码

```python

# ### 安装mysql => 通过超级管理员打开cmd黑窗口
# 切换路径
d:  -> 切换到d盘
dir -> 看一下盘符里面有什么
cd MySQL5.7
cd mysql-5.7.25-winx64
cd bin
# 执行命令
mysqld --initialize-insecure --user=mysql
mysqld install
# 启动mysql
net start mysql
# mysql>  安装成功 !!

# windows (启动或者关闭数据库,必须在超级管理员的身份下才能执行)
net start mysql
net stop mysql

# ### part1 
数据库: 关系型数据库 非关系型数据库
关系型数据库 : mysql , oracle , sql server
(把数据存储在文件,有行有列这样的结构表里,支持复杂的sql查询和事务处理)

非关系型数据库 : redis mongodb
(把数据存储在内存,以键值对这样的结构进行存储,没有关系表结构,读取速度较快)

# 存储引擎 (数据的存储方式)
innodb : 支持事务处理 , 行级锁 , 外键
myisam : 表级锁
	事务处理: 操作多条sql语句时,必须全部成功,才能最终提交数据,否则默认回滚,恢复到原来的状态;
	表级锁 : 有一个线程在操作文件,其他线程需要等待,不能同一时间多个用户修改同一个表文件
	行级锁 : 多个线程操作同一个数据表文件,只单独锁定要修改的这一行,可以支持多线程的并发修改;
	外键   : 把多个表通过关联字段连接在一起,要改全改,要删全删.

# ### part2 
# 登录数据库
mysql -u(用户名) -p(密码) -h(ip地址,默认本地) 
mysql -uroot -p (默认连接的本地数据库 127.0.0.1 <=> localhost )
mysql -uroot -p -h 14.215.177.38 (远程连接数据库)

# 退出 
exit;

# 授权用户登录到mysql数据库中
grant 权限 on 数据库.表 to "用户名"@"ip地址" identified by "密码"
"""
权限
all  代表所有权限
select 查看数据库权限
insert 插入数据库权限
update 修改数据库权限
delete 删除数据库权限
...
* 代表所有数据库,所有表
% 所有的ip都可以
"""
grant all on *.* to "ceshi12345"@"%" identified by "12345";
# 刷新权限,立刻生效
flush privileges

# mysql设置密码
# 查看当前登录的用户是谁
select user();
# 设置当前用户的密码
set password = password("33445566")
# 去除密码
set password = password("")

# ###part3.数据库的增删改查 (必须掌握)
# (1)操作数据库(文件夹)
增
	# 创建db数据库,设置字符集为utf8
	create database db1 charset utf8;

查:
	# 显示所有的数据库
	show databases;
	# 查看建库语句
	show create database db1; # CREATE DATABASE `db2` /*!40100 DEFAULT CHARACTER SET utf8 */ |

改:
	# 更改数据库的字符集
	alter database db1 charset gbk;
删:
	# 删除数据库db1
	drop database db1;

# (2)操作数据表(文件)
+-------+---------+------+-----+---------+-------+
| Field | Type    | Null | Key | Default | Extra |
+-------+---------+------+-----+---------+-------+
| id    | int(11) | YES  |     | NULL    |       |
| name  | char(1) | YES  |     | NULL    |       |
+-------+---------+------+-----+---------+-------+
use 数据库 (创建表之前需要先选择数据库)
增
	"""int 整数类型  char 字符串类型 enum 枚举类型"""
	create table t1(id int , name char);

查:
	# 显示所有数据表
	show tables
	# 查看表结构
	desc t1;
	# 查看建表语句
	show create table t1;
	# 垂直显示内容
	show create table t1\G 
	"""
	CREATE TABLE `t2` (
	  `id` int(11) DEFAULT NULL,
	  `name` char(1) DEFAULT NULL
	) ENGINE=InnoDB DEFAULT CHARSET=utf8
	"""
改:
	# modify 专门用来修改数据类型 , 指定char类型长度为4
	alter table t2 modify name char(4);
	# change 连名带类型一起改掉
	alter table t2 change name name666 char(1);
	# add 添加字段
	alter table t2 add sex enum("男性","女性");
	# drop 删除字段
	alter table t2 drop name666;
	# rename 更改表名
	alter table t2 rename t3;

删:
	# 删除表t3
	drop table t3;

# (3) 操作记录: (实例文件里面的内容)
增:
	# 一次插入一条数据
	insert into t1(id,name) values(1,"a");
	# 一次插入多条数据
	insert into t1(id,name) values(2,"b") ,(3,"c"),(4,"d");
	# 可以不指定具体某字段插入数据,但是要保证一一对应
	insert into t1 values(5,"e");
	# 可以具体指定某个字段进行插入
	insert into t1(id) values(6)
查:
	# 查询所有
	select * from t1;
	select id from t1;
	select t1.name from t1;
	# 查询当前数据库
	select database();
改:
	# update 表名 set 字段=值 where 条件
	update t1 set name = "z" where id = 1;
	# 不加条件该表所有
	update t1 set name = "z";
删:
	# 指定id删除
	delete from t1 where id = 1;
	# 删除所有
	delete from t1;
	# 重置表 (删除数据 + 重置id)
	truncate table t1;

# 事务处理
# 开始事务
begin;
# 修改数据
update t1 set name="c" where id = 1
# 回滚到初始状态
rollback;
# 最后提交数据
commit

# ### part4 数据类型
# 整型
tinyint: 1个字节 有符号(-128 ~ 127) 无符号 (0~255) unsigned 小整数
int    : 4个字节 有符号(-21亿 ~ 21亿作用) 无符号 (0~42亿) unsigned 大整数,范围更大
	
	create table t1(id int  ,sex tinyint);
	insert into t1 values(4200000000,1); error
	insert into t1 values(100,299); error
	insert into t1 values(1,0); 
	
# 浮点型
float(255,30)  单精度
double(255,30) 双精度
decimal(65,30) 金钱类型
	# float(5,2) 小数点后保留2为,整体长度是5位
	create table t2(f1 float(5,2),f2 double(5,2),f3 decimal(5,2))
	insert into t2 values(1.45678,1.45678,1.45678);
	
	# float和double比较,double小数位保留的更多,decimal默认只保留整数,存在四舍五入.
	create table t3(f1 float,f2 double,f3 decimal);
	insert into t3 values(12345.6789123488888888888,12345.6789123488888888888,12345.6789123488888888888);

	# 总长度是5,小数点最多保留2位,整数部分最多保留3位.
	create table t4(f1 float(5,2));
	insert into t4 values(123.456789);
	insert into t4 values(12345.456789); error
	insert into t4 values(12.456789);
	
# 字符串
char(11)    : 定长,固定开辟11个长度大小的空间 (手机号,身份证)
varchar(11) : 变长,动态开辟最大11个长度空间   (姓名,评论)
text        : 存大文本,(论文,小说 ... )
	# char(4) varchar(4) 代表字符的个数不能超过4个
	# char 最大不超过255个字符.varchar 最大不超过21845个字符
	# 有时不确定varchar是多少个字符上线,可以先写255个在调;
	create table t5(c char(4),v varchar(4),t text);
	insert into t5 values("你好啊啊","你好啊啊","sfsdfsd");
	insert into t5 values("你好啊啊","你好啊啊2","sfsdfsd");
	
# 时间类型 
"""select now() 获取的是当前的时间"""
date     YYYY-MM-DD  年月日 (出生日期)
time     HH:MM:SS    时分秒 (竞速比赛)
year     YYYY        年份   (红酒的制造年份)
datetime YYYY-MM-DD HH:MM:SS 年月日时分秒 (登录,注册,下单,退款时间)
	create table t6(d date ,t time , y year ,dt datetime);
	insert into t6 values("2020-09-20","14:46:50","2020","2020-09-20 14:46:50");
	# 默认以当前时间进行更新;
	insert into t6 values(now(),now(),now(),now());

timestamp YYYYMMDDHHMMSS 时间戳 系统自动更新时间戳,(修改数据,自动进行更新,用于标注最后一次修改时间)
	create table t7(dt datetime,ts timestamp);
	insert into t7 values(null,null);
	insert into t7 values(20200920144650,20200920144650);
	
# 枚举类型 enum  集合类型 set
enum 枚举 从一组数据当中选一个 (一般用在性别)
set  集合 从一组数据当中选多个 (一般用在爱好)
create table t8(
	id int unsigned,
	name varchar(10),
	money float(5,3),
	sex enum("man","woman"),
	hobby set("睡觉","吃饭","打豆豆")
);

# 枚举选一个,集合选多个(之间用逗号隔开)
insert into  t8(id,name,money,sex,hobby) values(1,'王文',3.123456,"man","睡觉,吃饭")
# 集合可以自动去重
insert into  t8(id,name,money,sex,hobby) values(1,'王文',3.123456,"man","睡觉,吃饭,吃饭,吃饭")

# ### part5 约束
"""字段名  字段类型  字段约束 => 创建表"""
unsigned     : 无符号整型
not null     : 不能为空
default      : 设置默认值
unique       : 唯一约束,数据唯一不重复
primary key  : 主键 , 唯一并且不能为空,辨别单条数据的唯一性
auto_increment: 自增加一
foreign key  : 外键,把多张表通过一个字段关联在一起,形成联级更新,联级删除效果

# unsigned     : 无符号整型
create table t1(id int unsigned );
insert into t1 values(-100); error
insert into t1 values(100);

# not null     : 不能为空
create table t2(id int unsigned not null , name varchar(255) );
insert into t2 values(1,"abc");
insert into t2(name) values("abc"); error

# default      : 设置默认值
create table t3(id int unsigned not null , name varchar(255) default "张俊文" );
insert into t3 values(11,null);
insert into t3(id) values(12);

# unique       : 唯一约束,数据唯一不重复 (唯一索引)
"""索引: 相当于字典首页的目录,可以快速定位到要查找的数据,加快查询速度"""
"""UNI 唯一索引 或者唯一约束 ,不能重复,但可以是多个null值"""
create table t4(id int unique , name varchar(255) default "张俊文" );
insert into t4(id ) values(1);
insert into t4(id ) values(1); error 1这个值重复
insert into t4(id ) values(null); 正确
insert into t4(id ) values(null); 正确

# primary key  : 主键 , 唯一并且不能为空,辨别单条数据的唯一性
"""PRI 主键 或者 主键索引, 一个表中,默认单个字段里只能有一个主键,不存在多个字段多个主键"""
create table t5(id int primary key  , name varchar(255) default "张俊文" );
insert into t5(id ) values(1);
insert into t5(id ) values(2);
insert into t5(id ) values(null); error

# auto_increment: 自增加一 (一般配合主键或者unique使用)
create table t6(id int primary key auto_increment , name varchar(255) default "张俊文" );
insert into t6(id) values(1);
insert into t6(id) values(null);
insert into t6(id) values(null);
insert into t6(id) values(null);

# 删除所有 (保留id)
delete from t6;
# 重置表 (删除数据 + 重置id)
truncate table t6;

# foreign key  : 外键,把多张表通过一个字段关联在一起,形成联级更新,联级删除效果
"""外键的要求:所关联另外一张表的字段至少具有唯一性"""
字段1 字段2 ...... 字段30(公司法人代表)
                     
student
	id name    age  classname sex  family    friend   time parent .... 
	1  wangwen 16   python5   男性 一家三口  绿巨人1990  马化腾

	2  lisi    17   python5   男性 一家三口  绿巨人1990  马化腾

	3  wangwu  18   python5   男性 一家三口  绿巨人1990  马化腾

student1
	id name    age  classid
	1  wangwen 16   1  
	2  lisi    17   2
	3  wangwu  18   1

class1
	id  classname
	1   python5
	2   python6
	3   python7

# foreign key(关联字段) references
"""如果被关联的字段是有符号的,那么主动关联的字段也需要有符号,要保证符号类型一致"""
create table class111(id int unsigned,classname varchar(255));

# 设置id变成unique
alter table class1 add unique(id);
desc class1;

create table student111(
	id int primary key auto_increment,
	name varchar(255),
	age tinyint unsigned,
	classid int unsigned,foreign key(classid) references class111(id)
);

# 插入数据
insert into class111 values(1,"python5"),(2,"python6"),(3,"python7");
insert into student111 values(null,"wangwen",16,1),(null,"lisi",17,2),(null,"wangwu",18,1);

# 如果是被修饰成外键,当前字段只有在无任何数据关联的情况下,才能够进行修改或者删除
delete from class111 where id = 1 error 
# 必须把其他关联的数据都删掉,才可以删掉对应的班级
delete from student111 where classid = 1;

"""
联级更新 : on update cascade
联级删除 : on delete cascade
"""
create table class222(id int unsigned,classname varchar(255));

# 设置id变成unique
alter table class222 add unique(id);
desc class222;

create table student222(
	id int primary key auto_increment,
	name varchar(255),
	age tinyint unsigned,
	classid int unsigned,
	foreign key(classid) references class222(id) on update cascade on delete cascade
	
);

# 插入数据
insert into class222 values(1,"python5"),(2,"python6"),(3,"python7");
insert into student222 values(null,"wangwen",16,1),(null,"lisi",17,2),(null,"wangwu",18,1);

# 联级删除
#delete from class222 where id = 1
# 联级更新
# update class222 set id = 20 where classname="python6"

# ### part6 表与表之间的关系
(1) 一对一 : 身份证 和 姓名
(2) 一对多 : 一个班级对应多个学生
(3) 多对多 : 一个作者可以写多本书,一本书可以被多个作者完成
			 一个学科可以被多个学生学习,一个学生可以学习多个学科

xueke (表1)
id name
1  math
2  english
3  wuli

student(表2)
id  name
1   wangwen
2   zhangsan
3   lisi

relation (表3 关系表)
"""可以吧xid和sid设置关联字段,关联xueke.id 以及  student.id 
把xid 和 sid 设置成外键,实现联级删除或者联级更新
"""
xid  sid
1    1
1    2
1    3
2    1
2    2
2    3
3    1 
3    2
3    3

"""
# 总结:
1.添加/删除 not null 约束
	alter table 表名 modify 别名 类型
	
2.添加/删除 unique 唯一索引
	alter table 表名 add unique(id);
	alter table 表名 drop  索引名
	
3.添加/删除 primary key 主键
	alter table 表名 add primary key(id)
	alter table 表名 drop primary key

4. 添加/删除froeign key 外键
	show create table student2\G 查看外键名
	alter table student2 drop foreign key 外键名字 `student2_ibfk_1`
	alter table student2 add foreign key(clas_id) references class2(id)
"""

```

### 📖 要点讲解

- ### 安装mysql => 通过超级管理员打开cmd黑窗口

- windows (启动或者关闭数据库,必须在超级管理员的身份下才能执行)

- ###part3.数据库的增删改查 (必须掌握)

- modify 专门用来修改数据类型 , 指定char类型长度为4

- (3) 操作记录: (实例文件里面的内容)

- 可以不指定具体某字段插入数据,但是要保证一一对应

- update 表名 set 字段=值 where 条件

- float(5,2) 小数点后保留2为,整体长度是5位

- float和double比较,double小数位保留的更多,decimal默认只保留整数,存在四舍五入.

- 总长度是5,小数点最多保留2位,整数部分最多保留3位.

- char(4) varchar(4) 代表字符的个数不能超过4个

- char 最大不超过255个字符.varchar 最大不超过21845个字符

- 有时不确定varchar是多少个字符上线,可以先写255个在调;

- unique       : 唯一约束,数据唯一不重复 (唯一索引)

- primary key  : 主键 , 唯一并且不能为空,辨别单条数据的唯一性

- auto_increment: 自增加一 (一般配合主键或者unique使用)

- foreign key  : 外键,把多张表通过一个字段关联在一起,形成联级更新,联级删除效果

- foreign key(关联字段) references

- 如果是被修饰成外键,当前字段只有在无任何数据关联的情况下,才能够进行修改或者删除

- 必须把其他关联的数据都删掉,才可以删掉对应的班级

- delete from class222 where id = 1

- update class222 set id = 20 where classname="python6"

---

## 3. 2.协程爬数据.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day11_协程_安装认识数据库_数据库表数据的增删改查_数据库类型_外键_单表多表/代码/2.协程爬数据.py", line 53, in <module>
    from gevent import monkey;monkey.patch_all()
    ^^^^^^^^^^^^^^^^^^^^^^^^^
ModuleNotFoundError: No module named 'gevent'

```

### 💻 完整代码

```python

# ### 协程的例子
"""
1.spawn(函数,参数1,参数2,参数3 ... ) 启动协程
2.join 阻塞,知道某个协程任务执行完毕之后,在放行
3.joinall 等待所有协程任务都执行完毕之后,在放行
4.value 获取协程任务中的返回值 
"""
# (1) 总结所有方法
"""
from gevent import monkey
monkey.patch_all() # 把下面所有引入的模块中的阻塞识别一下

import time
import gevent

import gevent
def eat():
	print("eat1")
	time.sleep(2)
	print("eat2")
	return "吃完了"
	
def play():
	print("play1")
	time.sleep(2)
	print("play2")
	return "玩完了"
	
# 利用gevent 创建协程对象g1
g1 = gevent.spawn(eat)
# 利用gevent 创建协程对象g2
g2 = gevent.spawn(play)
# 等待所有协程g1和g2执行完毕之后,在放行
gevent.joinall( [g1,g2] )

# 默认主线程不会等待协程任务就会终止程序.
print("程序结束")
print(g1.value)
print(g2.value)
"""
# (2) 利用协程爬取数据
"""
# 如果要写在一行,利用分号将代码隔开
a = 1 
b = 2
a = 3;b=3

HTTP 协议的状态码:
	200 ok
	400 bad request
	404 not found
"""
from gevent import monkey;monkey.patch_all()
import requests
import time
import gevent

# 返回对象
response = requests.get("http://www.baidu.com")
print(response)
# 获取状态码
print(response.status_code)
# 获取网页中的字符编码
res = response.apparent_encoding
print(res)
# 设置编码集,防止乱码
response.encoding = res
# 获取网页中的内容
res = response.text
# print(res)

url_list = [
"http://www.baidu.com",
"http://www.taobao.com",
"http://www.jingdong.com",
"http://www.4399.com",
"http://www.baidu.com",
"http://www.taobao.com",
"http://www.jingdong.com",
"http://www.4399.com",
"http://www.baidu.com",
"http://www.taobao.com",
"http://www.jingdong.com",
"http://www.4399.com",
"http://www.baidu.com",
"http://www.taobao.com",
"http://www.jingdong.com",
"http://www.4399.com",
"http://www.baidu.com",
"http://www.taobao.com",
"http://www.jingdong.com",
"http://www.4399.com",
"http://www.baidu.com",
"http://www.taobao.com",
"http://www.jingdong.com",
"http://www.4399.com",
"http://www.baidu.com",
"http://www.taobao.com",
"http://www.jingdong.com",
"http://www.4399.com",
"http://www.baidu.com",
"http://www.taobao.com",
"http://www.jingdong.com",
"http://www.4399.com",
"http://www.baidu.com",
"http://www.taobao.com",
"http://www.jingdong.com",
"http://www.4399.com",
"http://www.baidu.com",
"http://www.taobao.com",
"http://www.jingdong.com",
"http://www.4399.com",
"http://www.baidu.com",
"http://www.taobao.com",
"http://www.jingdong.com",
"http://www.4399.com",
"http://www.baidu.com",
"http://www.taobao.com",
"http://www.jingdong.com",
"http://www.4399.com",
"http://www.baidu.com",
"http://www.taobao.com",
"http://www.jingdong.com",
"http://www.4399.com"

]

# 1.普通方法爬取数据
"""
def get_url(url):
	response = requests.get(url)
	if response.status_code == 200:
		# res = response.apparent_encoding
		# print(res)
		# 设置编码集,防止乱码
		# response.encoding = res
		# print(response.text)
		pass
	
startime = time.time()
for i in url_list:
	get_url(i)
endtime = time.time()
print(endtime - startime) # 10.28054404258728
"""
# 2.协程方法爬取数据
def get_url(url):
	response = requests.get(url)
	if response.status_code == 200:
		# res = response.apparent_encoding
		# print(res)
		# 设置编码集,防止乱码
		# response.encoding = res
		# print(response.text)
		pass

lst	= []
startime = time.time()
for i in url_list:
	# 创建了url_list这个列表总个数的协程任务
	g = gevent.spawn(get_url,i)
	lst.append(g)
# 必须等待所有协程执行完毕之后在放行
gevent.joinall(lst)
endtime = time.time()
print(endtime - startime) # 1.085099220275879

"""
利用多进程,多线程,多协程可以让服务器运行速度更快,抗住更多用户并发访问的需求
"""

```

### 📖 要点讲解

- 等待所有协程g1和g2执行完毕之后,在放行

- res = response.apparent_encoding

- response.encoding = res

- res = response.apparent_encoding

- response.encoding = res

- 创建了url_list这个列表总个数的协程任务

---

## 4. 2.笔记.py

### 📋 运行结果

```

错误：  File "/tmp/python3_course/day11_协程_安装认识数据库_数据库表数据的增删改查_数据库类型_外键_单表多表/代码/2.笔记.py", line 48
    9.concat(参数1,参数2,参数3) 连接在一起(类似于os.path.join)
     ^
SyntaxError: invalid decimal literal

```

### 💻 完整代码

```python

# ### 1.单表查询
select  .. from .. where .. group by .. having .. order by .. limit ..

# 1.where 子句 : 对数据按照条件筛选
	"""
		1.符号: = > >= < <= != <> (不等于)
		2.between .. and  在两者之间[小值,大值] 
		3.is用来判断是否是null
		4.in   => in(值1,值2,值3...) 在当前括号里划定范围
	    5.like 模糊查询 %是通配符 _是通配符
			like "%a"  匹配以a结尾的任意长度字符串
			like "a%"  匹配以a开头的任意长度字符串
			like "%a%" 匹配含有a字符的任意长度字符串
			like "_a"  匹配以a结尾的2个长度的字符串
			like "a__" 匹配以a开头的共3个长度的字符串
		6.and or not 通过逻辑拼接条件
	"""
	
	1.查询部门是sale的所有员工姓名
	select emp_name from employee where post = "sale";
	
	2.找teacher部门,并且收入大于10000
	select * from employee where post="teacher" and salary > 10000;
	
	3.收入在10000~20000之间的所有姓名和收入
	select emp_name ,salary  from employee where salary between 10000 and 20000
	
	4.收入不在10000~20000之间的所有姓名和收入
	select emp_name ,salary  from employee where salary not  between 10000 and 20000
	
	5.找部门评论为null的数据 (必须用is来判断)
	select * from employee where post_comment = null; error 无数据 null是关键字需要用is来判断
	select * from employee where post_comment is null;
	
	6.找3000 3500 4000收入的员工姓名
	select emp_name,salary from employee where salary in (3000,3500,4000);
	select emp_name,salary from employee where salary  = 3000 or salary = 3500 or salary = 4000;
	
	7.找不在3000 3500 4000收入的员工姓名
	select emp_name,salary from employee where salary not in (3000,3500,4000);
	
	8.找a开头的名字
	# 必须是a开头,后面字符个数,种类都不限制
	select emp_name from employee where emp_name like "a%";
	# 必须是金结尾,前面字符个数是2个
	select emp_name from employee where emp_name like "__金";
	
	9.concat(参数1,参数2,参数3) 连接在一起(类似于os.path.join)
	select concat("姓名:",emp_name,"薪水",salary) from employee;
	
# 2.group by 分类,分组
	"""
	group by + 字段 按照当前这个字段分类
	按照什么分类,就搜索什么字段
	group_concat 对分类的内容进行数据拼接
	"""
	select sex from employee group by sex;
	select group_concat(emp_name) from employee group by sex;
	
	# 聚合函数
		# count 统计计数
		select count(*) from employee;
		# max   统计最大值
		select max(salary) from employee;
		# min   统计最小值
		select min(salary) from employee;
		# sum   统计总和
		select sum(salary) from employee;
		# avg   统计平均值
		select avg(salary) from employee;
	
	# 分组 + 聚合函数一起使用
	# 求各部门的平均薪资
	select post,avg(salary) from employee group by post;
	# 求各部门的最大薪资
	select post,max(salary) from employee group by post;
	
# 3.having 在分类完数据之后,进行数据的二次过滤.一般配合group by一起使用
	
	1.查询各岗位平均薪资大于10000以上的岗位名、平均工资
	select post,avg(salary) from employee group by post having avg(salary) > 10000;
	# as 就是起别名
	select post,avg(salary) as avg from employee group by post having avg(salary) > 10000;
	
# 4.order by 按照什么字段排序
+----+------------+--------+-----+------------+-----------------------------------------+--------------+------------+--------+-----------+
| id | emp_name   | sex    | age | hire_date  | post                                    | post_comment | salary     | office | depart_id |
+----+------------+--------+-----+------------+-----------------------------------------+--------------+------------+--------+-----------+
|  1 | egon       | male   |  18 | 2017-03-01 | 老男孩驻沙河办事处外交大使              | NULL         |    7300.33 |    401 |         1 |
|  2 | alex       | male   |  78 | 2015-03-02 | teacher                                 | NULL         | 1000000.31 |    401 |         1 |
|  3 | wupeiqi    | male   |  81 | 2013-03-05 | teacher                                 | NULL         |    8300.00 |    401 |         1 |
|  4 | yuanhao    | male   |  73 | 2014-07-01 | teacher                                 | NULL         |    3500.00 |    401 |         1 |
|  5 | liwenzhou  | male   |  28 | 2012-11-01 | teacher                                 | NULL         |    2100.00 |    401 |         1 |
|  6 | jingliyang | female |  18 | 2011-02-11 | teacher                                 | NULL         |    9000.00 |    401 |         1 |
|  7 | jinxin     | male   |  18 | 1900-03-01 | teacher                                 | NULL         |   30000.00 |    401 |         1 |
|  8 | 成龙       | male   |  48 | 2010-11-11 | teacher                                 | NULL         |   10000.00 |    401 |         1 |
|  9 | 歪歪       | female |  48 | 2015-03-11 | sale                                    | NULL         |    3000.13 |    402 |         2 |
| 10 | 丫丫       | female |  38 | 2010-11-01 | sale                                    | NULL         |    2000.35 |    402 |         2 |
| 11 | 丁丁       | female |  18 | 2011-03-12 | sale                                    | NULL         |    1000.37 |    402 |         2 |
| 12 | 星星       | female |  18 | 2016-05-13 | sale                                    | NULL         |    3000.29 |    402 |         2 |
| 13 | 格格       | female |  28 | 2017-01-27 | sale                                    | NULL         |    4000.33 |    402 |         2 |
| 14 | 张野       | male   |  28 | 2016-03-11 | operation                               | NULL         |   10000.13 |    403 |         3 |
| 15 | 程咬金     | male   |  18 | 1997-03-12 | operation                               | NULL         |   20000.00 |    403 |         3 |
| 16 | 程咬银     | female |  18 | 2013-03-11 | operation                               | NULL         |   19000.00 |    403 |         3 |
| 17 | 程咬铜     | male   |  18 | 2015-04-11 | operation                               | NULL         |   18000.00 |    403 |         3 |
| 18 | 程咬铁     | female |  18 | 2014-05-12 | operation                               | NULL         |   17000.00 |    403 |         3 |
+----+------------+--------+-----+------------+-----------------------------------------+--------------+------------+--------+-----------+
	# 默认升序,从小到大 asc
	# 1.把teacher部门的所有员工,按照年龄从小到大排序 asc
	select * from employee where post = "teacher" order by age ;
	select * from employee where post = "teacher" order by age asc;
	# 2.把teacher部门的所有员工,按照年龄从大到小排序 desc
	select * from employee where post = "teacher" order by age desc;
	# 3.在年龄倒序排列之后,在按照入职日期进行升序排序
	select * from employee where post = "teacher" order by age desc , hire_date asc;
	
# 5.limit 限制查询的条数(一般用于做分页)
	# 1. 只查询一条数据
	select * from employee limit 1;
	# 2.limit m,n  m代表从第几条开始搜 , n代表搜索几条 如果m=0,代表从第一条开始
	select * from employee limit 0,5
	select * from employee limit 5,5
	select * from employee limit 10,5
	
# ### 2.多表之间的查询
	# (1) 内联 (inner join ) : 将两表或者多表拼接在一起进行查询,要求必须双方都共有的数据可以联合
	语法: select 字段 from 表1 inner join 表2 on 必要关联的字段
	多表: select 字段 from 表1 inner join 表2 on 必要关联的字段 inner join 表3 on 必要关联的字段 inner join ... 

	# 内联查询 (双方都存在的数据才能联合)
	select * from employee inner join department on employee.dep_id = department.id
	# 用as 起别名
	select * from employee as e inner join department as d on e.dep_id = d.id;
	select * from employee,department where employee.dep_id = department.id #( 默认where 是内联查询)
	# as 本身都可以省略
	select * from employee e,department d where e.dep_id = d.id 
	
	# (2) 外联
		1.左联接 (left join)  : 以左表为主,右表为辅,完整查询左表所有数据,右表对不上的数据补null
			select * from employee left join department on employee.dep_id = department.id
		2.右联接 (right join) : 以右表为主,左表为辅,完整查询右表所有数据,左表对不上的数据补null
			select * from employee right join department on employee.dep_id = department.id
		3.全联接 (union)
			select * from employee left join department on employee.dep_id = department.id
			union
			select * from employee right join department on employee.dep_id = department.id
	
```

### 📖 要点讲解

- 1.where 子句 : 对数据按照条件筛选

- 3.having 在分类完数据之后,进行数据的二次过滤.一般配合group by一起使用

- 1.把teacher部门的所有员工,按照年龄从小到大排序 asc

- 2.把teacher部门的所有员工,按照年龄从大到小排序 desc

- 3.在年龄倒序排列之后,在按照入职日期进行升序排序

- 5.limit 限制查询的条数(一般用于做分页)

- 2.limit m,n  m代表从第几条开始搜 , n代表搜索几条 如果m=0,代表从第一条开始

- (1) 内联 (inner join ) : 将两表或者多表拼接在一起进行查询,要求必须双方都共有的数据可以联合

---

## 🖼️ 参考资料

![1555483227691.png](./assets/1555483227691.png)

![1555483413283.png](./assets/1555483413283.png)

![1555483481421.png](./assets/1555483481421.png)

![1555483637964.png](./assets/1555483637964.png)

![1555483666999.png](./assets/1555483666999.png)

![1555483797479.png](./assets/1555483797479.png)

![1555484649053.png](./assets/1555484649053.png)

![1555485036396.png](./assets/1555485036396.png)

![1555485058132.png](./assets/1555485058132.png)

![1555485093085.png](./assets/1555485093085.png)

![1555485497312.png](./assets/1555485497312.png)

![1555496062646.png](./assets/1555496062646.png)

![1555496477552.png](./assets/1555496477552.png)

![1555496520217.png](./assets/1555496520217.png)

![1555496622098.png](./assets/1555496622098.png)

![1555496747740.png](./assets/1555496747740.png)

![1559814156470.png](./assets/1559814156470.png)

![1559814284933.png](./assets/1559814284933.png)

![1559814354293.png](./assets/1559814354293.png)

![1559814570465.png](./assets/1559814570465.png)

![1559814916496.png](./assets/1559814916496.png)

![1559814989584.png](./assets/1559814989584.png)

![1559815060083.png](./assets/1559815060083.png)

![1559815117225.png](./assets/1559815117225.png)

![1559815729618.png](./assets/1559815729618.png)

![1559815780691.png](./assets/1559815780691.png)

![1559815827933.png](./assets/1559815827933.png)

![1559815988723.png](./assets/1559815988723.png)

![1559816020009.png](./assets/1559816020009.png)

![1559816137773.png](./assets/1559816137773.png)

![1559816206586.png](./assets/1559816206586.png)

![1559816380880.png](./assets/1559816380880.png)

![1560401672936.png](./assets/1560401672936.png)

![1560401690571.png](./assets/1560401690571.png)

![1560401702657.png](./assets/1560401702657.png)

![1560401713280.png](./assets/1560401713280.png)

![1560401726064.png](./assets/1560401726064.png)

![1560401741798.png](./assets/1560401741798.png)

![1560401751508.png](./assets/1560401751508.png)

![1560559430738.png](./assets/1560559430738.png)

![1560559452665.png](./assets/1560559452665.png)

![1560559463455.png](./assets/1560559463455.png)

![1560559471782.png](./assets/1560559471782.png)

![协程执行流程.png](./assets/协程执行流程.png)
