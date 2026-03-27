# Day 6: day06 time模块 random json os os.path shutil zipfile计算文件夹大小 类的初体验 类的封装之对象操作 类的封装之类操作 购物车效果 pickle json

> 对应原课程：day06_time模块_random_json_os_os.path_shutil_zipfile计算文件夹大小_类的初体验_类的封装之对象操作_类的封装之类操作_购物车效果_pickle_json

---

## 1. ceshi.py

### 📋 运行结果

```

错误：  File "/tmp/python3_course/day06_time模块_random_json_os_os.path_shutil_zipfile计算文件夹大小_类的初体验_类的封装之对象操作_类的封装之类操作_购物车效果_pickle_json/代码/ceshi.py", line 17
    print(res)
TabError: inconsistent use of tabs and spaces in indentation

```

### 💻 完整代码

```python

def countdown(n):
    while n >= 0:
        newvalue = (yield n) # 第一次停 返回5
        # If a new value got sent in, reset n with it
        if newvalue is not None:
            n = newvalue # n = 3
        else:
            n -= 1

# The holy grail countdown
c = countdown(5)
for x in c:
    print(x)
    # print(x) # # 5 2 1 0
    if x == 5:
        res = c.send(3)
		print(res)
"""
5
2
1
0

"""

```

### 📖 要点讲解

- If a new value got sent in, reset n with it

- The holy grail countdown

---

## 2. 1.time模块.py

### 📋 运行结果

```

1774571911.8189013
time.struct_time(tm_year=2026, tm_mon=3, tm_mday=27, tm_hour=0, tm_min=38, tm_sec=31, tm_wday=4, tm_yday=86, tm_isdst=0)
time.struct_time(tm_year=2020, tm_mon=8, tm_mday=16, tm_hour=1, tm_min=32, tm_sec=58, tm_wday=6, tm_yday=229, tm_isdst=0)
1597570640.0
Fri Mar 27 00:38:31 2026
Sun Aug 16 01:23:20 2020
Mon Aug 16 09:44:30 2020
1597571070.0
Sun Aug 16 09:44:30 2020
2020-08-16 09:50:30
2026-03-27 00:38:31
time.struct_time(tm_year=2020, tm_mon=8, tm_mday=16, tm_hour=9, tm_min=52, tm_sec=15, tm_wday=6, tm_yday=229, tm_isdst=-1)
程序运行时间是: 3.5119078159332275

```

### 💻 完整代码

```python

# ### time 模块
import time

"""
时间元组 => 时间戳 => 时间字符串
localtime => mktime => ctime
"""

#time()          获取本地时间戳
res = time.time()
print(res)

#localtime()     通过[时间戳]获取[时间元组] (默认当前时间)
# 默认当前时间
tup = time.localtime()
print(tup)

# 指定时间戳获取时间元组
tup = time.localtime(1597541578)
print(tup)

#mktime()        通过[时间元组]获取[时间戳] (参数是时间元组)
ttp = (2020,8,16,9,37,20,0,0,0)
res = time.mktime(ttp)
print(res)

#ctime()         通过[时间戳]获取[时间字符串] (默认当前时间)
# 默认当前时间
res = time.ctime()
print(res)

# 指定时间戳获取时间字符串
res = time.ctime(1597541000)
print(res)

#asctime()       通过[时间元组]获取[时间字符串](参数是时间元组) (了解)
ttp = (2020,8,16,9,44,30,0,0,0) # 不能够自动识别周几,只能手动填写,不推荐使用
res = time.asctime(ttp)
print(res)

# 改写
ttp = (2020,8,16,9,44,30,0,0,0)
res = time.mktime(ttp)
print(res)
res = time.ctime(res)
print(res)

"""
strftime 时间元组 -> 时间字符串
strptime 时间字符串 -> 时间元组
"""
#strftime()      通过[时间元组]格式化[时间字符串]  (格式化字符串,[可选时间元组参数])
ttp = (2020,8,16,9,50,30,0,0,0)
# 注意: 在windows中不支持中文的格式化,linux可以
res = time.strftime("%Y-%m-%d %H:%M:%S",ttp)
print(res) # 2020-08-16 09:50:30
# 默认当前时间进行格式化字符串
res = time.strftime("%Y-%m-%d %H:%M:%S")
print(res) # 2020-08-16 09:52:15

#strptime()      通过[时间字符串]提取出[时间元组]  (时间字符串,格式化字符串)
"""写字符串和格式化占位符时,不要随便添加任何字符,包括空格,要严丝合缝才能匹配到正确格式"""
ttp = time.strptime("2020-08-16 09:52:15","%Y-%m-%d %H:%M:%S")
print(ttp)

#sleep()         程序睡眠等待
# time.sleep(3)
# print("wake up ... ")

#perf_counter()  用于计算程序运行的时间 (了解)
# starttime = time.perf_counter()
starttime = time.time()
for i in range(100000000):
	pass

# endtime = time.perf_counter()
endtime = time.time()
print("程序运行时间是:",endtime-starttime)

```

### 📖 要点讲解

- time()          获取本地时间戳

- localtime()     通过[时间戳]获取[时间元组] (默认当前时间)

- mktime()        通过[时间元组]获取[时间戳] (参数是时间元组)

- ctime()         通过[时间戳]获取[时间字符串] (默认当前时间)

- asctime()       通过[时间元组]获取[时间字符串](参数是时间元组) (了解)

- strftime()      通过[时间元组]格式化[时间字符串]  (格式化字符串,[可选时间元组参数])

- 注意: 在windows中不支持中文的格式化,linux可以

- strptime()      通过[时间字符串]提取出[时间元组]  (时间字符串,格式化字符串)

- sleep()         程序睡眠等待

- print("wake up ... ")

- perf_counter()  用于计算程序运行的时间 (了解)

- starttime = time.perf_counter()

- endtime = time.perf_counter()

---

## 3. 1.注释.py

### 📋 运行结果

```

赵强同学,今年25,计算机,运维,14k,山西
刘重祥,今年25,通信,运维,12k,江西
奉双喜,今年28,电气,运维,12k,湖南

```

### 💻 完整代码

