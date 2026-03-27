# Day 10: day10 atm取款机part2 锁信号量 事件队列 生产者消费者模型 守护线程 死锁递归锁互斥锁 进程池线程池

> 对应原课程：day10_atm取款机part2_锁信号量_事件队列_生产者消费者模型_守护线程_死锁递归锁互斥锁_进程池线程池

---

## 1. 1.进程锁.py

### 📋 运行结果

```

person0查询票数 : 0
person0没有抢到票
person1查询票数 : 0
person1没有抢到票
person2查询票数 : 0
person2没有抢到票
person3查询票数 : 0
person3没有抢到票
person4查询票数 : 0
person4没有抢到票
person5查询票数 : 0
person5没有抢到票
person6查询票数 : 0
person6没有抢到票
person7查询票数 : 0
person7没有抢到票
person8查询票数 : 0
person8没有抢到票
person9查询票数 : 0
person9没有抢到票

```

### 💻 完整代码

```python

# ### 锁 (应用在多进程当中)
from multiprocessing import Process, Lock
import json,time
lock = Lock()
"""
# 互斥锁lock: 同一时间只能有一个进程使用
# 上锁
lock.acquire()
print(123)
# 解锁
lock.release()
"""
# 死锁:(只上锁不解锁会出现死锁)
"""
lock.acquire()
lock.acquire()
print("start ... ")
"""

# 模拟12306抢票

# 读写票数
def wr_info(sign,dic=None):
	if sign == "r":
		with open("ticket",mode="r",encoding="utf-8") as fp:
			dic = json.load(fp)
		return dic
		
	elif sign == "w":
		with open("ticket",mode="w",encoding="utf-8") as fp:
			json.dump(dic,fp)

# 抢票
def get_ticket(person):
	dic = wr_info("r")
	# 模拟网络延迟
	time.sleep(0.2)
	if dic["count"] > 0:
		print("%s抢到票了" % (person))
		# 更新数据库
		dic["count"] -= 1
		wr_info("w",dic)
	else:
		print("%s没有抢到票" % (person) )

# 用ticket方法对整体做统一调用
def ticket(person,lock):
	# 先读取票数
	dic = wr_info("r")	
	# 查询票数
	print("%s查询票数 : %s" % (person,dic["count"]))	
	
	# 在抢票时开始上锁
	lock.acquire()
	# 开始调用抢票
	get_ticket(person)
	# 在抢票之后开始解锁
	lock.release()

if __name__ == "__main__":
	# 创建一把锁,同一时间只能一个进程修改文件资源;
	lock = Lock()
	# 创建10个抢票的进程对象(人)
	for i in range(10):
		p = Process(   target=ticket , args=("person{}".format(i),lock)     )
		p.start()

"""
创建进程的时候,是异步并发程序
但是遇到上锁就会使程序变成同步.
"""

```

### 📖 要点讲解

- 互斥锁lock: 同一时间只能有一个进程使用

- 创建一把锁,同一时间只能一个进程修改文件资源;

---

## 2. 2.Semaphore.py

### 📋 运行结果

```

执行超时（可能是交互式程序）

```

### 💻 完整代码

```python

# ### 信号量 Semaphore 多个进程同一时间上多把锁
"""锁+数量= semaphore"""
from multiprocessing import Process,Semaphore
import time
def ktv(person,sem):
	sem.acquire()
	print("%s进入到ktv唱吧开始唱歌" % (person))
	time.sleep(3)
	print("%s离开了ktv唱吧" % (person))
	sem.release()
	
if __name__ == "__main__":
	# 多个进程同一时间上三把锁
	sem = Semaphore(3)
	for i in range(10):
		p = Process(target=ktv,args=("person%s" % (i) , sem ))
		p.start()
		
"""
创建10个进程是异步创建
执行任务的时候,最多只能有3个进程执行,变成同步程序;
"""

```

### 📖 要点讲解

- ### 信号量 Semaphore 多个进程同一时间上多把锁

---

## 3. 3.事件.py

### 📋 运行结果

```

执行超时（可能是交互式程序）

```

### 💻 完整代码

