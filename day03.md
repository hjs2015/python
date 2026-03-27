# Day 3: day03 字符串操作格式化 字符串的相关函数 列表的相关操作 列表的相关函数 集合字典相关操作函数 文件操作 文件的扩展模式

> 对应原课程：day03_字符串操作格式化_字符串的相关函数_列表的相关操作_列表的相关函数_集合字典相关操作函数_文件操作_文件的扩展模式

---

## 1. 1.字符串的相关操作.py

### 📋 运行结果

```

今天的天气,真不错
今天的天气,真不错
重要的事情说三遍重要的事情说三遍重要的事情说三遍
sfsdfsdfsdfsdfsdfsdafasdfsadfsadfsadfsadfasdf3453453452345
来
眼睛,但我却用它翻白眼
黑夜给我了黑色的
眼睛
黑我色睛我它眼
眼白翻它用却我但,睛眼的色黑了我给夜黑
黑夜给我了黑色的眼睛,但我却用它翻白眼

```

### 💻 完整代码

```python

# ### 字符串的相关操作
# (1)字符串的拼接 +
str1 = "今天的天气,"
str2 = "真不错"
strvar = str1 + str2
print(strvar )
str1 += str2 # str1 = str1 + str2
print(str1)

# (2)字符串的重复 *
strvar = "重要的事情说三遍"
res = strvar * 3
print(res)

# (3)字符串跨行拼接 \
strvar = "sfsdfsdfsdfsdfsdfsdafasdfsadfsadfsadfsadfasdf" \
"3453453452345"
print(strvar)

# (4)字符串的索引
#         0  1 2 3 4 5 6 7
strvar = "今天有新同学要来"
#         -8-7-6-5-4-3-2-1         
res = strvar[2]
res = strvar[-1]
print(res)

# (5)字符串的切片:(截取)
"""
语法 => 字符串[::]  完整格式：[开始索引:结束索引:间隔值]
	(1)[开始索引:]  从开始索引截取到字符串的最后
	(2)[:结束索引]  从开头截取到结束索引之前(结束索引-1)
	(3)[开始索引:结束索引]  从开始索引截取到结束索引之前(结束索引-1)
	(4)[开始索引:结束索引:间隔值]  从开始索引截取到结束索引之前按照指定的间隔截取字符
	(5)[:]或[::]  截取所有字符串
"""
strvar = "黑夜给我了黑色的眼睛,但我却用它翻白眼"
# (1)[开始索引:]  从开始索引截取到字符串的最后
res = strvar[8:]
print(res)
# (2)[:结束索引]  从开头截取到结束索引之前(结束索引-1)
res = strvar[:8]
print(res)
# (3)[开始索引:结束索引]  从开始索引截取到结束索引之前(结束索引-1)
res = strvar[8:10]
print(res)
# (4)[开始索引:结束索引:间隔值]  从开始索引截取到结束索引之前按照指定的间隔截取字符
# 正向截取
res = strvar[::3] # 0 3 6 9 12 ....
print(res)

# 逆向截取
res = strvar[::-1] #-1 -2 -3 -4 -5 ...
print(res)

# (5)[:]或[::]  截取所有字符串
res = strvar[:]
res = strvar[::]
print(res)

```

### 📖 要点讲解

- (1)[开始索引:]  从开始索引截取到字符串的最后

- (2)[:结束索引]  从开头截取到结束索引之前(结束索引-1)

- (3)[开始索引:结束索引]  从开始索引截取到结束索引之前(结束索引-1)

- (4)[开始索引:结束索引:间隔值]  从开始索引截取到结束索引之前按照指定的间隔截取字符

---

## 2. 2.format 格式化语法.py

### 📋 运行结果

```

陈勇给卢潼汐一个大大的拥抱
卢潼汐给陈勇一个大大的拥抱
陈勇给卢潼汐一个大大的拥抱
杨贵峰给张俊文一个飞吻,鼻血直冒3万多尺,喷血而亡

```

### 💻 完整代码

```python

# ###  format 格式化语法
"""
(1)顺序传参
(2)索引传参
(3)关键字传参
(4)容器类型数据(列表或元祖)传参
"""

# (1)顺序传参
strvar = "{}给{}一个大大的拥抱".format("陈勇","卢潼汐")
print(strvar)

# (2)索引传参
strvar = "{1}给{0}一个大大的拥抱".format("陈勇","卢潼汐")
print(strvar)

# (3)关键字传参
strvar = "{who1}给{who2}一个大大的拥抱".format(who1 = "陈勇",who2 = "卢潼汐")
print(strvar)

# (4)容器类型数据
strvar = "{0[0]}给{1[0]}一个飞吻,鼻血直冒3万多尺,喷血而亡".format(["黄启新","微微","张俊文"],("苏业清","刘硬","冯双喜"))
strvar = "{group2[1]}给{group1[1]}一个飞吻,鼻血直冒3万多尺,喷血而亡".format(group1=["黄启新","微微","张俊文"],group2=("苏业清","刘硬","冯双喜"))
strvar = "{group2[gf]}给{group1[2]}一个飞吻,鼻血直冒3万多尺,喷血而亡".format(group1=["黄启新","微微","张俊文"],group2={"syq":"苏叶青","gf":"杨贵峰"})
# (1)在format格式化语法中,获取字典的键不需要加上引号, (2) 不要使用逆向下标在格式化字符串中
# strvar = "{group2['gf']}给{group1[-1]}一个飞吻,鼻血直冒3万多尺,喷血而亡".format(group1=["黄启新","微微","张俊文"],group2={"syq":"苏叶青","gf":"杨贵峰"})
print(strvar)

```

