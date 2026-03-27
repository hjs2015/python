# Day 9: day09 黏包 大小文件的校验 tcp登录 socketserver 进程 join守护进程

> 对应原课程：day09_黏包_大小文件的校验_tcp登录_socketserver_进程_join守护进程

---

## 1. struct操作.py

### 📋 运行结果

```

b'\xb3\xb5V\x07' 4
2100000000

```

### 💻 完整代码

```python

import struct
"""
pack
	把任意长度的数字转化成具体固定4个字节长度的字节流
unpack
	把4个大小的字节流恢复成原来的数值大小，返回的是元组
"""
# i => int 要转换的当前数据,类型是整形,
res = struct.pack("i", 123123123)
print(res , len(res))

# 测试打包数据的长度上限 不超过22个亿左右范围在21个亿左右
res = struct.pack("i", 2100000000)
# i => int 代表转换成整形
tup = struct.unpack("i",res)
print(tup[0])

```

### 📖 要点讲解

- i => int 要转换的当前数据,类型是整形,

- 测试打包数据的长度上限 不超过22个亿左右范围在21个亿左右

---

## 2. 1.client.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day09_黏包_大小文件的校验_tcp登录_socketserver_进程_join守护进程/代码/1.黏包/1.client.py", line 5, in <module>
    sk.connect(  ("127.0.0.1",9000) )
ConnectionRefusedError: [Errno 111] Connection refused

```

### 💻 完整代码

```python

# ### 客户端
import socket
import time
sk = socket.socket()
sk.connect(  ("127.0.0.1",9000) )

# time.sleep(1)

print(sk.recv(1024))
print(sk.recv(1024))

sk.close()

```

---

## 3. 1.server.py

### 📋 运行结果

```

执行超时（可能是交互式程序）

```

### 💻 完整代码

```python

# ### 服务端
import socket
sk = socket.socket()
sk.bind( ("127.0.0.1",9000)  )
sk.listen()

conn,addr = sk.accept()

# 收发数据的逻辑
conn.send("hello,".encode())
conn.send("world".encode())
# 四次挥手
conn.close()
# 退还端口
sk.close()

```

---

## 4. 1.进程.py

### 📋 运行结果

```

1子进程id>>>181658 2父进程id>>>181657 1
1子进程id>>>181659 2父进程id>>>181657 2
1子进程id>>>181660 2父进程id>>>181657 3
1子进程id>>>181661 2父进程id>>>181657 4
1子进程id>>>181662 2父进程id>>>181657 5
1子进程id>>>181663 2父进程id>>>181657 6
1子进程id>>>181664 2父进程id>>>181657 7
1子进程id>>>181665 2父进程id>>>181657 8
主程序执行结束 ... 
1子进程id>>>181666 2父进程id>>>181657 9
1子进程id>>>181667 2父进程id>>>181657 10

```

### 💻 完整代码

```python

# ### 进程
import os
from multiprocessing import Process
import time
"""
print(os.getpid())  # 当前进程 (子进程)
print(os.getppid()) # 查看父进程(pycharm)
"""

# (1) 进程的基本语法
"""
进程对象 = Process(target=任务,args=(参数1,参数2)) args是元组
进程对象.start() 调用进程
"""

'''
def func():
	print("1子进程id>>>{} 2父进程id>>>{}".format(os.getpid(),os.getppid()))
	
# 当这个文件作为主程序调用时,下面的代码才执行,否则作为分模块导入时,下面代码不执行
"""下面代码不加在windows中直接报错,在linux中可以兼容"""
if __name__ == "__main__":
	# 创建一个子进程,由1.进程.py这个程序中创建
	p = Process(target=func)
	# 调用子进程
	p.start()
	
	print("3子进程id>>>{} 4父进程id>>>{}".format(os.getpid(),os.getppid()))
'''

