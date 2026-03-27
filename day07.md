# Day 7: day07 类中的删除构造方法 单继承多继承菱形继承 多态   del  new   单态模式 add bool str repr 魔术方法 装饰器

> 对应原课程：day07_类中的删除构造方法_单继承多继承菱形继承_多态___del__new___单态模式_add_bool_str_repr_魔术方法_装饰器

---

## 1. ceshi.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day07_类中的删除构造方法_单继承多继承菱形继承_多态___del__new___单态模式_add_bool_str_repr_魔术方法_装饰器/代码/ceshi.py", line 17, in <module>
    func()
    ^^^^
NameError: name 'func' is not defined

```

### 💻 完整代码

```python

class tx():
	a = 10
	# print(a)
	def __init__(self,num):
		self.a = num
		
	def func():	
		print(1)
	# print(a)

# mm = tx(100)
# print(tx.__dict__) # 'a': 10,
# print(mm.__dict__) # {'a': 15}
# print(mm.a)
# print(a)

func()

```

### 📖 要点讲解

- print(tx.__dict__) # 'a': 10,

- print(mm.__dict__) # {'a': 15}

---

## 2. 1.删除类对象中的成员.py

### 📋 运行结果

```

{'__module__': '__main__', 'oil': '百公里油耗100升', '_Car__price': '100万', 'taxis1': <function Car.taxis1 at 0x7e5251b01440>, '_Car__taxis2': <function Car.__taxis2 at 0x7e5251b68fe0>, 'race': <function Car.race at 0x7e5251b69300>, '_Car__race': <function Car.__race at 0x7e5251b693a0>, 'pub_info': <function Car.pub_info at 0x7e5251b69440>, 'pub_info2': <function Car.pub_info2 at 0x7e5251b694e0>, '__dict__': <attribute '__dict__' of 'Car' objects>, '__weakref__': <attribute '__weakref__' of 'Car' objects>, '__doc__': None}
100万
100万
小车可以载人拉客2
小车可以跑竞速,看谁跑的快2
100万
小车可以载人拉客2
100万
小车可以跑竞速,看谁跑的快2
{'oil': '百公里油耗50升'}
百公里油耗100升
{'taxis1': <function <lambda> at 0x7e5251fda2a0>}
小车可以载人拉客1
<==================>

```

### 💻 完整代码

```python

# ### 1.访问类中的私有成员 
class Car():
	# 公有成员
	oil = "百公里油耗100升"
	# 私有成员
	__price = "100万"
	
	# 公有绑定方法
	def taxis1(self):
		print("小车可以载人拉客1")
		
	# 私有绑定方法
	def __taxis2(self):
		print("小车可以载人拉客2")
		
	# 公有普通方法	
	def race():
		print("小车可以跑竞速,看谁跑的快1")
		
	# 私有普通方法
	def __race():
		print("小车可以跑竞速,看谁跑的快2")
		
	# 公有绑定方法
	def pub_info(self):
		print(self.__price)
		self.__taxis2()
		
	# 公有普通方法
	def pub_info2():
		 print(Car.__price)
		 Car.__race()
	
obj = Car()
print(Car.__dict__)
# 私有化:改名策略完成的(_类+私有成员) [不推荐使用,破坏了类中封装性]
print(obj._Car__price)
print(Car._Car__price)
obj._Car__taxis2()
Car._Car__race()

# 可以通过访问公有方法,间接的访问私有成员 [推荐性]
obj.pub_info()
Car.pub_info2()

# ### 2.删除类对象中的成员
"""
对象可以使用类中的公有成员,但是没有这个成员的归属权
对象使用成员时,先看看自己的对象空间是否存在,
有用自己的,没有的话使用类的,都没有的话直接报错
"""
# 删除对象中的成员属性
obj.oil = "百公里油耗50升"
print(obj.__dict__)
del obj.oil
print(obj.oil)

# 删除对象中的成员方法
obj.taxis1 = lambda : print("我是taxis1")
print(obj.__dict__)
del obj.taxis1
obj.taxis1()

print("<==================>")
# 删除类中的成员属性
del Car.oil
# print(car.oil) error
# print(obj.oil) error

# 删除类中的成员方法
del Car.taxis1
# Car.taxis1(1) error
# obj.taxis1()  error

```

### 📖 要点讲解

- 私有化:改名策略完成的(_类+私有成员) [不推荐使用,破坏了类中封装性]

- 可以通过访问公有方法,间接的访问私有成员 [推荐性]

---

## 3. 2.__init__魔术方法.py

### 📋 运行结果

```

构造方法被触发了... 
张三
李四5
小孩的名字joe,小孩的肤色是白色皮肤
joe一下生就哇哇哇的哭
小孩的名字mickle,小孩的肤色是黑色皮肤
mickle一下生跳着街舞就出来了
小孩的名字王宝强,小孩的肤色是绿色的皮肤
王宝强一下生就会演戏,唐人街探案3不错

```

### 💻 完整代码

```python

# ### 魔术方法(特定时机,自动触发)

#__init__魔术方法(构造方法)
'''
	触发时机：实例化对象,初始化的时候触发
	功能：为对象添加成员
	参数：参数不固定,至少一个self参数
	返回值：无
'''

# (1) 基本使用
class MyClass():
	def __init__(self):
		print("构造方法被触发了... ")
		self.name = "张三"
	