```python

# 注释:对代码的解释,方便大家阅读代码
# ctrl + q  notepad  | ctrl + / pycharm | ctrl + z 撤销 | ctrl + y 反撤销

# 注释的分类: (1) 单行注释  (2)多行注释

# (1)单行注释 # 
# python2.7  print '你好'   python3.x  print('你好')

# (2)多行注释 '''  """
'''
print("冯雍同学,今年26,计算机,运维,12k,湖北")
print("吕文康同学,今年30,网络,运维,15k,广西")
print("刘硬同学,今年保密,计算机,测试,呵呵,湖南")
print("赵强同学,今年25,计算机,运维,14k,山西")
print("刘重祥,今年25,通信,运维,12k,江西")
print("奉双喜,今年28,电气,运维,12k,湖南")
'''
"""
print("冯雍同学,今年26,计算机,运维,12k,湖北")
print("吕文康同学,今年30,网络,运维,15k,广西")
print("刘硬同学,今年保密,计算机,测试,呵呵,湖南")
print("赵强同学,今年25,计算机,运维,14k,山西")
print("刘重祥,今年25,通信,运维,12k,江西")
print("奉双喜,今年28,电气,运维,12k,湖南")
"""

# (3) 注释的嵌套
'''
如果外面使用了三个单引号,里面用三个双引号
如果外面使用了三个双引号,里面用三个单引号
需要把单双引号岔开
''' 

"""
print("冯雍同学,今年26,计算机,运维,12k,湖北")
print("吕文康同学,今年30,网络,运维,15k,广西")
print("刘硬同学,今年保密,计算机,测试,呵呵,湖南")
'''
print("赵强同学,今年25,计算机,运维,14k,山西")
'''
print("刘重祥,今年25,通信,运维,12k,江西")
print("奉双喜,今年28,电气,运维,12k,湖南")
"""

# (4) 注释的排错性
'''
包裹一部分代码,执行另外一部分,查看是否报错,
如果没问题,继续在拿出一部分代码运行,查看是否报错
如果有,可以直接找到错误,如果没有,依次推推
'''

"""
print("冯雍同学,今年26,计算机,运维,12k,湖北")
print("吕文康同学,今年30,网络,运维,15k,广西")
print("刘硬同学,今年保密,计算机,测试,呵呵,湖南")
"""
print("赵强同学,今年25,计算机,运维,14k,山西")

print("刘重祥,今年25,通信,运维,12k,江西")

print("奉双喜,今年28,电气,运维,12k,湖南")

```

### 📖 要点讲解

- ctrl + q  notepad  | ctrl + / pycharm | ctrl + z 撤销 | ctrl + y 反撤销

- 注释的分类: (1) 单行注释  (2)多行注释

- python2.7  print '你好'   python3.x  print('你好')

---

## 4. 2.pickle模块.py

### 📋 运行结果

```

b'\x80\x04\x95\x11\x00\x00\x00\x00\x00\x00\x00]\x94(K\x01K\x02K\x03K\x04K\x05K\x06e.' <class 'bytes'>
[1, 2, 3, 4, 5, 6] <class 'list'>
b'\x80\x04\x95\x15\x00\x00\x00\x00\x00\x00\x00\x8c\x08__main__\x94\x8c\x04func\x94\x93\x94.' <class 'bytes'>
<function func at 0x7b684e352160>
我是这个宇宙中,最帅的男人
b'\x80\x04\x958\x00\x00\x00\x00\x00\x00\x00\x8c\x08builtins\x94\x8c\x04iter\x94\x93\x94\x8c\x08builtins\x94\x8c\x05range\x94\x93\x94K\x00K\nK\x01\x87\x94R\x94\x85\x94R\x94.' <class 'bytes'>

```

### 💻 完整代码

```python

# ### pickle 模块
import pickle
"""
序列化:把不能够直接存储到文件的数据变得可存储的过程就是序列化
反序列化: 把序列化后的数据恢复成原来的数据类型
# pickle可以序列化一切数据
"""

lst= [1,2,3,4,5,6]
#dumps 把任意对象序列化成一个bytes
res = pickle.dumps(lst)
print(res , type(res))

#loads 把任意bytes反序列化成原来数据
res = pickle.loads(res)
print(res , type(res))

# 函数可以序列化
def func():
	print("我是这个宇宙中,最帅的男人")

res = pickle.dumps(func)
print(res , type(res))

# 函数可以反序列化
func = pickle.loads(res)
print(func)
func()

# 迭代器可以序列化
it = iter(range(10))
res = pickle.dumps(it)
print(res ,type(res))

# 迭代器可以反序列化
from collections import Iterator, Iterable
it = pickle.loads(res)
print(isinstance(it,Iterator))

for i in it:
	print(i)

print("<=====>")
it = iter(range(10))
#dump  把对象序列化后写入到file-like Object(即文件对象)
with open("ceshi.txt",mode="wb") as fp:	
	pickle.dump(it,fp)

#load  把file-like Object(即文件对象)中的内容拿出来,反序列化成原来数据
with open("ceshi.txt",mode="rb") as fp:
	it = pickle.load(fp)

for i in it:
	print(i)

print("<===111==>")
# 对比dumps 和 loads 操作文件
it = iter(range(10))
with open("ceshi2.txt",mode="wb") as fp:
	res = pickle.dumps(it)
	fp.write(res)
	
with open("ceshi2.txt",mode="rb") as fp:	
	res = fp.read()
	it = pickle.loads(res)

for i in it:
	print(i)

```

### 📖 要点讲解

- dumps 把任意对象序列化成一个bytes

- loads 把任意bytes反序列化成原来数据

- dump  把对象序列化后写入到file-like Object(即文件对象)

- load  把file-like Object(即文件对象)中的内容拿出来,反序列化成原来数据

---

## 5. 2.py

### 📋 运行结果

```

E:\python5周末班\day6\1.py

('', 'E:\\python5周末班\\day6\\1.py')
('', 'E:\\python5周末班\\day6\\1.py')
E:\python5周末班/day6/1.py
.py

```

### 💻 完整代码

```python

# ### os.path 路径模块 
"""(把包理解成文件夹,把模块理解成文件)"""
import os

pathvar = r"E:\python5周末班\day6\1.py"

#basename() 返回文件名部分
res = os.path.basename(pathvar)
print(res)

#dirname()  返回路径部分
res = os.path.dirname(pathvar)
print(res)

#split() 将路径拆分成单独的文件部分和路径部分 组合成一个元组
res = os.path.split(pathvar)
print(res)

#join()  将多个路径和文件组成新的路径 可以自动通过不同的系统加不同的斜杠  linux / windows\
path1 = r"E:\python5周末班"
path2 = "day6"
path3 = "1.py"

# \\ => \ 本身 让有意义的字符变得无意义 ***
print(res)# E:\python5周末班\day6\1.py
res = path1 + "\\" + path2 + "\\" + path3 #版本一
res = path1 + os.sep + path2 + os.sep + path3 # 版本二
res = os.path.join(path1,path2,path3)			# 版本三(推荐)
print(res)

#splitext() 将路径分割为后缀和其他部分 (了解)
"""可以使用字符串函数 split 来取代"""
pathvar = r"E:\python5周末班\day6\1.py"
tup = os.path.splitext(pathvar)
print(tup[-1])

#getsize()  获取文件的大小 ***
"""字节总个数就是文件大小,getsize只能计算文件的大小,算不了文件夹"""
res = os.path.getsize("part13.txt")
# res = os.path.getsize(r"E:\python5周末班\day1") error
print(res)

pathvar = r"E:\python5周末班\day6\1.py"
#isdir()    检测路径是否是一个文件夹 ***
res = os.path.isdir(pathvar)
print(res)

#isfile()   检测路径是否是一个文件   ***
res = os.path.isfile(pathvar)
print(res)

#islink()   检测路径是否是一个链接 
res = os.path.islink(pathvar)
print(res)

#getctime() [windows]文件的创建时间,[linux]权限的改动时间(返回时间戳)
pathvar = r"E:\python5周末班\day6\1.py"
res = os.path.getctime(pathvar)
print(res)

#getmtime() 获取文件最后一次修改时间(返回时间戳)
res = os.path.getmtime(pathvar)
print(res)

#getatime() 获取文件最后一次访问时间(返回时间戳)
res = os.path.getatime(pathvar)
print(res)

# 把时间戳 -> 时间字符串 localtime mktime ctime
import time
time_str = time.ctime(res)
print(time_str)

#exists()   检测指定的路径是否存在 ***
pathvar = r"E:\python5周末班\day6\1.py"
res = os.path.exists(pathvar)
print(res)

#isabs()    检测一个路径是否是绝对路径
#abspath()  将相对路径转化为绝对路径
pathvar = "../day4"
if not os.path.isabs(pathvar):
	pathnew = os.path.abspath(pathvar)
	print(pathnew)

# 如何计算一个文件夹的大小？

```

