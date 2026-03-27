# Day 4: day04 文件相关函数 函数的概念 函数的参数 函数的收集参数 命名关键字参数 返回值函数名全局局部变量 nonlocal 闭包函数 匿名递归函数

> 对应原课程：day04_文件相关函数_函数的概念_函数的参数_函数的收集参数_命名关键字参数_返回值函数名全局局部变量_nonlocal_闭包函数_匿名递归函数

---

## 1. 1.文件相关函数.py

### 📋 运行结果

```

True
================
abcdefgccc

			cxvxcv

		234                 

					23421341
================
['abcdefgccc\n', '\t\t\tcxvxcv\n', '\t\t234                 \n', '\t\t\t\t\t23421341']
['abcdefgccc', 'cxvxcv', '234', '23421341']

```

### 💻 完整代码

```python

# ### 刷新缓冲区 flush
    # 当文件关闭的时候自动刷新缓冲区
    # 当整个程序运行结束的时候自动刷新缓冲区
    # 当缓冲区写满了  会自动刷新缓冲区
    # 手动刷新缓冲区
"""
fp = open("ceshi1.txt",mode="a+",encoding="utf-8")
fp.write("ccc")
# 瞬间刷新缓冲区,把数据写入到文件
fp.flush()
while True:
	pass

fp.close()
"""
# ### 文件的相关函数
fp = open("ceshi1.txt",mode="r+",encoding="utf-8")
#readable()	    功能: 判断文件对象是否可读
res = fp.readable()
#writable()	    功能: 判断文件对象是否可写
res = fp.writable()
print(res)

# 可以直接遍历文件对象,按照一行一行进行读取
print("================")
for i in fp:	
	print(i)

print("================")
#readline()     功能: 读取一行文件内容
with open("ceshi1.txt",mode="r+",encoding="utf-8") as fp:	
	# 方法一
	"""
	res = fp.readline()
	print(res)
	res = fp.readline()
	print(res)
	res = fp.readline()
	print(res)
	res = fp.readline()
	print(res)
	"""
	
	# 方法二
	"""
	# 先读一行
	res = fp.readline()
	# 判断是不是空,不是空就继续执行循环,直到''空字符串的时候,为假,循环终止
	while res:
		# 打印当前行数据
		print(res)
		# 在读一行
		res = fp.readline()
	"""
	
	# 注意点:
	"""
		readline(字符个数)
		如果 字符个数 > 当前行总字符个数 => 按照当前行内容读取
		如果 字符个数 < 当前行总字符个数 => 按照实际字符个数读取
	"""
	"""
	# res = fp.readline(5) # 5的单位是字符的个数
	res = fp.readline(5000) 
	print(res)
	"""
	
#readlines()    功能：将文件中的内容按照换行读取到列表当中
lst_new = []
with open("ceshi1.txt",mode="r+",encoding="utf-8") as fp:	
	lst = fp.readlines()
	print(lst) # ['abcdefgccc\n', 'cxvxcv\n', '234\n', '23421341']
	
	# 处理文件当中包含的空白符
	for i in lst:
		res = i.strip()
		lst_new.append(res)
print(lst_new)

#writelines()   功能：将内容是字符串的可迭代性数据写入文件中 参数:内容为字符串类型的可迭代数据
"""
lst = ['床前明月光\n', '疑是地上霜\n', '举头望明月\n', '低头漏裤裆\n']
# lst = [1,2,3,4] # write() argument must be str, not int
with open("ceshi2.txt",mode="w+",encoding="utf-8") as fp:	
	fp.writelines(lst)
"""

#truncate()     功能: 把要截取的字符串提取出来,然后清空内容将提取的字符串重新写入文件中 (字节)
with open("ceshi2.txt",mode="r+",encoding="utf-8") as fp:	
	fp.truncate(3) # 3的单位是字节

"""
seek(3)  字节
read(3)  在r模式下是字符 , 在rb模式下字节
readline同理
turncate(3) 字节
"""

```

### 📖 要点讲解

- readable()	    功能: 判断文件对象是否可读

- writable()	    功能: 判断文件对象是否可写

- 可以直接遍历文件对象,按照一行一行进行读取

- readline()     功能: 读取一行文件内容

- 判断是不是空,不是空就继续执行循环,直到''空字符串的时候,为假,循环终止

- res = fp.readline(5) # 5的单位是字符的个数

- readlines()    功能：将文件中的内容按照换行读取到列表当中

- writelines()   功能：将内容是字符串的可迭代性数据写入文件中 参数:内容为字符串类型的可迭代数据

- lst = [1,2,3,4] # write() argument must be str, not int

- truncate()     功能: 把要截取的字符串提取出来,然后清空内容将提取的字符串重新写入文件中 (字节)

---

## 2. 2.函数.py

### 📋 运行结果

