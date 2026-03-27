# Day 8: day08 atm项目需求 类中方法property了解异常 异常处理 反射 模块的导入 网络的概念 tcp udp

> 对应原课程：day08_atm项目需求_类中方法property了解异常_异常处理_反射_模块的导入_网络的概念_tcp_udp

---

## 1. main1.py

### 📋 运行结果

```

['/tmp/python3_course/day08_atm项目需求_类中方法property了解异常_异常处理_反射_模块的导入_网络的概念_tcp_udp/代码/7.import_lianxi', '/usr/lib/python312.zip', '/usr/lib/python3.12', '/usr/lib/python3.12/lib-dynload', '/usr/local/lib/python3.12/dist-packages', '/usr/lib/python3/dist-packages']
我是mymodule模块
mymodule

```

### 💻 完整代码

```python

# ### 导入模块与包
"""
文件就是一个模块,文件夹就是一个包
"""
# ### 导入模块

# 1.基本使用
"""模块的导入,导入一次,终身受益,不会重复导入"""
"""
import mymodule
import mymodule

# 模块.变量
print(mymodule.girl)
# 模块.函数
mymodule.dog()
# 模块.类

cls = mymodule.MyClass
obj = cls()
print(obj.a)
"""

# 2.导入任意路径下的模块
import sys
# 系统找模块的默认路径
print(sys.path)
"""
路径中含有就直接导入,没有的话就导入失败
[
'E:\\python5周末班\\day8', 
'D:\\py_lianxi', 
'D:\\py_lianxi\\venv\\Scripts\\python36.zip', 
'C:\\Users\\KnightPlan\\AppData\\Local\\Programs\\Python\\Python36\\DLLs', 
'C:\\Users\\KnightPlan\\AppData\\Local\\Programs\\Python\\Python36\\lib', 
'C:\\Users\\KnightPlan\\AppData\\Local\\Programs\\Python\\Python36', 'D:\\py_lianxi\\venv', 
'D:\\py_lianxi\\venv\\lib\\site-packages', 'D:\\py_lianxi\\venv\\lib\\site-packages\\setuptools-40.8.0-py3.6.egg', 
'D:\\py_lianxi\\venv\\lib\\site-packages\\pip-19.0.3-py3.6.egg'
]
"""

pathvar = r"E:\python5周末班\day7"
# 把模块实际路径插入到系统路径的列表中,让系统自动寻找,从而加载模块
"""
sys.path.append(pathvar)

import mymodule2
print(mymodule2.wangwen)
"""
# 3.from .. import .. 从...导入具体..东西
# (1)引入单个成员
"""
from mymodule import girl
print(girl)
"""
# (2)引入多个成员
"""
from mymodule import boy,cat
print(boy)
cat()
"""

# as起别名
"""
from mymodule import boy as b,cat as c
print(b)
c()
"""
# (3)引入所有成员  * 代表所有
"""
from mymodule import * 
dog()
"""

# 可以指定*号的范围
"""
from mymodule import * 
print(boy)
dog()
"""

# 4.__name__ 获取当前模块的模块名
"""
当一个模块(文件)直接被直接的,返回的__main__ 代表本文件
当一个模块(文件)是被交接导入执行的,返回自己的模块名
"""
# print(__name__ ,type(__name__) ) # str
import mymodule

```

### 📖 要点讲解

- 把模块实际路径插入到系统路径的列表中,让系统自动寻找,从而加载模块

- 3.from .. import .. 从...导入具体..东西

- 4.__name__ 获取当前模块的模块名

- print(__name__ ,type(__name__) ) # str

---

## 2. main2.py

### 📋 运行结果

```

初始化文件被调用
1
2
非礼呀,你这个色狼.
我是getallsize方法
10

```

### 💻 完整代码

```python

# ### 导入模块与包
"""
文件就是一个模块,文件夹就是一个包
"""
# ### 导入包
"""
当导入一个包的时,系统会自动触发调用__init__.py初始化文件
"""
import package1
# 包.成员
print(package1.ceshi1)
print(package1.ceshi2)
package1.colorwolf()

# 一.import 调用当前文件夹下的某个文件 -> 调用包中的某个模块
# 1.导入包中的模块
"""
import package1.mypath
package1.mypath.getallsize()
"""
# 2.整体起别名
"""
import package1.mypath as pm
pm.getallsize()
"""
# 3.通过初始化文件实现间接导入
"""
import package1
# os.path.getsize()
package1.mypath.getallsize()
"""

# 二.from .. import 导入包中具体某个成员
# 1.导入包中的mypath这个模块
from package1 import mypath
mypath.getallsize()

# 2.导入包里的模块中的具体某个成员
# 导入单个
"""
from package1.mypath import lianxi1
print(lianxi1)
"""
# 导入多个
"""
from package1.mypath import lianxi1 as l1, lianxi2 as l2
print(l1)
print(l2)
"""
# 导入所有
"""
from package1.mypath import *
getallsize()
"""
# 指定*号的范围
from package1.mypath import *
# getallsize() error
print(lianxi1)

```

### 📖 要点讲解

- 一.import 调用当前文件夹下的某个文件 -> 调用包中的某个模块

- 二.from .. import 导入包中具体某个成员

---

## 3. main3.py

### 📋 运行结果

```

200
300
400
500
501
600
100

```

### 💻 完整代码

```python

# 单入口模式导入所有数据
"""
使用的都是相对路径
.  相对于当前路径
.. 相对于上一级路径
主入口去调用分模块所有的内容
单独的分模块内容是不能直接扔到pycharm内执行的
在本地创建文件 拖拽到pycharm中执行,
如果通过pycharm打开,会默认在文件添加路径,导致引入失败
"""
# 方法一
import package2.pkgone.pkgo_m1 as ppp1
print(ppp1.ceshi100) # 100

# 方法二
# from package2.pkgone import pkgo_m1
# print(pkgo_m1.ceshi100)

# 方法三
# from package2.pkgone.pkgo_m1 import ceshi100
# print(ceshi100)

```