```python

# ### 事件
from multiprocessing import Process,Event
import time,random
"""
# 阻塞事件 ：
	e = Event()生成事件对象e   
	e.wait()动态给程序加阻塞 , 程序当中是否加阻塞完全取决于该对象中的is_set() [默认返回值是False]
    # 如果是True  不加阻塞
    # 如果是False 加阻塞
# 控制这个属性的值
    # set()方法     将这个属性的值改成True
    # clear()方法   将这个属性的值改成False
    # is_set()方法  判断当前的属性是否为True  (默认上来是False)
"""
# 1
# e = Event()
# print(e.is_set())
# 默认内部成员属性为False,就是阻塞
# e.wait()
# print("start1 .. ")

# 2
"""
e = Event()
# 将内部成员属性改成True 
e.set()
# wait 不阻塞
e.wait()
print('start2 .. ')
"""

# 3
"""
e = Event()
# 将内部成员属性改成True 
e.set()
# 将内部成员属性改成False
e.clear()
# wait 不阻塞
e.wait()
print('start3 .. ')
"""

# 4 
"""
e = Event()
# 设置最大阻塞时间 3
e.wait(3)
print("start4 .. ")
"""

# ### 模拟经典红绿灯效果
# 模拟交通灯
def traffic_light(e):
	print("红灯亮")
	while True:
		if e.is_set(): 
			# 亮一秒钟
			time.sleep(1)
			# 切换成红灯
			print("红灯亮")
			e.clear() # True -> False
		else:
			# 亮一秒钟
			time.sleep(1)
			# 切换成绿灯
			print("绿灯亮")
			e.set() # False -> True
# e = Event()
# traffic_light(e)

# 模拟小车
def car(e,i):
	if not e.is_set():
		print("小车%s在等待" % (i))
		e.wait()
	print("小车%s放行" % (i) )
# car(e,10)

# 版本一
"""
if __name__ == "__main__":
	lst = []
	e = Event()
	# 单独创建进程执行红绿灯
	p1 = Process(target=traffic_light,args=(e,))
	p1.start()
	
	for i in range(20):
		time.sleep(random.uniform(0,2))
		p2 = Process(target=car,args=(e,i))
		p2.start()
		lst.append(p2)
	
	# 保证子进程和主进程的同步性,需要加join
	for i in lst:
		i.join()
	
	print("程序执行结束.. ")
"""
# 版本二(包头红绿灯,没有车的时候,把红绿灯给炸了)
if __name__ == "__main__":
	lst = []
	e = Event()
	# 单独创建进程执行红绿灯
	p1 = Process(target=traffic_light,args=(e,))
	p1.daemon = True
	p1.start()
	
	for i in range(20):
		time.sleep(random.uniform(0,1))
		p2 = Process(target=car,args=(e,i))
		p2.start()
		lst.append(p2)
	
	# 保证子进程和主进程的同步性,需要加join
	for i in lst:
		i.join()
	
	print("程序执行结束.. ")
	
```

### 📖 要点讲解

- set()方法     将这个属性的值改成True

- clear()方法   将这个属性的值改成False

- is_set()方法  判断当前的属性是否为True  (默认上来是False)

- 保证子进程和主进程的同步性,需要加join

- 版本二(包头红绿灯,没有车的时候,把红绿灯给炸了)

- 保证子进程和主进程的同步性,需要加join

---

## 4. 4.进程队列.py

### 📋 运行结果

```

主进程添加
子进程添加数据

```

### 💻 完整代码

```python

# ### 进程队列
from multiprocessing import Queue,Process
# (1) 基本用法
q = Queue()
# 1.把数据存放在q队列中
# q.put(111)
# q.put(222)
# q.put(333)
# 2.读取队列中的数据
# res = q.get()
# print(res)
# res = q.get()
# print(res)
# res = q.get()
# print(res)
# 3.获取队列中的值,如果已经全部取走,那么出现阻塞现象;
# res = q.get()
# print(res)

# 4.get_nowait,区别在于如果获取不到数据,直接报错
# res = q.get_nowait()
# print(res)
# error 
# res = q.get_nowait()
# print(res)

# 5.put_nowait,指定队列长度后,超出长度在存放会出现报错
"""
q2 = Queue(3)
q2.put(100)
q2.put(101)
q2.put(102)
# 指定队列长度为3之后,超出长度在存放会出现阻塞
# q2.put(103)
try:
	q2.put_nowait(103)
except:
	pass
"""

# (2)列用队列,实现进程之间共享数据
def func(q):
	# 2.子进程获取
	res = q.get()
	print(res)
	# 3.子进程添加数据
	q.put("子进程添加数据")
	
if __name__ =="__main__":
	q3 = Queue()
	p = Process(target=func,args=(q,))
	p.start()
	
	# 1.主进程里面添加数据
	q.put("主进程添加")
	
	# 等待子进程把数据放进去之后,主进程在拿
	p.join()
	
	# 4.主进程获取数据
	print(q.get())
	
```