```

这就是函数...
1*1= 1 
2*1= 2 2*2= 4 
3*1= 3 3*2= 6 3*3= 9 
4*1= 4 4*2= 8 4*3=12 4*4=16 
5*1= 5 5*2=10 5*3=15 5*4=20 5*5=25 
6*1= 6 6*2=12 6*3=18 6*4=24 6*5=30 6*6=36 
7*1= 7 7*2=14 7*3=21 7*4=28 7*5=35 7*6=42 7*7=49 
8*1= 8 8*2=16 8*3=24 8*4=32 8*5=40 8*6=48 8*7=56 8*8=64 
9*1= 9 9*2=18 9*3=27 9*4=36 9*5=45 9*6=54 9*7=63 9*8=72 9*9=81 
1*1= 1 
2*1= 2 2*2= 4 
3*1= 3 3*2= 6 3*3= 9 
4*1= 4 4*2= 8 4*3=12 4*4=16 
5*1= 5 5*2=10 5*3=15 5*4=20 5*5=25 
6*1= 6 6*2=12 6*3=18 6*4=24 6*5=30 6*6=36 
7*1= 7 7*2=14 7*3=21 7*4=28 7*5=35 7*6=42 7*7=49 
8*1= 8 8*2=16 8*3=24 8*4=32 8*5=40 8*6=48 8*7=56 8*8=64 
9*1= 9 9*2=18 9*3=27 9*4=36 9*5=45 9*6=54 9*7=63 9*8=72 9*9=81 
1*1= 1 
2*1= 2 2*2= 4 
3*1= 3 3*2= 6 3*3= 9 
4*1= 4 4*2= 8 4*3=12 4*4=16 
5*1= 5 5*2=10 5*3=15 5*4=20 5*5=25 
6*1= 6 6*2=12 6*3=18 6*4=24 6*5=30 6*6=36 
7*1= 7 7*2=14 7*3=21 7*4=28 7*5=35 7*6=42 7*7=49 
8*1= 8 8*2=16 8*3=24 8*4=32 8*5=40 8*6=48 8*7=56 8*8=64 
9*1= 9 9*2=18 9*3=27 9*4=36 9*5=45 9*6=54 9*7=63 9*8=72 9*9=81 
1*1= 1 
2*1= 2 2*2= 4 
3*1= 3 3*2= 6 3*3= 9 
4*1= 4 4*2= 8 4*3=12 4*4=16 
5*1= 5 5*2=10 5*3=15 5*4=20 5*5=25 
6*1= 6 6*2=12 6*3=18 6*4=24 6*5=30 6*6=36 
7*1= 7 7*2=14 7*3=21 7*4=28 7*5=35 7*6=42 7*7=49 
8*1= 8 8*2=16 8*3=24 8*4=32 8*5=40 8*6=48 8*7=56 8*8=64 
9*1= 9 9*2=18 9*3=27 9*4=36 9*5=45 9*6=54 9*7=63 9*8=72 9*9=81 
1*1= 1 
2*1= 2 2*2= 4 
3*1= 3 3*2= 6 3*3= 9 
4*1= 4 4*2= 8 4*3=12 4*4=16 
5*1= 5 5*2=10 5*3=15 5*4=20 5*5=25 
6*1= 6 6*2=12 6*3=18 6*4=24 6*5=30 6*6=36 
7*1= 7 7*2=14 7*3=21 7*4=28 7*5=35 7*6=42 7*7=49 
8*1= 8 8*2=16 8*3=24 8*4=32 8*5=40 8*6=48 8*7=56 8*8=64 
9*1= 9 9*2=18 9*3=27 9*4=36 9*5=45 9*6=54 9*7=63 9*8=72 9*9=81 
1*1= 1 
2*1= 2 2*2= 4 
3*1= 3 3*2= 6 3*3= 9 
4*1= 4 4*2= 8 4*3=12 4*4=16 
5*1= 5 5*2=10 5*3=15 5*4=20 5*5=25 
6*1= 6 6*2=12 6*3=18 6*4=24 6*5=30 6*6=36 
7*1= 7 7*2=14 7*3=21 7*4=28 7*5=35 7*6=42 7*7=49 
8*1= 8 8*2=16 8*3=24 8*4=32 8*5=40 8*6=48 8*7=56 8*8=64 
9*1= 9 9*2=18 9*3=27 9*4=36 9*5=45 9*6=54 9*7=63 9*8=72 9*9=81 
1*1= 1 
2*1= 2 2*2= 4 
3*1= 3 3*2= 6 3*3= 9 
4*1= 4 4*2= 8 4*3=12 4*4=16 
5*1= 5 5*2=10 5*3=15 5*4=20 5*5=25 
6*1= 6 6*2=12 6*3=18 6*4=24 6*5=30 6*6=36 
7*1= 7 7*2=14 7*3=21 7*4=28 7*5=35 7*6=42 7*7=49 
8*1= 8 8*2=16 8*3=24 8*4=32 8*5=40 8*6=48 8*7=56 8*8=64 
9*1= 9 9*2=18 9*3=27 9*4=36 9*5=45 9*6=54 9*7=63 9*8=72 9*9=81 
1*1= 1 
2*1= 2 2*2= 4 
3*1= 3 3*2= 6 3*3= 9 
4*1= 4 4*2= 8 4*3=12 4*4=16 
5*1= 5 5*2=10 5*3=15 5*4=20 5*5=25 
6*1= 6 6*2=12 6*3=18 6*4=24 6*5=30 6*6=36 
7*1= 7 7*2=14 7*3=21 7*4=28 7*5=35 7*6=42 7*7=49 
8*1= 8 8*2=16 8*3=24 8*4=32 8*5=40 8*6=48 8*7=56 8*8=64 
9*1= 9 9*2=18 9*3=27 9*4=36 9*5=45 9*6=54 9*7=63 9*8=72 9*9=81 
1*1= 1 
2*1= 2 2*2= 4 
3*1= 3 3*2= 6 3*3= 9 
4*1= 4 4*2= 8 4*3=12 4*4=16 
5*1= 5 5*2=10 5*3=15 5*4=20 5*5=25 
6*1= 6 6*2=12 6*3=18 6*4=24 6*5=30 6*6=36 
7*1= 7 7*2=14 7*3=21 7*4=28 7*5=35 7*6=42 7*7=49 
8*1= 8 8*2=16 8*3=24 8*4=32 8*5=40 8*6=48 8*7=56 8*8=64 
9*1= 9 9*2=18 9*3=27 9*4=36 9*5=45 9*6=54 9*7=63 9*8=72 9*9=81 
1*1= 1 
2*1= 2 2*2= 4 
3*1= 3 3*2= 6 3*3= 9 
4*1= 4 4*2= 8 4*3=12 4*4=16 
5

```

### 💻 完整代码

```python

# ### 函数 : 功能(包裹一部分代码 实现某一个功能 达成某一个目的)

# 1.函数的基本格式:
"""
# 定义函数
def 函数名():
	code1
	code2...
	
# 调用函数
函数名()	
"""

# 函数的定义
def func():
	print("这就是函数...")
	
# 函数的调用
func()

# 2.函数的命名
"""
字母数字下划线,首字符不能为数字
严格区分大小写,且不能使用关键字
函数命名有意义,且不能使用中文哦

驼峰命名法: 
	(1) 大驼峰命名法 :  每个单词的首字符大写
	mycar => MyCar  yourbigbrother => YourBigBrother  (面向对象 -> 类)
	(2) 小驼峰命名法 :  除了第一个单词的首字符小写,剩下每个单词的首字符大写
	mycar => myCar  yourbigbrother => yourBigBrother  (函数)
	
单词和单词之间用_隔开 (比较常用)
	my_car your_big_brother
"""

# 定义函数
def cheng_fa_biao_99():
	for i in range(1,10):
		for j in range(1,i+1):
			print("%d*%d=%2d " % (i,j,i*j) ,end="")
		print()

# 调用函数
for i in range(10):
	cheng_fa_biao_99()

# 函数的特点:
# 可以反复调用,提高代码的复用性,提高开发效率,便于维护管理

```