### 📖 要点讲解

- split() 将路径拆分成单独的文件部分和路径部分 组合成一个元组

- join()  将多个路径和文件组成新的路径 可以自动通过不同的系统加不同的斜杠  linux / windows\

- \\ => \ 本身 让有意义的字符变得无意义 ***

- splitext() 将路径分割为后缀和其他部分 (了解)

- getsize()  获取文件的大小 ***

- res = os.path.getsize(r"E:\python5周末班\day1") error

- isdir()    检测路径是否是一个文件夹 ***

- isfile()   检测路径是否是一个文件   ***

- islink()   检测路径是否是一个链接

- getctime() [windows]文件的创建时间,[linux]权限的改动时间(返回时间戳)

- getmtime() 获取文件最后一次修改时间(返回时间戳)

- getatime() 获取文件最后一次访问时间(返回时间戳)

- 把时间戳 -> 时间字符串 localtime mktime ctime

- exists()   检测指定的路径是否存在 ***

- isabs()    检测一个路径是否是绝对路径

- abspath()  将相对路径转化为绝对路径

---

## 6. 2.变量.py

### 📋 运行结果

```

余文杰
5
6
10 11
100 100
2
20
['False', 'None', 'True', 'and', 'as', 'assert', 'async', 'await', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']
别摸我bwm
香肠
jacklove
202 200
202 200
210202200010166688

```

### 💻 完整代码

```python

# ### 变量: 可以改变的量,实际指向的是内存的一块空间

# (1)变量的概念
jiudian408 = "王文"
jiudian408 = "余文杰"
print(jiudian408)

# (2)变量的声明
# 1
a = 5
b = 6
print(a)
print(b)

# 2
a,b = 10 , 11
print(a,b) # 让两个变量在一行打印出来,用逗号隔开

# 3
a = b = 100
print(a,b)

# (3)变量的命名
"""
		  变量的命名
字母数字下划线,首字符不能为数字
严格区分大小写,且不能使用关键字
变量命名有意义,且不能使用中文哦
"""
a1234 =  13333
# *_9087 = 444 error
# 1223ab_ = 555 error
abcd = 2
ABCD = 20

print(abcd)
print(ABCD)

# import 引入 keyword 系统的模块(文件) 模块.成员 来进行调用 => 打印所有的系统关键字
import keyword
print(keyword.kwlist)
"""
[
'False', 'None', 'True', 'and', 'as', 'assert', 'break', 
'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 
'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is',
 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 
 'while', 'with', 'yield'
 ]
"""

# print = 123
# print(print)

mycar = "特斯拉"
klasdfjasjdfasjkldf = "别摸我bwm" # 名字没有任何意义,不推荐,写名字的时候,要见名知意
print(klasdfjasjdfasjkldf)

my_dog_food = "香肠"
print(my_dog_food)

中文 = "jacklove"
print(中文)
"""
	(1) 容易乱码
		编码集utf-8 (万国码 , 可变长的unicode编码集) , 一个中文按照3个字节存储,英文数字特殊符号一个字节
		编码集gbk   (国标码) ,一个中文按照2个字节存储,英文数字特殊符号一个字节
		
	(2) 占用空间大
		zz = "jacklove"     占用2个字节
		中文 = "jacklove"  占用6个字节
"""

# (4)变量的交换
# 通用
a = 200
b = 202
tmp = a
a = b
b = tmp
print(a,b)

# python特有
a = 200
b = 202
a,b = b,a
print(a,b)

# (5)常量 : 不可改变的量 (约定俗成把都是大写的变量作为常量,意味着不能改变值)
SHENFENZHENG = 210202200010166688
print(SHENFENZHENG)

```

### 📖 要点讲解

- ### 变量: 可以改变的量,实际指向的是内存的一块空间

- import 引入 keyword 系统的模块(文件) 模块.成员 来进行调用 => 打印所有的系统关键字

- (5)常量 : 不可改变的量 (约定俗成把都是大写的变量作为常量,意味着不能改变值)

---

## 7. 3.json模块.py

### 📋 运行结果

```

{"age": 18, "classroom": "python5", "family": ["老爸", "老妈"], "name": "卢同喜"} <class 'str'>
{'age': 18, 'classroom': 'python5', 'family': ['老爸', '老妈'], 'name': '卢同喜'} <class 'dict'>
{'age': 18, 'classroom': 'python5', 'family': ['老爸', '老妈'], 'name': '卢同喜'} <class 'dict'>
{'a': 1, 'b': 2} <class 'dict'>
{'c': 3, 'd': 4} <class 'dict'>
{'a': 1, 'b': 2} <class 'dict'>
{'c': 3, 'd': 4} <class 'dict'>

```

### 💻 完整代码