### 📖 要点讲解

- 3.获取队列中的值,如果已经全部取走,那么出现阻塞现象;

- 4.get_nowait,区别在于如果获取不到数据,直接报错

- 5.put_nowait,指定队列长度后,超出长度在存放会出现报错

- 指定队列长度为3之后,超出长度在存放会出现阻塞

---

## 5. 5.生产者消费者模型.py

### 📋 运行结果

```

张俊文生产了小馒头0
张俊文生产了小馒头1
张俊文生产了小馒头2
主程序执行结束 .. 
赵强222吃了一个小馒头1
赵强吃了一个小馒头0
赵强吃了一个小馒头2

```

### 💻 完整代码

```python

# ### 生产者消费者模型
"""
# 爬虫案例
1号进程用来爬取网页里面内容
2号进程用来匹配想要的关键字

1号进程可以看成一个生产者
2号进程可以看成一个消费者
一个是负责往队列当中添加数据   生产者
一个是负责从队列当中获取数据   消费者

理想的生产者消费者模型,彼此的速度相当
如果有一方快或慢,可以适当地增加或者减少对应进程
"""
from multiprocessing import Process,Queue
import  time , random
# 生产者模型
def producer(q,name,food):
	for i in range(3):
		time.sleep(random.uniform(0.1,1))		
		print("%s生产了%s" % (name,food) + str(i) )
		q.put(food+str(i))

# 消费者模型
def consumer(q,name):
	while True:
		# 消费者取数据,如果拿到了None ,代表消费结束,终止循环
		food = q.get()
		if food is None:
			break
		time.sleep(random.uniform(0.1,1))	
		print("%s吃了一个%s" % (name,food))

# 1.程序无法正常结束 ..
"""
if __name__ == "__main__":
	q = Queue()
	p1 = Process(target=producer,args=(q,"张俊文","小馒头"))
	p1.start()
	
	c1 = Process(target=consumer,args=(q,"赵强"))
	# c1.daemon = True
	c1.start()	
	# p1.join()
	
	print("主程序执行结束 .. ")
"""
# 2.优化改善版
if __name__ == "__main__":
	q = Queue()
	# 生产者模型
	p1 = Process(target=producer,args=(q,"张俊文","小馒头"))
	p1.start()
	
	# 消费者1模型
	c1 = Process(target=consumer,args=(q,"赵强"))
	c1.start()	
	# 消费者2模型
	c2 = Process(target=consumer,args=(q,"赵强222"))
	c2.start()	
	
	# 等待生产者把所有数据添加到队列中
	p1.join()
	# 并且在尾部添加None,代表生产结束
	q.put(None)
	q.put(None)

	print("主程序执行结束 .. ")

```

### 📖 要点讲解

- 消费者取数据,如果拿到了None ,代表消费结束,终止循环

---

## 6. 6.JoinableQueue.py

### 📋 运行结果

```

张俊文生产了小馒头0
张俊文生产了小馒头1
张俊文生产了小馒头2
主程序执行结束 .. 

```

### 💻 完整代码