### 📖 要点讲解

- ### 函数 : 功能(包裹一部分代码 实现某一个功能 达成某一个目的)

- 可以反复调用,提高代码的复用性,提高开发效率,便于维护管理

---

## 3. 3.函数的参数.py

### 📋 运行结果

```

**********
**********
**********
**********
**********
**********
**********
**********
**********
**********
<=========================>
**********
**********
**********
**********
**********
**********
**********
<=========================>

```

### 💻 完整代码

```python

# ### 函数的参数: 配合函数运行时,需要的值
"""
函数的参数 : (1) 形参(形式参数)  (2) 实参(实际参数)

(1) 形参: 在函数的定义处
普通形参(位置形参) -> 默认形参 -> 普通收集形参 -> 命名关键字形参 -> 关键字收集形参

(2) 实参: 在函数的调用处
普通实参  -> 关键字实参

# 原则:
形参 和 实参 要一一对应

"""

# (1) 普通形参
# 在函数定义处
"""hang , lie 是形式参数,具体的是普通形参"""
def func(hang,lie):
	i = 0
	while i < hang:
		# 打印星星
		j = 0
		while j < lie:	
			print("*",end="")
			j+=1
			
		# 打印换行
		print()
		i += 1
# 在函数调用处
# 10,10是对应的hang和lie的两个实参
func(10,10)

print("<=========================>")
# (2) 默认形参
"""hang=10,lie=10 hang,lie是默认形参,带有默认值"""
"""
如果在调用函数时,给与了实参,那么使用实参本身
如果在调用函数时,没有给与实参,那么使用形参的默认值
"""
def func(hang=10,lie=10):
	i = 0
	while i < hang:
		# 打印星星
		j = 0
		while j < lie:	
			print("*",end="")
			j+=1
			
		# 打印换行
		print()
		i += 1
# 在函数调用处
# func()
func(7) # hang = 7
# func(4,6)

print("<=========================>")
# (3) 普通形参 + 默认形参
"""默认形参一定要跟在普通形参的后面,顺序是一定的"""
def func(hang,lie=10):
	i = 0
	while i < hang:
		# 打印星星
		j = 0
		while j < lie:	
			print("*",end="")
			j+=1
			
		# 打印换行
		print()
		i += 1
# func(4)
# func(4,7)

# (4) 关键字实参
"""
	1.关键字实参的顺序可以打乱排列,因为指定了参数名.
	2.关键字实参必须跟在普通实参的后面,顺序是一定的
"""
# 函数的定义处
def func(hang,a,b,c,lie=10):
	i = 0
	while i < hang:
		# 打印星星
		j = 0
		while j < lie:	
			print("*",end="")
			j+=1
			
		# 打印换行
		print()
		i += 1
# 函数的调用处
"""hang=1 ... 都是关键字实参"""
# func(hang=1,a=2,b=3,c=4,lie=5) ok
# func(lie=5,a=2,c=4,hang=1,b=3) ok 
# func(1,lie=5,2,3,4)	  error 必须把关键字实参放在普通实参的后面
# func(1,2,c=1,lie=5,b=7) #success 
		
```

### 📖 要点讲解

- ### 函数的参数: 配合函数运行时,需要的值

- 10,10是对应的hang和lie的两个实参

- func(hang=1,a=2,b=3,c=4,lie=5) ok

- func(lie=5,a=2,c=4,hang=1,b=3) ok

- func(1,lie=5,2,3,4)	  error 必须把关键字实参放在普通实参的后面

- func(1,2,c=1,lie=5,b=7) #success

---

## 4. 4.收集参数.py

### 📋 运行结果

```

1 2 3
(4, 5, 6, 7, 8, 9)
55
1 2 3
{'d': 4, 'e': 5, 'f': 6}
班花:刘硬
班草:朱慧
吃瓜群众 吕文矿,刘崇祥

```

### 💻 完整代码

```python

# ### 收集参数
"""
1.普通收集参数
	专门用来收集那些多余的没人要的普通实参,
	最后打包成元组.
	
	def func(*args):
		pass
		
	args => arguments 
"""
def func(a,b,c,*args):
	print(a,b,c) # 1 2 3
	print(args)
	
func(1,2,3,4,5,6,7,8,9)

# 计算任意个数的累加和
def func(a,b,c,d,e,f):
	print(a+b+c+d+e+f)

# func(1,2,3,4,5,6)   success
# func(1,2,3,4,5,6,7) error

def func(*args):
	total = 0 
	for i in args:
		total += i
	print(total)
# func(1,2,3,4,5,6)   # success
func(1,2,3,4,5,6,7,8,9,10) # success

"""
2.关键字收集参数
	专门用来收集那些多余的没人要的关键字实参
	最后打包成字典
	
	def func(**kwargs):	
		pass
		
	kwargs => keyword arguments
"""
def func(a,b,c,**kwargs):
	print(a,b,c)
	print(kwargs) # {'d': 4, 'e': 5, 'f': 6}
func(a=1,b=2,c=3,d=4,e=5,f=6)

# 做任意格式字符串的拼接
"""
班花:刘硬
班草:朱慧
吃瓜群众:吕文矿,刘崇祥
"""
def func(**kwargs):
	# 定义两个空的字符串
	strvar1 = ""
	strvar2 = ""
	# 定义字典: dic => 存放着对应的职位
	dic = {"class_flower":"班花","class_grass":"班草"}
	# print(kwargs) # {'class_flower': '刘硬', 'class_grass': '朱慧', 'eatgua1': '吕文矿', 'eatgua2': '刘崇祥'}

	# 遍历字典kwargs
	# k => class_flower  class_grass eatgua1 eatgua2
	for k,v in kwargs.items():
		# 判断当前k这个键在不在职位字典dic中
		if k in dic:
			strvar1 += dic[k] + ":" + v + "\n" # strvar1 = strvar1 + dic[k] + ":" + v
		# 如果不在就是属于吃瓜群众,直接拼接姓名即可;
		else:
			strvar2 += v + ","
			
	print(strvar1.strip())
	print("吃瓜群众",strvar2.strip(","))
	
func(class_flower="刘硬",class_grass="朱慧",eatgua1="吕文矿",eatgua2="刘崇祥")

"""
dic = {'class_flower': '刘硬', 'class_grass': '朱慧', 'eatgua1': '吕文矿', 'eatgua2': '刘崇祥'}
for i in dic:
	print(i)

for i in dic.items():
	print(i) # ('class_flower', '刘硬')

a,b = (3,4) #=> a=3,b=4

for k,v in dic.items():
	print(k,v)

变量的解包
k,v = ('class_flower', '刘硬')
k,v = ('class_grass', '朱慧')
k,v = ('eatgua1', '吕文矿')
k,v = ('eatgua2', '刘崇祥')
print(k,v)
class_flower 刘硬
class_grass 朱慧
eatgua1 吕文矿
eatgua2 刘崇祥

dic = {"class_flower":"班花","class_grass":"班草"}
#1
dic[k] => 班花职位  + 刘硬
#2
dic[k] => 班草职位  + 朱慧

"""

```