### 📖 要点讲解

- from package2.pkgone import pkgo_m1

- print(pkgo_m1.ceshi100)

- from package2.pkgone.pkgo_m1 import ceshi100

---

## 4. mymodule.py

### 📋 运行结果

```

我是mymodule模块
__main__
刘硬
我是中式柴犬

```

### 💻 完整代码

```python

# 用魔术属性__all__ 指定*导入的范围
__all__ = ["boy","cat","dog"]

girl = "刘硬"
boy = "郑飞"

def cat():
	print("我是英国美短")

def dog():
	print("我是中式柴犬")
	
class MyClass():
	a = 1
	
print("我是mymodule模块")

print(__name__) # mymodule

# 当一个模块写完时,用下面的代码做测试,不是用来导入的
# 当本文件当成模块被其他文件导入时,下面的代码不执行了
if __name__ == "__main__":
	print(girl)
	dog()

```

### 📖 要点讲解

- 用魔术属性__all__ 指定*导入的范围

- 当一个模块写完时,用下面的代码做测试,不是用来导入的

- 当本文件当成模块被其他文件导入时,下面的代码不执行了

---

## 5. __init__.py

### 📋 运行结果

```

初始化文件被调用

```

### 💻 完整代码

```python

print("初始化文件被调用")
ceshi1 = 1
ceshi2 = 2

def colorwolf():	
	print("非礼呀,你这个色狼.")
	
# 3.通过初始化文件实现间接导入
# from package1 import mypath

```

### 📖 要点讲解

- from package1 import mypath

---

## 6. mypath.py

### 💻 完整代码

```python

__all__ = ["lianxi1"]

def getallsize():
	print('我是getallsize方法')
	
lianxi1 = 10
lianxi2 = 20

```

---

## 7. pkg2_m1.py

### 💻 完整代码

```python

ceshi300 = 300
ceshi301 = 301

```

---

## 8. pkg2_m2.py

### 💻 完整代码

```python

ceshi400 = 400
ceshi401 = 401

```

---

## 9. pkgo_m1.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day08_atm项目需求_类中方法property了解异常_异常处理_反射_模块的导入_网络的概念_tcp_udp/代码/7.import_lianxi/package2/pkgone/pkgo_m1.py", line 12, in <module>
    from . import pkgo_m2
ImportError: attempted relative import with no known parent package

```

### 💻 完整代码

```python

# 单入口
"""
# 相对路径是不能直接找到的,只能通过主入口文件,间接寻址执行
# 所有包中的分模块不能直接执行.报错.找不到
# from 相对路径 import 具体成员(不含有点) , 可以是具体的模块,或者模块中的具体成员.或者包
"""

ceshi100 = 100
ceshi101 = 101

# 相对于当前路径,引入pkgo_m2模块
from . import pkgo_m2
# 模块.成员
print(pkgo_m2.ceshi200) # 200

# 相对于上一级,引入pkg2_m1模块
from .. import  pkg2_m1
print(pkg2_m1.ceshi300) # 300

# 相对于上一级,引入pkg2_m2模块中的ceshi400成员属性
from ..pkg2_m2 import ceshi400
# from .. import pkg2_m2.ceshi400 error
print(ceshi400)

# 相对于上一级,引入pkgtwo包中的pkgt_m1模块
from  ..pkgtwo import pkgt_m1
print(pkgt_m1.ceshi500)

# 相对于上一级,引入pkgtwo包中的pkgt_m1模块中的ceshi501成员属性
from  ..pkgtwo.pkgt_m1 import ceshi501
print(ceshi501)

# import 可以引入文件夹,但是import 中不能含有.
from .. import pkgthree
print(pkgthree.ceshi600)

```

### 📖 要点讲解

- 相对路径是不能直接找到的,只能通过主入口文件,间接寻址执行

- 所有包中的分模块不能直接执行.报错.找不到

- from 相对路径 import 具体成员(不含有点) , 可以是具体的模块,或者模块中的具体成员.或者包

- 相对于上一级,引入pkg2_m2模块中的ceshi400成员属性

- from .. import pkg2_m2.ceshi400 error

- 相对于上一级,引入pkgtwo包中的pkgt_m1模块

- 相对于上一级,引入pkgtwo包中的pkgt_m1模块中的ceshi501成员属性

- import 可以引入文件夹,但是import 中不能含有.

---

## 10. pkgo_m2.py

### 💻 完整代码

```python

ceshi200 = 200
ceshi201 = 201

```

---

## 11. pkgt_m1.py

### 💻 完整代码

```python

ceshi500 = 500
ceshi501 = 501

```

---

## 12. pkgt_m2.py

### 💻 完整代码

```python

```

---

## 13. __init__.py

### 💻 完整代码

```python

ceshi600 = 600

```

---

## 14. 1.类中方法.py

### 📋 运行结果

```

小狗喜欢喝小鸟伏特加,zbc,无情哈拉少
小狗的名字是詹姆斯·蛋,爱吃西红柿炒鸡蛋
小狗的名字是詹姆斯·蛋,爱吃西红柿炒鸡蛋
<class '__main__.Dog'>
詹姆斯·蛋
小狗喜欢舔主人的脚丫子
<class '__main__.Dog'>
詹姆斯·蛋
小狗喜欢舔主人的脚丫子
小狗喜欢接跳起来飞盘
小狗喜欢接跳起来飞盘

```

### 💻 完整代码

```python

# ### 类中方法
"""
普通方法: 无参时,只能用类来调用
绑定方法: 
	(1) 绑定到对象 : 对象调用时,会自动的传递该对象这个参数
	(2) 绑定到类   : 类/对象调用时,会自动的传递该类这个参数
静态方法:
	无论对象还是类都能调用,系统不会自动传递任何的参数;
"""

