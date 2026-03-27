# Day 5: day05 注册演示 登录小程序 迭代器 map filter reduce sorted 列表字典集合推导式 生成器 内置方法

> 对应原课程：day05_注册演示_登录小程序_迭代器_map_filter_reduce_sorted_列表字典集合推导式_生成器_内置方法

---

## 1. 测试1.py

### 📋 运行结果

```

103.3
4
15
15
423
-190
[-190, 12, 19, 78, 423]
423 -190
('黄启新', 50)
('张俊文', 18)
8
3
0
1
2
3
4
5
6
3
8
13
10
9
8
7
6
5
4
3
2
1
0b11111111
0o10
0x10
a
97
456 <class 'int'>
1122233
None
100
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
E:
ython5周末班	ay5
'E:\nython5周末班\tay5'
-2435614892153773427 -2435614892153773427

```

### 💻 完整代码

```python

# ### python的内置方法

# abs 绝对值函数
res = abs(-1)
res = abs(103.3)
print(res)

# round 四舍五入 (奇进偶不进 发生在n.5的情况下 n为偶数则舍去 n.5 n为奇数，则进一)
res = round(3.69)
res = round(3.5)
res = round(4.68)
res = round(4.51)
res = round(4.5)
print(res)

# sum    计算一个序列得和
lst = [1,2,3,4,5]
res = sum(lst)
print(res)

total = 0
for i in lst:
	total += i
print(total)

# max    获取一个序列里边的最大值
lst = [-190,19,78,423,12]
res = max(lst)
print(res)
# min    获取一个序列里边的最小值
lst = [-190,19,78,423,12]
res = min(lst)
print(res)

lst = sorted(lst)
print(lst)
maxval = lst[-1]
minval = lst[0]
print(maxval,minval)

# 自定义规则,找最大值和最小值(按照返回的数据,重新对传入的数据进行排序.找最大和最小的哪个)
lst = [("张俊文",18),("黄金生",19),("黄启新",50)]
def func(n):
	# print(n)
	return n[-1]
res = max(lst,key=func)
print(res)

res = min(lst,key=func)
print(res)

# pow    计算某个数值的x次方
res = pow(2,3)
print(res)
# 先把2的3次幂算完,在和5取余
res = pow(2,3,5)
print(res)

# range  产生指定范围数据的可迭代对象
# 一个参数
for i in range(3):
	print(i) # 0 1 2 
# 二个参数
for i in range(3,7): # 3 4 5 6 
	print(i)
# 三个参数
for i in range(3,14,5): # 3 8 13
	print(i)
	
# for 逆向取值
for i in range(10,0,-1): # 10 9 8 7 6 5 4 3 2 1
	print(i)

# bin    将10进制数据转化为二进制
res = bin(255)
print(res)

# oct    将10进制数据转化为八进制
res = oct(8)
print(res)

# hex    将10进制数据转化为16进制
res = hex(16)
print(res)

# chr    将ASCII编码转换为字符
res = chr(97)
print(res)

# ord    将字符转换为ASCII编码
res = ord("a")
print(res)

# eval   将字符串当作python代码执行
res = eval("456")
print(res , type(res))
res = eval("print(1122233)")
print(res)

'''eval("a = 100") # 不能够动态创建变量的,exec可以'''

# exec   将字符串当作python代码执行(功能更强大)
exec("a = 100")
print(a)
strvar = """
for i in range(10):
	print(i)
"""
exec(strvar)

'''# exec 和 eval 在和用户交互数据的时候,慎用,以防系统出现意外;'''

# repr   不转义字符输出字符串
pathvar = "E:\nython5周末班\tay5"
print(pathvar)
res = repr(pathvar)
print(res)

# input  接受输入字符串
"""
res = input("请输入你是否结过婚:")
print(res)
"""
# hash   生成哈希值
"""
相同的两个值,无论哈希多少次,都会差生相同的数据
1.文件校验
2.密码加密
"""
res1 = hash("abcde")
res2 = hash("abcde")
print(res1,res2)

```

### 📖 要点讲解

- round 四舍五入 (奇进偶不进 发生在n.5的情况下 n为偶数则舍去 n.5 n为奇数，则进一)

- 自定义规则,找最大值和最小值(按照返回的数据,重新对传入的数据进行排序.找最大和最小的哪个)

- range  产生指定范围数据的可迭代对象

- hex    将10进制数据转化为16进制

- eval   将字符串当作python代码执行

- exec   将字符串当作python代码执行(功能更强大)

---

## 2. 测试2.py

### 📋 运行结果

```

103.3
4
15
15
423
-190
[-190, 12, 19, 78, 423]
423 -190
('黄启新', 50)
('张俊文', 18)
8
3
0
1
2
3
4
5
6
3
8
13
10
9
8
7
6
5
4
3
2
1
0b11111111
0o10
0x10
a
97
456 <class 'int'>
1122233
None
100
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
E:
ython5周末班	ay5
'E:\nython5周末班\tay5'
-7094974593165561506 -7094974593165561506

```

### 💻 完整代码