### 📖 要点讲解

- func(1,2,3,4,5,6)   success

- func(1,2,3,4,5,6,7) error

- func(1,2,3,4,5,6)   # success

- 定义字典: dic => 存放着对应的职位

- print(kwargs) # {'class_flower': '刘硬', 'class_grass': '朱慧', 'eatgua1': '吕文矿', 'eatgua2': '刘崇祥'}

- k => class_flower  class_grass eatgua1 eatgua2

- 如果不在就是属于吃瓜群众,直接拼接姓名即可;

---

## 5. 5.命名关键字参数.py

### 📋 运行结果

```

1 2
3 4
(1, 3, 3, 45, 45, 45, 64, 56, 4564, 56456)
100
{'a': 1, 'b': 2, 'c': 3}
(1, 3, 3, 45, 45, 45, 64, 56, 4564, 56456)
100
1 2
3 4
<====>
1 2
3 4
<====>
1 2
3 4
a = 1 b = 2 c = 3 args = (4,) kw = {'d': 99, 'x': '#'}
a = 1 b = 2 c = 3 d = 88 kw = {'x': '#'}
a = 1 b = 2 c = 3 args = ('a', 'b') kw = {'x': 99, 'y': 77}
67

```

### 💻 完整代码

```python

# ### 命名关键字参数
"""
(1)跟在*号后面的参数是命名关键字参数
(2)在*args 和 **kwargs收集参数之间的参数是命名关键字参数
如果被定义成命名关键字参数,意味着函数调用时,必须使用关键字实参;(强制使用)
"""
# 定义方法一
def func(a,b,*,c,d):
	print(a,b)
	print(c,d)

# 在调用时,必须使用关键字实参;
func(1,2,c=3,d=4)

# 定义方法二
def func(*args,f,**kwargs):
	print(args)
	print(f)
	print(kwargs)
func(1,3,3,45,45,45,64,56,4564,56456,a=1,b=2,c=3,f=100)

def func(*args,f,**kwargs):
	print(args)
	print(f)
	
func(1,3,3,45,45,45,64,56,4564,56456,f=100)

# 关于 * 和 ** 的语法
"""
* 和 ** 在函数的定义处是用来打包,打包成元组或字典
* 和 ** 在函数的嗲用处是用来解包,解包列表/元组或者字典

* 和 ** 的优点: 可以控制参数的长度
	(1) 定义处参数的长度
	(2) 调用处参数的长度
	都可以动态的控制;
"""

# *号作用
def func(a,b,*,c,d):
	print(a,b)
	print(c,d)

lst = [1,2]
# *lst 把列表里面的元素,一个一个拿,迭代着拿出一个一个的值作为函数的实参
func(*lst,c=3,d=4) # func(1,2,c=3,d=4) 把列表里面的元素打散成一个一个的参数

print("<====>")
# **号作用
def func(a,b,*,c,d):
	print(a,b)
	print(c,d)

dic = {"c":3,"d":4}
# *dic 把字典里面的元素,一个一个拿,迭代着拿出拼凑成c=3,d=4作为函数的实参
func(1,2,**dic) # func(1,2,c=3,d=4) 把字典里面的元素打散成键=值的形式调用

print("<====>")
# 综合
func(*lst,**dic)

# 参数的顺序:
"""
顺序不能变 -> 是固定的
形参:普通形参 -> 默认形参 -> 普通收集形参 -> 命名关键字形参 -> 关键字收集形参
实参:普通实参 -> 关键字实参
def func(*args,**kwargs) 这种参数定义的形式可以接收到所有的实参;
"""
def f1(a, b, c=0, *args, **kw):
    print('a =', a, 'b =', b, 'c =', c, 'args =', args, 'kw =', kw)

def f2(a, b, c=0, *, d, **kw):
    print('a =', a, 'b =', b, 'c =', c, 'd =', d, 'kw =', kw)

# 以上两个函数 打印结果
#(一)
# f1(1, 2) # a=1,b=2,c=0,args=(),kw={}
# f1(1, 2, c=3) # a=1,b=2,c=3,args=(),kw={}
# f1(1, 2, 3, 'a', 'b') # a=1,b=2,c=3,args=(a,b)
# f1(1, 2, 3, 'a', 'b', x=99)#a=1,b=2,c=3,args=(a,b),kwargs={x:99}
# f2(1, 2, d=99, ext=None) #a=1,b=2,c=0,d=99,kw={ext:None}

#(二)
args = (1, 2, 3, 4)
kw = {'d': 99, 'x': '#'}
f1(*args, **kw) # a=1,b=2,c=3,args=(4,),kw={d:99,x:#}
"""
def f1(a, b, c=0, *args, **kw):
    print('a =', a, 'b =', b, 'c =', c, 'args =', args, 'kw =', kw)

f1(1,2,3,4,d=99,x=#)
"""

#(三)
def f2(a, b, c=0, *, d, **kw):
    print('a =', a, 'b =', b, 'c =', c, 'd =', d, 'kw =', kw)
myargs = (1, 2, 3)
mykw = {'d': 88, 'x': '#'}
f2(*myargs, **mykw) # a=1,b=2,c=3,d=88,kw={x:#}
# f2(1,2,3,d=88,x=#)
# a = 1 b = 2 c = 3 d = 88 kw = {'x': '#'}

#(四)
def f1(a, b, c=0, *args,d,**kw):
    print('a =', a, 'b =', b, 'c =', c, 'args =', args, 'kw =', kw)
    print(d)

f1(1,2,3, 'a', 'b',d=67, x=99,y=77)
# a=1,b=2,c=3,args=(a,b),d=67,kw(x:99,y:77)
# a = 1 b = 2 c = 3 args = ('a', 'b') kw = {'x': 99, 'y': 77}

import json

json.dumps()

```