# (2) 创建带有参数的进程
"""子进程在创建时,要分配cpu内存等相关资源,遇到阻塞cpu会立刻切换任务,所有主进程会比子进程快一点,但不绝对,要依照cpu的调度策略"""
"""
def func(n):
	for i in range(1,n+1): 
		print("1子进程id>>>{} 2父进程id>>>{}".format(os.getpid(),os.getppid()))
		
if __name__ == "__main__":
	n = 5
	# 创建子进程
	p = Process(target=func,args=(n,))
	# 调用子进程
	p.start()

	for i in range(1,n+1):
		print("*" * i)
"""
# (3) 进程之间的数据共享:默认不共享的(是彼此独立的两个程序)
"""
count = 1000
def func():
	global count
	count += 10

if __name__ == "__main__":
	p = Process(target=func)
	p.start()
	time.sleep(1)
	print(count)
"""
# (4) 多个进程可以异步并发
"""
程序在异步并发任务时,因为cpu的调度策略问题,不一定先执行谁或者后执行谁,
整体而言,主进程速度快于子进程,cpu遇到阻塞会立刻切换到其他进城任务中执行,等恢复到就绪态,在切换回来执行

主进程会默认等待所有子进程执行结束之后,在去关闭程序,释放资源
若不等待,子进程在后台不停的运行.不方便于进程的管理,容易出现僵尸进程,不停的占用系统资源,但是找不到是谁做的.
"""
def func(n):
	print("1子进程id>>>{} 2父进程id>>>{}".format(os.getpid(),os.getppid()) , n)
	
if __name__ == "__main__":
	for i in range(1,11):
		Process(target=func,args=(i,)).start()
	"""
	Process(target=func,args=(1,)).start()
	Process(target=func,args=(2,)).start()
	Process(target=func,args=(3,)).start()
	Process(target=func,args=(4,)).start()
	Process(target=func,args=(5,)).start()
	Process(target=func,args=(6,)).start()
	Process(target=func,args=(7,)).start()
	Process(target=func,args=(8,)).start()
	Process(target=func,args=(9,)).start()
	Process(target=func,args=(10,)).start()
	"""
	print("主程序执行结束 ... ")
	
```

### 📖 要点讲解

- 当这个文件作为主程序调用时,下面的代码才执行,否则作为分模块导入时,下面代码不执行

- 创建一个子进程,由1.进程.py这个程序中创建

- (3) 进程之间的数据共享:默认不共享的(是彼此独立的两个程序)

---

## 5. 1.hashlib.py

### 📋 运行结果

```

e2fc714c4727ee9395f324cd2e7f331f
ec92648437289d40ea756f953a1d57a1
4262f36f97394295d75ee1264596f5b3 32
47d80e3d06534ada8054f085b1e04d1eb9e0ecab0c1ca75bdcc701a37170b7fd38d6583eb89eadc380445da3ccbed0ee488b86a69d5db61caf967e0b4b6d7427 128

```

### 💻 完整代码

```python

# ### hashlib (作用:密码加密)

import hashlib
import random

# 基本语法
# (1) 创建一个算法的对象
hs = hashlib.md5() 
# (2) 把想要加密的字符串通过update更新到hs对象中进行处理 (数据是字节流)
hs.update("abcd".encode("utf-8"))
# (3) 返回32位长度的16禁止的字符串
res = hs.hexdigest()
print(res)

# 加盐(加入一个特殊的关键字,大大的增加密码的复杂度,防止密码被破解)
hs = hashlib.md5("ceShi%$#_".encode()) # 数据要求是字节流
hs.update("abcd".encode())
res = hs.hexdigest()
print(res) # ec92648437289d40ea756f953a1d57a1

# 动态加盐
res = str(random.randrange(10,1000000))
strvar = "ceShi%$#_"+res
hs = hashlib.md5(strvar.encode())
hs.update("abcd".encode())
res = hs.hexdigest()
print(res , len(res))