```python

# ### JoinableQueue
from multiprocessing import JoinableQueue,Process
"""
put 放
get 取
task_done 队列数减一
join  阻塞
task_done 和 join 是配合使用的
put       一次数据 , 队列中的属性个数+1
task_done 一次数据 , 队列中的属性个数-1
队列.join 就根据队列中的属性来判断是阻塞还是放行
队列中的属性 是0 ->放行 
队列中的属性 不是0 ->阻塞
"""
# 阻塞状态
# jq = JoinableQueue()
# jq.put("a")
# print(jq.get())
# jq.join()
# print(11111)

# 放行状态
"""
jq = JoinableQueue()
jq.put("a") # 队列属性+1
print(jq.get())
jq.task_done() # 队列属性-1
jq.join() # 判断队列属性=0 放行
print(11111)
"""

# 优化生产者消费者代码
from multiprocessing import Process,Queue
import  time , random
# 生产者模型
def producer(q,name,food):
	for i in range(3):
		time.sleep(random.uniform(0.1,1))		
		print("%s生产了%s" % (name,food) + str(i) )
		q.put(food+str(i))

# 消费者模型
def consumer(q,name):
	while True:
		# 消费者取数据,如果拿到了None ,代表消费结束,终止循环
		food = q.get()
		time.sleep(random.uniform(0.1,1))	
		print("%s吃了一个%s" % (name,food))
		q.task_done()
		
if __name__ == "__main__":
	q = JoinableQueue()
	# 生产者模型
	p1 = Process(target=producer,args=(q,"张俊文","小馒头"))
	p1.start()
	
	# 消费者1模型
	c1 = Process(target=consumer,args=(q,"赵强"))
	c1.daemon = True
	c1.start()	
	
	# 消费者2模型
	c2 = Process(target=consumer,args=(q,"赵强222"))
	c2.daemon = True
	c2.start()	
	
	# 等待生产者把所有数据添加到队列中
	p1.join()
	# 让jq这个队列等待或者放行,什么时候队列属性减到0了,什么时候放行
	"""因为join必须等待两个守护进程把队列属性减到0才放行"""
	q.join()

	"""主程序代码执行结束之后,立刻杀死守护进程"""
	print("主程序执行结束 .. ")

```

### 📖 要点讲解

- 消费者取数据,如果拿到了None ,代表消费结束,终止循环

- 让jq这个队列等待或者放行,什么时候队列属性减到0了,什么时候放行

---

## 7. 7.线程.py

### 📋 运行结果

```

True
181768
<Thread(Thread-1 (func), started 137868227901120)>
<Thread(download, started 137868227901120)>
download
137868237717632
当前进程号: 181768
当前进程号: 181768
当前线程号: 137868211115712
当前线程号: 137868219508416
当前进程号: 181768
当前线程号: 137868202723008
当前进程号: 181768
当前线程号: 137868194330304
当前进程号: 181768
当前线程号: 137867846219456
当前进程号: 181768
当前线程号: 137867837826752
当前进程号: 181768
当前线程号: 137867829434048
当前进程号: 181768
当前线程号: 137867821041344
当前进程号: 181768
当前线程号: 137867812648640
当前进程号: 181768
当前线程号: 137867804255936
[<_MainThread(MainThread, started 137868237717632)>, <Thread(download, started 137868227901120)>, <Thread(Thread-2 (func), started 137868219508416)>, <Thread(Thread-3 (func), started 137868211115712)>, <Thread(Thread-4 (func), started 137868202723008)>, <Thread(Thread-5 (func), started 137868194330304)>, <Thread(Thread-6 (func), started 137867846219456)>, <Thread(Thread-7 (func), started 137867837826752)>, <Thread(Thread-8 (func), started 137867829434048)>, <Thread(Thread-9 (func), started 137867821041344)>, <Thread(Thread-10 (func), started 137867812648640)>, <Thread(Thread-11 (func), started 137867804255936)>]
12
12

```

### 💻 完整代码