### 📖 要点讲解

- *lst 把列表里面的元素,一个一个拿,迭代着拿出一个一个的值作为函数的实参

- *dic 把字典里面的元素,一个一个拿,迭代着拿出拼凑成c=3,d=4作为函数的实参

- f1(1, 2) # a=1,b=2,c=0,args=(),kw={}

- f1(1, 2, c=3) # a=1,b=2,c=3,args=(),kw={}

- f1(1, 2, 3, 'a', 'b') # a=1,b=2,c=3,args=(a,b)

- f1(1, 2, 3, 'a', 'b', x=99)#a=1,b=2,c=3,args=(a,b),kwargs={x:99}

- f2(1, 2, d=99, ext=None) #a=1,b=2,c=0,d=99,kw={ext:None}

- a = 1 b = 2 c = 3 d = 88 kw = {'x': '#'}

- a=1,b=2,c=3,args=(a,b),d=67,kw(x:99,y:77)

- a = 1 b = 2 c = 3 args = ('a', 'b') kw = {'x': 99, 'y': 77}

---

## 6. 6.return返回值.py

### 📋 运行结果

```

None
111
222
333
0 <内部打印>
1 <内部打印>
2 <内部打印>
3 <内部打印>
4 <内部打印>
5 <外部打印>
123
None
123
None
除数不能为0
<============>
step1,把启动洗衣机
step2,把衣服扔进去,放点蓝月亮洗衣液
step3,拿出来,晾干!
<============>
Help on built-in function print in module builtins:

print(*args, sep=' ', end='\n', file=None, flush=False)
    Prints the values to a stream, or to sys.stdout by default.

    sep
      string inserted between values, default a space.
    end
      string appended after the last value, default a newline.
    file
      a file-like object (stream); defaults to the current sys.stdout.
    flush
      whether to forcibly flush the stream.

Help on function wash in module __main__:

wash(something)
    # 自定义函数的帮助文档
    功能: 洗东西
    参数: 物品名称
    返回值: 洗的状态

Prints the values to a stream, or to sys.stdout by default.

  sep
    string inserted between values, default a space.
  end
    string appended after the last value, default a newline.
  file
    a file-like object (stream); defaults to the current sys.stdout.
  flush
    whether to forcibly flush the stream.

	# 自定义函数的帮助文档
	功能: 洗东西
	参数: 物品名称
	返回值: 洗的状态
	
```

### 💻 完整代码

```python

# ### return 自定义返回值
"""
return + 返回值 : 把函数内部的值返回到函数的调用处
	(1) return 后面可以接六大标准数据类型 , 还可以返回类对象,函数
		如果没有定义任何返回值,默认返回的是None;
	(2) return 在执行之后,函数立刻终止,后面的代码不执行;
"""
# (1) return 后面可以接六大标准数据类型 , 还可以返回类对象,函数
# 如果没有定义任何返回值,默认返回的是None;

# 定义处
def func():
	# return 1
	# return "我是自定义的返回值"
	# return [1,2,34]
	# return {"a":1,"b":2}
	pass
# 调用处
res = func() # res = 1
print(res)

# (2) return 在执行之后,函数立刻终止,后面的代码不执行;
def func():
	print("111")
	print("222")
	return "333"
	print("444")
	print("555")

res = func()
print(res)

# (3) 注意点:
def func():
	for i in range(10):
		if i == 5:
			return i
		print(i,"<内部打印>")
res = func() # res = 5
# 0 1 2 3 4 5
print(res,"<外部打印>")

# 打印值和返回值不是同一个概念,返回值是自定义的;
res = print(123)
print(res) # None

def myprint(n):
	print(n)
	return None

res = myprint(123)
print(res)

# 小案例: 模拟计算器
# + - * /
def mycalc(sign,num1,num2):
	if sign == "+":
		res = num1 + num2
	elif sign == "-":
		res = num1 - num2
	elif sign == "*":
		res = num1 * num2
	elif sign == "/":
		if num2 == 0:
			return "除数不能为0"
		res = num1 / num2
	return res
res = mycalc("+",5,3)
res = mycalc("-",5,3)
res = mycalc("*",5,3)
res = mycalc("/",5,3)
res = mycalc("/",5,0)
print(res)

# __doc__ 获取函数的帮助文档 (魔术属性)
def wash(something):
	"""
	# 自定义函数的帮助文档
	功能: 洗东西
	参数: 物品名称
	返回值: 洗的状态
	"""
	print("step1,把启动洗衣机")
	print("step2,把{}扔进去,放点蓝月亮洗衣液".format(something))
	print("step3,拿出来,晾干!")
	
print("<============>")
wash("衣服")
print("<============>")

# 获取文档方法一	
help(print)
help(wash)
# 获取文档方法二
res = print.__doc__
print(res)
print(wash.__doc__)

```

### 📖 要点讲解

- (1) return 后面可以接六大标准数据类型 , 还可以返回类对象,函数

- 如果没有定义任何返回值,默认返回的是None;

- (2) return 在执行之后,函数立刻终止,后面的代码不执行;

- 打印值和返回值不是同一个概念,返回值是自定义的;

- __doc__ 获取函数的帮助文档 (魔术属性)

---

## 7. 7.函数名的使用.py