```python

# ### python的内置方法

# abs 绝对值函数
res = abs(-1)
res = abs(103.3)
print(res)

# round 四舍五入 (奇进偶不进 发生在n.5的情况下 n为偶数则舍去 n.5 n为奇数，则进一)
res = round(3.69)
res = round(3.5)
res = round(4.68)
res = round(4.51)
res = round(4.5)
print(res)

# sum    计算一个序列得和
lst = [1,2,3,4,5]
res = sum(lst)
print(res)

total = 0
for i in lst:
	total += i
print(total)

# max    获取一个序列里边的最大值
lst = [-190,19,78,423,12]
res = max(lst)
print(res)
# min    获取一个序列里边的最小值
lst = [-190,19,78,423,12]
res = min(lst)
print(res)

lst = sorted(lst)
print(lst)
maxval = lst[-1]
minval = lst[0]
print(maxval,minval)

# 自定义规则,找最大值和最小值(按照返回的数据,重新对传入的数据进行排序.找最大和最小的哪个)
lst = [("张俊文",18),("黄金生",19),("黄启新",50)]
def func(n):
	# print(n)
	return n[-1]
res = max(lst,key=func)
print(res)

res = min(lst,key=func)
print(res)

# pow    计算某个数值的x次方
res = pow(2,3)
print(res)
# 先把2的3次幂算完,在和5取余
res = pow(2,3,5)
print(res)

# range  产生指定范围数据的可迭代对象
# 一个参数
for i in range(3):
	print(i) # 0 1 2 
# 二个参数
for i in range(3,7): # 3 4 5 6 
	print(i)
# 三个参数
for i in range(3,14,5): # 3 8 13
	print(i)
	
# for 逆向取值
for i in range(10,0,-1): # 10 9 8 7 6 5 4 3 2 1
	print(i)

# bin    将10进制数据转化为二进制
res = bin(255)
print(res)

# oct    将10进制数据转化为八进制
res = oct(8)
print(res)

# hex    将10进制数据转化为16进制
res = hex(16)
print(res)

# chr    将ASCII编码转换为字符
res = chr(97)
print(res)

# ord    将字符转换为ASCII编码
res = ord("a")
print(res)

# eval   将字符串当作python代码执行
res = eval("456")
print(res , type(res))
res = eval("print(1122233)")
print(res)

'''eval("a = 100") # 不能够动态创建变量的,exec可以'''

# exec   将字符串当作python代码执行(功能更强大)
exec("a = 100")
print(a)
strvar = """
for i in range(10):
	print(i)
"""
exec(strvar)

'''# exec 和 eval 在和用户交互数据的时候,慎用,以防系统出现意外;'''

# repr   不转义字符输出字符串
pathvar = "E:\nython5周末班\tay5"
print(pathvar)
res = repr(pathvar)
print(res)

# input  接受输入字符串
"""
res = input("请输入你是否结过婚:")
print(res)
"""
# hash   生成哈希值
"""
相同的两个值,无论哈希多少次,都会差生相同的数据
1.文件校验
2.密码加密
"""
res1 = hash("abcde")
res2 = hash("abcde")
print(res1,res2) 

```

### 📖 要点讲解

- round 四舍五入 (奇进偶不进 发生在n.5的情况下 n为偶数则舍去 n.5 n为奇数，则进一)

- 自定义规则,找最大值和最小值(按照返回的数据,重新对传入的数据进行排序.找最大和最小的哪个)

- range  产生指定范围数据的可迭代对象

- hex    将10进制数据转化为16进制

- eval   将字符串当作python代码执行

- exec   将字符串当作python代码执行(功能更强大)

---

## 3. 1.迭代器.py

### 📋 运行结果

```

['__and__', '__class__', '__class_getitem__', '__contains__', '__delattr__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__getstate__', '__gt__', '__hash__', '__iand__', '__init__', '__init_subclass__', '__ior__', '__isub__', '__iter__', '__ixor__', '__le__', '__len__', '__lt__', '__ne__', '__new__', '__or__', '__rand__', '__reduce__', '__reduce_ex__', '__repr__', '__ror__', '__rsub__', '__rxor__', '__setattr__', '__sizeof__', '__str__', '__sub__', '__subclasshook__', '__xor__', 'add', 'clear', 'copy', 'difference', 'difference_update', 'discard', 'intersection', 'intersection_update', 'isdisjoint', 'issubset', 'issuperset', 'pop', 'remove', 'symmetric_difference', 'symmetric_difference_update', 'union', 'update']
True
['__class__', '__delattr__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__getstate__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__iter__', '__le__', '__length_hint__', '__lt__', '__ne__', '__new__', '__next__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__']
True
a
d
b
c
a <======1=====>
<============2===========>
d
b
c
<============2===========>
a
d
b
c

```

### 💻 完整代码

```python

# ### 迭代器 : 能被next调用,并不断返回下一个值的对象 (迭代器是对象)
"""
概念:
	迭代器指的是迭代取值的工具，迭代是一个重复的过程，每次重复都是基于上一次的结果而继续的，
	单纯的重复并不是迭代  
特征:
	并不依赖索引,而通过next指针(内存地址寻址)迭代所有数据,一次只取一个值,
	而不是一股脑的把所有数据放进内存.大大节省空间,
"""

# 1.可迭代对象
setvar = {"a","b","c","d"}
# dir 获取集合对象中的所有成员
res = dir(setvar)
print(res)
# 判断是否是可迭代对象 , 依赖__iter__成员
res = "__iter__" in dir(setvar)
print(res)

# 2.迭代器
"""
for 循环之所以能够遍历所有的数据,底层使用的是迭代器.依赖next指针,通过地址寻址的
方式,把内存中的数据一个一个拿出来.

可迭代对象 -> 迭代器  实际上就是从不能够被next直接调用 到 可以被next直接调用的过程

如果是一个可迭代对象,不一定是迭代器
如果是一个迭代器,一定是可迭代对象
"""
setvar = {"a","b","c","d"}
# 1.如何定义迭代器
it = iter(setvar)

# 2.如何判断迭代器
# __iter__ __next__
res = dir(it)
print(res)

res = "__iter__" in dir(it) and "__next__" in dir(it)
print(res)

# 3.如何调用迭代器
res = next(it)
print(res)
res = next(it)
print(res)
res = next(it)
print(res)
res = next(it)
print(res)
# next调用是单向不可逆的过程,如果超过了所有的数据个数,在调用会报错StopIteration
# res = next(it) error
# print(res)

# 4重置迭代器
it = iter(setvar)
print(next(it),"<======1=====>")

# 5.调用迭代器的其他方法
# for 
print("<============2===========>")
for i in it:	
	print(i)
print("<============2===========>")

# for + next
it = iter(setvar)
for i in range(3): # 只循环三次
	res = next(it) # 只调用三次
	print(res)

res = next(it)
print(res)
"""
res = next(it) error StopIteration (超过了能够调用的所有元素,停止迭代)
print(res)     error  
"""

# 6.其他判断迭代器或可迭代对象的方式
# 从 .. 引入 ..  Iterator 迭代器类型  Iterable 可迭代类型
from collections import Iterator,Iterable
res = isinstance(it,Iterator)
print(res)
res = isinstance(it,Iterable)
print(res)
# 如果该数据类型一个条件都不满足,返回False
res = isinstance(1234,(Iterable,Iterator))
print(res)
"""
# 判断该数据是不是这个类型的,如果是返回True , 如果不是,返回False
(1)isinstance(数据,类型)
# 如果该数据的类型在这个元组当中,返回True,如果一个都没有,返回False
(2)isinstance(数据,(类型1,类型2...))
"""

# 7 练习
# 把range对象变成迭代器
it = iter(range(5,25))
# for + next 通过迭代器获取数据
for i in range(10):
	res = next(it)
	print(res)

```