```python

# ### 线程
from multiprocessing import Process
from threading import Thread
import os , time ,random
# (1) 一个进程中包含多个线程,这些线程共享一份资源
"""线程是异步并发程序"""
"""
def func(num):
	time.sleep(random.uniform(0.1,1))
	print("当前进程号:",os.getpid())
	print("子线程参数:",num)
	
# 多线程中 下面判断可以不加(加上不错)
if __name__ == "__main__":
	for i in range(10):
		t = Thread(target=func,args=(i,))
		t.start()
		
	print("主线程执行结束 ... ")
	print(os.getpid())
"""
# (2)并发多进程和多线程,谁的速度快 ? 多线程
'''
def func(num):
	print("子线程对应的进程号:",os.getpid())
	print("当前参数是",num)

if __name__ == "__main__":
	
	lst = []
	startime = time.time()
	"""
	# 多线程 # 0.11968040466308594
	for i in range(1000):
		t = Thread(target=func,args=(i,))
		t.start()
		lst.append(t)
	"""
	
	# 多进程 # 21.300036430358887
	for i in range(1000):
		p = Process(target=func,args=(i,))
		p.start()
		lst.append(p)
		
	for i in lst:
		i.join()
	
	endtime = time.time()		
	print("使用时间:" , endtime - startime) 
'''

# (3) 多线程之间共享一个进程资源
"""
num = 50
lst = []
def func(i):
	global num 
	num -= 1

for i in range(50):
	t = Thread(target=func,args=(i,))
	t.start()
	lst.append(t)
	
# 等待所有子线程执行结束之后,在最后打印num
for i in lst:
	i.join()

print(num)
"""
# (4) 线程的相关函数
"""
线程.is_alive()    检测线程是否仍然存在
线程.setName()     设置线程名字
线程.getName()     获取线程名字
1.currentThread().ident 查看线程id号 
2.enumerate()        返回目前正在运行的线程列表
3.activeCount()      返回目前正在运行的线程数量
"""

# 1.检测线程是否仍然存在 is_alive
def func():
	time.sleep(1)

t = Thread(target=func)
t.start()
print(t.is_alive())
print(os.getpid())

# 2.设置线程名字 setName
print(t)
t.setName("download")
print(t)

# 3.线程.getName()     获取线程名字
print(t.getName())
# 4.currentThread().ident 查看线程id号 
from threading import currentThread
# 5.enumerate()        返回目前正在运行的线程列表
from threading import enumerate
# 6.activeCount()      返回目前正在运行的线程数量 (了解)
from threading import activeCount

print(currentThread().ident)

def func():
	print("当前进程号:",os.getpid())
	print("当前线程号:",currentThread().ident)
	time.sleep(1)

for i in range(10):
	t = Thread(target = func)
	t.start()
	
print(enumerate())
print(len(enumerate()))
print(activeCount())

```

### 📖 要点讲解

- (1) 一个进程中包含多个线程,这些线程共享一份资源

- (2)并发多进程和多线程,谁的速度快 ? 多线程

- 多线程 # 0.11968040466308594

- 多进程 # 21.300036430358887

- 等待所有子线程执行结束之后,在最后打印num

- 1.检测线程是否仍然存在 is_alive

- 3.线程.getName()     获取线程名字

- 4.currentThread().ident 查看线程id号

- 5.enumerate()        返回目前正在运行的线程列表

- 6.activeCount()      返回目前正在运行的线程数量 (了解)

---

## 8. 8.守护线程.py

### 📋 运行结果

```

我是func2任务 start ... 
我是func1任务
我是func1任务
我是func1任务
我是func1任务
我是func1任务
我是func1任务
我是func1任务
我是func1任务
我是func1任务
我是func2任务 end ... 
我是func1任务
我是func1任务
我是func1任务
我是func1任务
我是func1任务
我是func1任务
我是func1任务
主线程执行结束.. 

```

### 💻 完整代码

```python

# ### 守护线程 : 等待所有线程执行结束之后,自动终止,守护所有线程;
from threading import Thread
import time
def func1():
	while True:
		time.sleep(0.3)
		print("我是func1任务")
	
def func2():
	print('我是func2任务 start ... ')
	time.sleep(3)
	print('我是func2任务 end ... ')

if __name__ == "__main__":
	t1 = Thread(target=func1)
	# 在start调用之前,设置守护线程
	t1.setDaemon(True)
	
	t2 = Thread(target=func2)
	t1.start()
	t2.start()
	
	time.sleep(5)
	print("主线程执行结束.. ")

```

### 📖 要点讲解

- ### 守护线程 : 等待所有线程执行结束之后,自动终止,守护所有线程;

---

## 9. 9.线程的数据安全.py

### 📋 运行结果

```

主线程执行结束 ... 
0
1.2114918231964111

```

### 💻 完整代码