# ### sha系列算法
"""
sha1    长度为40的十六进制字符串
sha256  长度为64的十六进制字符串
sha512  长度为128的十六进制字符串
"""
hs = hashlib.sha1() 
hs = hashlib.sha256()
hs = hashlib.sha512()
hs.update("abc1234".encode())
res = hs.hexdigest()
print(res , len(res))

# ### hmac
"""hmac 加密的字符串,安全性更高不易破解"""
import hmac
# 数据要求是字节流
key = b"xboyww_"
msg = b"abcd"
hm = hmac.new(key , msg ) # 3.7/8 => 指定 digestmod="md5"
res = hm.hexdigest()
print(res , len(res))

# 动态加盐
import os
# 随机返回指定长度的二进制字节流
key = os.urandom(32)
print(key , len(key))

msg = b"abcd"
hm = hmac.new(key,msg)
res = hm.hexdigest()
print(res)

```

### 📖 要点讲解

- ### hashlib (作用:密码加密)

- (2) 把想要加密的字符串通过update更新到hs对象中进行处理 (数据是字节流)

- 加盐(加入一个特殊的关键字,大大的增加密码的复杂度,防止密码被破解)

---

## 6. 1.client.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day09_黏包_大小文件的校验_tcp登录_socketserver_进程_join守护进程/代码/3.tcp登录/1.client.py", line 5, in <module>
    sk.connect( ("127.0.0.1",9000)  )
ConnectionRefusedError: [Errno 111] Connection refused

```

### 💻 完整代码

```python

# ### 客户端
import socket
import json
sk = socket.socket()
sk.connect( ("127.0.0.1",9000)  )

# 处理收发数据的逻辑
usr = input("请输入您的用户名:>>>")
pwd = input("请输入您的密码:>>>")
# 把账号密码封装到字典中
dic = {"usrname":usr,"password":pwd,"operate":"login"}
# 通过json把字典序列化成字符串
res = json.dumps(dic)
# 把字符串转换成字节流发送给服务端验证;
sk.send(res.encode())

# 接受服务端发送过来的状态码
res_msg = sk.recv(1024).decode() # 字节流 -> 字符串
dic_code = json.loads(res_msg)# 字符串 -> 字典

if dic_code["code"] == 200:
	print("恭喜你! 登录成功")
else:
	print("抱歉! 登录失败")

sk.close()

```

---

## 7. 1.server.py

### 📋 运行结果

```

执行超时（可能是交互式程序）

```

### 💻 完整代码

```python

# ### 服务端
import socket
import hashlib
import json

def get_md5_code(usr,pwd):
	hs = hashlib.md5(usr.encode())
	hs.update(pwd.encode())
	return hs.hexdigest()
	
# print(get_md5_code("zhangsan","333"))
sk = socket.socket()
sk.bind( ("127.0.0.1",9000) )
sk.listen()

conn,addr = sk.accept()

# 处理收发数据的逻辑
msg = conn.recv(1024).decode()
# print(msg ,type(msg)) # {"usrname": "111", "password": "222", "operate": "login"} <class 'str'>
dic = json.loads(msg)
# print(dic ,type(dic))

sign = False
with open("userinfo.txt",mode="r",encoding="utf-8") as fp:
	for line in fp:
		usr,pwd = line.strip().split(":")
		print(usr,pwd) 
		if usr == dic["usrname"] and pwd == get_md5_code(dic["usrname"],dic["password"]):
			# 如果状态码是200 代表登录成功
			res = {"code":200}
			res_msg = json.dumps(res).encode()
			conn.send(res_msg)
			sign = True
			break

if sign == False:
	# 如果状态码是400 代表登录失败
	res = {"code":400}
	res_msg = json.dumps(res).encode()
	conn.send(res_msg)
	
conn.close()
sk.close()

```

### 📖 要点讲解

- print(get_md5_code("zhangsan","333"))

- print(msg ,type(msg)) # {"usrname": "111", "password": "222", "operate": "login"} <class 'str'>

- print(dic ,type(dic))

---