### 📋 运行结果

```

我是一个函数
我是一个函数
<==========>
<==========>
我是func2这个函数
[<function fun1 at 0x765d879acfe0>, <function func2 at 0x765d879ad300>, <function func3 at 0x765d880fe2a0>] <class 'list'>
我是func1函数
我是func2函数
我是func3函数

```

### 💻 完整代码

```python

# ### 函数名的使用
"""
python中的函数可以像变量一样,
动态创建,销毁,当参数传递,作为值返回,叫第一类对象.
其他语言功能有限
"""

a = 1
def func():
	a = 100
	print("我是一个函数")
	
# 1.动态的把a创建成函数
a = func
a()
a = func() # None
# print(a)

print("<==========>")
# 2.动态销毁函数
del a
# a()

print("<==========>")
# 3.当参数传递
def func(f):
	# 调用传进来的函数
	f()

def func2():
	print("我是func2这个函数")

func(func2) # f<=>func2 等价

# 4.作为值返回
def fun1():
	print("我是func1函数")

def func2():
	print("我是func2函数")

def func3():
	print("我是func3函数")

def func():
	return [fun1,func2,func3]

lst = func()
print(lst, type(lst))
"""
[
<function fun1 at 0x00000208C85849D8>, 
<function func2 at 0x00000208C8584A60>, 
<function func3 at 0x00000208C85848C8>
] <class 'list'>
"""
for i in lst:
	# 遍历的数据是一个个的函数
	# 函数后面加(),直接调用
	i()

```

---

## 8. 8.全局变量和局部变量.py

### 📋 运行结果

```

100
200
300
400
500
800

```

### 💻 完整代码

```python

# ### 全局变量和局部变量
"""
局部变量: 在函数内部定义的变量
全局变量: 在函数外部定义的,或者在函数内部使用global关键字定义的

作用域: 作用的范围

局部变量作用域: 在函数内部生效
全局变量作用域: 横跨整个文件
"""

# 1.局部变量
# 定义局部变量
def func():
	# 定义一个局部变量
	a = 100
	# 获取局部变量
	print(a)
	# 修改局部变量
	a = 200
	# 获取局部变量
	print(a)
func()
# 无法在全局范围内获取局部变量
# print(a)

# 2.全局变量
# 定义全局变量
b = 300
# 获取全局变量
print(b)
# 修改全局变量
b = 400
# 获取全局变量
print(b)

# 3.在函数内部定义全局变量 global
def func():
	# 定义一个全局变量c,在函数的内部
	global c
	# 给c赋值
	c = 500
func()
# 获取全局变能量
print(c)

# 4.在函数内部修改全局变量 global
d = 700
def func():
	# 在已经存在该全局变量的情况下,可以通过global 修改全局变量
	global d
	d = 800
func()
print(d)

"""
global 可以获取或者修改全局变量
	如果函数外存在该变量,配合global关键字可以修改当前全局变量
	如果函数外不存在该变量,配合global关键字可以在函数内部定义全局变量;
"""

```

### 📖 要点讲解

- 在已经存在该全局变量的情况下,可以通过global 修改全局变量

---

## 9. 9.函数的嵌套.py

### 📋 运行结果

```

我是smaller函数
<built-in function id>
<built-in function id>
<built-in function id>

```

### 💻 完整代码

```python

# ### 函数的嵌套
"""
函数的嵌套至少2层;
	嵌套在外层的函数叫外函数
	嵌套的内存的函数叫内函数
	
内置空间中的成员伴随着解释器的启动而创建,伴随着解释器的释放释放,加载到内存的内置命名空间
全局空间中的成员在解释器启动之后在开始加载数据到内存的全局命名空间,
局部空间中的成员是在调用函数之后再加载数据到内存的局部命名空间
释放的时候 -> 先释放局部命名空间 -> 释放全局命名空间 -> 释放内置命名空间 (了解)

生命周期: 作用的时间
从大到小: 内置变量 -> 全局变量 -> 局部变量(生命周期最小,调用函数的时候开辟空间,调用结束时,释放空间)
"""

def outer():
	inner()
	def inner():
		print("我是内函数..")
		
# (1)内部函数可以直接在函数外部调用么? 不行! 作用域
# inner()
# (2)调用外部函数后,内部函数可以在函数外部调用吗  不行! 作用域
# outer()
# inner()
# (3)内部函数可以在函数内部调用吗
# outer()
# (4)内部函数在函数内部调用时,是否有先后顺序 有! 必须先定义,在调用
# outer()
"""
在其他语言当中,存在预加载机制
提前把函数加载到内存中,然后在编译文件本身.找到内存中的该函数
但是python不支持预加载机制,只能先定义在调用,代码执行顺序从上到下;
"""

# 嵌套三层函数,最外层是outer ,中间层是inner  最里层是smaller ,smaller如何调用成功?
# a = 100

def outer():	
	def inner():		
		def smaller():			
			print("我是smaller函数")
			print(id)
		smaller()
		print(id)
	inner()
	print(id)
outer()

# LEGB 原则 (就近找变量原则)
"""
#找寻变量的调用顺序采用LEGB原则(即就近原则)
B —— Builtin(Python)；Python内置模块的命名空间      (内建作用域)
G —— Global(module)； 函数外部所在的命名空间        (全局作用域)
E —— Enclosing function locals；外部嵌套函数的作用域(嵌套作用域)
L —— Local(function)；当前函数内的作用域            (局部作用域)
依据就近原则,从下往上 从里向外 依次寻找
"""

# 命名空间: 三种(局部命名空间 -> 全局命名空间 -> 内置命名空间)

def func():
	a=10
func()
print(a)

```

### 📖 要点讲解

- (1)内部函数可以直接在函数外部调用么? 不行! 作用域

- (2)调用外部函数后,内部函数可以在函数外部调用吗  不行! 作用域

- (4)内部函数在函数内部调用时,是否有先后顺序 有! 必须先定义,在调用

- 嵌套三层函数,最外层是outer ,中间层是inner  最里层是smaller ,smaller如何调用成功?

- 找寻变量的调用顺序采用LEGB原则(即就近原则)

- 命名空间: 三种(局部命名空间 -> 全局命名空间 -> 内置命名空间)