# 实例化对象
obj = MyClass()
print(obj.name)

# (2) 带有多个参数的构造方法
class MyClass():
	def __init__(self,name):
		# self.成员属性 = 参数
		self.name = name # self.name = "李四"

# 实例化时,自动把李四这个参数赋值给name这个形参,self是系统自动传递
obj = MyClass("李四5")
print(obj.name)

# (3) 类可以是一个,对象可以是多个

class Children():
	def __init__(self,name,skin):
		# 为当前对象self添加成员属性
		self.name = name
		self.skin = skin
	
	def cry(self):
		print("{}一下生就哇哇哇的哭".format(self.name))
	
	def rap(self):
		print("{}一下生跳着街舞就出来了".format(self.name))
		
	def act(self):
		print("{}一下生就会演戏,唐人街探案3不错".format(self.name))
	
	def pub_info(self):
		print("小孩的名字{},小孩的肤色是{}".format(self.name,self.skin))
	
# 创建第一个对象
joe = Children("joe","白色皮肤")
joe.pub_info()
joe.cry()

# 创建第二个对象
mickle = Children("mickle","黑色皮肤")
mickle.pub_info()
mickle.rap()

# 创建第三个对象
baoqiang = Children("王宝强","绿色的皮肤")
baoqiang.pub_info()
baoqiang.act()

"""
总结:
	同一类可以创建出多个不同的对象
	多个对象之间彼此是独立的,但是都可以使用到类中的公有成员
"""

```

### 📖 要点讲解

- 实例化时,自动把李四这个参数赋值给name这个形参,self是系统自动传递

---

## 4. 3.单继承.py

### 📋 运行结果

```

古代人类爱抽烟
古代小孩喝奶奶

```

### 💻 完整代码

```python

# ### 继承 : 一个类继承另外一个类,将拥有该类所有的公有成员
"""
继承的这个类就是子类 (衍生类)
被继承的这个类就是父类 (超类,基类)

继承:
	(1) 单继承 (一个子类一个父类)
	(2) 多继承 (一个子类多个父类)
	
object 是所有类的父类
"""
# ### 单继承
class Human():
	__money = 10
	def smoke(self):
		print("古代人类爱抽烟")
		
	def drink(self):
		print("古代人类爱喝酒")
		
	def tangHead():
		print("古代人类爱扎鞭子")
		
# (1) 子父继承之后,子类可以使用父类的公有成员
class Man(Human):
	pass

obj = Man()
obj.smoke()

# (2) 子父继承之后,子类不能使用父类的私有成员
class Woman(Human):
	# 在子类定义一个公有方法,也不能调用父类的私有成员
	def pub_info(self):
		print(self.__money)
	
"""(了解)protected 属于受保护的成员,在子父继承之后,可以在子类使用,而类外不能调用 python不支持"""
obj = Woman()
# obj.pub_info() error

# (3) 子父继承之后,子类可以改写父类中的方法
"""
子父继承之后,子类对象在调用成员时,先看看当前子类成员是否存在,
有,就优先调用自己的,没有的话,就调用父类的,都没有,直接报错.
"""
class Children(Human):
	def drink(self):
		print("古代小孩喝奶奶")

obj = Children()
obj.drink()

"""
注意点:
	在定义类的地方class所在的位置写该类的父类,表达一种继承瓜关系;
"""

```

### 📖 要点讲解

- ### 继承 : 一个类继承另外一个类,将拥有该类所有的公有成员

- (1) 子父继承之后,子类可以使用父类的公有成员

- (2) 子父继承之后,子类不能使用父类的私有成员

- 在子类定义一个公有方法,也不能调用父类的私有成员

- (3) 子父继承之后,子类可以改写父类中的方法

---

## 5. 4.多继承.py

### 📋 运行结果

```

英明神武,英姿飒爽,一枝梨花压海棠
闭月羞花,一笑倾城,一枝红杏出墙来
爱学习,爱上班,爱老婆,爱加班 ~
跳街舞,唱rap,长相帅气小鲜肉
自己的m_hobby方法
<class 'super'>
<super: <class 'Son'>, <Son object>>
英明神武,英姿飒爽,一枝梨花压海棠
爱吃东西,爱逛街,爱花钱,爱要钱 ~

```

### 💻 完整代码

```python

# ### 多继承

# 1.基本使用
class Father():
	pty = "英明神武,英姿飒爽,一枝梨花压海棠"
	def f_hobby(self):
		print("爱学习,爱上班,爱老婆,爱加班 ~")

class Mother():
	pty = "闭月羞花,一笑倾城,一枝红杏出墙来"
	def m_hobby(self):
		print("爱吃东西,爱逛街,爱花钱,爱要钱 ~")
		
class Daughter(Father,Mother):
	pass

obj = Daughter()
print(obj.pty)

# 2.使用不同方式调用父类成员
"""
(1)super本身是一个类 super()是一个对象 用于调用父类的绑定方法
(2)super() 只应用在绑定方法中,默认自动传递self对象 (前提:super所在作用域存在self)
(3)super用途: 解决复杂的多继承调用顺序	
"""

class Father():
	pty = "英明神武,英姿飒爽,一枝梨花压海棠"
	def f_hobby():
		print("爱学习,爱上班,爱老婆,爱加班 ~")
		