## 8. 1.client_tcp循环消息.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day09_黏包_大小文件的校验_tcp登录_socketserver_进程_join守护进程/代码/4.socketserver/1.client_tcp循环消息.py", line 5, in <module>
    sk.connect( ("127.0.0.1",9000)  )
ConnectionRefusedError: [Errno 111] Connection refused

```

### 💻 完整代码

```python

# ### 客户端
import socket
import json
sk = socket.socket()
sk.connect( ("127.0.0.1",9000)  )

# 处理收发数据的逻辑
while True:
	sk.send(b"i love you")
	print(sk.recv(1024).decode())

sk.close()

```

---

## 9. 1.server_tcp循环消息.py

### 📋 运行结果

```

执行超时（可能是交互式程序）

```

### 💻 完整代码

```python

# ### 服务端
import socket
import hashlib
import json

sk = socket.socket()
sk.bind( ("127.0.0.1",9000) )
sk.listen()

# 处理收发数据的逻辑
while True:
	# 循环等待建立三次握手连接
	conn,addr = sk.accept()
	# 当此次连接结束之后,为了防止服务端结束.外层套了一个while 循环,等待下一次连接
	while True:
		msg = conn.recv(1024)
		print(msg.decode())
		conn.send(msg.decode().upper().encode())
	# 四次挥手
	conn.close()
		
sk.close()

```

### 📖 要点讲解

- 当此次连接结束之后,为了防止服务端结束.外层套了一个while 循环,等待下一次连接

---

## 10. 2.client.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day09_黏包_大小文件的校验_tcp登录_socketserver_进程_join守护进程/代码/1.黏包/2.client.py", line 5, in <module>
    sk.connect(  ("127.0.0.1",9000) )
ConnectionRefusedError: [Errno 111] Connection refused

```

### 💻 完整代码

```python

# ### 客户端
import socket
import time
sk = socket.socket()
sk.connect(  ("127.0.0.1",9000) )

time.sleep(1)
res = sk.recv(1) 
num = int(res.decode("utf-8"))
print(num , type(num))
print(sk.recv(num))
print(sk.recv(1024))

sk.close()

```

---

## 11. 2.server.py

### 📋 运行结果

```

执行超时（可能是交互式程序）

```

### 💻 完整代码

```python

# ### 服务端
import socket
sk = socket.socket()
sk.bind( ("127.0.0.1",9000)  )
sk.listen()

conn,addr = sk.accept()

# 收发数据的逻辑
conn.send("6".encode())
conn.send("hello,".encode())
conn.send("world".encode())

# 四次挥手
conn.close()
# 退还端口
sk.close()

```

---

## 12. 2.join.py

### 📋 运行结果

```

3子进程id>>>181681 4父进程id>>>181526
1子进程id>>>181682 2父进程id>>>181681
1000

```

### 💻 完整代码

```python

# ### join的使用  : 用来同步子父进程的
"""(必须等待当前子进程执行完毕之后,再去打开阻塞放行,执行下面的代码)"""

from multiprocessing import Process
import time,random
# 1.join的基本使用
"""
def func():
	print("发送第一封邮件~")
	
if __name__ == "__main__":
	p = Process(target=func)
	p.start()
	
	# time.sleep(1)
	p.join()
	
	print("发送第二封邮件 ... ")
"""

# 2.多个子进程配合join使用

'''
def func(index):
	time.sleep(random.uniform(0.1,0.9))
	print("发送%s封邮件" % (index) )
	
if __name__ == "__main__":
	lst = []
	for i in range(1,11):
		p = Process(target=func,args=(i,))	
		p.start()
		# 当前程序会变成同步
		# p.join()
		# 把所有的进程对象都塞到列表之后,此刻仍然是异步并发所有进程
		lst.append(p)
		
	# p.join()
	# print(lst)	
	"""
		为了确保子进程全部执行结束之后,在执行主进程,通过循环列表加join的形式添加阻塞,直到所有子进程执行完毕为止
	"""
	for i in lst:
		i.join()
	
	print("主进程负责发送最后一封邮件")
'''
# ### 使用自定义类的方法创建进程(扩展)
"""
自定义类时的要求:
(1) 必须继承Process这个类
(2) 把所有进程执行的逻辑写在run方法里面
"""

import os
# (1) 基本语法
'''
class MyProcess(Process):
	# run这个名字不能随意改变 <=> handle
	def run(self):
		print("1子进程id>>>{} 2父进程id>>>{}".format(os.getpid(),os.getppid()))
		
if __name__ == "__main__":
	p = MyProcess()
	p.start()
	print("3子进程id>>>{} 4父进程id>>>{}".format(os.getpid(),os.getppid()))
'''
# (2) 带有参数的自定义进程类
class MyProcess(Process):
	def __init__(self,arg):
		# 必须调用父类的构造方法(初始化系统的相应属性)
		super().__init__()
		# 给传进来的参数初始化
		self.arg = arg		
		
	def run(self):
		print("1子进程id>>>{} 2父进程id>>>{}".format(os.getpid(),os.getppid()))
		print(self.arg)
	
if __name__ == "__main__":
	p = MyProcess(1000)
	p.start()
	print("3子进程id>>>{} 4父进程id>>>{}".format(os.getpid(),os.getppid()))
	
```