---

## 10. 10.nonlocal使用.py

### 📋 运行结果

```

200
200
700
700
500
[1, 2, 3, 400]

```

### 💻 完整代码

```python

# ### nonlocal 用来修饰局部变量
"""
nonlocal 遵循LEGB原则(就近找变量原则)
1.修改当前作用域上一层空间中的局部变量
2,如果上一层空间没有,继续向上寻找

"""

# 1.修改当前作用域上一层空间中的局部变量
def outer():
	a = 100
	def inner():
		nonlocal a
		a = 200
		print(a)
	inner()
	print(a)
outer()

# 2,如果上一层空间没有,继续向上寻找
def outer():
	a  = 500
	def inner():	
		a = 600
		def smaller():
			
			nonlocal a
			a = 700
			print(a) # 700
		smaller()
		print(a) # 700
	inner()
	print(a) # 500
outer()

# 3.直到最后再也找不到了,直接报错
# 全局变量
a  = 500
"""nonlocal只能修改局部变量,不能修改全局变量"""
"""
def outer():	 
	def inner():		
		def smaller():
			# 用来修改局部变量
			nonlocal a
			print(a) # 500
		smaller()
		print(a) # 500
	inner()
	print(a) # 500
outer()
"""

# 4.不依赖nonlocal 是否可以修改局部变量

def outer():
	lst = [1,2,3,4]
	def inner():
		lst[-1] = 400
	inner()
	print(lst)
outer() # [1, 2, 3, 400]

```

### 📖 要点讲解

- ### nonlocal 用来修饰局部变量

- 4.不依赖nonlocal 是否可以修改局部变量

---

## 11. 11.闭包函数.py

### 📋 运行结果

```

苏业清喜欢看电影,尤其在疫情阶段,经常包场看!感觉爽极了
<function python5_team.<locals>.live_master at 0x7ae7637ad4e0>
(<function python5_team.<locals>.money_process1 at 0x7ae7637ad3a0>, <function python5_team.<locals>.money_process2 at 0x7ae7637ad440>)
刘硬就喜欢还钱,买了包包花了400,还剩下600
薇薇看好了一辆特斯拉,花了200还剩下400
600
800

```

### 💻 完整代码

```python

# ### 闭包函数
"""
内函数使用了外函数的局部变量,
外函数把内函数返回出来的过程,叫做闭包
里面的这个内函数叫做闭包函数;
"""

# 基本语法
def outer():
	name = "苏业清"
	def inner():
		print("{}喜欢看电影,尤其在疫情阶段,经常包场看!感觉爽极了".format(name))
	return inner
func = outer()
func()

# 升级闭包函数
"""一个大的闭包函数当中,包含了2个小的闭包函数被简介返回,而大的闭包函数被直接返回"""
def python5_team():	
	study_one = "刘硬"
	study_last = "薇薇"
	money = 1000
	
	def money_process1():
		nonlocal money
		money -= 400
		print("{}就喜欢还钱,买了包包花了400,还剩下{}".format(study_one,money))
		
	def money_process2():
		nonlocal money
		money -= 200
		print("{}看好了一辆特斯拉,花了200还剩下{}".format(study_last,money))
		
	def live_master():
		return (money_process1,money_process2)
	
	return live_master
	
"""
live_master使用了外函数的局部变量 money_process1  money_process2,
外函数python5_team 把内函数live_master 返回出来的过程是闭包
里面live_master是闭包函数 , 是被外函数直接返回的
"""
live_master = python5_team()
print(live_master)

tup = live_master()
print(tup) # (money_process1,money_process2)
"""
(
<function python5_team.<locals>.money_process1 at 0x0000026C4A5149D8>,
 <function python5_team.<locals>.money_process2 at 0x0000026C4A514A60>
 )
"""

# money_process1 和 money_process2 是被间接返回到python5_team函数外的,所以也是闭包
# 通过0下标 -> 获取money_process1
money_process1 = tup[0]
money_process1() # 1000 - 400 = 600
# 通过1下标 -> 获取money_process2
money_process2 = tup[1]
money_process2() # 600 - 200 = 400
# 发现money的值,两个函数用的是同一个,基于上一个money值进行修改,证明money的生命周期延长了.
# print(money_process1,money_process2)
	
# 正常的函数(在调用结束之后,直接释放)
def func(money):
	a = 1000
	return a - money
	
print(func(400)) # 600
print(func(200)) # 800

```

### 📖 要点讲解

- money_process1 和 money_process2 是被间接返回到python5_team函数外的,所以也是闭包

- 通过0下标 -> 获取money_process1

- 通过1下标 -> 获取money_process2

- 发现money的值,两个函数用的是同一个,基于上一个money值进行修改,证明money的生命周期延长了.

- print(money_process1,money_process2)

---

## 12. 12.闭包特点和意义.py

### 📋 运行结果

```

5
1
2
3
4
901
1
2
3
4
5

```

### 💻 完整代码

```python

# ### 闭包的特点
"""
内函数使用了外函数的局部变量,
外函数的局部变量与内函数发生绑定,
延长该局部变量的生命周期~ (生命周期的长度等价于全局变量,等文件全部执行结束之后,在释放该局部变量)
"""
def outer(n):
	def inner(v):
		return n - v
	return inner
func = outer(15) # inner
res = func(10) # 5
print(res)

"""
func = outer(15)  <=> n = 15
func = inner
res = func(10) <=> v = 10
	  func(10) <=> inner(10)        
	  return n - v <=> 15 - 10 <=> 5
res = 5

inner 是闭包函数,使用了外函数outer的局部变量n
那么该变量n与内函数inner 发生绑定,延长该变量n的生命周期,
直到文件直接结束之后在释放;
所以在下次使用n-v的时候 , 还能在获取到15这个数据.

"""

# ### 闭包的意义
"""
闭包可以优先使用外函数中的局部变量,
并对闭包中的值起到了封装保护的作用.
外部无法访问.
"""
# 模拟计数鼠标点击次数
""""""
num = 0
def click_count():
	global num
	num +=1 # num = num + 1
	print(num)

click_count()
click_count()
click_count()
click_count()
num = 900
click_count()

# 利用闭包函数,改造计数函数
def outer():
	num = 0
	def click_num():
		nonlocal num
		num += 1
		print(num)
	return click_num

click_num = outer()
click_num()
click_num()
click_num()
click_num()
num = 1000
click_num()

```