```python

# ### 线程的数据安全 依赖lock锁
from threading import Thread,Lock
import time
"""在保证数据安全的基础上,尽量减少上锁和解锁的次数,提升效率和时间"""

n = 0
def func1(lock):
	global n
	# 上锁的简写方法 可以使用with语法,自动完成上锁和解锁操作
	with lock:
		for i in range(1000000):		
			n += 1
			
def func2(lock):
	global n 
	with lock:
		for i in range(1000000):		
			n -= 1
		
if __name__ == "__main__":
	lock = Lock()
	lst = []
	startime = time.time()
	for i in range(10):
		t1 = Thread(target=func1,args=(lock,))
		t1.start()
		t2 = Thread(target=func2,args=(lock,))
		t2.start()
		lst.append(t1)
		lst.append(t2)
		
	for i in lst:
		i.join()
		
	print("主线程执行结束 ... ")
	print(n)
	endtime = time.time()
	print(endtime - startime) 

	# 45.38959050178528  # 1.4281795024871826

```

### 📖 要点讲解

- 上锁的简写方法 可以使用with语法,自动完成上锁和解锁操作

- 45.38959050178528  # 1.4281795024871826

---

## 10. 10.线程Semaphore.py

### 📋 运行结果

```

执行超时（可能是交互式程序）

```

### 💻 完整代码

```python

# ### 信号量 Semaphore
"""同一时间可以设置允许多少个线程上锁;"""
from threading import Semaphore,Thread
import time , random
def func(i,sem):	
	sem.acquire()	
	print(i)
	time.sleep(3)
	sem.release()
	
if __name__ == "__main__":
	sem = Semaphore(3)
	for i in range(10):
		Thread(target=func,args=(i,sem)).start()
		
	print("主线程执行结束... ")
	
"""
执行线程时是异步并发程序
当遇到上锁时,程序会变成同步;
"""

```

---

## 11. 11.死锁,互斥锁,递归锁.py

### 📋 运行结果

```

start 2 ,,,
>================?
陈勇抢到面条
陈勇抢到筷子
陈勇正在吃
黄启新抢到面条
黄启新抢到筷子
黄启新正在吃
刘英抢到筷子
刘英抢到面条
刘英正在吃
叶元明抢到筷子
叶元明抢到面条
叶元明正在吃

```

### 💻 完整代码

```python

# ### 死锁,互斥锁,递归锁
# (1) 死锁 : 只上锁不解锁是死锁
from threading import Thread,Lock
import time

"""
# 一把锁不能连续嵌套
lock = Lock()
lock.acquire()
lock.acquire()
print("start .. ")
lock.release()
lock.release()
"""

# 多把锁可以互相嵌套
'''
lock1 = Lock()
lock2 = Lock()
lock1.acquire()
lock2.acquire()
print('start 1 .... ')
lock2.release()
lock1.release()
'''

# (2) 死锁 : 逻辑上的死锁
"""
noodle = Lock()
kuaizi = Lock()

def eat1(name):
	noodle.acquire()
	print("{}抢到面条".format(name))
	kuaizi.acquire()
	print("{}抢到筷子".format(name))
	
	print("{}正在吃".format(name))
	time.sleep(1)
	
	kuaizi.release()
	noodle.release()
	
def eat2(name):
	kuaizi.acquire()
	print("{}抢到筷子".format(name))
	noodle.acquire()
	print("{}抢到面条".format(name))
	
	print("{}正在吃".format(name))
	time.sleep(1)
	
	noodle.release()
	kuaizi.release()
	
if __name__ == "__main__":
	namelst1 = ["陈勇","黄启新"]
	namelst2 = ["刘英","叶元明"]
	for i in namelst1:
		Thread(target=eat1,args=(i,)).start()
		
	for i in namelst2:
		Thread(target=eat2,args=(i,)).start()
"""
# ### 递归锁
"""
专门用于快速解决线上死锁问题的
"""
from threading import Thread,RLock
rlock = RLock()
rlock.acquire()
rlock.acquire()
rlock.acquire()
rlock.acquire()

rlock.release()
rlock.release()
rlock.release()
rlock.release()
print("start 2 ,,,")

# ### 优化代码
# noodle = Lock()
# kuaizi = Lock()
"""
noodle = kuaizi = RLock()
def eat1(name):
	noodle.acquire()
	print("{}抢到面条".format(name))
	kuaizi.acquire()
	print("{}抢到筷子".format(name))
	
	print("{}正在吃".format(name))
	time.sleep(1)
	
	kuaizi.release()
	noodle.release()
	
def eat2(name):
	kuaizi.acquire()
	print("{}抢到筷子".format(name))
	noodle.acquire()
	print("{}抢到面条".format(name))
	
	print("{}正在吃".format(name))
	time.sleep(1)
	
	noodle.release()
	kuaizi.release()
	
if __name__ == "__main__":
	namelst1 = ["陈勇","黄启新"]
	namelst2 = ["刘英","叶元明"]
	for i in namelst1:
		Thread(target=eat1,args=(i,)).start()
		
	for i in namelst2:
		Thread(target=eat2,args=(i,)).start()
"""
# ### 正确的处理方式
"""尽量使用一把锁解决问题,不用锁嵌套的形式语法,容易逻辑死锁"""
print(">================?")

lock = Lock()
def eat1(name):
	lock.acquire()
	print("{}抢到面条".format(name))
	print("{}抢到筷子".format(name))
	
	print("{}正在吃".format(name))
	time.sleep(1)

	lock.release()
	
def eat2(name):
	lock.acquire()
	print("{}抢到筷子".format(name))
	print("{}抢到面条".format(name))
	
	print("{}正在吃".format(name))
	time.sleep(1)

	lock.release()
	
if __name__ == "__main__":
	namelst1 = ["陈勇","黄启新"]
	namelst2 = ["刘英","叶元明"]
	for i in namelst1:
		Thread(target=eat1,args=(i,)).start()
		
	for i in namelst2:
		Thread(target=eat2,args=(i,)).start()

```