### 📖 要点讲解

- ### join的使用  : 用来同步子父进程的

- 把所有的进程对象都塞到列表之后,此刻仍然是异步并发所有进程

- ### 使用自定义类的方法创建进程(扩展)

- run这个名字不能随意改变 <=> handle

- 必须调用父类的构造方法(初始化系统的相应属性)

---

## 13. 2.文件校验.py

### 📋 运行结果

```

f42910ee62d0e6af25f6abb3fccbdc94 f42910ee62d0e6af25f6abb3fccbdc94
23974d3a6c3a0142c20a53c718b692ec
23974d3a6c3a0142c20a53c718b692ec
f42910ee62d0e6af25f6abb3fccbdc94 f42910ee62d0e6af25f6abb3fccbdc94
f42910ee62d0e6af25f6abb3fccbdc94 f42910ee62d0e6af25f6abb3fccbdc94

```

### 💻 完整代码

```python

# ### 文件校验
import hashlib
"""
如果文件模式是r模式
fp.read(3) 读取的是3个字符

如果文件模式是rb模式
fp.read(3) 读取的是3个字节
"""

# (1) 针对于小文件的内容校验
def check_md5(file):
	hs = hashlib.md5()	
	with open(file,mode="rb") as fp:		
		hs.update(fp.read())
	return hs.hexdigest()

res1 = check_md5("ceshi1.txt")
res2 = check_md5("ceshi2.txt")
print(res1 , res2)

# (2) 针对于大文件的内容校验
# 原理
hs = hashlib.md5()	
hs.update("昨天飞机晚点了,原计划11点55分到深圳,结果6点才到深圳".encode())
print(hs.hexdigest()) # 23974d3a6c3a0142c20a53c718b692ec
# 分批加密和单独一次加密结果一致
hs = hashlib.md5()	
hs.update("昨天飞机晚点了,原计划11点55分到深圳,".encode())
hs.update("结果6点才到深圳".encode())
print(hs.hexdigest())

# 1.大文件校验,分批加密
def check_md5(file):
	hs = hashlib.md5()	
	with open(file,mode="rb") as fp:
		while True:
			# 一次最多读取10个字节
			content = fp.read(10)
			if content:
				hs.update(content)
			else:
				break
		return hs.hexdigest()

res1 = check_md5("ceshi1.txt")
res2 = check_md5("ceshi2.txt")
print(res1 , res2)

# 2.大文件校验,通过计算字节大小实现的;
import os 
def check_md5(file):
	file_size = os.path.getsize(file)
	hs = hashlib.md5()	
	with open(file,mode="rb") as fp:
		while file_size:
			# 一次最多读取10个字节
			content = fp.read(10)
			hs.update(content)
			file_size -= len(content)
		return hs.hexdigest()

res1 = check_md5("ceshi1.txt")
res2 = check_md5("ceshi2.txt")
print(res1 , res2)

```