```python

# ### json 模块
"""
json 可以序列化的类型有:(int float bool str list tuple dict None)
所有编程语言都能够识别的数据格式叫做json,是字符串
pickle 可以把任意数据类型都做存储
	   应用:可以做数据的存储
json   可以让任意编程语言都能识别,
	   用用:可以做数据的传输
"""
import json

dic = {"name":"卢同喜","age":18,"classroom":"python5","family":["老爸","老妈"]}
#dumps 和 loads 是一对 , 可以把数据序列化成字符串
"""
# ensure_ascii = False 代表显示中文
# sort_keys=True 对字典的键进行排序
"""
res = json.dumps(dic , ensure_ascii = False, sort_keys=True)
print(res , type(res))

dic = json.loads(res)
print(dic , type(dic))

#dump 和 load  针对于文件内容进行序列化
with open("ceshi.json",mode="w",encoding="utf-8") as fp:
	json.dump(dic,fp,ensure_ascii=False)

with open("ceshi.json",mode="r",encoding="utf-8") as fp:
	dic = json.load(fp)
	print(dic , type(dic))
	
# json 和 pickle的使用区别:
# json
"""
json 可以连续进行dump,但是不能连续load
load 是一次性读取所有数据
"""
dic1 = {"a":1,"b":2}
dic2 = {"c":3,"d":4}
with open("ceshi11.json",mode="w",encoding="utf-8") as fp:
	json.dump(dic1,fp)
	fp.write("\n")
	json.dump(dic2,fp)
	fp.write("\n")
	
# load不能分配读取单个数据,error
"""
with open("ceshi11.json",mode="r",encoding="utf-8") as fp:
	res = json.load(fp)
	print(res,type(res))
	# {"a": 1, "b": 2}
	# {"c": 3, "d": 4}
"""

# 解决办法: 使用loads
with open("ceshi11.json",mode="r",encoding="utf-8") as fp:
	for line in fp:
		dic = json.loads(line)
		print(dic, type(dic))

# pickle
"""
pickle 可以连续进行dump,也可以连续load
"""
import pickle
dic1 = {"a":1,"b":2}
dic2 = {"c":3,"d":4}
with open("ceshi22.pkl",mode="wb") as fp:
	pickle.dump(dic1,fp)
	pickle.dump(dic2,fp)

"""
with open("ceshi22.pkl",mode="rb") as fp:
	dic = pickle.load(fp)
	print(dic , type(dic))
	dic = pickle.load(fp)
	print(dic , type(dic))
"""
# 改造:可否一次性拿出所有数据?
with open("ceshi22.pkl",mode="rb") as fp:
	try:
		while True:
			dic = pickle.load(fp)
			print(dic , type(dic))
	except:
		pass
"""
# 使用异常处理,抑制报错 try .. except ..  把有问题的代码放到try之后,如果
# 发生的异常,直接执行except 这个代码块,来抑制错误
"""

# ### json 和 pickle 两个模块的区别:
"""
(1)json序列化之后的数据类型是str,所有编程语言都识别,
   但是仅限于(int float bool)(str list tuple dict None)
   json不能连续load,只能一次性拿出所有数据
(2)pickle序列化之后的数据类型是bytes,
   所有数据类型都可转化,但仅限于python之间的存储传输.
   pickle可以连续load,多套数据放到同一个文件中
"""

```

### 📖 要点讲解

- dumps 和 loads 是一对 , 可以把数据序列化成字符串

- ensure_ascii = False 代表显示中文

- sort_keys=True 对字典的键进行排序

- dump 和 load  针对于文件内容进行序列化

- 使用异常处理,抑制报错 try .. except ..  把有问题的代码放到try之后,如果

- 发生的异常,直接执行except 这个代码块,来抑制错误

- ### json 和 pickle 两个模块的区别:

---

## 8. 3.int.py

### 📋 运行结果

```

67
<class 'int'>
11757800
5
520
<class 'int'>
255
<class 'int'>

```

### 💻 完整代码

```python

# ### Number -> int 

# int 整型(正整数,0,负整数)

intvar = 67
print(intvar)

# type 获取一个值的类型
res = type(intvar)
print(res)

# id 获取一个值的地址
res = id(intvar)
print(res)

# 二进制整型
intvar = 0b101
print(intvar)

# 八进制整型
intvar = 0o1010
print(intvar)
print( type(intvar) )

# 十六进制
intvar = 0xff
print(intvar)
print( type(intvar) )

```

---

## 9. 4.random随机模块.py

### 📋 运行结果

```

0.10501502823127296
2
2
4
2
1.95543337119998
1.3770924648401137
3
['张勇']
['刘勇', '陈勇', '炉筒溪', '张勇', '李勇']
bBCP

```

### 💻 完整代码

```python

# ### 随机模块 random
import random

#random()    获取随机0-1之间的小数(左闭右开) 0 <= x < 1
res = random.random()
print(res)

#randrange() 随机获取指定范围内的整数(包含开始值,不包含结束值,间隔值)
"""推荐"""
res = random.randrange(3) # 0 1 2 
print(res)
res = random.randrange(1,5) # 1 2 3 4
print(res)
res = random.randrange(1,8,3) # 1 4 7
print(res)

#randint()   随机产生指定范围内的随机整数 (了解)
"""必须是2个参数,功能性上差与randrange,不推荐"""
res = random.randint(1,3) # 1 2 3
print(res)

#uniform() 获取指定范围内的随机小数(左闭右开)
res = random.uniform(1,3) # 1 <= x < 3
print(res)
res = random.uniform(3,1) # 1 < x <=3
print(res)
"""
a = 3 , b = 1
return a + (b-a) * self.random()
return a + (b-a) * 0<=x<1
return 3 + (1-3) * 0<=x<1
return 3 + -2 * 0<=x<1
return 3 +  -2 < x <= 0
retirm 1 < x <=3
"""

#choice()  随机获取序列中的值(多选一)
lst = [1,2,3,4]
res = random.choice(lst)
print(res)

#sample()  随机获取序列中的值(多选多) [返回列表]
lst = ["炉筒溪","张勇","陈勇","李勇","刘勇"]
res = random.sample(lst,1)
print(res)

#shuffle() 随机打乱序列中的值(直接打乱原序列)
lst = ["炉筒溪","张勇","陈勇","李勇","刘勇"]
random.shuffle(lst)
print(lst)

# 网站验证码
# 数字 小写字母 大写字母 4位
def yanzhengma():
	strvar = "" 
	for i in range(4):
		# 数字
		num = str(random.randrange(10))
		# 小写字母
		s_char = chr(random.randrange(97,123))
		# 大写字母
		b_char = chr(random.randrange(65,91))
		# 把每次抽到的元素用字符串拼接到一起
		lst = [num,s_char,b_char]		
		strvar += random.choice(lst)
	return strvar
	
res = yanzhengma()
print(res)

```

### 📖 要点讲解

- random()    获取随机0-1之间的小数(左闭右开) 0 <= x < 1

- randrange() 随机获取指定范围内的整数(包含开始值,不包含结束值,间隔值)

- randint()   随机产生指定范围内的随机整数 (了解)

- uniform() 获取指定范围内的随机小数(左闭右开)

- choice()  随机获取序列中的值(多选一)

- sample()  随机获取序列中的值(多选多) [返回列表]

- shuffle() 随机打乱序列中的值(直接打乱原序列)

---

## 10. 5.os对系统操作的模块.py

### 📋 运行结果

```

```

### 💻 完整代码