### 📖 要点讲解

- ### 迭代器 : 能被next调用,并不断返回下一个值的对象 (迭代器是对象)

- 判断是否是可迭代对象 , 依赖__iter__成员

- next调用是单向不可逆的过程,如果超过了所有的数据个数,在调用会报错StopIteration

- 从 .. 引入 ..  Iterator 迭代器类型  Iterable 可迭代类型

- 如果该数据类型一个条件都不满足,返回False

- 判断该数据是不是这个类型的,如果是返回True , 如果不是,返回False

- 如果该数据的类型在这个元组当中,返回True,如果一个都没有,返回False

---

## 4. 2.map.py

### 📋 运行结果

```

[1, 2, 3, 4]
1
2
3
4
1
2
1
[1, 2, 3, 4]
[3, 6, 9, 12]
[3, 6, 9, 12] >+++?
97 a
98 b
99 c
{'a': 97, 'b': 98, 'c': 99}
[97, 98, 99]
[97, 98, 99]

```

### 💻 完整代码

```python

# ### 高阶函数 : 能够把函数当成参数传递的就是高阶函数 (map , reduce, sorted ,filter)

# map
"""
map(func,iterable)
功能:
	处理数据
	把iterable中的数据一个一个拿出来,扔到func当中做处理,通过迭代器的调用获取返回的数据
参数:
	func 自定义或者内置函数
	iterable 可迭代性数据 (range对象,迭代器,容器类型数据)
返回值:
	迭代器
"""
# 例子1
lst = ["1","2","3","4"]  # => [1,2,3,4]

# 普通写法
lst_new = []
for i in lst:
	lst_new.append(int(i))
print(lst_new)

# map改写
# 调用迭代器方式1 for
it = map(int,lst)
for i in it:
	print(i)

# 调用迭代器方式2 for + next (推荐)
it = map(int,lst)
for i in range(2):
	print(next(it))

# 调用迭代器方式3 next 
it = map(int,lst)
res = next(it)
print(res)

# 调用迭代器方式4 list强转成列表
it = map(int,lst)
lst = list(it)
print(lst)

"""
代码解析:
第一次调用迭代器时,把字符串"1" 放到int当中做处理,处理后的结果是整型1,通过迭代器的调用返回
第二次调用迭代器时,把字符串"2" 放到int当中做处理,处理后的结果是整型2,通过迭代器的调用返回
第三次调用迭代器时,把字符串"3" 放到int当中做处理,处理后的结果是整型3,通过迭代器的调用返回
第四次调用迭代器时,把字符串"4" 放到int当中做处理,处理后的结果是整型4,通过迭代器的调用返回
到此程序结束
"""
# 例子2
lst = [1,2,3,4] #=> [3,6,9,12]
lst_new =[]
for i in lst:
	lst_new.append(i * 3)
print(lst_new)

def func(n):
	return n * 3
it = map(func,lst)
it = map(lambda n : n*3 , lst)
"""
print(next(it)) # 3
print(next(it)) # 6 
print(next(it)) # 9
print(next(it)) # 12
"""
print(list(it),">+++?")

# 例子3
 # 当给与参数为["a","b","c"] =>[97,98,99]
dic = {97:"a",98:"b",99:"c"}
# 1.翻转字典
dic_new = {}
for k,v in dic.items():
	print(k,v)
	dic_new[v] = k

print(dic_new) # {'a': 97, 'b': 98, 'c': 99}

# 2.通过键找对应的ascii码
lst = ["a","b","c"]
lst_new = []
for i in lst:
	# print(dic_new[i])
	lst_new.append(dic_new[i])
print(lst_new)

# 使用map进行改写
def func(n):
	dic_new = {}
	for k,v in dic.items():
		dic_new[v] = k
	return  dic_new[n]

lst = ["a","b","c"]
it = map(func,lst)
"""
print(next(it)) # 97
print(next(it)) # 98 
print(next(it)) # 99
"""
lst = list(it)
print(lst)

"""
总结: 使用map的时候,在自定义函数时,别忘加形参和return 返回值,以供迭代器的调取;
"""

```

### 📖 要点讲解

- ### 高阶函数 : 能够把函数当成参数传递的就是高阶函数 (map , reduce, sorted ,filter)

- 调用迭代器方式2 for + next (推荐)

- 当给与参数为["a","b","c"] =>[97,98,99]

---

## 5. 3.filter.py

### 📋 运行结果

```

[2, 4, 6, 8, 100]
[2, 4, 6, 8, 100]
[2, 4, 6, 8, 100]

```

### 💻 完整代码

```python

# ### filter 
"""
filter(func,iterable)
功能:
	过滤数据
	在自定义函数中,如果返回True  , 代表这个数保留
	在自定义函数中,如果返回False , 代表这个数舍弃
参数:
	func : 自定义函数
	iterable:(容器类型数据,range对象,迭代器)
返回值:
	迭代器
"""
# 获取所有的偶数
lst = [1,2,3,4,5,6,7,8,9,100]
lst_new = []
for i in lst:
	if i % 2 == 0:
		lst_new.append(i)

print(lst_new)

# 通过filter改写
lst = [1,2,3,4,5,6,7,8,9,100]
def func(n):	
	if n % 2 == 0:
		return True
	else:
		return False
		
it = filter(func,lst)
"""
print(next(it))
print(next(it))
print(next(it))
print(next(it))
print(next(it))
"""
print(list(it))

# lambda 表达式

it = filter(lambda n : True if n % 2 == 0 else False,lst)
print(list(it))

```

---

## 6. 4.reduce.py

### 📋 运行结果