---

## 14. 2.client_udp循环.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day09_黏包_大小文件的校验_tcp登录_socketserver_进程_join守护进程/代码/4.socketserver/2.client_udp循环.py", line 13, in <module>
    msg,addr = sk.recvfrom(1024)	
               ^^^^^^^^^^^^^^^^^
ConnectionRefusedError: [Errno 111] Connection refused

```

### 💻 完整代码

```python

# ### 客户端
import socket
import json
sk = socket.socket(type=socket.SOCK_DGRAM)
sk.connect( ("127.0.0.1",9000)  )

# 处理收发数据的逻辑
while True:
	message = "you can you up"
	# 发送
	sk.sendto(message.encode("utf-8") , ("127.0.0.1",9000) )
	# 接受
	msg,addr = sk.recvfrom(1024)	
	print(msg.decode())
sk.close()

```

---

## 15. 2.server_udp循环.py

### 📋 运行结果

```

执行超时（可能是交互式程序）

```

### 💻 完整代码

```python

# ### 服务端
"""
tcp协议下,默认只有四次挥手之后,新的客户端才可以与服务端建立连接
udp协议下,默认可以同一时间与多个客户端进行数据交流
"""

import socket
import hashlib
import json

sk = socket.socket(type=socket.SOCK_DGRAM)
sk.bind( ("127.0.0.1",9000) )

while True:
	# 接受
	msg,cli_addr = sk.recvfrom(1024)
	print(msg.decode())
	sk.sendto( msg.decode().upper().encode(), cli_addr )
		
sk.close()

```

---

## 16. 3.client.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day09_黏包_大小文件的校验_tcp登录_socketserver_进程_join守护进程/代码/1.黏包/3.client.py", line 5, in <module>
    sk.connect(  ("127.0.0.1",9000) )
ConnectionRefusedError: [Errno 111] Connection refused

```

### 💻 完整代码

```python

# ### 客户端
import socket
import time
sk = socket.socket()
sk.connect(  ("127.0.0.1",9000) )

time.sleep(1)
res = sk.recv(8) 
num = int(res.decode("utf-8"))
print(num , type(num))
print(sk.recv(num))
print(sk.recv(1024))

sk.close()

```

---

## 17. 3.server.py

### 📋 运行结果

```

执行超时（可能是交互式程序）

```

### 💻 完整代码

```python

# ### 服务端
import socket
sk = socket.socket()
sk.bind( ("127.0.0.1",9000)  )
sk.listen()

conn,addr = sk.accept()
"10"  "120"
# 收发数据的逻辑
conn.send("00000120".encode())
strvar = "hello," * 20
conn.send(strvar.encode())
conn.send("world".encode())

# 四次挥手
conn.close()
# 退还端口
sk.close()

"""
print(int("00001234"))
print(int("00000123"))
print(int("00000017"))
print(int("00000009"))
"""

```

---

## 18. 3.守护进程.py

### 📋 运行结果

```

当前3号服务器功能:统计财务报表 ... 
当前服务器状态异常: 请报修

```

### 💻 完整代码