class Mother():
	pty = "闭月羞花,一笑倾城,一枝红杏出墙来"
	def m_hobby(self):
		print("爱吃东西,爱逛街,爱花钱,爱要钱 ~")

class Son(Father,Mother):
	pty = "跳街舞,唱rap,长相帅气小鲜肉"
	
	def m_hobby(self):
		print("自己的m_hobby方法")
	
	# 用类的方式调用父类成员
	def skill1(self):
		print(Mother.pty)
		Father.f_hobby()
		
	# 用对象的方法调用父类成员
	def skill2(self):
		print(self.pty)
		self.m_hobby()
		
	# 用super专门用来调用父类成员(super()只能调用绑定方法,定义方法时加self形参.)
	def skill3(self):
		print(super)
		print(super()) # super() <=> obj
		# 只调用父类的成员属性
		print(super().pty)
		# 使用super()调用时,会自动传递本类对象(Son_obj)
		super().m_hobby()
		
obj = Son()
obj.skill1()
obj.skill2()
obj.skill3()

"""
self 和 super() 调用之间的区别:
self  如果自己对象有,调用自己的,没有调用子类的,在没有调用父类的,都没有,直接报错
super 只调用父类的成员属性或者方法,如果父类没有,直接报错.不会找自己的成员.
	  super调用方法时,会自动的把自己本类的对象当成参数传递给父类方法.调绑定方法.
"""

```

### 📖 要点讲解

- 用super专门用来调用父类成员(super()只能调用绑定方法,定义方法时加self形参.)

- 使用super()调用时,会自动传递本类对象(Son_obj)

---

## 6. 5.菱形继承.py

### 📋 运行结果

```

现代小孩天热了吃冰棍7
<super: <class 'Children'>, <Children object>>
现代男人天热了喝啤酒3
<__main__.Children object at 0x75ad60d8a6c0>
现代女人天热了脱衣服5
<__main__.Children object at 0x75ad60d8a6c0>
古代人类天热了跳河1
4 <__main__.Children object at 0x75ad60d8a6c0> <====>
古代人类天冷了烧火2
现代男人天冷了穿衣服6
现代男人天冷了喝白酒4
现代男人天冷了吃汉堡8
[<class '__main__.Children'>, <class '__main__.Man'>, <class '__main__.Woman'>, <class '__main__.Human'>, <class 'object'>]
True
True

```

### 💻 完整代码

```python

# ### 菱形继承
"""
	 Human
Man		    Woman
	Children
	
(1)super本身是一个类 super()是一个对象 用于调用父类的绑定方法
(2)super() 只应用在绑定方法中,默认自动传递self对象 (前提:super所在作用域存在self)
(3)super用途: 解决复杂的多继承调用顺序	
"""

class Human():
	pty = 1
	def feelT(self):		
		print("古代人类天热了跳河1")
		print(self.pty,self,"<====>") # Children_obj
		print("古代人类天冷了烧火2")

class Man(Human):
	pty = 2
	def feelT(self):
		print("现代男人天热了喝啤酒3")
		print(self) # Children_obj
		super().feelT()
		print("现代男人天冷了喝白酒4")
	
class Woman(Human):
	pty = 3
	def feelT(self):
		print("现代女人天热了脱衣服5")
		print(self) # Children_obj
		super().feelT()
		print("现代男人天冷了穿衣服6")
	
class Children(Man,Woman):
	pty = 4
	def feelT(self):
		print("现代小孩天热了吃冰棍7")
		print(super()) # Children_obj
		super().feelT()
		print("现代男人天冷了吃汉堡8")
	
obj = Children()
obj.feelT()
# 73512648
# 73512648

# mro 采用c3算法,在多继承中,super按照顺序关系列表依次进行调用 语法: 类.mro()
"""python3.x版本中 super中的c3算法不在采用过去的深度优先原则,而是采用广度优先原则,横向发展"""
lst = Children.mro()
print(lst)

# 为什么Human中的self.pty是4
"""
super().feelT() , 默认传递Children对象给Man
Man   中的Children 对象 会通过super()继续传递给Woman
Woman 中的Children 对象 会通过super()继续传递给Human
Human 接收到的Children 对象 , 所有 self.pyt => 4
"""

# ### issubclass 和 isintance 语法上一模一样
# issubclass 用来判断子父关系
class MyClass():
	pass
res = issubclass(Children,Man)
"""在一条继承链上互为子父关系"""
res = issubclass(Children,Human)
# 在元组中的父类中,有一个满足即为True
res = issubclass(Children,(Human,MyClass))
print(res)

# isinstance  用来判断对象和类型
res = isinstance(obj,Children)
"""在一条继承链上即为该对象的类型"""
res = isinstance(obj,Human)
# 在元组中的类型中,有一个满足即为True
res = isinstance(obj,(Human,MyClass))
print(res)

```

### 📖 要点讲解

- mro 采用c3算法,在多继承中,super按照顺序关系列表依次进行调用 语法: 类.mro()

- ### issubclass 和 isintance 语法上一模一样

- isinstance  用来判断对象和类型

---

## 7. 6.多态.py

### 📋 运行结果

```

将军请下令:
1.全体出击
2.全体撤退
3.空军上,其他人撤退

将军请下令:

```

### 💻 完整代码

```python

# ###多态:不同的子类对象,调用相同的父类方法,产生不同的执行结果
"""
多态应用的场景是在对象身上
关键字: 继承,重写
"""