### 📖 要点讲解

- (1)在format格式化语法中,获取字典的键不需要加上引号, (2) 不要使用逆向下标在格式化字符串中

- strvar = "{group2['gf']}给{group1[-1]}一个飞吻,鼻血直冒3万多尺,喷血而亡".format(group1=["黄启新","微微","张俊文"],group2={"syq":"苏叶青","gf":"杨贵峰"})

---

## 3. 3.format的填充符号的使用.py

### 📋 运行结果

```

***吕文康****在>>>>>>>电影院拉屎!!!!!!!!
李辉一个月的工资是20000元
李辉一个月的工资是20000元
2*4=8 
2*4= 8 
目前美国新冠疫情感染比例是%98.100000
目前美国新冠疫情感染比例是%98.20
你好帅
123,456,789

```

### 💻 完整代码

```python

# ### (5)format的填充符号的使用( ^ > < )
"""
^ 原字符串居中
> 原字符串居右
< 原字符串居左

{who:*^10}
who : 关键字
*   : 填充字符
^   : 填充的方向
10  : 填充的长度
总长度(10) = 原字符串长度 + 填充符号的长度
"""
strvar = "{who:*^10}在{where:>>10}{do:!<10}".format(who="吕文康",where="电影院",do="拉屎")
print(strvar)

# ### (6)进制转换等特殊符号的使用( :d :f :s :, )
# :d 整型占位符 要求类型必须是整型,不会自动强转.
# strvar = "李辉一个月的工资是{:d}元".format(20000.58) error
strvar = "李辉一个月的工资是{:d}元".format(20000)
print(strvar)

# 系统会自动进行强转
strvar = "李辉一个月的工资是%d元" % (20000.58)
print(strvar)

# :2d 整型占位符 (占两位) 原字符串默认居右
strvar = "{:d}*{:d}={:<2d}".format(2,4,8)
print(strvar)
strvar = "{:d}*{:d}={:^3d}".format(2,4,8)
print(strvar)

# :f 浮点型占位符
strvar = "目前美国新冠疫情感染比例是%{:f}".format(98.1) # (默认小数部分保留6位)
print(strvar)
# :.2f 小数保留2位 (存在四舍五入的情况)
strvar = "目前美国新冠疫情感染比例是%{:.2f}".format(98.199)
print(strvar)

# :s 字符串占位符
strvar = "{:s}".format("你好帅")
print(strvar)

# :, 金钱占位符
strvar = "{:,}".format(123456789)
print(strvar)

```

### 📖 要点讲解

- ### (5)format的填充符号的使用( ^ > < )

- ### (6)进制转换等特殊符号的使用( :d :f :s :, )

- :d 整型占位符 要求类型必须是整型,不会自动强转.

- strvar = "李辉一个月的工资是{:d}元".format(20000.58) error

- :2d 整型占位符 (占两位) 原字符串默认居右

- :.2f 小数保留2位 (存在四舍五入的情况)

---

## 4. 4.字符串的相关方法.py

### 📋 运行结果

```

I am a boy
You Are Beautiful
YOU ARE BEAUTIFUL
you are beautiful
yOU aRE bEAUTIFUL
0
-1
21
True
True
['you', 'can', 'you@up@no@can@no@bb']
you can you up no can no bb
大风车呀,跑呀转呀转呀,今天的节目真好看
True
True
15
@@@刘德华@@@@
<==============>
    刘德华   
刘德华
刘德华 <----->
   刘德华
刘德华   

```

### 💻 完整代码