```python

# ### 守护进程
"""
守护进程守护的主进程,如果主进程代码执行结束了,意味着守护进程立刻终止.

进程对象.daemon = True
设置守护进程,需要在start调用之前设置

默认情况下,主进程会等待所有子进程执行结束之后在终止程序
守护进程会在主进程代码执行结束的时候,直接杀死.

"""
from multiprocessing import Process
# (1) 基本语法
"""
def func():
	print("start .. 当前子进程")
	print("end   .. 结束当前子进程")
	
if __name__ == "__main__":
	p = Process(target=func)
	# 设置子进程p为守护进程
	p.daemon = True
	p.start()
	
	print("主进程执行结束 .. ")
"""

# (2) 多个子进程的场景
"""
import time
def func1():
	count = 1
	while True:
		print("*" * count )
		time.sleep(0.5)
		count += 1

def func2():
	print("start func2 执行当前子进程")
	time.sleep(2)
	print("end   func2 结束当前子进程")
	
if __name__ == "__main__":
	p1 = Process(target=func1)
	p2 = Process(target=func2)
	
	# 设置p1进程为守护进程
	p1.daemon = True
	
	p1.start()
	p2.start()
	
	# 等到第二个子进程执行结束之后,在放行主进程的代码
	# 主进程代码执行结束时,会立刻杀死守护进行;
	p2.join()
	
	print("主进程执行结束 .. ")
"""

# (3) 守护进程的实际用途: 监控报活
import time
def alive():
	while True:
		time.sleep(0.5)
		print("给监控服务器发消息: 当前3号服务器功能正常~ i am ok")
	
def func():
	while True:
		try:
			time.sleep(3)
			print("当前3号服务器功能:统计财务报表 ... ")
			# 主动抛出异常
			raise RuntimeError
		except:
			break

if __name__ == "__main__":
	p1 = Process(target=func)
	p1.start()
	
	p2 = Process(target=alive)
	# 设置alive这个任务为守护进程
	p2.daemon = True
	p2.start()
	
	# 只要func任务不断开,当前服务器就会一直给监控服务器报活
	p1.join()
	
	print("当前服务器状态异常: 请报修")
	
```

### 📖 要点讲解

- 等到第二个子进程执行结束之后,在放行主进程的代码

- 主进程代码执行结束时,会立刻杀死守护进行;

- 只要func任务不断开,当前服务器就会一直给监控服务器报活

---

## 19. 3.client_socketserver语法.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day09_黏包_大小文件的校验_tcp登录_socketserver_进程_join守护进程/代码/4.socketserver/3.client_socketserver语法.py", line 5, in <module>
    sk.connect( ("127.0.0.1",9000) )
ConnectionRefusedError: [Errno 111] Connection refused

```

### 💻 完整代码

```python

# 客户端
import socket

sk = socket.socket()
sk.connect( ("127.0.0.1",9000) )
# 收发数据的逻辑

sk.close()

```

---

## 20. 3.serve_socketserver语法.py

### 📋 运行结果

```

执行超时（可能是交互式程序）

```

### 💻 完整代码

```python

# 服务端
import socketserver

class MyServer(socketserver.BaseRequestHandler):
	# 必须使用handle的函数名,系统底层会默认调用
	def handle(self):
		print("我是handle 方法 ... ")
		
# ThreadingTCPServer( 地址,自定义类 )
server = socketserver.ThreadingTCPServer( ("127.0.0.1",9000) , MyServer )
server.serve_forever()

```

### 📖 要点讲解

- 必须使用handle的函数名,系统底层会默认调用

- ThreadingTCPServer( 地址,自定义类 )

---

## 21. 4.client.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day09_黏包_大小文件的校验_tcp登录_socketserver_进程_join守护进程/代码/1.黏包/4.client.py", line 6, in <module>
    sk.connect(  ("127.0.0.1",9000) )
ConnectionRefusedError: [Errno 111] Connection refused

```

### 💻 完整代码

```python

# ### 客户端
import socket
import time
import struct
sk = socket.socket()
sk.connect(  ("127.0.0.1",9000) )

# 接受数据的长度
res = sk.recv(4)
tup = struct.unpack("i",res)
print(tup)
# 接受真实的数据
print(sk.recv(tup[0]).decode())
# 接受接下来的数据(以测试是否黏包)
print(sk.recv(1024).decode())

sk.close()

```

---

## 22. 4.server.py

### 📋 运行结果

```

执行超时（可能是交互式程序）

```

### 💻 完整代码