class Soldier():
	def attack(self):
		pass
		
	def back(self):
		pass

class Army(Soldier):
	
	def attack(self):
		print("[陆军]拿起ak47向敌方扫射,嘴里大喊鸭子给给~")
	
	def back(self):
		print("[陆军]撒腿就跑,嘴里大喊,三有哪啦")
		
class Navy(Soldier):
	
	def attack(self):
		print("[海军]仍鱼叉的能力一级棒,拿鱼叉投射敌人,插死一个算一个")

	def back(self):
		print("[海军]跳海喂鱼")
		
class AirForce(Soldier):
	
	def attack(self):
		print("[空军]在天上打飞机,射死一个算一个")
		
	def back(self):
		print("[空军]契机跳伞,落地成盒")
		
# 创建陆军士兵
obj_Army = Army()
# 创建海军士兵
obj_Navy = Navy()
# 创建空军士兵
obj_AirForce = AirForce()
# 把各种士兵组织在一起
lst = [obj_Army,obj_Navy,obj_AirForce]

# 将军拿起遥控器指挥战斗
strvar = """
将军请下令:
1.全体出击
2.全体撤退
3.空军上,其他人撤退
"""
print(strvar)

while True:
	num = input("将军请下令:")

	if num in ["1","2","3"]:
		for i in lst:
			if num == "1":
				i.attack()
			elif num== "2":
				i.back()
			elif num == "3":
				# 判断当前对象的类型是AirForce
				if isinstance(i,AirForce):
					i.attack()
				else:
					i.back()
	else:
		print("风太大,将军 我听不到~")
				
"""
总结:
	不同的子类对象,调用相同的方法,出现了不同的结果,就是多态
	针对的是对象,有对象就有一切,python中万物皆是对象.
"""		

```

### 📖 要点讲解

- ###多态:不同的子类对象,调用相同的父类方法,产生不同的执行结果

---

## 8. 7.析构方法.py

### 📋 运行结果

```

甜甜
135513322594832 135513322594832
<========start=======>
析构方法被触发 ... 
<========end=======>
### OOP 面向对象的程序开发

```
#用几大特征表达一类事物称为一个类,类更像是一张图纸,表达的是一个抽象概念
#对象是类的具体实现,更像是由这图纸产出的具体物品,类只有一个,但对象可以通过这个类实例化出多个
#对象是类的实例,类是对象的模板
#*类中的成员只有方法和属性,不要裸露的把判断和循环直接写在类中,而是用方法包起来

(1)类的定义
(2)类的实例化
(3)类的基本结构
(4)类的命名
```
### 面向对象三大特征: 封装 继承 多态

```
#-封装:对类中成员属性和方法的保护,控制外界对内部成员的访问,修改,删除等操作
#-继承:一个类除了自身所拥有的属性方法之外,还获取了另外一个类的成员属性和方法
#-多态:不同的子类对象,调用相同的父类方法,产生不同的执行结果
```

### python对成员的保护分为两个等级

```
私有的: private
	在本类内部可以访问,类的外部不可以访问.(python中 属性或者方法前面加上两个下划线__)
公有的: public
	在本类的内部和外部都可以访问.
#(了解)在其他高级语言当中,如java php c++等语言,有三个等级 private public protected
```

```
# 私有成员的改名策略 [_类名__成员名]
# 对象的相关操作
    (1)实例化的对象访问公有成员属性和方法
    (2)实例化的对象动态添加公有成员属性和方法
    (3)实例化的对象删除公有成员属性和方法
# 类的相关操作
    (1)定义的类访问公有成员属性和方法
    (2)定义的类动态添加公有成员属性和方法
    (3)定义的类删除公有成员属性和方法
    
普通方法:  没有任何参数传递,只能类调用
绑定方法:  把默认传参的方法叫做绑定方法,绑定到对象(默认传对象),绑定到类(默认传类)
非绑定方法:静态方法(无需传任何参数,对象和类都能调用)
```

```
私有的：只能载类或者对象的结构中访问
公有的：可以载任何位置访问
受保护：可以载当前类或者对象 和子类或者子类对象中访问

		类内   子类中    类外部
公有的：  √       √        √  
私有的：  √       X        X
受保护：  √       √        X (python语言不支持)
```

### 编程语言的发行时间 

```
1972	C
1983	C++(即带有类概念的C语言,更名于1983年7月)
1989	Python
1991	Visual Basic
1993	Ruby
1995	JavaScript
1995	PHP
1996	Java
2001	C#
2009	Go
```

```

### 💻 完整代码

```python

# ### __del__ (析构方法)
'''
	触发时机:当对象被内存回收的时候自动触发[1.页面执行完毕触发 2.所有对象被del的时候触发]
    功能：对象使用完毕后资源回收
	参数：一个self接受对象
	返回值：无
'''
# 1.基本使用
class Cat():
	def __init__(self,name):
		self.name = name
		
	def uptree(self):
		print("小猫会上树")
	
	def __del__(self):
		print("析构方法被触发 ... ")
	
# 1.页面执行完毕触发__del__ 析构方法
obj = Cat("甜甜")
print(obj.name)

# 2.所有对象被del的时候触发
obj2 = obj
print(id(obj2) , id(obj))
print("<========start=======>")
del obj
del obj2
print("<========end=======>")

# 3.面向对象的思想模拟文件操作