```python

# ### os 对系统操作的模块
import os

#system()  在python中执行系统命令
# os.system("ipconfig")
# os.system("calc")
# os.system("mspaint")
# windows 创建文件的方法
# os.system("echo 123455667 > ceshi100.txt") 

#popen()   执行系统命令返回对象,通过read方法读出字符串
"""执行命令,打印字符串时使用popen防止乱码"""
obj = os.popen("ipconfig") # 返回对象
res = obj.read() # 对象.read方法 默认转成gbk格式在输出;
print(res)

#listdir() 获取指定文件夹中所有内容的名称列表
"""
相对路径: 相对于当前文件的位置进行查找
绝对路径: 相对于根,获取完整的路径

相对路径
.   相对于当前
..  相对于上一级

绝对路径
[windows] E:\python5周末班\day6 
[linux]   /root/etc/abc/
"""
# 相对:
lst = os.listdir(".")
# 绝对:切记在路径前加上r 防止转义;
lst = os.listdir(r"E:\python5周末班\day6")
print(lst)
['1.py', '2.py', '3.py', '4.py', '5.py', 'ceshi.json', 'ceshi.py', 'ceshi.txt', 'ceshi100.txt', 'ceshi11.json', 'ceshi2.txt', 'ceshi22.pkl', 'part10.md', 'part11.md', 'part12.md', 'part13.md']

# getcwd()  获取当前文件所在的默认路径
pathvar = os.getcwd()
print(pathvar) #E:\python5周末班\day6

# 魔术属性 __file__
print(__file__) # E:/python5周末班/day6/5.py

#chdir()   修改当前文件工作的默认路径
# os.chdir(r"E:\python5周末班")
# os.system("echo 你好啊 > ceshi100.txt")

#environ   获取或修改环境变量
"""
相当于: 右键qq属性->找到路径
右键我的电脑属性 -> 找到高级系统设置 -> 环境变量 -> Path -> 新建一个,把路径追加进去 -> 在执行qq命令时,系统自动按照环境变量中的路径找命令;
"""
"""
往系统环境变量PATH当中追加路径,可以在执行命令的时候,让系统自动通过路径找到对应的命令,否则找不到报错. 上下操作的过程是等价的;
[linux操作方法]先创建脚本wangwen.sh -> 写入ifconfig-> chmod 777 wangwen.sh -> ./wangwen.sh   (了解)
		       如果能够执行成功,把这个脚本的路径写到python environ环境变量中, 在通过python执行一遍也可以.(了解)
"""
print(os.environ)
os.environ["PATH"] += ";C:\Program Files (x86)\Tencent\QQ\Bin"
"""
environ(
{
'ALLUSERSPROFILE': 'C:\\ProgramData', 
'APPDATA': 'C:\\Users\\KnightPlan\\AppData\\Roaming', 
'COMMONPROGRAMFILES': 'C:\\Program Files\\Common Files', 
'COMMONPROGRAMFILES(X86)': 'C:\\Program Files (x86)\\Common Files', 'COMMONPROGRAMW6432': 'C:\\Program Files\\Common Files', 'COMPUTERNAME': 'DESKTOP-IPO65L5', 'COMSPEC': 'C:\\WINDOWS\\system32\\cmd.exe', 'DRIVERDATA': 'C:\\Windows\\System32\\Drivers\\DriverData', 'ERLANG_HOME': 'C:\\Program Files\\erl10.5', 'FPS_BROWSER_APP_PROFILE_STRING': 'Internet Explorer', 'FPS_BROWSER_USER_PROFILE_STRING': 'Default', 'HOMEDRIVE': 'C:', 'HOMEPATH': '\\Users\\KnightPlan', 'IDEA_INITIAL_DIRECTORY': 'C:\\Users\\KnightPlan\\Desktop', 
'LOCALAPPDATA': 'C:\\Users\\KnightPlan\\AppData\\Local', 'LOGONSERVER': '\\\\DESKTOP-IPO65L5', 'NUMBER_OF_PROCESSORS': '6', 'ONEDRIVE': 'C:\\Users\\KnightPlan\\OneDrive', 'OS': 'Windows_NT', 
'PATH': 'D:\\py_lianxi\\venv\\Scripts;C:\\Program Files\\Python36\\Scripts\\;C:\\Program Files\\Python36\\;C:\\Windows\\system32;C:\\Windows;C:\\Windows\\System32\\Wbem;C:\\Windows\\System32\\WindowsPowerShell\\v1.0\\;C:\\Windows\\System32\\OpenSSH\\;C:\\Program Files (x86)\\NVIDIA Corporation\\PhysX\\Common;C:\\Program Files (x86)\\Intel\\Intel(R) Management Engine Components\\DAL;C:\\Program Files\\Intel\\Intel(R) Management Engine Components\\DAL;C:\\Program Files\\Git\\cmd;D:\\MySQL5.7\\mysql-5.7.25-winx64\\bin;C:\\Program Files (x86)\\Tencent\\QQ\\Bin;D:\\Redis\\;C:\\Program Files\\nodejs\\;%SystemRoot%\\system32;%SystemRoot%;%SystemRoot%\\System32\\Wbem;%SYSTEMROOT%\\System32\\WindowsPowerShell\\v1.0\\;%SYSTEMROOT%\\System32\\OpenSSH\\;C:\\Users\\KnightPlan\\AppData\\Local\\Programs\\Python\\Python36\\Scripts\\;C:\\Users\\KnightPlan\\AppData\\Local\\Programs\\Python\\Python36\\;C:\\Users\\KnightPlan\\AppData\\Local\\Microsoft\\WindowsApps;;C:\\Program Files\\JetBrains\\PyCharm 2019.1.3\\bin;;C:\\Users\\KnightPlan\\AppData\\Roaming\\npm', 'PATHEXT': '.COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.MSC', 'PROCESSOR_ARCHITECTURE': 'AMD64', 'PROCESSOR_IDENTIFIER': 'Intel64 Family 6 Model 158 Stepping 10, GenuineIntel', 'PROCESSOR_LEVEL': '6', 'PROCESSOR_REVISION': '9e0a', 'PROGRAMDATA': 'C:\\ProgramData', 'PROGRAMFILES': 'C:\\Program Files', 'PROGRAMFILES(X86)': 'C:\\Program Files (x86)', 'PROGRAMW6432': 'C:\\Program Files', 
'PROMPT': '(venv) $P$G', 'PSMODULEPATH': 'C:\\Program Files\\WindowsPowerShell\\Modules;C:\\WINDOWS\\system32\\WindowsPowerShell\\v1.0\\Modules', 'PT7HOME': 'd:\\Program Files\\Cisco Packet Tracer 7.2', 'PUBLIC': 'C:\\Users\\Public', 'PYCHARM': 'C:\\Program Files\\JetBrains\\PyCharm 2019.1.3\\bin;', 'PYCHARM_HOSTED': '1', 'PYTHONIOENCODING': 'UTF-8', 'PYTHONPATH': 'D:\\py_lianxi', 'PYTHONUNBUFFERED': '1', 'QT_DEVICE_PIXEL_RATIO': 'auto', 'SESSIONNAME': 'Console', 'SYSTEMDRIVE': 'C:', 'SYSTEMROOT': 'C:\\WINDOWS', 'TEMP': 'C:\\Users\\KnightPlan\\AppData\\Local\\Temp', 'TMP': 'C:\\Users\\KnightPlan\\AppData\\Local\\Temp', 'USERDOMAIN': 'DESKTOP-IPO65L5', 'USERDOMAIN_ROAMINGPROFILE': 'DESKTOP-IPO65L5', 'USERNAME': 'KnightPlan', 'USERPROFILE': 'C:\\Users\\KnightPlan', 'VIRTUAL_ENV': 'D:\\py_lianxi\\venv', 'WINDIR': 'C:\\WINDOWS', '_OLD_VIRTUAL_PATH': 'C:\\Program Files\\Python36\\Scripts\\;C:\\Program Files\\Python36\\;C:\\Windows\\system32;C:\\Windows;C:\\Windows\\System32\\Wbem;C:\\Windows\\System32\\WindowsPowerShell\\v1.0\\;C:\\Windows\\System32\\OpenSSH\\;C:\\Program Files (x86)\\NVIDIA Corporation\\PhysX\\Common;C:\\Program Files (x86)\\Intel\\Intel(R) Management Engine Components\\DAL;C:\\Program Files\\Intel\\Intel(R) Management Engine Components\\DAL;C:\\Program Files\\Git\\cmd;D:\\MySQL5.7\\mysql-5.7.25-winx64\\bin;C:\\Program Files (x86)\\Tencent\\QQ\\Bin;D:\\Redis\\;C:\\Program Files\\nodejs\\;%SystemRoot%\\system32;%SystemRoot%;%SystemRoot%\\System32\\Wbem;%SYSTEMROOT%\\System32\\WindowsPowerShell\\v1.0\\;%SYSTEMROOT%\\System32\\OpenSSH\\;C:\\Users\\KnightPlan\\AppData\\Local\\Programs\\Python\\Python36\\Scripts\\;C:\\Users\\KnightPlan\\AppData\\Local\\Programs\\Python\\Python36\\;C:\\Users\\KnightPlan\\AppData\\Local\\Microsoft\\WindowsApps;;C:\\Program Files\\JetBrains\\PyCharm 2019.1.3\\bin;;C:\\Users\\KnightPlan\\AppData\\Roaming\\npm', 
'_OLD_VIRTUAL_PROMPT': '$P$G'})

"""
# os.system("QQScLauncher")

#--os 模块属性
#name 获取系统标识   linux,mac ->posix      windows -> nt
print(os.name) # 
#sep 获取路径分割符号  linux,mac -> /       window-> \
print(os.sep)  # ***
#linesep 获取系统的换行符号  linux,mac -> \n    window->\r\n 或 \n
print(repr(os.linesep))

```

