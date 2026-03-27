# Day 1: day01 进制转换 8进制和16进制的转换 注释 变量 number str dict set Number容器的类型转换 字典的强转

> 对应原课程：day01_进制转换_8进制和16进制的转换_注释_变量_number_str_dict_set_Number容器的类型转换_字典的强转

---

## 1. 1.注释.py

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

## 2. 2.变量.py

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

## 3. 3.int.py

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

## 4. 4.float_bool_complex.py

### 📋 运行结果

```

<class 'float'>
0.0031412
<class 'float'>
<class 'bool'>
False
<class 'complex'>
(-0-90j)
(3+7j)

```

### 💻 完整代码

```python

# ### Number (float bool complex )

# float 浮点型(小数)
# 表示方式一
floatvar = 5.88
print( type(floatvar) )

# 表示方式二 (科学计数法)
floatvar = 3.14e5
floatvar = 314.12e-5
print(floatvar) # 314000.0   
print( type(floatvar)  )

# bool 布尔类型(True -> 真值 False -> 假值)
boolvar = True
boolvar = False
print( type(boolvar) )
print(boolvar)

# complex 复数类型
"""
复数 = 实数 + 虚数
complexvar = 3 + 7j
实数: 3
虚数: 7j
j   : 如果有一个数,它的平方等于-1,那么这个数等于j,表达一个高精度的类型(科学家认为有)

"""
# 表达方式一
complexvar = 3 + 7j
complexvar = -90j
print( type(complexvar) )
print(complexvar)

# 表达方式二
'''complex(实数,虚数)'''
complexvar = complex(3,7)
print(complexvar)

```

### 📖 要点讲解

- ### Number (float bool complex )

- bool 布尔类型(True -> 真值 False -> 假值)

---

## 5. 5.字符串.py

### 📋 运行结果

```

刘硬是班级里面唯一一个女生 <class 'str'>
吕文康真"帅" <class 'str'>

今天是python5期,重开线下班的第一天
同学都来学习,不容易
给大家点个'赞'
预祝大家在"未来"的学习生活中
更上一层楼

E:\nyth\tay1
奉双喜今天买了 9个风油精
奉双喜今天买了9 个风油精
刘崇祥看好了一个高达模型,需要9.92元
张俊文和印象中它是不一样的,印象中的它长得像金城武
赵强今天发工资20000.9元,买了9个特斯拉
赵强今天发工资20000.8888元,买了9个特斯拉

```

### 💻 完整代码

```python

# ### 字符串类型 str
'''用引号引起来的就是字符串'''
"""
# 转义字符:\ + 字符
	(1) 把有意义的字符变得无意义
	(2) 把无意义的字符变得有意义
	
\n   : 换行
\r\n : 换行
\t   : 缩进tab (水平制表符)
\r   : 把\r后面的字符串拉到当前行行首
"""

# (1) 单引号字符串
strvar = '刘硬是班级里面唯一一个女生'
print(  strvar   ,  type(strvar) )

# (2) 双引号字符串
# 把无意义的字符变得有意义
strvar = "吕文康真帅,\n帅的掉渣"
strvar = "吕文康真帅,\r\n帅的掉渣"
strvar = "吕文康\t真帅,帅的掉渣"
strvar = "吕文康\n真帅,\r帅的掉渣"
# 把有意义的字符变得无意义
strvar = "吕文康真\"帅\"" 
strvar = '吕文康真"帅"'
print( strvar , type(strvar) )

# (3) 三引号字符串 (可以换行)
strvar = '''
今天是python5期,重开线下班的第一天
同学都来学习,不容易
给大家点个'赞'
预祝大家在"未来"的学习生活中
更上一层楼
'''
print( strvar )

# (4) 元字符串 r"字符串" 不转义字符,原型化输出字符串
path = r"E:\nyth\tay1"
print(path)

# (5) 字符串的格式化
"""
语法:
	"字符串" % (值1,值2,值3 .... )
	
	%d 整型占位符
	%f 浮点型占位符
	%s 字符串占位符
"""

# %d 整型占位符
strvar = "我今天买了%d个苹果" % (100)
# %2d 占两位,不够两位的拿空格来补,原字符串居右
strvar = "奉双喜今天买了%2d个风油精" % (9)
print(strvar)
# %-2d 占两位,不够两位的拿空格来补,原字符串居左
strvar = "奉双喜今天买了%-2d个风油精" % (9)
print(strvar)

# %f 浮点型占位符
strvar = "刘崇祥看好了一个高达模型,需要%f元" % (9.9)
# %.2f 小数点保留2位(存在四舍五入)
strvar = "刘崇祥看好了一个高达模型,需要%.2f元" % (9.9188)
print(strvar)

# %s 字符串占位符
strvar = "%s" % ("张俊文和印象中它是不一样的,印象中的它长得像金城武")
print(strvar)

# 综合案例
strvar = "%s今天发工资%.1f元,买了%d个特斯拉" % ("赵强",20000.8888,9)
print(strvar)

strvar = "%s今天发工资%s元,买了%s个特斯拉" % ("赵强",20000.8888,9)
print(strvar)

```