```

4399
43
4399
4399
555555555565555555555655555555556555555555565555555555655555555556555555555565555555555655555555556555555555567
567 <class 'int'>

```

### 💻 完整代码

```python

# ### reduce
"""
reduce(func,iterable)
功能:
	计算数据
	把iterable中的两个值拿出来,扔到func当中做处理,把计算的结果在和iterable的第三个元素
	扔到func当中做处理,依次类推,直到算完所有数据.
参数:
	func: 自定义函数
	iterable : 可迭代性数据(range对象 , 迭代器, 容器类型数据)
返回值:
	计算最后的结果
"""
lst = [4,3,9,9] # 4399

# 方法一
strvar = ""
for i in lst:	
	strvar += str(i)
print(int(strvar))

# 方法二
it = iter(lst)
num1 = next(it) # 第一次调用迭代器 获取数据4
num2 = next(it) # 第二次调用迭代器 获取数据3

num = num1 * 10 + num2
print(num) # 43

# 再把43 和另外一个9 做运算是439 ... 以此类推 ... 
for i in it:
	num = num * 10 + i
print(num)

# 改写reduce
from functools import reduce
lst = [4,3,9,9]

def func(x,y):	
	return x * 10 + y
res = reduce(func,lst)
print(res)
"""
代码解析:
第一次的结果
首先从lst当中拿出两个元素,一个是4,一个是3,扔到func当中做运算
x=4 , y =3  return 4*10+3 => return 43

第二次的结果
是拿43和lst中的第三个元素9, 扔到func当中做运算
x=43,y=9 return 43 * 10 + 9 => return 439

第三次的结果
是拿439和lst中的第四个元素9, 扔到func当中做运算
x = 439,y = 9 return 439 * 10 + 9 => return 4399

到此,列表中的所有元素计算完毕,返回4399,程序终止;
"""

# "567"  => 567 不能使用int
strvar = "567"
def func(x,y):	
	return x * 10 + y
res = reduce(func,list(strvar)) # ["5","6","7"]
print(res)

def func2(n):
	dic = {"0":0,"1":1,"2":2,"3":3,"4":4,"5":5,"6":6,"7":7,"8":8,"9":9}
	return dic[n]
# print(func2("5"))
# print(func2("6"))
# print(func2("7"))

it = map(func2,"567")
# res = reduce(func,list(it))
res = reduce(func,it)
print(res,type(res))

```

### 📖 要点讲解

- 再把43 和另外一个9 做运算是439 ... 以此类推 ...

- "567"  => 567 不能使用int

- res = reduce(func,list(it))

---

## 7. 5.sorted.py

### 📋 运行结果

```

[-100, -2, 2, 3, 13, 23, 23, 54]
[54, 23, 23, 13, 3, 2, -2, -100]
['a', 'b', 'c', 'i', 'o', 'u']
[-100, 10, 20, 30]
[-100, 10, 20, 30]
['a', 'b', 'c']
1000
[10, 20, 30, -100]
[21, 52, 63, 34, 17]

```

### 💻 完整代码

```python

# ### sorted 
"""
sorted(iterable,reverse=False,key=函数)
功能: 对数据排序
参数:
	iterable : 可迭代对象(迭代器,range对象,容器类型数据)
	reverse  : reverse= False 默认从小到大排序  reverse= True 从大到小排序
	key      : 自定义函数 或者 内置函数
返回值:
	排序后的结果
"""

# 一.默认从小到大排序
lst= [13,54,23,23,2,3,-100,-2]
res = sorted(lst)
print(res)

# 从大到小排序
res = sorted(lst,reverse=True)
print(res)

# 排序时,可以排序多种容器类型数据
# 字符串排序 (按照ascii编码排序)
strvar = "uioabc"
res = sorted(strvar)
print(res)

# 元组排序
tup = (10,20,30,-100)
res = sorted(tup)
print(res)

# 集合排序
setvar = {10,20,30,-100}
res = sorted(setvar)
print(res)

# 字典排序
dic = {"c":3,"a":1,"b":2}
res = sorted(dic)
print(res) # ['a', 'b', 'c']

# 二.可以按照指定函数进行排序
print(abs(-1000)) # 1000
# 1.按照绝对值排序
lst = [10,20,30,-100]
lst = sorted(lst,key=abs)
print(lst) # [10, 20, 30, -100]
"""
10 -> abs(10) => 10
20 -> abs(20) => 20
30 -> abs(30) => 30
-100 -> abs(-100) => 100
[10,20,30,-100]
"""

# 2.按照自定义函数排序
lst = [17,21,34,52,63]
# 按照余数排序
def func(n):
	return n % 10
lst = sorted(lst,key=func)
print(lst) # [21, 52, 63, 34, 17]
"""
21 func(21) => 1
52 func(21) => 2
63 func(63) => 3
34 func(21) => 4
17 func(17) => 7
21 52 63 24 17
"""

"""
sort 和 sorted 区别
# 一.数据类型
	(1) sort   只能对列表进行排序
	(2) sorted 可以对所有容器类型数据排序
# 二.返回值
	(1) sort 是基于原有的列表进行排序
	(2) sorted 是直接返回新的列表.
"""

```

---

## 8. 6.推导式.py

### 📋 运行结果