class Dog():
	name = "詹姆斯·蛋"
	
	# 普通方法
	def drink():
		print("小狗喜欢喝小鸟伏特加,zbc,无情哈拉少")
		
	# 绑定方法(对象)
	def eat(self):
		print("小狗的名字是{},爱吃西红柿炒鸡蛋".format(self.name))
		
	# 绑定方法(类)
	@classmethod
	def tian(cls):
		print(cls)
		print(cls.name)
		print("小狗喜欢舔主人的脚丫子")
		
	# 静态方法
	@staticmethod
	def jump():
		print("小狗喜欢接跳起来飞盘")
	
obj = Dog()

# 普通方法
Dog.drink()

# 绑定方法(对象)
"""默认传递当前的对象作为成员方法的参数"""
obj.eat()
Dog.eat(obj)

# 绑定方法(类) 
"""默认传递当前的类作为成员方法的参数"""

obj.tian()
Dog.tian()

# 静态方法
"""无论是对象还是类都可以调用,不会自动传递参数"""
obj.jump()
Dog.jump()

```

---

## 15. 1.client.py

### 📋 运行结果

```

执行超时（可能是交互式程序）

```

### 💻 完整代码

```python

# ### 客户端
import socket
# 1.创建udp对象 type=socket.SOCK_DGRAM
sk = socket.socket(type=socket.SOCK_DGRAM)

# 2.处理收发数据的逻辑 (发送的数据都是字节流)
# 发送数据
msg = "我好想你呀"
sk.sendto( msg.encode() ,("127.0.0.1", 9000) )
# 接收数据
msg,ser_addr = sk.recvfrom(1024)
print(msg.decode)
print(ser_addr)

# 3.关闭连接
sk.close()

```

### 📖 要点讲解

- 1.创建udp对象 type=socket.SOCK_DGRAM

- 2.处理收发数据的逻辑 (发送的数据都是字节流)

---

## 16. 1.server.py

### 📋 运行结果

```

执行超时（可能是交互式程序）

```

### 💻 完整代码

```python

# ### 服务端
import socket
# 1.创建udp对象 type=socket.SOCK_DGRAM
sk = socket.socket(type=socket.SOCK_DGRAM)
# 2.绑定地址端口号
sk.bind( ("127.0.0.1", 9000) )

# 3.udp协议,因为没有三次握手,不能在一开始的时候就知道对方的ip端口号,所以默认第一次是接收数据

# 接收数据
msg,cli_addr = sk.recvfrom(1024)
print(msg.decode() , cli_addr)
# msg.decode() 我好想你呀
# cli_addr  ('127.0.0.1', 54612)

# 发送数据
sk.sendto( "我也是".encode() , cli_addr )

# 4.关闭连接
sk.close()

```

### 📖 要点讲解

- 1.创建udp对象 type=socket.SOCK_DGRAM

- 3.udp协议,因为没有三次握手,不能在一开始的时候就知道对方的ip端口号,所以默认第一次是接收数据

- cli_addr  ('127.0.0.1', 54612)

---

## 17. 1.client.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day08_atm项目需求_类中方法property了解异常_异常处理_反射_模块的导入_网络的概念_tcp_udp/代码/9.tcp发消息/1.client.py", line 10, in <module>
    sk.connect( ("127.0.0.1",9000) )
ConnectionRefusedError: [Errno 111] Connection refused

```

### 💻 完整代码

```python

# ### 客户端
"""
客户端和服务端在收发数据时
一发一收必须配对,否则可能数据异常
"""
import socket
# 1.创建一个socket对象
sk = socket.socket()
# 2.连接远程的服务端
sk.connect( ("127.0.0.1",9000) )
# 3.处理收发数据的逻辑 

# 发送数据
# sk.send(要求的数据是二进制字节流)
sk.send("今天吃鸡,大吉大利".encode("utf-8"))

# 接收数据
res = sk.recv(1024) #一次最多接收1024字节
print(res.decode())

# 4.关闭连接
sk.close()

```

### 📖 要点讲解

- sk.send(要求的数据是二进制字节流)

---

## 18. 1.server.py

### 📋 运行结果

```

执行超时（可能是交互式程序）

```

### 💻 完整代码

```python

# ### socket 服务端
import socket

# 1.创建socket 对象
sk = socket.socket()
# 2.绑定对应的ip和端口号(在网络中注册该主机,让别人找得到)
"""默认本地ip:127.0.0.1 localhost  端口号推荐使用9000以上"""
sk.bind( ("127.0.0.1",9000) )
# 3.开启监听
sk.listen()
# 4.建立三次握手
conn,addr = sk.accept()
"""
conn:
<socket.socket fd=472, family=AddressFamily.AF_INET, type=SocketKind.SOCK_STREAM, proto=0, laddr=('127.0.0.1', 9000), raddr=('127.0.0.1', 57878)> 
addr:
('127.0.0.1', 57878)

"""
print(conn , addr)

# 5.收发数据的逻辑
# 接收数据
res = conn.recv(1024) # 一次最多发送1024字节
print(res)
print(res.decode())

# 发送数据
conn.send("今晚吃鸭,臭鱼烂虾".encode("utf-8"))

# 6.四次挥手
conn.close()

# 7.退还端口
sk.close()

```

### 📖 要点讲解

- 2.绑定对应的ip和端口号(在网络中注册该主机,让别人找得到)

---

## 19. 2.property.py

### 📋 运行结果

```

赵强
设置成员值时,自动触发
吕文康
吕文康
张俊文
设置成员值时,自动触发
李辉

```

### 💻 完整代码