import os
class ReadFile():
	
	def __init__(self,filename):
		# 1.判断文件是否存在?
		if os.path.exists(filename):
			self.fp = open(filename,mode="r",encoding="utf-8")
		else:
			self.fp = None
			return print("没有该文件")
		
	def readcontent(self):
		# 2.读取文件数据
		if self.fp:
			return self.fp.read()
	
	def __del__(self):
		# 3.关闭文件
		if self.fp:
			self.fp.close()
	
obj = ReadFile("part13.md")
res = obj.readcontent()
print(res)

```

### 📖 要点讲解

- 1.页面执行完毕触发__del__ 析构方法

---

## 9. 8.__new__魔术方法.py

### 📋 运行结果

```

<class '__main__.MyClass'>
1
2
铁锤
铁杵
黑色
女性
abc
new方法被触发 ...
199

```

### 💻 完整代码

```python

#__new__ 魔术方法
'''
	触发时机：实例化类生成对象的时候触发(触发时机在__init__之前)
	功能：控制对象的创建过程
	参数:至少一个cls接受当前的类,其他根据情况决定
	返回值：通常返回对象或None
'''

# (1) 基本使用
"""控制对象的创建过程"""

class Ceshi():
	a = 199
obj2 = Ceshi()

class MyClass():
	def __new__(cls):
		# 借助父类object中__new__魔术方法来创建
		# 1.控制返回该类对象
		# 类.属性 类.方法  为当前MyClass这个类创建对象
		return object.__new__(MyClass)		
		# 2.控制返回其他类的对象
		# return obj2
		# 3.控制不返回对象
		# pass
obj = MyClass()

# return 第二种情况时,才有199
# print(obj)
# print(obj.a) # 199

# <__main__.MyClass object at 0x000002BCB0C32828>
# None <__main__.MyClass object at 0x000001B97C8D29E8>

# (2) __new__ 对比 __init__方法,谁的速度更快?
"""
__new__  用来先创建一个对象
__init__ 用来初始化一个对象
先触发的__new__,后触发的是__init__
"""
class MyClass():
	def __new__(cls):
		print(cls)
		print(1)
		return object.__new__(cls)
	def __init__(self):
		print(2)
obj = MyClass()

# 1.带参数的情况
class MyClass():

	def __new__(cls,name):
		return object.__new__(cls)
		
	def __init__(self,name):
		print(name)
		
obj = MyClass("铁锤")

# 2.如果是多个参数的情况,可以使用收集参数
""" *args,**kwargs 收集参数可以收集到 所有的普通实参和关键字实参  """
class MyClass():

	def __new__(cls,*args,**kwargs):
		return object.__new__(cls)
		
	def __init__(self,name,skin,sex,xuexing = "xo"):
		print(name)
		print(skin)
		print(sex)
		print(xuexing)
		
obj = MyClass("铁杵","黑色","女性",xuexing = "abc")

# 3.注意事项
"""如果返回的对象不是自己本类的,那么不会触发构造方法."""
class MyClass():
	def __new__(cls,*args,**kwargs):
		print("new方法被触发 ...")
		return obj2
		
	def __init__(self,name):
		print("构造方法被触发 ... ")
		self.name = name
		
obj = MyClass("王宝强")
print(obj.a)
# print(obj.name)

```

### 📖 要点讲解

- 借助父类object中__new__魔术方法来创建

- 类.属性 类.方法  为当前MyClass这个类创建对象

- <__main__.MyClass object at 0x000002BCB0C32828>

- None <__main__.MyClass object at 0x000001B97C8D29E8>

- (2) __new__ 对比 __init__方法,谁的速度更快?

- 2.如果是多个参数的情况,可以使用收集参数

---

## 10. 9.单态模式.py

### 📋 运行结果

```

<__main__.SingleTon object at 0x714f3b78dfd0>
<__main__.SingleTon object at 0x714f3b78dfd0>
<__main__.SingleTon object at 0x714f3b78dfd0>
124585114132768 124585114132768
刘硬
刘硬

```

### 💻 完整代码

```python

# ### 单态模式 : 一个类无论实例化多少次,都有且只有一个对象
"""
优点: 应用在不需要对对象动态添加成员的场景用单态,节省内存空间
"""
class SingleTon():
	__obj = None
	def __new__(cls):
		# 类.属性
		if cls.__obj is None:
			cls.__obj = object.__new__(cls)
		return cls.__obj

"""
第一次执行时, cls.__obj is None 条件为真 执行cls.__obj = object.__new__(cls)
return cls.__obj

第二次执行时, cls.__obj is None 条件为假 
return cls.__obj

第三次执行时, cls.__obj is None 条件为假 
return cls.__obj

对obj这个成员进行私有化,防止类外进行调用,以更改其本意;
"""
obj = SingleTon()
print(obj)
obj = SingleTon()
print(obj)
obj = SingleTon()
print(obj)

# 注意点:因为单态模式的存在,无论实例化几次,所指代的是同一个对象;
class SingleTon():
	__obj = None
	def __new__(cls,*args,**kwargs):
		# 类.属性
		if cls.__obj is None:
			cls.__obj = object.__new__(cls)
		return cls.__obj
		
	def __init__(self,name):
		self.name  = name