```python

# ### 服务端
import socket
import struct
sk = socket.socket()
sk.bind( ("127.0.0.1",9000)  )
sk.listen()

conn,addr = sk.accept()

# 收发数据的逻辑
strvar = input("请输入要发送的数据内容>>>:")
msg = strvar.encode()
# 计算总大小
length = len(msg)

res = struct.pack("i",length)
# 发送打包后的数据(内容包含了数据的总长度)
conn.send(res)
conn.send(msg)
conn.send("来了深圳就是深圳人,可惜爱不起,房价太贵".encode())

# 四次挥手
conn.close()
# 退还端口
sk.close()

"""
print(int("00001234"))
print(int("00000123"))
print(int("00000017"))
print(int("00000009"))
"""

```

### 📖 要点讲解

- 发送打包后的数据(内容包含了数据的总长度)

---

## 23. 4.client_socketserver并发循环发消息.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day09_黏包_大小文件的校验_tcp登录_socketserver_进程_join守护进程/代码/4.socketserver/4.client_socketserver并发循环发消息.py", line 5, in <module>
    sk.connect( ("127.0.0.1",9001) )
ConnectionRefusedError: [Errno 111] Connection refused

```

### 💻 完整代码

```python

# 客户端
import socket

sk = socket.socket()
sk.connect( ("127.0.0.1",9001) )
# 收发数据的逻辑
while True:
	# 发送数据
	sk.send(b"no can no bb")
	# 接受数据
	msg = sk.recv(1024)
	print(msg.decode())
sk.close()

```

---

## 24. 4.server_socketserver并发循环发消息.py

### 📋 运行结果

```

执行超时（可能是交互式程序）

```

### 💻 完整代码

```python

# 服务端
import socketserver

class MyServer(socketserver.BaseRequestHandler):
	# 必须使用handle的函数名,系统底层会默认调用
	def handle(self):
		# conn 三次握手连接后的对象
		print(self.request) 
		# addr 客户端的ip端口号
		print(self.client_address) # addr
		"""
		<socket.socket fd=456, family=AddressFamily.AF_INET, type=SocketKind.SOCK_STREAM, proto=0, laddr=('127.0.0.1', 9001), raddr=('127.0.0.1', 54842)>
		('127.0.0.1', 54842)
		我是handle 方法 ... 	

		socketserver 模块中的handle方法写的内容是七剑下天山中的第五步,
		剩下的所有内容,socketserver都已经封装完毕
		第五步写到handle方法里即可
		"""
		
		while True:
			# 接受数据
			res = self.request.recv(1024)
			print(res.decode())
			# 发送数据
			self.request.send(res.decode().upper().encode())
	
		print("我是handle 方法 ... ")
		
# ThreadingTCPServer( 地址,自定义类 )
server = socketserver.ThreadingTCPServer( ("127.0.0.1",9001) , MyServer )
server.serve_forever()

```

### 📖 要点讲解

- 必须使用handle的函数名,系统底层会默认调用

- ThreadingTCPServer( 地址,自定义类 )

---

## 🖼️ 参考资料

![黏包.png](./assets/黏包.png)

![多级反馈.png](./assets/多级反馈.png)

![并发_并行.png](./assets/并发_并行.png)

![监控报活.png](./assets/监控报活.png)

![1555372027666.png](./assets/1555372027666.png)

![1555372055442.png](./assets/1555372055442.png)

![1555372108386.png](./assets/1555372108386.png)

![1555372355580.png](./assets/1555372355580.png)

![1555374519652.png](./assets/1555374519652.png)

![1555374663853.png](./assets/1555374663853.png)

![1555454444379.png](./assets/1555454444379.png)

![1555454621256.png](./assets/1555454621256.png)

![1555456389523.png](./assets/1555456389523.png)

![1555906308602.png](./assets/1555906308602.png)

![1555906852982.png](./assets/1555906852982.png)

![1559165147948.png](./assets/1559165147948.png)

![1559165234479.png](./assets/1559165234479.png)

![1559171471044.png](./assets/1559171471044.png)

![生产者消费者.png](./assets/生产者消费者.png)

![socketserver语法.png](./assets/socketserver语法.png)