---

## 12. 12.线程队列.py

### 📋 运行结果

```

100
101
401
400
1
3
13
james
jordan
kobi
(18, 'wangwen', 100)
(18, 'wangwen', 200)
(58, 'machengong')
(98, 'fengshuangxi')

```

### 💻 完整代码

```python

# ### 线程队列
from queue import Queue
"""
put 在队列中存数据
get 在队列中取数据
put_nowait 超过了队列长度,存放时报错
get_nowait 如果队列中没有值可获取直接报错
"""
# (1) Queue 先进先出,后进后出
q = Queue()
q.put(100)
q.put(101)
print(q.get())
print(q.get())
# print(q.get()) 阻塞
# q.get_nowait() 报错

# 限定队列长度
q2 = Queue(2)
q2.put(111)
q2.put(222)
# q2.put(333) 阻塞
# q2.put_nowait(333) 报错

# (2) LifoQueue 先进后出,后进先出
from queue import LifoQueue
lq = LifoQueue()
lq.put(400)
lq.put(401)
print(lq.get())
print(lq.get())

# (3) PriorityQueue 按照优先级的顺序取值
from queue import PriorityQueue
# 1.存放的数字,默认从小到大进行取值
pq = PriorityQueue()
pq.put(13)
pq.put(3)
pq.put(1)

print(pq.get())
print(pq.get())
print(pq.get())

# 2.存放的字符串,默认按照ascii编码进行获取
pq = PriorityQueue()
pq.put("kobi")
pq.put("jordan")
pq.put("james")

print(pq.get())
print(pq.get())
print(pq.get())

# 3.存放的容器,按照容器中第一个元素进行排序后获取,如果第一个相同,依次去找元组中后面的值进行比较;
pq = PriorityQueue()
pq.put( (18,"wangwen",200) )
pq.put( (58,"machengong") )
pq.put( (98,"fengshuangxi") )
pq.put( (18,"wangwen",100) )

print(pq.get())
print(pq.get())
print(pq.get())
print(pq.get())

# 4.要么都是数字,或者字符串,或者 容器,不能混参,要放就都放同一种类型的数据
"""
error
pq = PriorityQueue()
pq.put(1)
pq.put("bad")
pq.put([1,2,3])
"""

```

### 📖 要点讲解

- q2.put_nowait(333) 报错

- (2) LifoQueue 先进后出,后进先出

- (3) PriorityQueue 按照优先级的顺序取值

- 2.存放的字符串,默认按照ascii编码进行获取

- 3.存放的容器,按照容器中第一个元素进行排序后获取,如果第一个相同,依次去找元组中后面的值进行比较;

- 4.要么都是数字,或者字符串,或者 容器,不能混参,要放就都放同一种类型的数据