---

## 13. 13.匿名函数.py

### 📋 运行结果

```

11223344
<class 'list'>
<class 'str'>
123
120

```

### 💻 完整代码

```python

# ### 匿名函数 
"""
匿名函数追求简洁,高效.
概念: 用一句话来表达只有返回值的函数
语法: lambda 参数 : 返回值
"""

# 1.无参的lambda 表达式
def func():
	return "11223344"

# 改写
func = lambda  : "11223344"
print(func())

# 2.有参的lambda 表达式
def func(n):
	return type(n)
print(func([1,2,3]))
	
# 改写
func = lambda n : type(n)
print(func("strvar"))

# 3.带有判断条件的lambda 表达式
def func(x,y):
	if x > y:
		return x
	else:
		return y
	
# 改写
func = lambda x,y :  x if x > y else y
res = func(12,123)
print(res)

# 4.三元(目)运算符 (用来表达双项分支)
"""
语法:   真值  if 条件表达式 else 假值
"""
x = 120
y = 5
res = x if x > y else y
print(res)

```

### 📖 要点讲解

- 4.三元(目)运算符 (用来表达双项分支)

---

## 14. 14.递归函数.py

### 📋 运行结果

```

5 <===1==>
4 <===1==>
3 <===1==>
2 <===1==>
1 <===1==>
0 <===1==>
0 <===2==>
1 <===2==>
2 <===2==>
3 <===2==>
4 <===2==>
5 <===2==>
120

```

### 💻 完整代码

```python

# ### 递归函数
"""
递归函数 : 自己调用自己的函数
递: 去
归: 回
一去一回是递归函数
"""

def digui(n):
	print(n,"<===1==>")
	if n > 0:
		digui(n-1)
	print(n,"<===2==>")
digui(5)

"""
# 去的过程
n = 5 print(5,"<===1==>") 5 > 0 digui(5-1) => digui(4) 代码阻塞在第12行
n = 4 print(4,"<===1==>") 4 > 0 digui(4-1) => digui(3) 代码阻塞在第12行
n = 3 print(3,"<===1==>") 3 > 0 digui(3-1) => digui(2) 代码阻塞在第12行
n = 2 print(2,"<===1==>") 2 > 0 digui(2-1) => digui(1) 代码阻塞在第12行
n = 1 print(1,"<===1==>") 1 > 0 digui(1-1) => digui(0) 代码阻塞在第12行
n = 0 print(0,"<===1==>") 0 > 0 条件不成立,不执行递归调用, print(0,"<===2==>")

# 回的过程
n = 1 把剩下没走完的代码走完,从第12行继续执行直到结束.print(1,"<===2==>")
n = 2 把剩下没走完的代码走完,从第12行继续执行直到结束.print(2,"<===2==>")
n = 3 把剩下没走完的代码走完,从第12行继续执行直到结束.print(3,"<===2==>")
n = 4 把剩下没走完的代码走完,从第12行继续执行直到结束.print(4,"<===2==>")
n = 5 把剩下没走完的代码走完,从第12行继续执行直到结束.print(5,"<===2==>")
5432100  12345
"""

"""
(1) 每次调用函数的时候都会在内存中开辟栈帧空间,每次调用结束时,再去释放当前的栈帧空间
	递归函数就是不停的开辟和释放栈帧空间的过程,每层函数的栈帧空间的数据都彼此隔离独立;
	
(2) 触发递归回的过程有2点:
	1.当函数调用到最后一层空间,代码彻底执行结束的时候,触发回的过程,回到上一层空间的调用处(阻塞处)再往下执行结束,以此类推
	2.遇到return的时候,触发回的过程,终止当前函数,回到上一层空间的调用处(阻塞处)
	
(3) 写递归函数必须给与跳出的条件,不能无限次的开辟空间,占用内存资源,否则内存溢出死机
	如果递归的层数过多,不推荐使用递归.
"""

# 官方说法: 递归最大层数默认是1000层,后期可以通过sys模块修改层数;
"""
def maxlenth():
	maxlenth()
maxlenth()
"""

# 计算5! = 5*4*3*2*1  计算任意数n的阶乘
def jiecheng(n):
	if n <= 1:
		return 1

	return n * jiecheng(n-1)

res = jiecheng(5)
print(res)

"""
# 代码解析:
# 去的过程
n = 5 return 5 * jiecheng(5-1) => 5 * jiecheng(4)
n = 4 return 4 * jiecheng(4-1) => 4 * jiecheng(3)
n = 3 return 3 * jiecheng(3-1) => 3 * jiecheng(2)
n = 2 return 2 * jiecheng(2-1) => 2 * jiecheng(1)
n = 1 return 1 

# 当最后一层空间执行结束,有确切的返回值时,触发回的过程
n = 2 return 2 * jiecheng(2-1) => 2 * 1
n = 3 return 3 * jiecheng(3-1) => 3 * 2 * 1
n = 4 return 4 * jiecheng(4-1) => 4 * 3 * 2 * 1
n = 5 return 5 * jiecheng(5-1) => 5 *  4 * 3 * 2 * 1

return => 5 *  4 * 3 * 2 * 1 => 120
递归到最上层 彻底结束 120

jiecheng(1) => 1
jiecheng(2) => 2 * jiecheng(1)
jiecheng(3) => 3 * jiecheng(2)
jiecheng(4) => 4 * jiecheng(3)
jiecheng(5) => 5 * jiecheng(4)
"""

```

### 📖 要点讲解

- 官方说法: 递归最大层数默认是1000层,后期可以通过sys模块修改层数;

- 计算5! = 5*4*3*2*1  计算任意数n的阶乘

- 当最后一层空间执行结束,有确切的返回值时,触发回的过程

---

## 🖼️ 参考资料

![LEGB.png](./assets/LEGB.png)

![函数的调用顺序.png](./assets/函数的调用顺序.png)

![递归原理.png](./assets/递归原理.png)

![递归逻辑图.png](./assets/递归逻辑图.png)