```python

# ### 字符串的相关方法
# *capitalize 字符串首字母大写 
strvar = "i am a boy"
# strvar = "我是一个男孩ooo" # 对于中文特殊字符无效
res = strvar.capitalize()
print(res)

# *title 每个单词的首字母大写 (非字母隔开的单词)
strvar = "you are beautiful"
res = strvar.title()
print(res)

# *upper 将所有字母变成大写
strvar = "you are beautiful"
res = strvar.upper()
print(res)
# *lower 将所有字母变成小写 
res = strvar.lower()
print(res)

# *swapcase 大小写互换  
strvar = "You Are Beautiful"
res = strvar.swapcase()
print(res)

# *count 统计字符串中某个元素的数量 
strvar = "我好喜欢你哦哦哦哦哦"
res = strvar.count("哦")
# strvar.count(val,start,end) # end最大值取不到,取到它之前的元素
res = strvar.count("哦",1,5) # 1 2 3 4
print(res)

# *find 查找某个字符串第一次出现的索引位置  (推荐)
'''strvar.find(val,start,end) '''
strvar= "oh Father this is my favorate girl"
res = strvar.find("Father") # 3
# 区分大小写,从4这个索引下标开始寻找
res = strvar.find("f",4) # 从4开始找,一直到最后 => 21
# 当找不到对应字符的时候,返回的是-1
res = strvar.find("f",4,20) # 4~19  => -1
print(res)

# *index 与 find 功能相同 find找不到返回-1,index找不到数据直接报错 (了解)
res = strvar.index("f",4)
# res = strvar.index("f",4,20) 直接报错
print(res)

# *startswith 判断是否以某个字符或字符串为开头 
'''strvar.startswith(val,start,end) '''
strvar= "oh Father this is my favorate girl"
res = strvar.startswith("oh")
res = strvar.startswith("this",10)
res = strvar.startswith("this",10,14) # 10 11 12 13
print(res)

# *endswith 判断是否以某个字符或字符串结尾
res = strvar.endswith("girl")
res = strvar.endswith("rate",-9,-5) # -9 -8 -7 -6
print(res)

# 重要 ***
# *split 按某字符将字符串分割成列表(默认字符是空格)
strvar = "you can you up no can no bb"
lst = strvar.split()
strvar = "you@can@you@up@no@can@no@bb"
lst = strvar.split("@")
# 第二个参数值=>切割的次数
lst = strvar.split("@",2)
print(lst)

# *join  按某字符将列表拼接成字符串(容器类型都可)
lst = ['you', 'can', 'you', 'up', 'no', 'can', 'no', 'bb']
strvar = " ".join(lst)
print(strvar)

# *replace 替换字符串(可选择替换的次数)
'''replace("被替换的字符串","要替换的字符串","替换的次数")'''
strvar = "大风车呀,转呀转呀转呀,今天的节目真好看"
strvar1 = strvar.replace("转呀","跑呀")
strvar2 = strvar.replace("转呀","跑呀",1)
print(strvar2)

# *isdecimal 检测字符串是否以数字组成  必须是纯数字
strvar = "13424sasdf"
strvar = "1342423423423"
res = strvar.isdecimal()
print(res)

#isspace   判断字符串是否由空白符组成
strvar = "     						\n\t"
res = strvar.isspace()
print(res)

strvar = "我爱你,你爱我么?我爱你个锤子"
res = len(strvar)
print(res)

# *center 填充字符串,原字符居中 (默认填充空格)
strvar = "刘德华"
# 10代表的是总长度 = 填充符号的长度 + 原字符串的长度
res = strvar.center(10) # 默认填充空格
res = strvar.center(10,"@")
print(res)

# *strip  默认去掉首尾两边的空白符 
"""场景:在数据存储时,要先把两边的空白符去掉在存储."""
print("<==============>")
strvar = "    刘德华   "
print(strvar)
res = strvar.strip()
print(res)

strvar = " @@@刘德华###"
res = strvar.strip(" @#")
print(res,"<----->")

# rstrip 去掉右边的空白符
strvar = "   刘德华   "
strvar1 = strvar.rstrip()
print(strvar1)
# lstrip 去掉左边的空白符
strvar = "   刘德华   "
strvar2 = strvar.lstrip()
print(strvar2)

```

### 📖 要点讲解

- strvar = "我是一个男孩ooo" # 对于中文特殊字符无效

- *title 每个单词的首字母大写 (非字母隔开的单词)

- strvar.count(val,start,end) # end最大值取不到,取到它之前的元素

- *find 查找某个字符串第一次出现的索引位置  (推荐)

- *index 与 find 功能相同 find找不到返回-1,index找不到数据直接报错 (了解)

- res = strvar.index("f",4,20) 直接报错

- *startswith 判断是否以某个字符或字符串为开头

- *endswith 判断是否以某个字符或字符串结尾

- *split 按某字符将字符串分割成列表(默认字符是空格)

- *join  按某字符将列表拼接成字符串(容器类型都可)

- *replace 替换字符串(可选择替换的次数)

- *isdecimal 检测字符串是否以数字组成  必须是纯数字

- isspace   判断字符串是否由空白符组成

- *center 填充字符串,原字符居中 (默认填充空格)

- 10代表的是总长度 = 填充符号的长度 + 原字符串的长度

---

## 5. 5.列表的相关操作.py

### 📋 运行结果

```

['奉双喜', '赵强', '吕文康', '刘重祥', '黄金生', '李辉']
['奉双喜', '赵强', '吕文康', '奉双喜', '赵强', '吕文康', '奉双喜', '赵强', '吕文康']
['何仙姑', '蓝采和', '曹国舅', '王文', '汉钟离']
['铁拐李', '张果老', '吕公滨', '何仙姑', '蓝采和', '曹国舅']
['曹国舅', '王文']
['王文', '曹国舅', '蓝采和', '何仙姑', '吕公滨']
['蓝采和', '王文']
['铁拐李', '张果老', '吕公滨', '何仙姑', '蓝采和', '曹国舅', '王文', '汉钟离']
李辉
['马成龙', '黄金生', '李辉']
['铁拐李', '张果老', 'a', 'b', 'c', 'd', '曹国舅', '王文', '汉钟离']
['是宋亚', '张果老', '吕公滨', '魏玮', '蓝采和', '曹国舅', '炉筒溪', '汉钟离']
['铁拐李', '张果老', '吕公滨', '何仙姑', '蓝采和', '曹国舅', '王文', '汉钟离']

```