### 📖 要点讲解

- system()  在python中执行系统命令

- os.system("ipconfig")

- os.system("echo 123455667 > ceshi100.txt")

- popen()   执行系统命令返回对象,通过read方法读出字符串

- listdir() 获取指定文件夹中所有内容的名称列表

- getcwd()  获取当前文件所在的默认路径

- chdir()   修改当前文件工作的默认路径

- os.chdir(r"E:\python5周末班")

- os.system("echo 你好啊 > ceshi100.txt")

- os.system("QQScLauncher")

- name 获取系统标识   linux,mac ->posix      windows -> nt

- sep 获取路径分割符号  linux,mac -> /       window-> \

- linesep 获取系统的换行符号  linux,mac -> \n    window->\r\n 或 \n

---

## 11. 6.os对文件进行操作.py

### 💻 完整代码

```python

# ### os 模块 之 对文件进行操作
import os
"""
os     -> 新建/删除/
shutil -> 复制/移动/
"""
#os.mknod   创建文件
"""windows不兼容 linux支持"""
# os.mknod("1.txt")
# os.system("echo abc > 1.txt")
#os.remove  删除文件
# os.remove("1.txt")

# os.mkdir   创建目录(文件夹)
# os.mkdir("ceshi200")
# os.rmdir   删除目录(文件夹)
# os.rmdir("ceshi200")
#os.rename  对文件,目录重命名
# os.rename("ceshi200","ceshi300")
#os.makedirs   递归创建文件夹
# os.makedirs("a/b/c/d/e")
#os.removedirs 递归删除文件夹（空文件夹）
# os.removedirs("a/b/c/d/e")

# ### shutil (主要用在复制和移动)
import shutil
#copyfile(src,dst)   #单纯的仅复制文件内容 , 底层调用了 copyfileobj
# shutil.copyfile("part13.md","part13.txt")

#copytree(src,dst)   #拷贝文件夹里所有内容(递归拷贝)
# shutil.copytree(r"E:\python5周末班\day1",r"E:\python5周末班\dayceshi")
#rmtree(path)        #删除当前文件夹及其中所有内容(递归删除)
# shutil.rmtree(r"E:\python5周末班\dayceshi")
#move(path1,paht2)   #移动文件或者文件夹
# shutil.move(r"E:\python5周末班\ceshi100.txt",r"E:\soft")

```

### 📖 要点讲解

- os.system("echo abc > 1.txt")

- os.rename("ceshi200","ceshi300")

- os.makedirs   递归创建文件夹

- os.makedirs("a/b/c/d/e")

- os.removedirs 递归删除文件夹（空文件夹）

- os.removedirs("a/b/c/d/e")

- ### shutil (主要用在复制和移动)

- copyfile(src,dst)   #单纯的仅复制文件内容 , 底层调用了 copyfileobj

- shutil.copyfile("part13.md","part13.txt")

- copytree(src,dst)   #拷贝文件夹里所有内容(递归拷贝)

- shutil.copytree(r"E:\python5周末班\day1",r"E:\python5周末班\dayceshi")

- rmtree(path)        #删除当前文件夹及其中所有内容(递归删除)

- shutil.rmtree(r"E:\python5周末班\dayceshi")

- move(path1,paht2)   #移动文件或者文件夹

- shutil.move(r"E:\python5周末班\ceshi100.txt",r"E:\soft")

---

## 12. 7.os.path路径模块.py

### 📋 运行结果

```

E:\python5周末班\day6\1.py

('', 'E:\\python5周末班\\day6\\1.py')
('', 'E:\\python5周末班\\day6\\1.py')
E:\python5周末班/day6/1.py
.py
22
False
False
False

```

### 💻 完整代码

```python

# ### os.path 路径模块 
"""(把包理解成文件夹,把模块理解成文件)"""
import os

pathvar = r"E:\python5周末班\day6\1.py"

#basename() 返回文件名部分
res = os.path.basename(pathvar)
print(res)

#dirname()  返回路径部分
res = os.path.dirname(pathvar)
print(res)

#split() 将路径拆分成单独的文件部分和路径部分 组合成一个元组
res = os.path.split(pathvar)
print(res)

#join()  将多个路径和文件组成新的路径 可以自动通过不同的系统加不同的斜杠  linux / windows\
path1 = r"E:\python5周末班"
path2 = "day6"
path3 = "1.py"

# \\ => \ 本身 让有意义的字符变得无意义 ***
print(res)# E:\python5周末班\day6\1.py
res = path1 + "\\" + path2 + "\\" + path3 #版本一
res = path1 + os.sep + path2 + os.sep + path3 # 版本二
res = os.path.join(path1,path2,path3)			# 版本三(推荐)
print(res)

#splitext() 将路径分割为后缀和其他部分 (了解)
"""可以使用字符串函数 split 来取代"""
pathvar = r"E:\python5周末班\day6\1.py"
tup = os.path.splitext(pathvar)
print(tup[-1])

#getsize()  获取文件的大小 ***
"""字节总个数就是文件大小,getsize只能计算文件的大小,算不了文件夹"""
res = os.path.getsize("part13.txt")
# res = os.path.getsize(r"E:\python5周末班\day1") error
print(res)

pathvar = r"E:\python5周末班\day6\1.py"
#isdir()    检测路径是否是一个文件夹 ***
res = os.path.isdir(pathvar)
print(res)

#isfile()   检测路径是否是一个文件   ***
res = os.path.isfile(pathvar)
print(res)

#islink()   检测路径是否是一个链接 
res = os.path.islink(pathvar)
print(res)

#getctime() [windows]文件的创建时间,[linux]权限的改动时间(返回时间戳)
pathvar = r"E:\python5周末班\day6\1.py"
res = os.path.getctime(pathvar)
print(res)

#getmtime() 获取文件最后一次修改时间(返回时间戳)
res = os.path.getmtime(pathvar)
print(res)

#getatime() 获取文件最后一次访问时间(返回时间戳)
res = os.path.getatime(pathvar)
print(res)

# 把时间戳 -> 时间字符串 localtime mktime ctime
import time
time_str = time.ctime(res)
print(time_str)

#exists()   检测指定的路径是否存在 ***
pathvar = r"E:\python5周末班\day6\1.py"
res = os.path.exists(pathvar)
print(res)

#isabs()    检测一个路径是否是绝对路径
#abspath()  将相对路径转化为绝对路径
pathvar = "../day4"
if not os.path.isabs(pathvar):
	pathnew = os.path.abspath(pathvar)
	print(pathnew)

# 如何计算一个文件夹的大小？

```