### 📖 要点讲解

- (4) 元字符串 r"字符串" 不转义字符,原型化输出字符串

- %2d 占两位,不够两位的拿空格来补,原字符串居右

- %-2d 占两位,不够两位的拿空格来补,原字符串居左

---

## 6. 6.list_tuple.py

### 📋 运行结果

```

错误：  File "/tmp/python3_course/day01_进制转换_8进制和16进制的转换_注释_变量_number_str_dict_set_Number容器的类型转换_字典的强转/6.list_tuple.py", line 80
    strvar[0] = "z" error
                    ^^^^^
SyntaxError: invalid syntax

```

### 💻 完整代码

```python

# ### list 列表类型

# 1.定义列表
"""特点: 可获取,可修改,有序"""
# 空列表
listvar = []
print(listvar , type(listvar) )

# 普通列表

# 正向索引下标    0          1        2       3      4       5
listvar =      ["奉双喜","刘重祥","张俊文","赵强","刘硬","吕文康"]
# 逆向索引下标   -6        -5        -4       -3    -2       -1

# 2.获取列表当中的元素
res = listvar[1]
res = listvar[-1]
print(res)

# 3.修改列表当中的元素
listvar[1] = "刘翔"
print(listvar)

# 4.获取列表中最后一个元素
listvar =  ["奉双喜",True,4-90j,15,23.4]
# python特有
res = listvar[-1]
print(res)

# 所有语言通用 (len 获取容器类型数据的所有元素个数)
length = len(listvar) # 5
res = listvar[length - 1] # 5 - 1 = 4
print(res)

# ### tuple 元组类型
"""特点:可获取,不可修改,有序"""
# (1) 定义元组
# 空元组
tuplevar = ()
print(tuplevar , type(tuplevar))

# 普通元组
# 正向索引下标    0          1        2       3      4       5
tuplevar =    ("奉双喜","刘重祥","张俊文","赵强","刘硬","吕文康")
# 逆向索引下标   -6        -5        -4       -3    -2       -1

# (2)可获取元组当中的元素
res = tuplevar[4]
res = tuplevar[-2]
print(res)

# (3) 可修改元组当中的元素么? 不可以
# tuplevar[2] = 123  error

# (4) 元组的注意点:
'''逗号是元组的标识符'''
tuplevar = (3+90j,)
tuplevar = 3+90j,
print( tuplevar , type(tuplevar) )

# ### str 字符串类型
"""特点:可获取,不可修改,有序"""
# 1.定义字符串
#         01234
strvar = 'abcde'
#        -5-4-3-2-1

# 定义空字符串
strvar = ''

# 2.获取字符串当中的元素
res = strvar[3]
res = strvar[-2]
print(res)

# 3.可以修改字符串中的元素么? 不行
strvar[0] = "z" error

```

### 📖 要点讲解

- 正向索引下标    0          1        2       3      4       5

- 逆向索引下标   -6        -5        -4       -3    -2       -1