### 💻 完整代码

```python

# ### 列表的相关操作
# (1)列表的拼接   (同元组) *
lst1 = ["奉双喜","赵强","吕文康"]
lst2 = ["刘重祥","黄金生","李辉"]
lst = lst1 + lst2
print(lst)

# (2)列表的重复   (同元组) *
lst1 = ["奉双喜","赵强","吕文康"]
lst = lst1 * 3
print(lst)

# (3)列表的切片   (同元组)
# 语法 => 列表[::]  完整格式：[开始索引:结束索引:间隔值]	
	
lst = ["铁拐李","张果老","吕公滨","何仙姑","蓝采和","曹国舅","王文","汉钟离"]
# (1)[开始索引:]  从开始索引截取到列表的最后
res = lst[3:]
print(res)
# (2)[:结束索引]  从开头截取到结束索引之前(结束索引-1)
res = lst[:6] # 0 1 2 3 4 5 
print(res)

# (3)[开始索引:结束索引]  从开始索引截取到结束索引之前(结束索引-1)
res = lst[-3:-1] # -3 -2 
print(res)

# (4)[开始索引:结束索引:间隔值]  从开始索引截取到结束索引之前按照指定的间隔截取列表元素值
# 从右向左截取
res = lst[-2:-7:-1] #-2 -3 -4 -5 -6 
print(res)

# 从左向右截取
res = lst[-4:-1:2] #-4 -2 
print(res)

# (5)[:]或[::]  截取所有列表
res = lst[:]
res = lst[::]
print(res)

# (4)列表的获取   (同元组)
#         0        1        2  
lst = ["刘重祥","黄金生","李辉"]
#         -3      -2        -1
res = lst[-1]
res = lst[2]
print(res)

# (5)列表的修改   ( 可切片 )
# 一次改一个
lst = ["刘重祥","黄金生","李辉"]
lst[0] = "马成龙"
print(lst)

# 一次改一堆 
"""切片赋值时,必须是可迭代性的数据(容器类型数据,range对象,迭代器)  """
lst = ["铁拐李","张果老","吕公滨","何仙姑","蓝采和","曹国舅","王文","汉钟离"]
# 在用切片修改值的时候,先把值找到,然后删掉,把替换的值一个个的放到被切出的元素位置.
lst[2:5] = [1,2,3,4] # 2 3 4 
lst[2:6] = "abcd"
print(lst)

# 如何切片时,使用了步长,那么切多少,改多少
lst = ["铁拐李","张果老","吕公滨","何仙姑","蓝采和","曹国舅","王文","汉钟离"]
lst[::3] = ("是宋亚","魏玮","炉筒溪") # 0 3 6  铁拐李 何仙姑 王文
print(lst)

# (6)列表的删除   ( 可切片 )
lst = ["铁拐李","张果老","吕公滨","何仙姑","蓝采和","曹国舅","王文","汉钟离"]
# 删除单个
# del lst[0]
# print(lst)

# 删除多个
# del lst[2:6] # 2 3 4 5
# print(lst)
res = lst[0]
# 删除的是res变量和列表无关.
del res
print(lst)

```

### 📖 要点讲解

- 语法 => 列表[::]  完整格式：[开始索引:结束索引:间隔值]

- (1)[开始索引:]  从开始索引截取到列表的最后

- (2)[:结束索引]  从开头截取到结束索引之前(结束索引-1)

- (3)[开始索引:结束索引]  从开始索引截取到结束索引之前(结束索引-1)

- (4)[开始索引:结束索引:间隔值]  从开始索引截取到结束索引之前按照指定的间隔截取列表元素值

- 在用切片修改值的时候,先把值找到,然后删掉,把替换的值一个个的放到被切出的元素位置.

- 如何切片时,使用了步长,那么切多少,改多少

- del lst[2:6] # 2 3 4 5

---

## 6. 6.列表的相关函数.py

### 📋 运行结果

```

['石松亚', '黄奇鑫', '魏玮', '陈勇']
['石松亚', '黄奇鑫', '张俊文', '魏玮']
['石松亚', '黄奇鑫', '魏玮', 1, 2, 3, 'a', 'b']
魏玮
['石松亚', '黄奇鑫']
石松亚
['黄奇鑫']
['石松亚', '黄奇鑫', '苏叶青', '魏玮', '苏叶青']
[]
2
3
[-99, -3, -1, 0, 22, 100]
[100, 22, 0, -1, -3, -99]
['王闻', '黄启新']
['jordon', 'james', 'yaoming', 'kobi']

```

### 💻 完整代码