### 📖 要点讲解

- split() 将路径拆分成单独的文件部分和路径部分 组合成一个元组

- join()  将多个路径和文件组成新的路径 可以自动通过不同的系统加不同的斜杠  linux / windows\

- \\ => \ 本身 让有意义的字符变得无意义 ***

- splitext() 将路径分割为后缀和其他部分 (了解)

- getsize()  获取文件的大小 ***

- res = os.path.getsize(r"E:\python5周末班\day1") error

- isdir()    检测路径是否是一个文件夹 ***

- isfile()   检测路径是否是一个文件   ***

- islink()   检测路径是否是一个链接

- getctime() [windows]文件的创建时间,[linux]权限的改动时间(返回时间戳)

- getmtime() 获取文件最后一次修改时间(返回时间戳)

- getatime() 获取文件最后一次访问时间(返回时间戳)

- 把时间戳 -> 时间字符串 localtime mktime ctime

- exists()   检测指定的路径是否存在 ***

- isabs()    检测一个路径是否是绝对路径

- abspath()  将相对路径转化为绝对路径

---

## 13. 8.计算文件夹的大小.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day06_time模块_random_json_os_os.path_shutil_zipfile计算文件夹大小_类的初体验_类的封装之对象操作_类的封装之类操作_购物车效果_pickle_json/代码/8.计算文件夹的大小.py", line 4, in <module>
    lst = os.listdir(pathvar)
          ^^^^^^^^^^^^^^^^^^^
FileNotFoundError: [Errno 2] No such file or directory: 'E:\\python5周末班\\day6\\ceshi300'

```

### 💻 完整代码

```python

# ### 计算文件夹的大小
import os
pathvar = r"E:\python5周末班\day6\ceshi300"
lst = os.listdir(pathvar)
print(lst)

# 1.基本思路
size = 0
for i in lst:
	# 拼接一个绝对路径(无论什么情况都有效)
	pathnew = os.path.join(pathvar,i)
	if os.path.isfile(pathnew):
		print(i,"[是一个文件]")
		size += os.path.getsize(pathnew)
	elif os.path.isdir(pathnew):
		print(i,"[是一个文件夹]")
print(size)

# 2.使用递归函数计算文件夹大小
def getallsize(pathvar):
	# 初始化文件大小为0
	size = 0
	# 打开文件夹
	lst = os.listdir(pathvar)
	print(lst)
	
	# 遍历这个文件夹中所有的文件
	for i in lst:
		# 拼接完整的绝对路径
		pathnew = os.path.join(pathvar,i)
		print(pathnew)
		# 判断是否是文件
		if os.path.isfile(pathnew):
			print(i,"[文件]")
			# 文件大小的累加和
			size += os.path.getsize(pathnew)
		# 判断是否是文件夹
		elif os.path.isdir(pathnew):
			print(i,"[文件夹]")
			# 文件大小的累加和
			size += getallsize(pathnew)
			
	# 返回最终的文件大小
	return size
	
res = getallsize(pathvar)
print(res)

```

---

## 14. 9.zipfile.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day06_time模块_random_json_os_os.path_shutil_zipfile计算文件夹大小_类的初体验_类的封装之对象操作_类的封装之类操作_购物车效果_pickle_json/代码/9.zipfile.py", line 9, in <module>
    zf.write(r"E:\python5周末班\day1\1.注释.py","1.注释.py")
  File "/usr/lib/python3.12/zipfile/__init__.py", line 1854, in write
    zinfo = ZipInfo.from_file(filename, arcname,
            ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/lib/python3.12/zipfile/__init__.py", line 573, in from_file
    st = os.stat(filename)
         ^^^^^^^^^^^^^^^^^
FileNotFoundError: [Errno 2] No such file or directory: 'E:\\python5周末班\\day1\\1.注释.py'

```

### 💻 完整代码

```python

# ### zipfile 压缩包 (后缀 .zip 支持with语法操作)
import zipfile

# 1.创建压缩包
# (1)创建压缩包对象
zf = zipfile.ZipFile("ceshi0816_1.zip",mode="w",compression=zipfile.ZIP_DEFLATED)
# (2)在压缩包中存入文件
"""write(路径,别名)"""
zf.write(r"E:\python5周末班\day1\1.注释.py","1.注释.py")
zf.write(r"E:\python5周末班\day1\2.变量.py","2.变量.py")
zf.write(r"E:\python5周末班\day1\3.int.py",r"tmp\3.int.py")
# (3)关闭文件
zf.close()

# 2.对压缩包解压
zf =  zipfile.ZipFile("ceshi0816_1.zip","r")
# 解压单个
# zf.extract("1.注释.py","ceshi0816_1")
# 解压所有
zf.extractall("ceshi0816_1")
zf.close()

# 3.怎么追加文件 (自动执行关闭操作)
with zipfile.ZipFile("ceshi0816_1.zip","a",zipfile.ZIP_DEFLATED) as zf:
	zf.write(r"E:\python5周末班\day1\part1.md","part1.md")

# 4.怎么查看压缩包
with zipfile.ZipFile("ceshi0816_1.zip","r") as zf:
	lst = zf.namelist()
	print(lst)

```

### 📖 要点讲解

- ### zipfile 压缩包 (后缀 .zip 支持with语法操作)

- zf.extract("1.注释.py","ceshi0816_1")

---

## 15. 10.oop面向对象的程序开发.py

### 📋 运行结果

```

<__main__.Car object at 0x7d12b233f7d0>
5

```

### 💻 完整代码

```python

# ### oop 面向对象的程序开发
# (1)类的定义
class Car:
	pass

# 推荐使用
class Car(): 
	pass
	
class Car(object):
	pass

# (2)类的实例化
class Car():
	pass
	
# 类的实例化(实例化对象)
obj = Car()
print(obj)

# (3)类的基本结构
"""
类中的成员只有两个:
	成员属性(变量)
	成员方法(函数)
	
不能直接裸露的把逻辑判断和循环直接写在类当中
而是用成员方法封装一下,再类中只保留成员属性和方法;
"""
class Car():
	a = 5
	if a == 5:
		print(a)

# 改写
class Car():
	def func():
		a = 5
		if a == 5:
			print(a)

# (4)类的命名
"""
# 推荐使用: 大驼峰命名法(每个单词的首字母大写)
# mycar => MyCar 
# mybaby => MyBaby
"""

```