```

[1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48, 49, 50, 51, 52, 53, 54, 55, 56, 57, 58, 59, 60, 61, 62, 63, 64, 65, 66, 67, 68, 69, 70, 71, 72, 73, 74, 75, 76, 77, 78, 79, 80, 81, 82, 83, 84, 85, 86, 87, 88, 89, 90, 91, 92, 93, 94, 95, 96, 97, 98, 99, 100, 101, 102, 103, 104, 105, 106, 107, 108, 109, 110, 111, 112, 113, 114, 115, 116, 117, 118, 119, 120, 121, 122, 123, 124, 125, 126, 127, 128, 129, 130, 131, 132, 133, 134, 135, 136, 137, 138, 139, 140, 141, 142, 143, 144, 145, 146, 147, 148, 149, 150, 151, 152, 153, 154, 155, 156, 157, 158, 159, 160, 161, 162, 163, 164, 165, 166, 167, 168, 169, 170, 171, 172, 173, 174, 175, 176, 177, 178, 179, 180, 181, 182, 183, 184, 185, 186, 187, 188, 189, 190, 191, 192, 193, 194, 195, 196, 197, 198, 199, 200, 201, 202, 203, 204, 205, 206, 207, 208, 209, 210, 211, 212, 213, 214, 215, 216, 217, 218, 219, 220, 221, 222, 223, 224, 225, 226, 227, 228, 229, 230, 231, 232, 233, 234, 235, 236, 237, 238, 239, 240, 241, 242, 243, 244, 245, 246, 247, 248, 249, 250, 251, 252, 253, 254, 255, 256, 257, 258, 259, 260, 261, 262, 263, 264, 265, 266, 267, 268, 269, 270, 271, 272, 273, 274, 275, 276, 277, 278, 279, 280, 281, 282, 283, 284, 285, 286, 287, 288, 289, 290, 291, 292, 293, 294, 295, 296, 297, 298, 299, 300, 301, 302, 303, 304, 305, 306, 307, 308, 309, 310, 311, 312, 313, 314, 315, 316, 317, 318, 319, 320, 321, 322, 323, 324, 325, 326, 327, 328, 329, 330, 331, 332, 333, 334, 335, 336, 337, 338, 339, 340, 341, 342, 343, 344, 345, 346, 347, 348, 349, 350, 351, 352, 353, 354, 355, 356, 357, 358, 359, 360, 361, 362, 363, 364, 365, 366, 367, 368, 369, 370, 371, 372, 373, 374, 375, 376, 377, 378, 379, 380, 381, 382, 383, 384, 385, 386, 387, 388, 389, 390, 391, 392, 393, 394, 395, 396, 397, 398, 399, 400, 401, 402, 403, 404, 405, 406, 407, 408, 409, 410, 411, 412, 413, 414, 415, 416, 417, 418, 419, 420, 421, 422, 423, 424, 425, 426, 427, 428, 429, 430, 431, 432, 433, 434, 435, 436, 437, 438, 439, 440, 441, 442, 443, 444, 445, 446, 447, 448, 449, 450, 451, 452, 453, 454, 455, 456, 457, 458, 459, 460, 461, 462, 463, 464, 465, 466, 467, 468, 469, 470, 471, 472, 473, 474, 475, 476, 477, 478, 479, 480, 481, 482, 483, 484, 485, 486, 487, 488, 489, 490, 491, 492, 493, 494, 495, 496, 497, 498, 499, 500, 501, 502, 503, 504, 505, 506, 507, 508, 509, 510, 511, 512, 513, 514, 515, 516, 517, 518, 519, 520, 521, 522, 523, 524, 525, 526, 527, 528, 529, 530, 531, 532, 533, 534, 535, 536, 537, 538, 539, 540, 541, 542, 543, 544, 545, 546, 547, 548, 549, 550, 551, 552, 553, 554, 555, 556, 557, 558, 559, 560, 561, 562, 563, 564, 565, 566, 567, 568, 569, 570, 571, 572, 573, 574, 575, 576, 577, 578, 579, 580, 581, 582, 583, 584, 585, 586, 587, 588, 589, 590, 591, 592, 593, 594, 595, 596, 597, 598, 599, 600, 601, 602, 603, 604, 605, 606, 607, 608, 609, 610, 611, 612, 613, 614, 615, 616, 617, 618, 619, 620, 621, 62

```

### 💻 完整代码

```python

# ### 推导式 : 通过一行循环判断,遍历出一系列数据的方式是推导式
"""
推导式种类
    [val for val in Iterable]  列表推导式
    {val for val in Iterable}  集合推导式
    {a:b for a,b in iterable}  字典推导式
"""

# 创建一个列表,列表中1~5000这么多的数据
lst = []
for i in range(1,5001):
	lst.append(i)
print(lst)

# 1.推导式的基本使用
lst = [i for i in range(1,5001)]
print(lst)

# 2.具有判断条件的单循环推导式
"""判断条件只能是单项分支跟在for循环的后面"""
lst = [1,3,4,5,6,7,8,9]
lst_new = []
for i in lst:
	if i % 2 == 1:
		lst_new.append(i)
print(lst_new)

# 改写
lst = [i for i in lst if i % 2 == 1]
print(lst) # [1, 3, 5, 7, 9]

# 3.双循环的推导式
lst1 = ["张俊文","黄金生","冯双喜"]
lst2 = ["刘崇祥","苏叶青","吕文康"]
# "谁"+枪毙了+"谁"
lst = []
for i in lst1:
	for j in lst2:
		lst.append(i +"枪毙了" + j)
print(lst)

# 改写
lst = [i +"枪毙了" + j for i in lst1 for j in lst2]
print(lst)

# 4.带有判断条件的双循环推导式
lst1 = ["张俊文","黄金生","冯双喜"]
lst2 = ["刘崇祥","苏叶青","吕文康"]
lst = []
for i in lst2:
	for j in lst1:
		if lst2.index(i) == lst1.index(j):	
			lst.append(i + "枪毙了" + j)
print(lst)

# 改写
lst = [i + "枪毙了" + j for i in lst2 for j in lst1 if lst2.index(i) == lst1.index(j)]
print(lst)

```

### 📖 要点讲解

- ### 推导式 : 通过一行循环判断,遍历出一系列数据的方式是推导式

- 创建一个列表,列表中1~5000这么多的数据

---

## 9. 7.集合字典推导式.py

### 📋 运行结果

```

[{'name': '谢岳恒', 'money': 1900, 'age': 19}, {'name': '黄启新', 'money': 1000000, 'age': 50}, {'name': '黄金生', 'money': 5500, 'age': 18}, {'name': '李辉', 'money': 0, 'age': 73}]
{'抠脚大汉卡老谢', '抠脚大汉卡老李', '尊贵VIP卡老黄', '抠脚大汉卡老黄'}
{'抠脚大汉卡老谢', '抠脚大汉卡老李', '尊贵VIP卡老黄', '抠脚大汉卡老黄'}

```

### 💻 完整代码