- 所有语言通用 (len 获取容器类型数据的所有元素个数)

- 正向索引下标    0          1        2       3      4       5

- 逆向索引下标   -6        -5        -4       -3    -2       -1

- tuplevar[2] = 123  error

---

## 7. 7.dict_set.py

### 📋 运行结果

```

{'王文', '郭富城', '张学友', '刘德华'} <class 'set'>
{'王文', '郭富城', '张学友', '刘德华'}
set() <class 'set'>
{} <class 'dict'>
王文
{'zjl': '周杰伦', 'wy': '王硬', 'mam': '毛阿敏', 'zzx': '赵忠祥', 'ww': '王文'} <class 'dict'>
5
{1: 1, False: 'ss', (3+4j): 2, 5.67: 3, '中文': 4, (1, 2, 3): 5} <class 'dict'>
set()

```

### 💻 完整代码

```python

# ### set 集合 (作用:交差并补)
"""特点: 集合无序,自动去重"""
# 1.定义集合
setvar = {"王文","张学友","刘德华","郭富城"}
print(setvar , type(setvar))

# 2.集合的无序性:(既不能获取其中的元素,也不能修改其中的元素)
# 集合不能获取元素
# res = setvar[0] error

# 集合不能修改元素
# setvar[0] = 1 error
# print(setvar)

# 3.自动去重
setvar = {"王文","张学友","刘德华","郭富城","郭富城","郭富城"}
print(setvar)

# 4.集合的注意点
setvar = set()
print(setvar , type(setvar))

# ### dict 字典
"""
特点: 键值对存储的数据,表面上有序,实际上无序.
dictvar = {键1:值1,键2:值2, .....}
"""
# 1.定义字典
# 空字典
dictvar = {}
print(dictvar , type(dictvar))

# 普通字典
dictvar = {"zjl":"周杰伦","wy":"王源","mam":"毛阿敏","zzx":"赵忠祥","ww":"王文"}

# 2.获取字典当中的值
res = dictvar["zjl"]
res = dictvar["ww"]
print(res)

# 3.修改字典当中的值
dictvar["wy"] = "王硬"
print(dictvar , type(dictvar))

# ### 对于字典的键 和 集合中的值有数据类型上的要求:
'''
# 不可变的数据类型(可哈希) 允许
Number(int bool float complex) str tuple
# 可变的数据类型(不可哈希) 不允许
list  set  dict

哈希算法: 字典和集合底层在进行存储时,都使用了哈希算法,存储时是无序的散列
作用:更加均匀的把数据分配在内存中进行存储.计算值时必须是Number str tuple
提到哈希算法: 无序散列

3.6版本之后,对字典做了优化,存储时仍然是无序的散列
拿出时按照字面顺序重新排列,表面上有序的,实际上无序,

在做字典的键时: 推荐使用变量命名的字符串
'''

dic = {1:1,False : "ss" , 3+4j:2 , 5.67:3 , "中文":4 , (1,2,3):5}
res = dic[(1,2,3)]
print(res)
print(dic , type(dic))

# setvar = {1,2,3,[1,2,3]} error
# setvar = {"a",(1,2,3,[4,5,6])} error
print(setvar)

```

### 📖 要点讲解

- 2.集合的无序性:(既不能获取其中的元素,也不能修改其中的元素)

- res = setvar[0] error

- ### 对于字典的键 和 集合中的值有数据类型上的要求:

- setvar = {1,2,3,[1,2,3]} error

- setvar = {"a",(1,2,3,[4,5,6])} error

---

## 8. 8.Number的强制转换.py

### 📋 运行结果

```

1234 <class 'int'>
1234.0
(1234+0j)
False <class 'bool'>

```

### 💻 完整代码