### 📖 要点讲解

- 推荐使用: 大驼峰命名法(每个单词的首字母大写)

---

## 16. 11.封装-对象的相关操作.py

### 📋 运行结果

```

<__main__.MyCar object at 0x742e5178a1b0>
月牙白色
小车出厂时,都能跑 月牙白色
皮质座垫
{'zuodian': '皮质座垫', 'color': '屎黄色'}
小车出厂时,都能跑 屎黄色
我的车能变形,请叫我大黄蜂~
{'zuodian': '皮质座垫', 'color': '屎黄色', 'dahuangfeng': <function dahuangfeng at 0x742e51bda2a0>}
我的车能变形,一柱擎天!,请叫我擎天柱,我的颜色是屎黄色
<=====>
我的车能变形,一柱擎天!,请叫我擎天柱,我的颜色是屎黄色
请叫我威震天
月牙白色

```

### 💻 完整代码

```python

# ### 面向对象oop - 封装 - 对象的相关操作
"""
封装等级:
	(1) 公有成员 : (在类内或者类外都能够访问的成员)
	(2) 私有成员 : (只能在类内访问的到,类外访问不到)
	
封装成员:
	(1) 成员属性
	(2) 成员方法
	
封装使用:
	(1) 对象.成员属性
	(2) 对象.成员方法
	
绑定方法:
	(1) 绑定到对象:
			在使用对象调用类中方法时,系统会自动把该对象当成参数进行调用
			传递给类中的方法的过程,叫做绑定到对象的方法;
	(2) 绑定到类:
			在使用对象或类调用类中方法时,系统会自动把该类当成参数进行调用
			传递给类中的方法的过程,叫做绑定到类的方法
"""
class MyCar():
	# 公有成员属性
	color = "月牙白色"
	# 私有成员属性
	__price = "300万"	
	
	# 公有成员方法
	def run(self):
		# self <=> obj
		print("小车出厂时,都能跑",self.color)		
	# 私有成员方法
	def __price_info():
		print("小车的价格保密")
	
# 实例化对象
obj = MyCar()
print(obj)
	
# (1)实例化的对象访问公有成员属性和方法
# 成员属性
print(obj.color) # 月牙白色
# 成员方法
obj.run()
# 私有成员无法在类外调用
# obj.__price error
	
# (2)实例化的对象动态添加公有成员属性和方法
# 类外添加成员属性
obj.zuodian = "皮质座垫"
print(obj.zuodian)
# 获取类对象中的成员 __dict__ 返回字典
obj.color = "屎黄色"
print(obj.__dict__)
obj.run()	
	
# 类外添加成员方法
"""在类外动态添加成员方法时,系统不会自动传递obj对象参数;"""
# 普通版 (无参方法)
def dahuangfeng():
	print("我的车能变形,请叫我大黄蜂~")

obj.dahuangfeng = dahuangfeng
obj.dahuangfeng()
print(obj.__dict__)
	
# 升级版 (有参方法)
def qingtianzhu(obj,name):
	print("我的车能变形,一柱擎天!,请叫我{},我的颜色是{}".format(name,obj.color))

obj.qingtianzhu = qingtianzhu
obj.qingtianzhu(obj,"擎天柱")
	
# 究极版 (绑定方法)
"""在类外创建绑定方法"""
import types
# MethodType(方法,对象) 把方法和对象绑定在一起 -> 形成绑定方法(系统自动传递对象)
# print(types.MethodType(qingtianzhu,obj)) # bound method qingtianzhu
obj.qingtianzhu =  types.MethodType(qingtianzhu,obj)
# 调用方法
print("<=====>")
obj.qingtianzhu("擎天柱")

# 也可以绑定lambda表达式
obj.weizhentian = lambda : print("请叫我威震天")
obj.weizhentian()
	
print(MyCar.color)
	
```

### 📖 要点讲解

- ### 面向对象oop - 封装 - 对象的相关操作

- (2)实例化的对象动态添加公有成员属性和方法

- 获取类对象中的成员 __dict__ 返回字典

- MethodType(方法,对象) 把方法和对象绑定在一起 -> 形成绑定方法(系统自动传递对象)

- print(types.MethodType(qingtianzhu,obj)) # bound method qingtianzhu

---

## 17. 12.封装-类的相关操作.py

### 📋 运行结果

```

吕文康
飞机能飞
{'__module__': '__main__', 'captain': '吕文康', '_Plane__sister': '5个', 'fly': <function Plane.fly at 0x763e7f345440>, '_Plane__sister_info': <function Plane.__sister_info at 0x763e7f3acfe0>, '__dict__': <attribute '__dict__' of 'Plane' objects>, '__weakref__': <attribute '__weakref__' of 'Plane' objects>, '__doc__': None, 'passenger': '100个'}
飞机可以发射导弹,开火
飞机的机身构造异常,是可以隐身的
飞机可以空中旋转365度

```

### 💻 完整代码

```python

# ### 面向对象oop - 封装 -> 类的相关操作

class Plane():	
	# 公有成员
	captain = "吕文康"
	# 私有成员
	__sister = "5个"

	# 公有方法
	def fly():
		print("飞机能飞")
		
	# 私有方法
	def __sister_info():
		print("飞机上空姐年龄是保密的")
		
# 实例化对象
# obj = Plane()
# obj.fly() error 因为没有定义形参 形参实参不能一一对应

# (1)定义的类访问公有成员属性和方法
# 成员属性
print(Plane.captain)
# 成员方法
Plane.fly()

# 可以调用私有成员么?
# Plane.__sister_info() error

# (2)定义的类动态添加公有成员属性和方法
# 成员属性
Plane.passenger = "100个"
print(Plane.__dict__) # 系统内置的 + 自定义的成员都在一个字典中
# 成员方法
# (1) 无参方法
def fire():
	print("飞机可以发射导弹,开火")

# Plane.成员属性 = 函数
Plane.fire = fire
Plane.fire()

# (2) 有参方法
def skin(typeplane):
	print("飞机的机身构造异常,是可以{}的".format(typeplane))
Plane.skin = skin
Plane.skin("隐身")

# (3) lambda 表达式
Plane.xuanzhuan365 = lambda : print("飞机可以空中旋转365度")
Plane.xuanzhuan365()

# 对象和类之间的注意点
"""
#对象是类的实例,类是对象的模板

对象和类是两个完全不同的空间
对象在调用成员时,先看看自己对象空间中是否存在,
有则调用,没有则调用类中的公有成员
类中如果也没有,直接报错

对象允许调用类中的成员
类中不能调用对象中的成员

"""

```

### 📖 要点讲解

- ### 面向对象oop - 封装 -> 类的相关操作

- obj.fly() error 因为没有定义形参 形参实参不能一一对应

- Plane.__sister_info() error

---

## 🖼️ 参考资料

![类和对象.png](./assets/类和对象.png)

![递归解析图.png](./assets/递归解析图.png)