```python

# ### 集合推导式 
"""
案例:
	满足年龄在18到21,存款大于等于5000 小于等于5500的人,
	开卡格式为:尊贵VIP卡老x(姓氏),否则开卡格式为:抠脚大汉卡老x(姓氏)	
	把开卡的种类统计出来
"""
lst = [
	{"name":"谢岳恒" , "money":1900 , "age":19},
	{"name":"黄启新" , "money":1000000 , "age":50},
	{"name":"黄金生" , "money":5500 , "age":18},
	{"name":"李辉" , "money":0,"age":73}
]

setvar = set()
print(lst)
for i in lst:
	if 18<= i["age"]<=21 and 5000 <= i["money"] <= 5500:
		setvar.add("尊贵VIP卡老{}".format(i["name"][0]))
	else:
		setvar.add("抠脚大汉卡老{}".format(i["name"][0]))
		
print(setvar)
#  三运运算符 + for循环推导式
setvar = {"尊贵VIP卡老{}".format(i["name"][0]) if 18<= i["age"]<=21 and 5000 <= i["money"] <= 5500 else "抠脚大汉卡老{}".format(i["name"][0]) for i in lst}
print(setvar)

# ### 字典推导式
### (1)enumerate
"""
enumerate(iterable,[start=0])
功能:枚举 ; 将索引号和iterable中的值,一个一个拿出来配对组成元组放入迭代器中
参数:
    iterable: 可迭代性数据 (常用:迭代器,容器类型数据,可迭代对象range) 
    start:  可以选择开始的索引号(默认从0开始索引)
返回值:迭代器
"""
lst = ["苏叶青","吕文康","微微"]
it = enumerate(lst)
from collections import Iterator,Iterable
res = isinstance(it,Iterator)
print(res)

# 调用迭代器方式一
"""
res = next(it)
print(res)
res = next(it)
print(res)
res = next(it)
print(res)
"""
# 调用迭代器方式二
"""
for i in it:
	print(i)
"""

# 调用迭代器方式三
"""
for i in range(1):
	res = next(it)
	print(res)
"""
# 调用迭代器方式四
lst = list(it)
print(lst)

# enumerate 可以指定默认的开始值
lst = ["苏叶青","吕文康","微微"]
it = enumerate(lst,start = 1)
print(list(it)) # [(1, '苏叶青'), (2, '吕文康'), (3, '微微')]

# enumerate 配合推导式使用
print("<=============>")
dic = {k:v for k,v in enumerate(lst,start=1)}
print(dic)

# enumerate 配合 dict强转成字典
dic = dict(enumerate(lst))
print(dic)

### (2)zip
"""
zip(iterable, ... ...)
    功能: 将多个iterable中的值,一个一个拿出来配对组成元组放入迭代器中
    iterable: 可迭代性数据 (常用:迭代器,容器类型数据,可迭代对象range) 
返回: 迭代器

会把具有相同索引下标的数据凑到一个元组当中
如果缺少某个元素,将不能配对.改组会被舍弃.

"""
lst1 = ["张俊文","刘硬","冯双喜"]
lst2 = ["赵强","吕文康","刘崇祥"]
it = zip(lst1,lst2)
lst = list(it)
print(lst) # [('张俊文', '赵强'), ('刘硬', '吕文康'), ('冯双喜', '刘崇祥')]

lst1 = ["张俊文","刘硬","冯双喜"]
lst2 = ["赵强","吕文康","刘崇祥"]
lst3 = ["黄金生","李辉","郑飞"]
it = zip(lst1,lst2,lst3)
print(list(it)) # [('张俊文', '赵强', '黄金生'), ('刘硬', '吕文康', '李辉'), ('冯双喜', '刘崇祥', '郑飞')]

lst1 = ["张俊文","刘硬","冯双喜"]
lst2 = ["赵强","吕文康","刘崇祥"]
lst3 = ["黄金生"]
it = zip(lst1,lst2,lst3)
print(list(it)) # [('张俊文', '赵强', '黄金生')]

# zip 配合推导式使用
dic = {k:v for k,v in zip(lst1,lst2)}
print(dic)

# zip 配合 dict强转成字典
dic = dict(zip(lst1,lst2))
print(dic)

lst = [(False,5),(False,9),(False,7),(False,8),(True,4),(True,6),(True,1),(True,7)]

print(sorted(lst))

```

### 📖 要点讲解

- enumerate 配合 dict强转成字典

---

## 10. 8.生成器表达式.py

### 📋 运行结果

```

<generator object <genexpr> at 0x7bd9e6d31900>

```

### 💻 完整代码

```python

# ### 生成器表达式
"""
#元组推导式的返回值是一个生成器对象,简称生成器,生成器本质就是迭代器.
#生成器可以用两种方式创建:
    (1)生成器表达式  (里面是推导式,外面用圆括号)
    (2)生成器函数    (用def定义,里面含有yield)
"""

# 1.定义一个生成器表达式
gen = (i for i in range(1,10))
# gen = [i for i in range(1,10)]
print(gen)

# 2.判断生成器类型
from collections import Iterator,Iterable
res = isinstance(gen,Iterator)
print(res)

# 3.如何调用生成器
# next 
res = next(gen)
print(res)
res = next(gen)
print(res)
# for
"""
for i in gen:
	print(i)
"""
# for + next
print("<================>")
for i in range(3):
	res = next(gen)
	print(res)

# list直接强转成列表,拿去所有数据
print("<================>")
res = list(gen)
print(res)

```

### 📖 要点讲解

- 元组推导式的返回值是一个生成器对象,简称生成器,生成器本质就是迭代器.

- gen = [i for i in range(1,10)]

---

## 11. 9.生成器函数.py

### 📋 运行结果