```python

# ### Number 强制类型转换 (int , float , bool , complex)
var1 = 15
var2 = 15.8
var3 = True
var4 = 9-90j
var5 = "1234"
var6 = "abc234"

# int 强制转换成整型
res = int(var2) # 15
res = int(False) # True -> 1 False -> 0
# res = int(var4) error
res = int(var5) #1234
# res = int(var6) error
print(res , type(res))

# float 强制转换成浮点型
res = float(var1) # 15.0
res = float(False) # True -> 1.0 False -> 0.0
res = float(var5) # 1234.0
print(res)

# complex 强制转换成复数
res = complex(var1) # 15 + 0j
res = complex(var2) # 15.8 + 0j
res = complex(False) # True => 1+0j False => 0j
res = complex(var5) # (1234+0j)
print(res)

# bool 强制转换成布尔 (*** 重要 ***)
""" 0 0.0 False 0j '' [] () set() {}  None  """
res = bool( False )
print(res , type(res))

# None 是系统的关键字, 代表空的,什么也没有,一般用来初始化操作,在一开始的时候复制
a = None
b = None

```

### 📖 要点讲解

- ### Number 强制类型转换 (int , float , bool , complex)

- res = int(var4) error

- res = int(var6) error

- bool 强制转换成布尔 (*** 重要 ***)

- None 是系统的关键字, 代表空的,什么也没有,一般用来初始化操作,在一开始的时候复制

---

## 9. 9.Number的自动转换.py

### 📋 运行结果

```

11
12.2
0j
28.6
(14+6j)
(10.780000000000001+67j)
False

```

### 💻 完整代码

```python

# ### Number 的自动类型转换
"""
原则: 精度从低向高进行转换
	bool -> int -> float -> complex
"""

# bool + int
res = True + 10 # True => 1  => 1 + 10
print(res)

# bool + float
res = True + 11.2 # True => 1.0 => 1.0 + 11.2
print(res)

# bool + complex
res = False + 0j # False => 0j => 0j + 0j =>0j
print(res)

# int + float
res = 13 + 15.6 # 13 => 13.0 => 13.0+15.6 => 28.6
print(res)

# int + complex
res = 14 + 6j # 14 => 14 + 0j => 14 +0j +6j
print(res)

# float + complex
res = 6.78 + 4 + 67j # 10.78 + 0j => 10.78 + 67j
print(res)

# 计算机计算小数时,存在精度损耗;
print(0.1 + 0.2 == 0.3)

```

---

## 10. 10.容器类型的强制转换.py

### 📋 运行结果

```

123 <class 'str'>
'123'
['翔翔', '嘻嘻', '强强', '康康', '莹莹', '文文'] <class 'list'>
('yy', 'xx', 'ww') <class 'tuple'>
{'ww', 'yy', 'xx'} <class 'set'>

```

### 💻 完整代码

```python

# ### 容器类型的强制转换 (str , list ,tuple , set , dict)
var1 = "我爱你,亲爱的菇凉"
var2 = ["莹莹","翔翔","嘻嘻","文文","强强","康康"]
var3 = ("莹莹","翔翔","嘻嘻","文文","强强","康康")
var4 = {"莹莹","翔翔","嘻嘻","文文","强强","康康"}
var5 = {'yy':"莹莹" , "xx":"翔翔" ,"xx":"嘻嘻" ,"ww":"文文"}
var6 = 123

# str 强制转换成字符串
"""
在原有的数据两边套上引号
"""
res = str(var2)
res = str(var6)
print(res , type(res) )

# repr  <=>  r"字符串"  不转义字符,原型化输出字符串
print(  repr(res)  )

# list 强制转换成列表
"""
如果是字符串,把字符串中的每个元素单独提取,作为列表中的新元素
如果是字典,只提取字典的键,组成新的列表
如果是其他容器,在数据类型的两边换上[]
"""
res = list(var1)
res = list(var3)
res = list(var4)
# res = list(var5)
print(res , type(res))

# tuple 强制转换成元组
"""
如果是字符串,把字符串中的每个元素单独提取,作为元组中的新元素
如果是字典,只提取字典的键,组成新的元组
如果是其他容器,在数据类型的两边换上()
"""
res = tuple(var1)
res = tuple(var2)
res = tuple(var5)
print(res , type(res))

# set 强制转换成集合
"""
如果是字符串,把字符串中的每个元素单独提取,作为集合中的新元素[无序,自动去重]
如果是字典,只提取字典的键,组成新的集合
如果是其他容器,在数据类型的两边换上{}
"""
res = set(var1)
res = set(var2)
res = set(var5)
print(res , type(res))

```