"""
第一次实例化对象时,创建了一个对象存放__obj私有成员中
第二次实例化对象时,因为 cls.__obj is None不符合,直接返回了上一个对象
两个对象是一样的,只不过用不同的两个变量指向该对象而已.

第一次name为卢喜彤 ,第二次name为刘硬 ,内存中存储的是刘硬 , 
所以打印两次都是刘硬
"""

obj1 = SingleTon("卢喜彤")
obj2 = SingleTon("刘硬")

print(id(obj1) , id(obj2))

print(obj1.name)   #刘硬
print(obj2.name)   #刘硬

```

### 📖 要点讲解

- ### 单态模式 : 一个类无论实例化多少次,都有且只有一个对象

- 注意点:因为单态模式的存在,无论实例化几次,所指代的是同一个对象;

---

## 11. 10.__str__repr__.py

### 📋 运行结果

```

小猫名字是汤姆,它的天赋是卖萌
小猫名字是汤姆,它的天赋是卖萌
老鼠的名字杰瑞,老鼠的天赋是龙生龙凤生凤,老鼠的儿子会打洞

```

### 💻 完整代码

```python

#__str__ 魔术方法
'''
	触发时机: 使用print(对象)或者str(对象)的时候触发
	功能:     查看对象相应说明
	参数:     一个self接受当前对象
	返回值:   必须返回字符串类型
'''

class Cat():
	gift = "卖萌"
	def __init__(self,name):
		self.name = name
	
	def __str__(self):
		return self.cat_info()

	def cat_info(self):
		return "小猫名字是{},它的天赋是{}".format(self.name,self.gift)
	
	__repr__ = __str__
	
tom = Cat("汤姆")
# (1) print(对象)时 , 自动触发__str__魔术方法
# print(tom)
# (2 )str(对象)的时候触发
res = str(tom)
print(res)

# 如果__repr__ = __str__ 添加操作 通过repr也可以触发
print(repr(tom))

#__repr__ 魔术方法
'''
	触发时机: 使用repr(对象)的时候触发
	功能:     查看对象,与魔术方法__str__相似
	参数:     一个self接受当前对象
	返回值:   必须返回字符串类型
'''

class Mouse():
	gift = "打洞"
	def __init__(self,name):
		self.name = name
		
	def __repr__(self):
		return self.mouse_info()
		
	def mouse_info(self):
		return "老鼠的名字{},老鼠的天赋是龙生龙凤生凤,老鼠的儿子会{}".format(self.name,self.gift)
	
	# 把方法看成函数,是变量的赋值操作
	"""
	def __func__():
		pass
	def __func12__():
		pass
	__func12__ = __func__
	# 因为底层写了一句话  __str__ = __repr__
	# __str__ = __repr__
	"""

jerry = Mouse("杰瑞")
# repr在强转对象时,自动触发__repr__方法
# res = repr(jerry)
# print(res , type(res))

# 在print 或者 str强转对象时候, 也可以触发__repr__ 魔术方法

# print(jerry)
res = str(jerry)
print(res)

```

### 📖 要点讲解

- (1) print(对象)时 , 自动触发__str__魔术方法

- 如果__repr__ = __str__ 添加操作 通过repr也可以触发

- 因为底层写了一句话  __str__ = __repr__

- repr在强转对象时,自动触发__repr__方法

- print(res , type(res))

- 在print 或者 str强转对象时候, 也可以触发__repr__ 魔术方法

---

## 12. 11.__bool__add_len.py

### 📋 运行结果

```

False
130
6
11
6

```

### 💻 完整代码

```python

# ### __bool__ 魔术方法
'''
	触发时机：使用bool(对象)的时候自动触发
	功能：强转对象
	参数：一个self接受当前对象
	返回值：必须是布尔类型
'''

class MyClass():
	def __bool__(self):
		return False
	
obj = MyClass()
# 强转对象时自动触发
print(bool(obj))

# ### __add__ 魔术方法  (与之相关的__radd__ 反向加法)
'''
	触发时机：使用对象进行运算相加的时候自动触发
	功能：对象运算
	参数：二个对象参数
	返回值：运算后的值
'''

class MyClass():
	def __init__(self,num):
		self.num = num
	
	# 对象在+号的左侧时,自动触发
	'''self接收的是对象,other接收的是+号右侧的部分'''
	def __add__(self,other):
		return self.num * 2 + other
		
	# 对象在+号的右侧时,自动触发
	"""self接收的是对象,other接收的是+号左侧的部分"""
	def __radd__(self,other):
		return self.num * 3  - other

# 第一种情况	
a = MyClass(5)
print(a + 120)
	
# 第二种情况
b = MyClass(7)
print(15 + b)

# 第三种情况
res = a+b
print(res)

"""
第一次
res = a+b    先触发__add__ self => a  other => b
return a.num * 2 + b => 10 + b
res = 10 + b

第二次
res = 10+b   后触发__radd__ self=>b other=>10
return b.num*3-10  =>7 * 3 - 10 => 11
res = 11
"""

# ### __len__ 魔术方法
'''
	触发时机：使用len(对象)的时候自动触发 
	功能：用于检测对象中或者类中某个内容的个数
	参数：一个self接受当前对象
	返回值：必须返回整型
'''
# 当len(对象)时,计算类中的自定义成员个数.
class MyClass():
	pty1 = 1
	pty2 = 2
	__pty3 = 3
	
	def func1():
		pass
	def func2():
		pass
	def __func3():
		pass

	def __len__(self):
		# 方法一
		"""
		lst = []
		for i in MyClass.__dict__:
			if not (i.startswith("__") and i.endswith("__")):
				lst.append(i)
				
		return len(lst)
		"""	
		# 方法二
		return len([  i for i in  MyClass.__dict__ if not (i.startswith("__") and i.endswith("__")) ])
		