```python

# ### property 
"""property 装饰器 , 可以修饰类中的成员方法变成属性"""
"""
property装饰器可以修饰方法变属性 可以控制类中成员的:获取,设置,删除操作
	1.@property        :在获取属性时自动触发
	2.@username.setter :在设置属性时自动触发
	3.@username.deleter:在删除属性时自动触发
"""

# 写法一
class MyClass():
	def __init__(self,name):	
		# 设置name属性为私有,不让类外直接获取,只能通过username的方式得到
		self.__name = name
		
	@property         # 获取
	def username(self):
		return self.__name
		# pass
		
	@username.setter  # 设置
	def username(self,val):
		print("设置成员值时,自动触发")
		self.__name = val
		pass
		
	@username.deleter # 删除
	def username(self):
		# del self.__name
		pass
		
obj = MyClass("赵强")
# 在获取属性时自动触发
res = obj.username
print(res)
# 在设置属性时自动触发
obj.username = "吕文康"
print(obj.username)
# 在删除属性时自动触发
del obj.username
print(obj.username)

# 写法二
class MyClass2():
	def __init__(self,name):	
		# 设置name属性为私有,不让类外直接获取,只能通过username的方式得到
		self.__name = name
		
	# 获取属性
	def get_username(self):
		return self.__name
		# pass

	# 设置属性
	def set_username(self,val):
		print("设置成员值时,自动触发")
		self.__name = val
		pass

	# 删除属性
	def del_username(self):
		del self.__name
		# pass
		
	# 顺序: 获取,设置,删除 这样的顺序,不能乱;
	username = property(get_username,set_username,del_username)

obj = MyClass2("张俊文")
print(obj.username)
obj.username = "李辉"
print(obj.username)
del obj.username
print(obj.username)

```

### 📖 要点讲解

- 设置name属性为私有,不让类外直接获取,只能通过username的方式得到

- 设置name属性为私有,不让类外直接获取,只能通过username的方式得到

- 顺序: 获取,设置,删除 这样的顺序,不能乱;

---

## 20. 3.了解异常.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day08_atm项目需求_类中方法property了解异常_异常处理_反射_模块的导入_网络的概念_tcp_udp/代码/3.了解异常.py", line 37, in <module>
    from collections import Iterator,Iterable
ImportError: cannot import name 'Iterator' from 'collections' (/usr/lib/python3.12/collections/__init__.py)

```

### 💻 完整代码

```python

# ### 了解异常处理

# IndexError                索引超出序列的范围
"""
lst = [1,2,3]
lst[100]
"""

# KeyError                  字典中查找一个不存在的关键字
"""
dic = {"a":1,"b":2,"c":3}
print(dic["d"])
"""

# NameError                 尝试访问一个不存在的变量
"""
print(wangwen)
"""

# IndentationError          缩进错误
"""
if 5 == 5:
	print(1)
    print(2)
"""

# AttributeError            尝试访问未知的对象属性
"""
class MyClass():
	a = 1 
	b = 2
obj = MyClass()
obj.c
"""

# StopIteration             迭代器没有更多的值
from collections import Iterator,Iterable
it = iter(range(3))
res = isinstance(it, Iterator)
print(res)
"""
res = next(it)
print(res)
res = next(it)
print(res)
res = next(it)
print(res)
res = next(it)
print(res)
"""

# AssertionError			 断言语句（assert）失败
"""assert 猜 , 猜一猜3>1是否正确,如果正确没有任何反应,如果不正确,直接抛出异常"""
assert 3 > 1
assert 3 < 1
print("正常执行")

"""
assert 如果判断的条件为假的,直接报错
if     如果判断的条件为假的,直接不执行
"""

```

### 📖 要点讲解

- IndexError                索引超出序列的范围

- KeyError                  字典中查找一个不存在的关键字

- NameError                 尝试访问一个不存在的变量

- IndentationError          缩进错误

- AttributeError            尝试访问未知的对象属性

- StopIteration             迭代器没有更多的值

- AssertionError			 断言语句（assert）失败

---

## 21. 4.异常处理.py

### 📋 运行结果

```

有异常错误
<generator object mygen at 0x775608f35d80>
start ...
1
2
3
return 的返回值是4
1
该程序有异常
<=====================>
0
1
2
请输入您要判断的值:

```

### 💻 完整代码

```python

# ### 异常处理的使用
"""
try .. except .. 
把可能出错的代码写到try这个代码块中,
如果出现了异常
执行ecxept 这个分支
否则不执行
"""

# 1.基本使用
try:
	print(name)
except:
	pass

# 2.带有except分支的异常处理
try:
	# print(name)
	lst = [1,2,3]
	# print(lst[100])
	dic = {"a":1,"b":2}
	print(dic["cccc"])
except NameError:
	print("name这个变量没有定义")
except IndexError:
	print("list index out of range")
except:
	print("有异常错误")

# 3.处理迭代器的异常报错

def mygen():
	print("start ...")
	yield 1
	yield 2
	yield 3
	return 4
	print("end ...")
gen = mygen()
print(gen)

# 获取迭代器中的返回值,用打印对象的方式实现.
try:
	res = next(gen)
	print(res)
	res = next(gen)
	print(res)
	res = next(gen)
	print(res)
	res = next(gen)
	print(res)
# except 异常类 as 对象 给StopIteration这个类实例化对象,起别名是e
except StopIteration as e:
	print("return 的返回值是",end="")
	# 打印对象时,自动触发StopIteration异常类中的魔术方法__str__
	# 返回的数据正好是捕捉到的返回值
	print(e)

# 4.其他写法
# try .. finally .. 无论代码是否异常,都必须要执行的代码写到finally当中.
"""
try:
	print(1)
	print(name)
finally:
	print("finally这个代码块执行了")
	print("必须要关闭数据库连接,释放资源")
"""
# try ... except .. else .. 
'''
如果没有异常,执行else这个分支
如果有异常,不执行else这个分支
'''
try:
	print(1)
	print(name)
except:
	print("该程序有异常")
else:
	print("该程序没有异常")

print("<=====================>")
# 额外扩展关于else分支.
"""在循环中,如果遇到break,异常终止的循环,不执行else分支"""
# for/while ... else ...
for i in range(5):
	if i == 3:
		break
	print(i)
else:
	print("正常循环")

# 计算一个数是不是质数
"""
质数是指在大于1的自然数中，除了1和它本身以外不再有其他因数的自然数。
"""