### 📖 要点讲解

- ### 容器类型的强制转换 (str , list ,tuple , set , dict)

- repr  <=>  r"字符串"  不转义字符,原型化输出字符串

---

## 11. 11.字典的强制转换.py

### 📋 运行结果

```

(4, 5, 6, {'a': 1, 'b': [10, 11, 'bingo']})
{'a': 1, 'b': [10, 11, 'bingo']}
[10, 11, 'bingo']
bingo
bingo
[(1, 2, 3), [4, 5, 6], {7, 8, 9, 10, 11, 12}]
{'a': 1, 'c': 3, 'b': 2}

```

### 💻 完整代码

```python

# 二级容器 (list tuple set dict)

# 二级列表
lst = [1,2,3,[4,4,6]]
# 二级元组
tup = (4,5,6,(5,6,7))
# 二级集合 
setvar = {"a","b",(1,2,3)}

# 二级字典
dic = {"a":1,"b":{"c":2,"d":3}}

# 四级容器
container = [1,2,3,(4,5,6,{"a":1,"b":[10,11,"bingo"]})]
# 获取bingo
res1 = container[-1]
print(res1) # (4, 5, 6, {'a': 1, 'b': [10, 11, 'bingo']})

res2 = res1[-1]
print(res2) #{'a': 1, 'b': [10, 11, 'bingo']}

res3 = res2["b"]
print(res3) # [10, 11, 'bingo']

res4 = res3[-1]
print(res4) # bingo

# 简写
res = container[-1][-1]["b"][-1]
print(res)

# 等长的二级容器
"""1.里面的元素都是容器,2.容器里的元素的个数相同"""
container = [(1,2,3),[4,5,6],{7,8,9}]
container = [(1,2,3),[4,5,6],{7,8,9,10,11,12}] # 不是等长的
print(container)

# ### 字典的强制转换
"""
1.需要等长的二级容器 2.里面的元素个数得是2个.
"""

# 1.外面容器是列表或者元组或者集合,里面的容器是列表或者元组 (推荐)
container = [["a",1],("b",2),["c",3]]
container = (["a",1],("b",2),["c",3])
container = {("a",1),("b",2),("c",3)}
dic = dict(container)
print(dic)

# 2.如果里面的容器是集合 , 不推荐(集合无序)
container = [["a",1],("b",2),{"c",3}]

# 3.如果里面的容器是字符串, 不推荐(字符串的长度有局限性)
container = [["a",1],("b",2),"c34"]

dic = dict(container)
print(dic)

```

### 📖 要点讲解

- 二级容器 (list tuple set dict)

- 1.外面容器是列表或者元组或者集合,里面的容器是列表或者元组 (推荐)

- 2.如果里面的容器是集合 , 不推荐(集合无序)

- 3.如果里面的容器是字符串, 不推荐(字符串的长度有局限性)

---

## 🖼️ 参考资料

![8_16.png](./assets/8_16.png)

![变量.png](./assets/变量.png)

![哈希算法.png](./assets/哈希算法.png)

![字体设置.png](./assets/字体设置.png)

![滚轮调整字体大小.png](./assets/滚轮调整字体大小.png)

![皮肤设置.png](./assets/皮肤设置.png)

![缩进的设置.png](./assets/缩进的设置.png)

![2_8_16_10(2).png](./assets/2_8_16_10(2).png)

![2_8_16_10.png](./assets/2_8_16_10.png)

![1557729534117.png](./assets/1557729534117.png)

![1557736597833.png](./assets/1557736597833.png)

![1557740809484.png](./assets/1557740809484.png)

![1557740921885.png](./assets/1557740921885.png)

![1557741069674.png](./assets/1557741069674.png)

![1557741277521.png](./assets/1557741277521.png)