```python

# ### 列表的相关函数
# 增
lst = ["石松亚","黄奇鑫","魏玮"]
# append 向列表的末尾添加新的元素
lst.append("陈勇")
print(lst)

# insert 在指定索引之前插入元素
lst = ["石松亚","黄奇鑫","魏玮"]
lst.insert(-1,"张俊文")
print(lst)

# extend 迭代追加所有元素
lst = ["石松亚","黄奇鑫","魏玮"]
lst2 = [1,2,3]
dic= {"a":1,"b":2}
# 迭代追加,把里面的元素一个一个拿出来,插入到列表中
lst.extend(lst2)
# 如果迭代追加的是字典,那么追加的字典的键
lst.extend(dic)
print(lst)

#删
lst = ["石松亚","黄奇鑫","魏玮"]
# pop 通过指定索引删除元素,若没有索引移除最后那个

# 默认删除(最后一个)
res = lst.pop()
print(res)
print(lst)
# 指定删除(下标)
res2 = lst.pop(0)
print(res2)
print(lst)

lst = ["石松亚","苏叶青","黄奇鑫","苏叶青","魏玮","苏叶青"]
# remove 通过给予的值来删除,如果多个相同元素,默认删除第一个
lst.remove("苏叶青") # 默认删除第一个
print(lst)

# clear 清空列表
lst.clear()
print(lst)

#改查 参考5.py

# 列表的其他操作
# index 获取某个值在列表中的索引
lst = ["石松亚","苏叶青","黄奇鑫"]
res = lst.index("黄奇鑫")
print(res)

# 如果找不到对应的元素,直接报错
# lst.index("abc") error

# count 计算某个元素出现的次数
lst = ["石松亚","苏叶青","黄奇鑫","苏叶青","魏玮","苏叶青"]
res = lst.count("苏叶青") # 只能是一个参数
print(res)

# sort 列表排序 (默认小到大排序) 基于原来的列表排序
lst = [-99,100,-3,-1,0,22]
lst.sort()
print(lst)

# reverse=True 从大到小排序
lst.sort(reverse=True)
print(lst)

# 可以对字母进行排序
"""按照ascii编码排序 字母一位一位的进行比较"""
lst = ["kobi","yaoming","james","jordon"]
lst.sort()

# 可以对中文进行排序么? 可以[排序] ,但是无规律可循;
lst = ["王闻","黄启新"] 
lst.sort()
print(lst)

# reverse 列表反转操作
lst = ["kobi","yaoming","james","jordon"]
lst.reverse()
print(lst)

```

### 📖 要点讲解

- 迭代追加,把里面的元素一个一个拿出来,插入到列表中

- pop 通过指定索引删除元素,若没有索引移除最后那个

- remove 通过给予的值来删除,如果多个相同元素,默认删除第一个

- lst.index("abc") error

- sort 列表排序 (默认小到大排序) 基于原来的列表排序

- 可以对中文进行排序么? 可以[排序] ,但是无规律可循;

---

## 7. 7.深浅拷贝.py

### 📋 运行结果

```

[1, 2, 3]
[1, 2, 3] <====>
[1, 2, 3, [4, 5, 6, 7], 999]
[1, 2, 3, [4, 5, 6]]

```

### 💻 完整代码

```python

# ### 深浅拷贝
"""
a = 10
b = a
a = 15
print(b)

lst1 = [1,2,3]
lst2 = lst1
lst1.append(4)
print(lst2)
"""

# 浅拷贝
# import引入 copy 模块(文件)
import copy
"""
同名模块下的,同名方法,用点.来调用,调用其中的方法实现效果
copy.copy 浅拷贝
"""
lst1 = [1,2,3]
lst2 = copy.copy(lst1)
lst1.append(5)
print(lst2)

# 方法二
lst1 = [1,2,3]
lst2 = lst1.copy()
lst1.append(5)
print(lst2,"<====>")

# 深拷贝
"""
copy.deepcopy 深拷贝
"""
lst1 = [1,2,3,[4,5,6]]
lst2 = copy.deepcopy(lst1)
lst1[-1].append(7)
lst1.append(999)
print(lst1)
print(lst2)

"""
浅拷贝只拷贝一级容器中的所有元素
深拷贝会复制所有层级的所有元素,都单独开辟空间进行存储;

浅拷贝 : 速度快,空间小
深拷贝 : 速度慢,空间大
"""
"""
tuple 只有两个函数
index 和 count 可以用
"""

```

---

## 8. 8.字典相关的函数.py

### 📋 运行结果

```

{'top': 'the shy', 'middle': 'rookie', 'bottom': 'jacklelove'}
{'top': None, 'middle': None, 'bottom': None}
{'top': [], 'middle': [], 'bottom': []}
{'top': [1], 'middle': [1], 'bottom': [1]}
the shy
{'middle': 'rookie', 'bottom': 'jacklelove'}
字典中没有这个键
<===>
('bottom', 'jacklelove')
{'top': 'the shy', 'middle': 'rookie'}
{}
{'top': 'wangwen', 'middle': 'rookie', 'bottom': 'jacklelove', 'support': '神秘男孩', 'jungle': 'xboyww'}
该键不存在
dict_keys(['ssy', 'hqx', 'ww', 'cy', 'zjw'])
dict_values(['睡觉', '喝酒', '走神', '溜号', '脑子快'])
dict_items([('ssy', '睡觉'), ('hqx', '喝酒'), ('ww', '走神'), ('cy', '溜号'), ('zjw', '脑子快')])
ssy 睡觉
hqx 喝酒
ww 走神
cy 溜号
zjw 脑子快

```

### 💻 完整代码