obj = MyClass()
print(len(obj))

"""
{
'__module__': '__main__', 
'pty1': 1, 
'pty2': 2, 
'_MyClass__pty3': 3, 
'func1': <function MyClass.func1 at 0x000001536CD94B70>, 
'func2': <function MyClass.func2 at 0x000001536CD94BF8>, 
'_MyClass__func3': <function MyClass.__func3 at 0x000001536CD94C80>, 
'__len__': <function MyClass.__len__ at 0x000001536CD94D08>, 
'__dict__': <attribute '__dict__' of 'MyClass' objects>, 
'__weakref__': <attribute '__weakref__' of 'MyClass' objects>, 
'__doc__': None
}
"""

```

### 📖 要点讲解

- ### __add__ 魔术方法  (与之相关的__radd__ 反向加法)

- 当len(对象)时,计算类中的自定义成员个数.

---

## 13. 12.__call__.py

### 📋 运行结果

```

call方法被触发了
~~~~模拟洗澡~~~~
第一步,脱衣服裤子鞋子
第二步,整点沐浴露,冲一冲
第三步,擦一擦出来晾干
done
0
-3
3
-1123332 <==============>
0 <==============>
0 <========`11======>
1233 <========`22======>
抱歉不能转换 <========`22======>
3
23332
1123332
1123332
-1123332
0

```

### 💻 完整代码

```python

# ### __call__ 魔术方法
'''
	触发时机：把对象当作函数调用的时候自动触发
	功能: 模拟函数化操作
	参数: 参数不固定,至少一个self参数
	返回值: 看需求
'''

# (1)基本使用
class MyClass():
	''''''
	def __call__(self):
		print("call方法被触发了")
	
# 把对象当作函数调用的时候自动触发
obj = MyClass()
obj()

# (2)模拟函数化操作
"""使用call方法做统一调用"""
class Wash():
	def __call__(self,something):
		print("~~~~模拟{}~~~~".format(something))
		self.step1()
		self.step2()
		self.step3()
		return "done"
		
	def step1(self):
		print("第一步,脱衣服裤子鞋子")
		
	def step2(self):
		print("第二步,整点沐浴露,冲一冲")

	def step3(self):
		print("第三步,擦一擦出来晾干")
		
obj = Wash()
# 方法一
"""
obj.step1()
obj.step2()
obj.step3()
"""
# 方法二
res = obj("洗澡")
print(res)
# (3)自定义myint来模拟int强转操作
""" bool int float 纯数字字符串"""
class MyInt():
	def __call__(self,num):
		# bool
		if isinstance(num,bool):
			if num == True:
				return 1
			else:
				return 0
			return num
			
		# int
		elif isinstance(num,int):
			return num
			
		# float
		elif isinstance(num,float):
			
			# 方法一
			"""
			num = -3.14
			res = str(-3.14).split(".")[0]
			print(res, type(res))
			res2 = eval(res)
			print(res2,type(res2))
			"""
			# 方法二
			import math
			"""
			num = 3.14
			if num >=0:
				res = math.floor(3.89)
			else:
				res = math.ceil(-3.89)
			print(res)
			"""
			return math.floor(3.89) if num >=0 else math.ceil(-3.89)
			
		# str
		elif isinstance(num,str):
			# +00000000000001123332  -00000000000001123332
			if (num[0] == "+" or num[0] == "-" ) and num[1:].isdecimal():

				if num[0] == "+":
					sign = 1
				else:
					sign = -1
					
				return self.calc(num[1:],sign)
				
			#00000000000001123332
			elif num.isdecimal():
				return self.calc(num)
			# 不能计算的情况
			else:
				return  "抱歉不能转换"

	def calc(self,strnum,sign=1):
		strnum = strnum.lstrip("0")
		# 排除全都是0的情况
		if strnum == "":
			return 0
		# 100 * 1 => 100 |  100 * -1 = -100
		return eval(strnum) * sign
		"""
		00000000000001123332
		1
		00000000000001123332
		-1
		"""
						
myint = MyInt()
print(myint(0))
print(myint(-3.145))
print(myint(3.145))
print(myint("-00000000000001123332"),"<==============>")
print(myint("-0000000000000000000"),"<==============>")
print(myint("0000000000000000000"),"<========`11======>")
print(myint("00000000000000001233"),"<========`22======>")
print(myint("abc"),"<========`22======>")
print(int(3.14))
# print(int("abc")) error

print(int("23332"))
print(int("00000000000001123332"))
print(int("+00000000000001123332"))
print(int("-00000000000001123332"))
print(int("-0000000000000000000"))
# eval("")
# strnum = "0000000000000000".lstrip("0")
# print(repr(strnum))

```

### 📖 要点讲解

- (3)自定义myint来模拟int强转操作

- +00000000000001123332  -00000000000001123332

- 100 * 1 => 100 |  100 * -1 = -100

- print(int("abc")) error

- strnum = "0000000000000000".lstrip("0")

---

## 14. 13.math.py

### 📋 运行结果

```

-4
-5
3.0
3.141592653589793