```

start ...
1
2
3
我的球衣号码是1号
我的球衣号码是2号
我的球衣号码是3号
我的球衣号码是4号
我的球衣号码是5号
我的球衣号码是6号
我的球衣号码是7号
我的球衣号码是8号
我的球衣号码是9号
我的球衣号码是10号
我的球衣号码是11号
我的球衣号码是12号
我的球衣号码是13号
我的球衣号码是14号
我的球衣号码是15号
我的球衣号码是16号
我的球衣号码是17号
我的球衣号码是18号
我的球衣号码是19号
我的球衣号码是20号
我的球衣号码是21号
我的球衣号码是22号
我的球衣号码是23号
我的球衣号码是24号
我的球衣号码是25号
我的球衣号码是26号
我的球衣号码是27号
我的球衣号码是28号
我的球衣号码是29号
我的球衣号码是30号
<=============>
我的球衣号码是31号
我的球衣号码是32号
我的球衣号码是33号
我的球衣号码是34号
我的球衣号码是35号
我的球衣号码是36号
我的球衣号码是37号
我的球衣号码是38号
我的球衣号码是39号
我的球衣号码是40号
我的球衣号码是41号
我的球衣号码是42号
我的球衣号码是43号
我的球衣号码是44号
我的球衣号码是45号
我的球衣号码是46号
我的球衣号码是47号
我的球衣号码是48号
我的球衣号码是49号
我的球衣号码是50号
我的球衣号码是51号
我的球衣号码是52号
我的球衣号码是53号
我的球衣号码是54号
我的球衣号码是55号
我的球衣号码是56号
我的球衣号码是57号
我的球衣号码是58号
我的球衣号码是59号
我的球衣号码是60号
我的球衣号码是61号
我的球衣号码是62号
我的球衣号码是63号
我的球衣号码是64号
我的球衣号码是65号
我的球衣号码是66号
我的球衣号码是67号
我的球衣号码是68号
我的球衣号码是69号
我的球衣号码是70号
我的球衣号码是71号
我的球衣号码是72号
我的球衣号码是73号
我的球衣号码是74号
我的球衣号码是75号
我的球衣号码是76号
我的球衣号码是77号
我的球衣号码是78号
我的球衣号码是79号
我的球衣号码是80号
<=============>
我的球衣号码是81号
我的球衣号码是82号
我的球衣号码是83号
我的球衣号码是84号
我的球衣号码是85号
我的球衣号码是86号
我的球衣号码是87号
我的球衣号码是88号
我的球衣号码是89号
我的球衣号码是90号
<=============>
staring ..
one 外部打印
111 内部打印1
two 外部打印
222 内部打印2
three 外部打印
>=====?
1
2
3
4
>=====?
1
1
2
3
5

```

### 💻 完整代码

```python

# ### 生成器函数
"""
# yield 类似于 return
共同点在于:执行到这句话都会把值返回出去
不同点在于:yield每次返回时,会记住上次离开时执行的位置 , 下次在调用生成器 , 会从上次执行的位置往下走
		   而return直接终止函数,每次重头调用.
yield 6 和 yield(6) 2种写法都可以 yield 6 更像 return 6 的写法 推荐使用
"""

# 1.生成器基本语法
def mygen():
	print("start ...")
	yield 1
	
	yield 2
	
	yield 3
	
	print("end ... ")

#  初始化生成器函数 , 返回生成器对象 -> 简称生成器
gen = mygen()

# 在调用生成器的时,才会执行生成器函数中的内容;
res = next(gen)
print(res)
res = next(gen)
print(res)
res = next(gen)
print(res)
# res = next(gen)
# print(res) error 没有更多的yield返回数据了,直接报错

"""
代码解析:
gen = mygen() 没有执行代码,支持单纯的创建了一个生成器
第一次调用
print("start ...") yield 1 保存当前代码执行状态第13行,将1返回 res = 1并且打印1,等待下一次调用
第二次调用
它会从上一次代码记录的状态13行往下走, yield 2 保存当前代码执行状态第15行,将2返回 res = 2 并且打印2,等待下一次调用
第三次调用
它会从上一次代码记录的状态15行往下走, yield 3 保存当前代码执行状态第15行,将3返回 res = 3 并且打印3,等待下一次调用

第四次调用
从17行往下走 print(end .. ) 但是没有更多的yield返回数据,所以直接报错,StopIteration
"""

# 2.优化语法
def mygen():
	for i in range(1,101):
		strvar = "我的球衣号码是{}号".format(i)
		yield strvar

# 初始化生成器函数 -> 生成器对象 (简称生成器)
gen = mygen()

for i in range(30):
	print(next(gen))

print("<=============>")
for i in range(50):
	print(next(gen))

print("<=============>")
for i in range(10):
	print(next(gen))

# 3.send的使用 : 既能取值,又能发送值,给上一个yield传值用的
"""
### send
# next和send区别:
	next 只能取值
	send 不但能取值,还能发送值
# send注意点:
	第一个 send 不能给 yield 传值 默认只能写None
	最后一个yield 接受不到send的发送值
"""
print("<=============>")
def mygen():
	print("staring ..")
	res = yield "one"
	print(res,"内部打印1")
	
	res = yield "two"
	print(res,"内部打印2")

	res = yield "three"
	print(res,"内部打印3")

	print("ending .. ")

# 初始化生成器函数 => 生成器对象 -> 简称生成器
gen = mygen()
# 第一次发送时,还没有遇到上一个yield,所以默认传递None(语法要求)
res = gen.send(None)
print(res,"外部打印")

# 第二次发送时,可以遇到yield
res = gen.send(111)
print(res,"外部打印")

# 第三次发送时,可以遇到yield
res = gen.send(222)
print(res,"外部打印")
"""
error
res = gen.send(333)
print(res,"外部打印")
"""

"""
第一次发送时,因为还没有遇到yield,所以只能发送None
生成器函数开始执行,print("staring ..") , res = yield "one"  保存代码当前状态82行,将"one"返回
res = "one" print("one","外部打印")

第二次发送时,gen.send(111),把111发送给了上一个yield接收 res = 111 print(111,"内部打印1")
然后执行84行 res = yield "two",保存当前代码执行状态第84行,将"two"返回给send发送处
res = "two" print("two","外部打印")

第三次发送时,gen.send(222),把222发送给了上一个yield接收 res = 222 print(222,"内部打印2")
然后执行87行 res = yield "three",保存当前代码执行状态第87行,将"three"返回给send发送处
res = "three" print("three","外部打印")

第四次发送时,print(333,"内部打印3") print("ending .. ") 
因为没有更多的yield返回数据了,所有直接报错 StopIteration .

"""

# 4.yield from : 将一个可迭代对象变成一个迭代器返回	
print(">=====?")
def mygen():
	# yield [1,2,3,4]
	yield from [1,2,3,4]

gen = mygen()
res = next(gen)
print(res)
res = next(gen)
print(res)
res = next(gen)
print(res)
res = next(gen)
print(res)

# 5.斐波那契数列
print(">=====?")
"""1 1 2 3 5 8 13 21 34 55 ... """
def fib(maxlen):
	a,b = 0,1
	i = 0
	while i < 5:
		yield b
		a,b = b,a+b
		i+=1
	
gen = fib(5)
for i in gen:
	print(i)
"""
内层while循环来说:
第一次循环
print(1)
a,b = b,a+b  
# a = 1,b = 1

第二次循环
print(1)
a,b = b,a+b  
a = 1, b=2

第三次循环
print(2)
a是上上个值  b是上一个值
a,b=b,a+b
a=2,b=3
"""

```