```python

# ### 字典相关的函数
# 增
# 传统添加键值对 (推荐)
dic = {}
dic["top"] = "the shy"
dic["middle"] = "rookie"
dic["bottom"] = "jacklelove"
print(dic)

#fromkeys()  使用一组键和默认值创建字典
lst = ["top","middle","bottom"] # 把所有键放到列表中
dic = {}.fromkeys(lst,None) # 把列表中的每个键都赋值None进行初始化,形成字典
print(dic) # 快读批量创建字典的键值对

# 注意点
"""字典中的三个键所指向的列表是同一个 , 不推荐"""
dic = {}.fromkeys(lst,[])
print(dic)
dic["top"].append(1)
print(dic)
# 改写
"""
duc["top"] = []
duc["middle"] = []
duc["bottom"] = []
"""

# 删
dic = {'top': 'the shy', 'middle': 'rookie', 'bottom': 'jacklelove'}
#pop()       通过键去删除键值对 (若没有该键可设置默认值,预防报错)
res = dic.pop("top")
print(res)
print(dic)

# 当获取不存在的键时,直接报错
# res = dic.pop("top111222334")
# 可以为不存在的键设置默认值,防止报错
res = dic.pop("top111222334","字典中没有这个键")
print(res)

#popitem()   删除最后一个键值对 
print("<===>")
dic = {'top': 'the shy', 'middle': 'rookie', 'bottom': 'jacklelove'}
res = dic.popitem()
print(res)
print(dic)

#clear()  清空字典
dic.clear()
print(dic)

#改
dic = {'top': 'the shy', 'middle': 'rookie', 'bottom': 'jacklelove'}
# update() 批量更新(有该键就更新,没该键就添加)
dic_new = {"top":"wangwen","support":"神秘男孩","jungle":"xboyww"} 
dic.update(dic_new)
print(dic)

#查
#get()    通过键获取值(若没有该键可设置默认值,预防报错)
# res = dic["top"]
# res = dic["top13224234"] error
# print(res)
# get可以预防报错,返回None
res = dic.get("top")
# 可以为不存在的键,设置默认值以做提示
res = dic.get("top13224234","该键不存在")
print(res)

dic = {"ssy":"睡觉","hqx":"喝酒","ww":"走神","cy":"溜号","zjw":"脑子快"}
#keys()   将字典的键组成新的可迭代对象
res = dic.keys()
print(res)

#values() 将字典中的值组成新的可迭代对象
res = dic.values()
print(res)

#items()  将字典的键值对凑成一个个元组,组成新的可迭代对象 
res = dic.items()
print(res)

for k,v in dic.items():
	print( k,v)

```

### 📖 要点讲解

- fromkeys()  使用一组键和默认值创建字典

- pop()       通过键去删除键值对 (若没有该键可设置默认值,预防报错)

- res = dic.pop("top111222334")

- popitem()   删除最后一个键值对

- update() 批量更新(有该键就更新,没该键就添加)

- get()    通过键获取值(若没有该键可设置默认值,预防报错)

- res = dic["top13224234"] error

- keys()   将字典的键组成新的可迭代对象

- values() 将字典中的值组成新的可迭代对象

- items()  将字典的键值对凑成一个个元组,组成新的可迭代对象

---

## 9. 9.集合的相关操作.py

### 📋 运行结果

```

{'赵忠祥'}
{'赵忠祥'}
{'李宇春', '周杰伦'}
{'李宇春', '周杰伦'}
{'赵忠祥', '这就是街舞', '掏粪男孩', '周杰伦', '李宇春', '易烊千玺'}
{'赵忠祥', '这就是街舞', '掏粪男孩', '周杰伦', '李宇春', '易烊千玺'}
{'这就是街舞', '掏粪男孩', '易烊千玺', '周杰伦', '李宇春'}
{'这就是街舞', '掏粪男孩', '易烊千玺', '周杰伦', '李宇春'}
False <====>
False
True <=====>
True
False
{'唐人街探案3', '姜子牙'}
{'关于摄像头如何安装不被别人发现', '隔壁姐姐家的爱情故事', '论跑路的重要性', '唐人街探案3', '姜子牙'}
set()
唐人街探案3
{'唐人街探案3', '关于摄像头如何安装不被别人发现'}
{'唐人街探案3', '关于摄像头如何安装不被别人发现', '姜子牙'}
frozenset({'b'})

```

### 💻 完整代码