```

### 💻 完整代码

```python

import math
#ceil()  向上取整操作 (对比内置round)
res = math.ceil(3.045)
res = math.ceil(-4.56)
print(res)

#floor() 向下取整操作 (对比内置round)
res = math.floor(4.99999999)
res = math.floor(-4.001)
print(res)

#sqrt() 开平方运算(结果浮点数)
res = math.sqrt(9)
print(res)

#圆周率常数 pi
res = math.pi
print(res)

```

### 📖 要点讲解

- ceil()  向上取整操作 (对比内置round)

- floor() 向下取整操作 (对比内置round)

---

## 15. 14.装饰器.py

### 📋 运行结果

```

厕所前,蓬头垢面
我是帅哥一枚
厕所后,干净整齐
<===================>
厕所前,蓬头垢面
我是靓女一枚
厕所后,干净整齐
<===================>
厕所前,饥肠辘辘3
厕所前,蓬头垢面1
我是靓女一枚5
厕所后,干净整齐2
厕所后,酒足饭饱4
<===================>
厕所前,文静雅观
吕文康在鸟窝,拉屎
厕所后,斯文败类
<===================>
厕所前,文质彬彬
解手的场所 水里
解手的场所 电影院
厕所后,龇牙咧嘴
['李辉拉了100顿', '吕文康拉了100斤', '赵强拉了10克']

```

### 💻 完整代码

```python

# ### 装饰器
"""
概念:在不改变原有代码的前提下,为原函数扩展新功能的一种语法
语法: @ (语法糖) 
"""

# (1) 装饰器原型
def kuozhan(func):
	def newfunc():
		print("厕所前,蓬头垢面")
		func() # myfunc()
		print("厕所后,干净整齐")
	return newfunc

def myfunc():
	print("我是帅哥一枚")

# 形参func 接收实参 myfunc 返回 newfunc => myfunc = newfunc
myfunc = kuozhan(myfunc)
myfunc() #  myfunc() <=> newfunc()
"""
		print("厕所前,蓬头垢面")
		func()
		print("厕所后,干净整齐")
"""

# (2) 使用@号简化操作
print("<===================>")
"""
@符的两个作用:
	(1) 可以把下面被装饰的函数当成参数自动传递给装饰器
	(2) 将返回的新函数 赋值给 旧函数 ,实现替换效果,从而扩展新功能
"""
def kuozhan(func):
	def newfunc():
		print("厕所前,蓬头垢面")
		func()
		print("厕所后,干净整齐")
	return newfunc

@kuozhan
def myfunc():
	print("我是靓女一枚")

myfunc()
print("<===================>")
# (3) 装饰器的嵌套
def kuozhan1(func):
	def newfunc():
		print("厕所前,蓬头垢面1")
		func()
		print("厕所后,干净整齐2")
	return newfunc

def kuozhan2(func):
	def newfunc():
		print("厕所前,饥肠辘辘3")
		func()
		print("厕所后,酒足饭饱4")
	return newfunc	

@kuozhan2
@kuozhan1
def myfunc():
	print("我是靓女一枚5")

myfunc()

# 13524
# 314152
# 31524
# 13524
# 354152
# 13542

print("<===================>")
# (4) 带有参数的装饰器
"""原函数如果有参数,装饰之后也应该有参数,保持一致"""
def kuozhan(func):
	def newfunc(who,where):
		print("厕所前,文静雅观")
		func(who,where)
		print("厕所后,斯文败类")
	return newfunc
	
@kuozhan
def myfunc(who,where):
	print("{}在{},拉屎".format(who,where))

# myfunc("吕文康","鸟窝") <=>  newfunc("吕文康","鸟窝")
myfunc("吕文康","鸟窝")

print("<===================>")
# (5) 带有参数返回值的装饰器
"""
* 和 ** 在定义处是负责打包 
* 和 ** 在调用处是负责解包
原函数有返回值, 新函数就有返回值,保持一致
"""
def kuozhan(func):
	def newfunc(*args,**kwargs): # 定义处
		print("厕所前,文质彬彬")
		res = func(*args,**kwargs) # 调用处
		print("厕所后,龇牙咧嘴")
		return res
	return newfunc

@kuozhan
def myfunc(*args,**kwargs):
	lst = []
	dic = {"lh":"李辉","lwk":"吕文康","zhaoqiang":"赵强"}
	# 遍历拉屎的场所
	for i in args:
		print("解手的场所",i)
	# print(kwargs)
	
	# 拼凑拉屎的人员
	for k,v in kwargs.items():
		# print(k,v)
		if k in dic:
			strvar = dic[k] + "拉了" + v
			lst.append(strvar)
			
	# 返回拉屎的列表
	return lst
	
res = myfunc("水里","电影院",lh="100顿",lwk="100斤",zhaoqiang="10克")
print(res)

```

### 📖 要点讲解

- 形参func 接收实参 myfunc 返回 newfunc => myfunc = newfunc

- myfunc("吕文康","鸟窝") <=>  newfunc("吕文康","鸟窝")

---

## 🖼️ 参考资料

![新式类3.x_广度优先.png](./assets/新式类3.x_广度优先.png)

![经典类2.x_深度优先.png](./assets/经典类2.x_深度优先.png)

![菱形继承.png](./assets/菱形继承.png)

![课堂图解.png](./assets/课堂图解.png)