### 📖 要点讲解

- 初始化生成器函数 , 返回生成器对象 -> 简称生成器

- 在调用生成器的时,才会执行生成器函数中的内容;

- print(res) error 没有更多的yield返回数据了,直接报错

- 初始化生成器函数 -> 生成器对象 (简称生成器)

- 3.send的使用 : 既能取值,又能发送值,给上一个yield传值用的

- 初始化生成器函数 => 生成器对象 -> 简称生成器

- 第一次发送时,还没有遇到上一个yield,所以默认传递None(语法要求)

- 4.yield from : 将一个可迭代对象变成一个迭代器返回

---

## 12. 10.python的内置方法.py

### 📋 运行结果

```

103.3
4
15
15
423
-190
[-190, 12, 19, 78, 423]
423 -190
('黄启新', 50)
('张俊文', 18)
8
3
0
1
2
3
4
5
6
3
8
13
10
9
8
7
6
5
4
3
2
1
0b11111111
0o10
0x10
a
97
456 <class 'int'>
1122233
None
100
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
E:
ython5周末班	ay5
'E:\nython5周末班\tay5'
8400982992415445036 8400982992415445036
False

```

### 💻 完整代码

```python

# ### python的内置方法

# abs 绝对值函数
res = abs(-1)
res = abs(103.3)
print(res)

# round 四舍五入 (奇进偶不进 发生在n.5的情况下 n为偶数则舍去 n.5 n为奇数，则进一)
res = round(3.69)
res = round(3.5)
res = round(4.68)
res = round(4.51)
res = round(4.5)
print(res)

# sum    计算一个序列得和
lst = [1,2,3,4,5]
res = sum(lst)
print(res)

total = 0
for i in lst:
	total += i
print(total)

# max    获取一个序列里边的最大值
lst = [-190,19,78,423,12]
res = max(lst)
print(res)
# min    获取一个序列里边的最小值
lst = [-190,19,78,423,12]
res = min(lst)
print(res)

lst = sorted(lst)
print(lst)
maxval = lst[-1]
minval = lst[0]
print(maxval,minval)

# 自定义规则,找最大值和最小值(按照返回的数据,重新对传入的数据进行排序.找最大和最小的哪个)
lst = [("张俊文",18),("黄金生",19),("黄启新",50)]
def func(n):
	# print(n)
	return n[-1]
res = max(lst,key=func)
print(res)

res = min(lst,key=func)
print(res)

# pow    计算某个数值的x次方
res = pow(2,3)
print(res)
# 先把2的3次幂算完,在和5取余
res = pow(2,3,5)
print(res)

# range  产生指定范围数据的可迭代对象
# 一个参数
for i in range(3):
	print(i) # 0 1 2 
# 二个参数
for i in range(3,7): # 3 4 5 6 
	print(i)
# 三个参数
for i in range(3,14,5): # 3 8 13
	print(i)
	
# for 逆向取值
for i in range(10,0,-1): # 10 9 8 7 6 5 4 3 2 1
	print(i)

# bin    将10进制数据转化为二进制
res = bin(255)
print(res)

# oct    将10进制数据转化为八进制
res = oct(8)
print(res)

# hex    将10进制数据转化为16进制
res = hex(16)
print(res)

# chr    将ASCII编码转换为字符
res = chr(97)
print(res)

# ord    将字符转换为ASCII编码
res = ord("a")
print(res)

# eval   将字符串当作python代码执行
res = eval("456")
print(res , type(res))
res = eval("print(1122233)")
print(res)

'''eval("a = 100") # 不能够动态创建变量的,exec可以'''

# exec   将字符串当作python代码执行(功能更强大)
exec("a = 100")
print(a)
strvar = """
for i in range(10):
	print(i)
"""
exec(strvar)

'''# exec 和 eval 在和用户交互数据的时候,慎用,以防系统出现意外;'''

# repr   不转义字符输出字符串
pathvar = "E:\nython5周末班\tay5"
print(pathvar)
res = repr(pathvar)
print(res)

# input  接受输入字符串
"""
res = input("请输入你是否结过婚:")
print(res)
"""
# hash   生成哈希值
"""
相同的两个值,无论哈希多少次,都会差生相同的数据
1.文件校验
2.密码加密
"""
res1 = hash("abcde")
res2 = hash("abcde")
print(res1,res2)

with open("day7.rar",mode="rb") as fp:
	res1 = hash(fp.read())

with open("day6.rar",mode="rb") as fp:
	res2 = hash(fp.read())
print(res1 == res2)

```

### 📖 要点讲解

- round 四舍五入 (奇进偶不进 发生在n.5的情况下 n为偶数则舍去 n.5 n为奇数，则进一)

- 自定义规则,找最大值和最小值(按照返回的数据,重新对传入的数据进行排序.找最大和最小的哪个)

- range  产生指定范围数据的可迭代对象

- hex    将10进制数据转化为16进制

- eval   将字符串当作python代码执行

- exec   将字符串当作python代码执行(功能更强大)

---

## 🖼️ 参考资料

![1注册.png](./assets/1注册.png)

![2注册.png](./assets/2注册.png)

![1.png](./assets/1.png)

![2.png](./assets/2.png)