---

## 13. 13.进程池_线程池.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day10_atm取款机part2_锁信号量_事件队列_生产者消费者模型_守护线程_死锁递归锁互斥锁_进程池线程池/代码/13.进程池_线程池.py", line 79, in <module>
    from collections import Iterator,Iterable
ImportError: cannot import name 'Iterator' from 'collections' (/usr/lib/python3.12/collections/__init__.py)

```

### 💻 完整代码

```python

# ### 进程池 和 线程池
from concurrent.futures import ProcessPoolExecutor , ThreadPoolExecutor
import os,time,random

def func(i):
	time.sleep(random.uniform(0.1,2))
	print(i)
	print("任务执行中start ... " , os.getpid())	
	print("任务执行结束end ... " , os.getpid())
	return i
	
# (1) ProcessPoolExecutor  进程池的基本语法
'''
"""默认如果一个进程短时间内可以完成更多的任务,就不会创建额外的进程来执行,以节省系统资源"""
if __name__ == "__main__":
	lst = []
	# 获取的是逻辑核心数
	res = os.cpu_count()
	print(res) #
	# (1) 创建进程池对象
	"""默认会根据逻辑核心数的数量开辟对应数量的进程数"""
	p = ProcessPoolExecutor()
	
	# (2) 执行异步任务
	for i in range(10):
		# submit(任务函数,参数1,参数2 ... )
		obj = p.submit(func,i)
		lst.append(obj)
		
	# (3) 获取当前进程任务的返回值
	"""通过result 获取的返回值是同步的"""
	"""
	for i in lst:
		print(i.result())
	"""
	# (4) 等待所有子进程执行结束后,主进程代码在执行
	p.shutdown() # join
	print("主程序执行结束")
'''

# (2) ThreadPoolExecutor  进程池的基本语法
"""默认如果一个线程短时间内可以完成更多的任务,就不会分配额外的线程来执行,以节省系统资源"""
'''
from threading import currentThread
def func(i):
	# time.sleep(random.uniform(0.1,2))
	# print(i)
	# print("任务执行中start ... " , os.getpid())	
	# print("任务执行结束end ... " , os.getpid())
	return currentThread().ident
	
if __name__ == "__main__":
	lst = []
	setvar = set()
	# (1) 创建线程池 默认并发30个线程
	tp = ThreadPoolExecutor() #v 30
	
	# (2) 异步提交任务	
	for i in range(100):
		"""submit(任务函数,参数1,参数2 ... ) """
		obj = tp.submit(func,i)
		lst.append(obj)
		
	# (3) 获取返回值
	for i in lst:
		# add 一次插一个 ,  update 一次插一堆
		setvar.add(i.result())
		
	# (4) 等待所有子线程执行结束
	tp.shutdown()
	
	print(len(setvar))	
	print("主线程执行结束 .. ")
'''

# (3) 线程池 map
from threading import currentThread as cthread
from collections import Iterator,Iterable
def func(i):
	time.sleep(random.uniform(0.1,4))
	return "*" * i

if __name__ == "__main__":
	# 按照顺序存放到迭代器中
	tp = ThreadPoolExecutor(6)
	it = tp.map(func,range(1,20))
	print(isinstance(it,Iterator))
	
	tp.shutdown()
	for i in it:
		print(i)
	
```

### 📖 要点讲解

- (1) ProcessPoolExecutor  进程池的基本语法

- submit(任务函数,参数1,参数2 ... )

- (4) 等待所有子进程执行结束后,主进程代码在执行

- (2) ThreadPoolExecutor  进程池的基本语法

- time.sleep(random.uniform(0.1,2))

- print("任务执行中start ... " , os.getpid())

- print("任务执行结束end ... " , os.getpid())

- add 一次插一个 ,  update 一次插一堆

---

## 🖼️ 参考资料

![GIL全局解释器锁.png](./assets/GIL全局解释器锁.png)

![解释图.png](./assets/解释图.png)

![锁.png](./assets/锁.png)

![队列,先进先出,后进后厨.png](./assets/队列,先进先出,后进后厨.png)

![1555906308602.png](./assets/1555906308602.png)

![1555906852982.png](./assets/1555906852982.png)

![生产者消费者.png](./assets/生产者消费者.png)