# 方法一  python特有
"""
num = int(input("请输入您要判断的值:"))
for i in range(2,num):
	if num % i == 0: #2345
		print("不是质数")
		break
else:
	print("是质数")

# 输入2循环跑不起来,就当是跑完了,走else
for i in range(2,2):
	print(i)
"""
# 方法二
sign = False
num = int(input("请输入您要判断的值:"))
for i in range(2,num):
	if num % i == 0: #2345
		print("不是质数")
		sign = True
		break

if sign == False:
	print("是一个质数")

```

### 📖 要点讲解

- 获取迭代器中的返回值,用打印对象的方式实现.

- except 异常类 as 对象 给StopIteration这个类实例化对象,起别名是e

- 打印对象时,自动触发StopIteration异常类中的魔术方法__str__

- try .. finally .. 无论代码是否异常,都必须要执行的代码写到finally当中.

- try ... except .. else ..

- for/while ... else ...

- 输入2循环跑不起来,就当是跑完了,走else

---

## 22. 5.主动抛异常.py

### 📋 运行结果

```

错误号:404
错误信息:因为人类没有这种性别
错误文件:/tmp/python3_course/day08_atm项目需求_类中方法property了解异常_异常处理_反射_模块的导入_网络的概念_tcp_udp/代码/5.主动抛异常.py
错误行号:68

```

### 💻 完整代码

```python

# ### 主动抛出异常
"""
主动报错
raise + 异常错误类 / 异常错误类对象

Exception     常见异常错误类的父类
BaseException 所有异常类的父类
"""

# 1.基本语法
"""
raise TypeError   # 异常错误类
raise TypeError() # 异常错误类对象
print("正常执行 ...")
"""
# BaseException是所有异常类的父类,可以接住所有异常.
try:	
	raise BaseException
except BaseException:
	pass

# 简写
try:	
	raise
except:
	pass

# ### 自定义异常
"""所有自定义的异常类都必须继承父类BaseException"""

# 该函数如果想要触发,必须要依赖抛出异常才能获取到行号和文件名;
def return_errorinfo(n):
	import sys
	f = sys.exc_info()[2].tb_frame.f_back
	if n==1:		
		return str(f.f_lineno)      #返回当前行数
	elif n == 2:	
		return f.f_code.co_filename #返回文件名	

# 主动触发,获取对应的行号和文件名
def get_info(n):
	try :
		raise
	except:
		return return_errorinfo(n)

# 自定义异常类
class MyException(BaseException):
	def __init__(self,num,msg,filename,filenum):
		# 自定义错误号
		self.num = num
		# 自定义错误信息
		self.msg = msg
		# 自定义错误文件
		self.filename = filename
		# 自定义错误行号
		self.filenum = filenum
		
	# 打印对象时触发
	def __str__(self):
		return "错误号:{}\n错误信息:{}\n错误文件:{}\n错误行号:{}".format(self.num,self.msg,self.filename,self.filenum)

sex = "雌雄双体"
try:
	if sex == "雌雄双体":
		raise MyException(404,"因为人类没有这种性别",get_info(2),get_info(1))
except MyException as e:
	print(e)
	
```

### 📖 要点讲解

- BaseException是所有异常类的父类,可以接住所有异常.

- 该函数如果想要触发,必须要依赖抛出异常才能获取到行号和文件名;

---

## 23. 6.反射.py

### 📋 运行结果

```

{}
{'__module__': '__main__', '__doc__': '\n类中成员属性: sex \n类中成员方法: eat laugh\n类的功能: 描述小孩特征\n\t', 'sex': '磁性双体', 'eat': <function Children.eat at 0x7d6a4e348fe0>, 'laugh': <function Children.laugh at 0x7d6a4e349300>, 'drink': <function Children.drink at 0x7d6a4e3493a0>}

类中成员属性: sex 
类中成员方法: eat laugh
类的功能: 描述小孩特征
	
类中成员属性: sex 
类中成员方法: eat laugh
类的功能: 描述小孩特征
	