```python

# ### 集合的相关操作
set1 = {"周杰伦","李宇春","赵忠祥"}
set2 = {"易烊千玺","掏粪男孩","这就是街舞","赵忠祥"}
# 交集  intersection
res = set1.intersection(set2)
print(res)

# 简写符号 &
res = set1 & set2
print(res)

# 差集
res = set1.difference(set2)
print(res)

# 简写符号 -
res = set1 - set2
print(res)

#union()  并集 
res = set1.union(set2)
print(res)

# 简写符号 | 
res = set1 | set2
print(res)

# 对称差集 symmetric_difference
res = set1.symmetric_difference(set2)
print(res)

# 简写符号 ^
res = set1 ^ set2
print(res)

set1 = {"周杰伦","李宇春","赵忠祥"}
set2 = {"周杰伦","李宇春"}
#issubset()   判断是否是子集
res = set1.issubset(set2)
print(res,"<====>")

# 简写符号 <
res = set1 <= set2
print(res)

#issuperset() 判断是否是父集
res = set1.issuperset(set2)
print(res,"<=====>")
res = set1 >= set2
print(res)

#isdisjoint() 检测两集合是否不相交  不相交 True  相交False
res = set1.isdisjoint(set2)
print(res)

# ### 集合相关的函数
setvar = {"唐人街探案3"}
# 增
#add()    向集合中添加数据 (一次只加一个)
setvar.add("姜子牙")
print(setvar)

#update() 迭代着增加(一次加一堆)
lst = ["隔壁姐姐家的爱情故事","关于摄像头如何安装不被别人发现","论跑路的重要性"]
setvar.update(lst)
print(setvar)

# 删
#clear()  清空集合
setvar.clear()
print(setvar)

#pop()    随机删除集合中的一个数据
setvar = {'唐人街探案3', '姜子牙', '关于摄像头如何安装不被别人发现'}
res = setvar.pop()
print(res)

#remove()  删除集合中指定的值(不存在则报错)
setvar = {'唐人街探案3', '姜子牙', '关于摄像头如何安装不被别人发现'}
setvar.remove("姜子牙")
# setvar.remove("姜子牙112") 不存在的直接删除会报错
print(setvar)

#discard() 删除集合中指定的值(不存在的不删除 )  推荐使用
setvar = {'唐人街探案3', '姜子牙', '关于摄像头如何安装不被别人发现'}
# setvar.discard("姜子牙")
setvar.discard("姜子牙112") # 不存在的值不删除,不会报错
print(setvar)

# ### 冰冻集合 frozenset (了解)
"""冰冻集合只能做交叉并补,不能做增删相关的操作"""
setvar1 = ("a","b")
setvar2 = ("b","c")

# 冰冻集合只能做交叉并补
fz1 = frozenset(setvar1)
fz2 = frozenset(setvar2)
res = fz1 & fz2
print(res)

# 不能做增删相关的操作
# fz1.add("zzzs") error

```

### 📖 要点讲解

- 对称差集 symmetric_difference

- isdisjoint() 检测两集合是否不相交  不相交 True  相交False

- add()    向集合中添加数据 (一次只加一个)

- update() 迭代着增加(一次加一堆)

- pop()    随机删除集合中的一个数据

- remove()  删除集合中指定的值(不存在则报错)

- setvar.remove("姜子牙112") 不存在的直接删除会报错

- discard() 删除集合中指定的值(不存在的不删除 )  推荐使用

- setvar.discard("姜子牙")

- ### 冰冻集合 frozenset (了解)

- fz1.add("zzzs") error

---

## 10. 10.文件操作.py

### 📋 运行结果

```

把大象推进去,使劲~
<class 'bytes'> <class 'type'>
b'\xe6\x88\x91\xe7\x88\xb1\xe4\xbd\xa0'
我爱你
爱
我很丑,但我很温柔,外表冷漠,内心狂热,却从不退缩

```

### 💻 完整代码

```python

# ### 文件操作
"""
fp = open(文件名,模式,编码集)
fp 文件io对象 (文件句柄)
i => input  输入
o => output 输出

"""
# (1) 写入文件
# 一.打开文件
fp = open("ceshi0726.txt",mode="w",encoding="utf-8") # 打开冰箱门
# 二.存入内容
fp.write("把大象推进去,使劲~") # 把大象推进去
# 三.关闭文件
fp.close() # 把冰箱门关上

# (2) 读取文件
# 一.打开文件
fp = open("ceshi0726.txt",mode="r",encoding="utf-8")
# 二.读取内容
res = fp.read()
# 三.关闭文件
fp.close()

print(res)

# (3) 字节流
"""
字符串: 由多个字符组合在一起叫做字符串
字节流: 由多个字节组合在一起叫做字节流
字节流和字符串都可以在文件汇总做存储

# 字节流:(二进制的形式) 用来存储和传输的;
如果是ascii码范围内的字符,表达二进制字节流时,前面加上b
例如: b"1223" , b"abc"
不能在中文字符串的前面加b,直接报错,中文不在ascii编码范围内
"""

bytes_ = b'abc'
# bytes_ = b"我爱你" error
print(bytes , type(bytes))

# 将字符串和字节流(Bytes流)类型进行转换 (参数写成转化的字符编码格式)
    #encode() 编码  将字符串转化为字节流(Bytes流)
    #decode() 解码  将Bytes流转化为字符串

strvar = "我爱你"
# encode 将字符串->字节流
res = strvar.encode("utf-8")
print(res)

# decode  将字节流->字符串
res2 = res.decode("utf-8")
print(res2)

# 把字节流-> 字符串  b"\xe7\x88\xb1" => 爱
res = b"\xe7\x88\xb1".decode("utf-8")
print(res)

# (4) 写入二进制字节流 (不要加encoding)
fp = open("ceshi0726_2.txt",mode="wb")
strvar = "我很丑,但我很温柔,外表冷漠,内心狂热,却从不退缩".encode("utf-8")
fp.write(strvar)
fp.close()

# (5) 读取二进制字节流
fp = open("ceshi0726_2.txt",mode="rb")
res = fp.read()
fp.close()
print(res.decode("utf-8"))

# (6)图片的复制 (图片,视频,音频)
# 读取文件所有内容(二进制字节流)
fp = open("集合.png",mode="rb")
bytes_ = fp.read()
fp.close()

# 把读到的字节流写入到另外一个文件中
fp = open("集合2.png",mode="wb")
fp.write(bytes_)
fp.close()

```