myfunc <class 'str'>
小孩下生时,仰天大笑:老子可算出来了
Children <class 'str'>
小孩下生时,仰天大笑:老子可算出来了
<class '__main__.Children'>
(<class '__main__.Man'>, <class '__main__.Woman'>)
True
True
小孩下生时,只会喝奶奶
我是个无参的普通方法
该成员不存在
刘硬
玻璃花
玻璃花
{'sys': <module 'sys' (built-in)>, 'builtins': <module 'builtins' (built-in)>, '_frozen_importlib': <module '_frozen_importlib' (frozen)>, '_imp': <module '_imp' (built-in)>, '_thread': <module '_thread' (built-in)>, '_warnings': <module '_warnings' (built-in)>, '_weakref': <module '_weakref' (built-in)>, '_io': <module '_io' (built-in)>, 'marshal': <module 'marshal' (built-in)>, 'posix': <module 'posix' (built-in)>, '_frozen_importlib_external': <module '_frozen_importlib_external' (frozen)>, 'time': <module 'time' (built-in)>, 'zipimport': <module 'zipimport' (frozen)>, '_codecs': <module '_codecs' (built-in)>, 'codecs': <module 'codecs' (frozen)>, 'encodings.aliases': <module 'encodings.aliases' from '/usr/lib/python3.12/encodings/aliases.py'>, 'encodings': <module 'encodings' from '/usr/lib/python3.12/encodings/__init__.py'>, 'encodings.utf_8': <module 'encodings.utf_8' from '/usr/lib/python3.12/encodings/utf_8.py'>, '_signal': <module '_signal' (built-in)>, '_abc': <module '_abc' (built-in)>, 'abc': <module 'abc' (frozen)>, 'io': <module 'io' (frozen)>, '__main__': <module '__main__' from '/tmp/python3_course/day08_atm项目需求_类中方法property了解异常_异常处理_反射_模块的导入_网络的概念_tcp_udp/代码/6.反射.py'>, '_stat': <module '_stat' (built-in)>, 'stat': <module 'stat' (frozen)>, '_collections_abc': <module '_collections_abc' (frozen)>, 'genericpath': <module 'genericpath' (frozen)>, 'posixpath': <module 'posixpath' (frozen)>, 'os.path': <module 'posixpath' (frozen)>, 'os': <module 'os' (frozen)>, '_sitebuiltins': <module '_sitebuiltins' (frozen)>, '_distutils_hack': <module '_distutils_hack' from '/usr/lib/python3/dist-packages/_distutils_hack/__init__.py'>, 'types': <module 'types' from '/usr/lib/python3.12/types.py'>, 'importlib._bootstrap': <module '_frozen_importlib' (frozen)>, 'importlib._bootstrap_external': <module '_frozen_importlib_external' (frozen)>, 'warnings': <module 'warnings' from '/usr/lib/python3.12/warnings.py'>, 'importlib': <module 'importlib' from '/usr/lib/python3.12/importlib/__init__.py'>, 'importlib._abc': <module 'importlib._abc' from '/usr/lib/python3.12/importlib/_abc.py'>, 'itertools': <module 'itertools' (built-in)>, 'keyword': <module 'keyword' from '/usr/lib/python3.12/keyword.py'>, '_operator': <module '_operator' (built-in)>, 'operator': <module 'operator' from '/usr/lib/python3.12/operator.py'>, 'reprlib': <module 'reprlib' from '/usr/lib/python3.12/reprlib.py'>, '_coll

```

### 💻 完整代码

```python

# ### 1.类中属性
class Man():
	pass
	
class Woman():
	pass
	
class Children(Man,Woman):
	"""
类中成员属性: sex 
类中成员方法: eat laugh
类的功能: 描述小孩特征
	"""
	sex = "磁性双体"
	
	def eat(self):
		print("小孩下生时,只会喝奶奶")
		
	def laugh(self,func):
		# 获取函数或者类的名字
		res = func.__name__
		print(res , type(res)) # myfunc
		print("小孩下生时,仰天大笑:老子可算出来了")
		
	def drink():
		print("我是个无参的普通方法")
		
obj = Children()
# __dict__ 获取对象或类的内部成员结构
print(obj.__dict__)
print(Children.__dict__)
# __doc__  获取对象或类的内部文档
print(obj.__doc__)
print(Children.__doc__)
# __name__ 获取类名函数名
def myfunc():
	print("我是myfunc函数")

obj.laugh(myfunc)
obj.laugh(Children)

# __class__ 获取当前对象所属的类
print(obj.__class__) # <class '__main__.Children'>
# __bases__ 获取一个类直接继承的所有父类,返回元组
print(Children.__bases__) # (<class '__main__.Man'>, <class '__main__.Woman'>)

# ### 2.反射 : 通过字符串操作类对象 或者模块中的成员;
# (1)类中的反射
#hasattr() 检测对象/类是否有指定的成员
# 对象
res = hasattr(obj,"sex")
print(res)
# 类
res = hasattr(Children,"eat")
print(res)

#getattr() 获取对象/类成员的值
# 对象
eat = getattr(obj,"eat")
# 返回的是绑定方法(对象系统自动传递,不需要手动.)
eat()
# 类
drink = getattr(Children,"drink")
drink()
# 如果反射的成员不存在,可以设置默认值;
res = getattr(Children,"drink123342","该成员不存在")
print(res)

#setattr() 设置对象/类成员的值
# 对象
setattr(obj,"name","刘硬")
print(obj.name)
# 类
setattr(Children,"eye","玻璃花")
print(Children.eye)
print(obj.eye)

#delattr() 删除对象/类成员的值 
delattr(obj,"name")
# print(obj.name)
delattr(Children,"eye")
# print(Children.eye)
# print(obj.eye)

# 小应用
"""
strvar = input("请输入你要反射的方法:")
print(strvar,type(strvar))
if hasattr(obj,strvar):
	# 反射实际的函数
	func = getattr(obj,strvar)
	# 调用实际的函数
	func()
"""

# (2)模块的反射
"""sys.modules 返回一个系统字典,字典的键是加载的所有模块"""
import sys
print(sys.modules)
"""
返回的这个系统字典中: 键就是模块名 值就是模块对象
{
'builtins': <module 'builtins' (built-in)>, 
'sys': <module 'sys' (built-in)>, 
'_frozen_importlib': <module '_frozen_importlib' (frozen)>, '_imp': <module '_imp' (built-in)>, '_warnings': <module '_warnings' (built-in)>, '_thread': <module '_thread' (built-in)>, '_weakref': <module '_weakref' (built-in)>, '_frozen_importlib_external': <module '_frozen_importlib_external' (frozen)>, '_io': <module 'io' (built-in)>, 'marshal': <module 'marshal' (built-in)>, 'nt': <module 'nt' (built-in)>, 'winreg': <module 'winreg' (built-in)>, 'zipimport': <module 'zipimport' (built-in)>, 'encodings': <module 'encodings' from 'C:\\Users\\KnightPlan\\AppData\\Local\\Programs\\Python\\Python36\\lib\\encodings\\__init__.py'>, 'codecs': <module 'codecs' from 'C:\\Users\\KnightPlan\\AppData\\Local\\Programs\\Python\\Python36\\lib\\codecs.py'>, 
'_codecs': <module '_codecs' (built-in)>, 'encodings.aliases': <module 'encodings.aliases' from 'C:\\Users\\KnightPlan\\AppData\\Local\\Programs\\Python\\Python36\\lib\\encodings\\aliases.py'>, 'encodings.utf_8': <module 'encodings.utf_8' from 'C:\\Users\\KnightPlan\\AppData\\Local\\Programs\\Python\\Python36\\lib\\encodings\\utf_8.py'>, '_signal': <module '_signal' (built-in)>, 
'__main__': <module '__main__' from 'E:/python5周末班/day8/6.py'>, 'encodings.latin_1': <module 'encodings.latin_1' from 'C:\\Users\\KnightPlan\\AppData\\Local\\Programs\\Python\\Python36\\lib\\encodings\\latin_1.py'>, 
'io': <module 'io' from 'C:\\Users\\KnightPlan\\AppData\\Local\\Programs\\Python\\Python36\\lib\\io.py'>, 'abc': <module 'abc' from 'C:\\Users\\KnightPlan\\AppData\\Local\\Programs\\Python\\Python36\\lib\\abc.py'>, '_weakrefset': <module '_weakrefset' from 'C:\\Users\\KnightPlan\\AppData\\Local\\Programs\\Python\\Python36\\lib\\_weakrefset.py'>, 'site': <module 'site' from 'C:\\Users\\KnightPlan\\AppData\\Local\\Programs\\Python\\Python36\\lib\\site.py'>, 
'os': <module 'os' from 'C:\\Users\\KnightPlan\\AppData\\Local\\Programs\\Python\\Python36\\lib\\os.py'>, 'errno': <module 'errno' (built-in)>, 'stat': <module 'stat' from 'C:\\Users\\KnightPlan\\AppData\\Local\\Programs\\Python\\Python36\\lib\\stat.py'>, '_stat': <module '_stat' (built-in)>, 'ntpath': <module 'ntpath' from 'C:\\Users\\KnightPlan\\AppData\\Local\\Programs\\Python\\Python36\\lib\\ntpath.py'>, 'genericpath': <module 'genericpath' from 'C:\\Users\\KnightPlan\\AppData\\Local\\Programs\\Python\\Python36\\lib\\genericpath.py'>, 
'os.path': <module 'ntpath' from 'C:\\Users\\KnightPlan\\AppData\\Local\\Programs\\Python\\Python36\\lib\\ntpath.py'>, '_collections_abc': <module '_collections_abc' from 'C:\\Users\\KnightPlan\\AppData\\Local\\Programs\\Python\\Python36\\lib\\_collections_abc.py'>, '_sitebuiltins': <module '_sitebuiltins' from 'C:\\Users\\KnightPlan\\AppData\\Local\\Programs\\Python\\Python36\\lib\\_sitebuiltins.py'>, '_bootlocale': <module '_bootlocale' from 'C:\\Users\\KnightPlan\\AppData\\Local\\Programs\\Python\\Python36\\lib\\_bootlocale.py'>, 
'_locale': <module '_locale' (built-in)>, 'encodings.gbk': <module 'encodings.gbk' from 'C:\\Users\\KnightPlan\\AppData\\Local\\Programs\\Python\\Python36\\lib\\encodings\\gbk.py'>, '_codecs_cn': <module '_codecs_cn' (built-in)>, '_multibytecodec': <module '_multibytecodec' (built-in)>, 'sysconfig': <module 'sysconfig' from 'C:\\Users\\KnightPlan\\AppData\\Local\\Programs\\Python\\Python36\\lib\\sysconfig.py'>, 'encodings.cp437': <module 'encodings.cp437' from 'C:\\Users\\KnightPlan\\AppData\\Local\\Programs\\Python\\Python36\\lib\\encodings\\cp437.py'>}
"""
def func1():
	print("我是func1函数")
def func2():
	print("我是func2函数")
def func3():
	print("我是func3函数")
# 返回本模块的对象
print(sys.modules["__main__"]) # <module '__main__' from 'E:/python5周末班/day8/6.py'>
mymodule = sys.modules["__main__"]

# 反射出本模块中的一些方法
if hasattr(mymodule,"func1"):
	func1 = getattr(mymodule,"func1")
	func1()

# 小应用
while True:
	strvar = input("请输入您要反射的方法")
	if hasattr(mymodule,strvar):
		func = getattr(mymodule,strvar)
		func()
	else:
		print("对不起,没有本函数方法")

```

### 📖 要点讲解

- __dict__ 获取对象或类的内部成员结构

- __bases__ 获取一个类直接继承的所有父类,返回元组

- ### 2.反射 : 通过字符串操作类对象 或者模块中的成员;

- hasattr() 检测对象/类是否有指定的成员

- 返回的是绑定方法(对象系统自动传递,不需要手动.)

---

## 24. 8.网络笔记.py

### 📋 运行结果

```

错误：  File "/tmp/python3_course/day08_atm项目需求_类中方法property了解异常_异常处理_反射_模块的导入_网络的概念_tcp_udp/代码/8.网络笔记.py", line 42
    ip地址的最后一位0或者255 两个数字不能用，
                           ^
SyntaxError: invalid character '，' (U+FF0C)

```

### 💻 完整代码

```python

# ### 1.网络开发的两大架构
a文件 -> b文件, 借助c文件
a文件把数据放在c文件中,b文件从中读取
b文件把数据放在c文件中,a文件从中读取
构成了早期数据交互的模型 -> socket(套接字)
socket是收发数据的工具

后来有了网络之后
a文件中的数据,通过网络协议,转化1010电信号进行发送
a文件通过socket打包数据发送
b文件通过socket解包数据接收

# 二大架构
c/s
	c => client 客户端
		具体的软件,比如qq,微信,腾讯会议
	s => server 服务端
		也是一台主机,相较于普通电脑,性能运算速度更快,能够抗住更大的并发访问;
		天河三号,秒计算是百亿亿次

b/s
	b => brower 浏览器
		具体通过网址,访问对方的服务器,响应请求之后,
		把对应的数据返回,浏览器解析数据,呈现在电脑上
	s => server 服务端
		也是一台主机,相较于普通电脑,性能运算速度更快,能够抗住更大的并发访问;
		天河三号,秒计算是百亿亿次

# b/s c/s两大架构, b/s是未来的主流趋势
	(1) 省去下载安装环节,节省电脑的硬盘内存空间
	(2) 因为手机的便捷性,随时随地可以访问到想要的各种应用,提升效率,加快速度

# ### 2.网络的概念
# (1) ip
ip -> cmd -> ipconfig
标识一台电脑有2个重要地址
	(1) ip  逻辑地址 可改
		ipv4  0.0.0.0 ~ 255.255.255.255 2^32-1 43个亿的ip数量(已经不够了) 2^32-1
		ipv6  0:0:0:0:0:0:0:0 ~ FFFF:FFFF:FFFF:FFFF:FFFF:FFFF:FFFF:FFFF  2^128-1
		
		ip地址的最后一位0或者255 两个数字不能用，
		一般最后一位0表达的是网段,255代表广播地址
		
	(2) mac 物理地址 不可改
	
# (2) 网段 : IP地址和子网掩码相与得到的值相同就是同一网段
	#子网掩码:区分网段和主机
	
	255.255.255.0   / 255.255.0.0 /  255.0.0.0
	ip1 : 192.168.4.15
	子网掩码: 255.255.255.0
	11000000.10101000.00000100.00001111  ip1
	11111111.11111111.11111111.00000000  子网掩码
	11000000.10101000.00000100.00000000  网段192.168.4.0

	ip2 : 192.168.4.154
	子网掩码: 255.255.255.0
	11000000.10101000.00000100.10011010  ip1
	11111111.11111111.11111111.00000000  子网掩码
	11000000.10101000.00000100.00000000  网段192.168.4.0
	
	ip1 : 192.168.40.15
	子网掩码: 255.255.0.0
	11000000.10101000.00101000.00001111  ip1
	11111111.11111111.00000000.00000000  子网掩码
	11000000.10101000.00000000.00000000  网段192.168.0.0

	ip2 : 192.168.37.154
	子网掩码: 255.255.0.0
	11000000.10101000.00100101.10011010  ip1
	11111111.11111111.00000000.00000000  子网掩码
	11000000.10101000.00000000.00000000  网段192.168.0.0	
	
	因为2个ip 的网段相同 ,所以可以实现通信; 通过更改子网掩码,可以扩大网段的范围;

# (3) 端口 0~65535 
	ip可以找到这个世界上的任何一个电脑
	端口可以找到电脑中的具体某个软件或者某个程序服务
	ip+端口 可以找到世界上任何一台电脑中的任何一个程序(软件)
	
	知名端口:
		FTP（文件传输）协议代理服务器常用端口号：21
		SSH（安全登录）、SCP（文件传输）、端口号重定向，默认的端口号为22/tcp
		Telnet（远程登录）协议代理服务器常用端口号：23
		简单邮件传输协议（SMTP）25
		HTTP协议代理服务器常用端口号:80
		HTTPS（securely transferring web pages）服务器，默认的端口号为443；
		MySQL 数据库服务 3306

# ### 3.osi网络七层模型
	应用层: (应用层,表示层,会话层)
		依据不同的协议,封装对应个数的数据消息
		HTTP (超文本传输协议)
		HTTPS(加密传输超文本协议)
		FTP  (文件传输协议)
		SMTP (电子邮箱传输协议)

	传输层:
		封装端口:
			指定传输的协议(TCP协议/UDP协议)
			
	网络层:
		封装ip
			版本ipv4 / ipv6
	
	数据链路层:
		封装mac地址
			指定链路层协议(arp协议/rarp协议)

	物理层:
		给数据打包,变成二进制的字节流,然后通过网络进行传输.

ARP地址解析协议     :通过ip->mac的过程
RARP反向地址解析协议:通过mac->ip的过程

# ### 4.TCP/UDP 协议
SYN 创建连接
ACK 确认响应
FIN 断开连接
# 三次握手
	客户端发送一个请求,与服务端建立连接
	服务端接收到这个请求,并且响应与客户端连接的请求
	(服务端的响应和请求是在一次发送当中完成的)
	客户端接收到服务器的响应后,再发送一个确认请求
	到此 , 三次握手结束, 
	
	接下来就是数据传输的过程
	每次发送的时候,接收方都会发送回执消息,
	如果发送方没有接收到接收方的回执消息
	会把该数据包在发送一次,直到收到回执消息为止.
	这就是为什么TCP协议传输稳定不丢包的原因.
	
# 四次挥手
	客户端向服务店发送一个断开连接的请求(代表客户端没有数据给服务端)
	服务端接收请求,发送响应
	等待服务端所有数据收发完毕之后
	服务端向客户端发送断开连接的请求(代表服务端没有数据给客户端)
	客户端接收响应,等到2msl,最大报文生存时间之后
	客户端与服务端彻底断开连接

2msl : 有可能出现网络问题,导致b服务端一直没有接收到客户端a发送过来的确认消息
	   b服务端会一直给客户端a发数据,等待2msl就是为了防止这种现象发生,所以客户端a
	   会多响应几次,但是超过2msl,客户端a也不管了,直接断开.

```

### 📖 要点讲解

- b/s c/s两大架构, b/s是未来的主流趋势

- (2) 网段 : IP地址和子网掩码相与得到的值相同就是同一网段

---

## 🖼️ 参考资料

![bs架构_交换机.png](./assets/bs架构_交换机.png)

![socket.png](./assets/socket.png)

![传输数据流程.png](./assets/传输数据流程.png)

![传输数据流程解析.png](./assets/传输数据流程解析.png)

![局域网.png](./assets/局域网.png)

![局域网解析.png](./assets/局域网解析.png)

![模块.png](./assets/模块.png)

![1555372027666.png](./assets/1555372027666.png)

![1555372055442.png](./assets/1555372055442.png)

![1555372108386.png](./assets/1555372108386.png)

![1555372355580.png](./assets/1555372355580.png)

![1555374519652.png](./assets/1555374519652.png)

![1555374663853.png](./assets/1555374663853.png)

![1555454444379.png](./assets/1555454444379.png)

![1555454621256.png](./assets/1555454621256.png)

![1555456389523.png](./assets/1555456389523.png)

![1559165147948.png](./assets/1559165147948.png)

![1559165234479.png](./assets/1559165234479.png)

![1559171471044.png](./assets/1559171471044.png)