### 📖 要点讲解

- 字节流:(二进制的形式) 用来存储和传输的;

- bytes_ = b"我爱你" error

- 将字符串和字节流(Bytes流)类型进行转换 (参数写成转化的字符编码格式)

- encode() 编码  将字符串转化为字节流(Bytes流)

- decode() 解码  将Bytes流转化为字符串

- 把字节流-> 字符串  b"\xe7\x88\xb1" => 爱

- (4) 写入二进制字节流 (不要加encoding)

---

## 11. 11.文件的扩展模式.py

### 💻 完整代码

```python

# ### 文件的扩展模式
# (utf-8编码格式下 默认一个中文三个字节 一个英文或符号 占用一个字节)
    #read()		功能: 读取字符的个数(里面的参数代表字符个数)
    #seek()		功能: 调整指针的位置(里面的参数代表字节个数)
		# seek(0)   把光标放到文件开头
		# seek(0,2) 把光标放到文件结尾
    #tell()		功能: 当前光标左侧所有的字节数(返回字节数)

# r+ 先读后写 (默认文件光标在开头)
"""
fp = open("ceshi0726_3.txt",mode="r+",encoding="utf-8")
# 先读
res = fp.read()
print(res) # abc
# 再写
fp.write(res)
# 在读
# 移动光标的位置到文件开头
fp.seek(0)
res = fp.read()
print(res)
fp.close()
"""

# r+ 先写后读(默认文件光标在开头)
"""
fp = open("ceshi0726_3.txt",mode="r+",encoding="utf-8")
# 先把光标移动到文件最后
fp.seek(0,2)
fp.write("123")
# 读取时,把光标移动到开头
fp.seek(0)
res = fp.read()
print(res)

# r模式,会按照光标移动的位置,继续添加内容,而a模式会强制写入到文件的最后.
'''
fp.seek(3)
fp.write("999")
'''
fp.close()
"""

# w+ 可写可读(默认文件光标在开头)
"""
fp = open("ceshi0726_4.txt",mode="w+",encoding="utf-8")
fp.write("麻了~好好振奋一下")
# 移动光标到文件开头
fp.seek(0)
res = fp.read()
print(res)

fp.close()
"""
# a+ 可写可读(默认文件光标在结尾)
'''
fp = open("ceshi0726_5.txt",mode="a+",encoding="utf-8")
fp.write("大家都最棒的")

# 移动一下文件光标到开头
fp.seek(0)
res = fp.read()
print(res)

# 移动光标到字节数为3的位置,是否会从3字节数的位置继续往后写入呢?
"""
在a模式下,无论如何移动光标,只要是写入内容,一定是从后面追加.
fp.seek(3)
fp.write("999")
"""

fp.close()
'''

# read tell seek 函数的使用
"""
fp = open("ceshi0726_5.txt",mode="a+",encoding="utf-8")
fp.seek(3)# 移动到第3个字节的位置
res = fp.read(3)# 读取3个字符
print(res)
# 获取当前光标左侧所有内容的字节数
res = fp.tell()
print(res)
fp.close()
"""

# 注意点
"""在使用seek移动时,如果出现了中文字符,切记不要移动到当前中文字节内,会出现无法识别的现象"""
"""
fp = open("ceshi0726_5.txt",mode="a+",encoding="utf-8")
fp.seek(2)
fp.read()
fp.close()
# b'\xe4\xbd\xa0'
# print("你".encode())
"""

# ### with语法 (省略掉close操作)

# 读取文件所有内容(二进制字节流)
with open("集合.png",mode="rb") as fp:
	bytes_ = fp.read()

# 把读到的字节流写入到另外一个文件中 (绝对路径的方式)
with open(r"E:\数据库视频\集合3.png",mode="wb") as fp:
	fp.write(bytes_)

# 在简写
with open("集合.png",mode="rb") as fp1,open(r"E:\数据库视频\集合4.png",mode="wb") as fp2:
	bytes_ = fp1.read()
	fp2.write(bytes_)

```

### 📖 要点讲解

- (utf-8编码格式下 默认一个中文三个字节 一个英文或符号 占用一个字节)

- read()		功能: 读取字符的个数(里面的参数代表字符个数)

- seek()		功能: 调整指针的位置(里面的参数代表字节个数)

- tell()		功能: 当前光标左侧所有的字节数(返回字节数)

- r模式,会按照光标移动的位置,继续添加内容,而a模式会强制写入到文件的最后.

- 移动光标到字节数为3的位置,是否会从3字节数的位置继续往后写入呢?

- ### with语法 (省略掉close操作)

- 把读到的字节流写入到另外一个文件中 (绝对路径的方式)

---

## 🖼️ 参考资料

![深浅拷贝.png](./assets/深浅拷贝.png)

![集合.png](./assets/集合.png)

![集合2.png](./assets/集合2.png)

![E:\数据库视频\集合3.png](./assets/E:\数据库视频\集合3.png)

![E:\数据库视频\集合4.png](./assets/E:\数据库视频\集合4.png)
