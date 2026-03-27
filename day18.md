# Day 18: day18 django初体验 正则表达式 正则路由url 正则路由补充 视图语法 模板语法 图书管理系统

> 对应原课程：day18_django初体验_正则表达式_正则路由url_正则路由补充_视图语法_模板语法_图书管理系统

---

## 1. manage.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day18_django初体验_正则表达式_正则路由url_正则路由补充_视图语法_模板语法_图书管理系统/web1005/manage.py", line 10, in main
    from django.core.management import execute_from_command_line
ModuleNotFoundError: No module named 'django'

The above exception was the direct cause of the following exception:

Traceback (most recent call last):
  File "/tmp/python3_course/day18_django初体验_正则表达式_正则路由url_正则路由补充_视图语法_模板语法_图书管理系统/web1005/manage.py", line 21, in <module>
    main()
  File "/tmp/python3_course/day18_django初体验_正则表达式_正则路由url_正则路由补充_视图语法_模板语法_图书管理系统/web1005/manage.py", line 12, in main
    raise ImportError(
ImportError: Couldn't import Django. Are you sure it's installed and available on your PYTHONPATH environment variable? Did you forget to activate a virtual environment?

```

### 💻 完整代码

```python

#!/usr/bin/env python
"""Django's command-line utility for administrative tasks."""
import os
import sys

def main():
    os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'web1005.settings')
    try:
        from django.core.management import execute_from_command_line
    except ImportError as exc:
        raise ImportError(
            "Couldn't import Django. Are you sure it's installed and "
            "available on your PYTHONPATH environment variable? Did you "
            "forget to activate a virtual environment?"
        ) from exc
    execute_from_command_line(sys.argv)

if __name__ == '__main__':
    main()

```

---

## 2. __init__.py

### 💻 完整代码

```python

```

---

## 3. admin.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day18_django初体验_正则表达式_正则路由url_正则路由补充_视图语法_模板语法_图书管理系统/web1005/dj1_touch/admin.py", line 1, in <module>
    from django.contrib import admin
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.contrib import admin

# Register your models here.

```

### 📖 要点讲解

- Register your models here.

---

## 4. apps.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day18_django初体验_正则表达式_正则路由url_正则路由补充_视图语法_模板语法_图书管理系统/web1005/dj1_touch/apps.py", line 1, in <module>
    from django.apps import AppConfig
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.apps import AppConfig

class Dj1TouchConfig(AppConfig):
    name = 'dj1_touch'

```

---

## 5. models.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day18_django初体验_正则表达式_正则路由url_正则路由补充_视图语法_模板语法_图书管理系统/web1005/dj1_touch/models.py", line 1, in <module>
    from django.db import models
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.db import models

# Create your models here.

```

### 📖 要点讲解

- Create your models here.

---

## 6. tests.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day18_django初体验_正则表达式_正则路由url_正则路由补充_视图语法_模板语法_图书管理系统/web1005/dj1_touch/tests.py", line 1, in <module>
    from django.test import TestCase
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.test import TestCase

# Create your tests here.

```

### 📖 要点讲解

- Create your tests here.

---

## 7. views.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day18_django初体验_正则表达式_正则路由url_正则路由补充_视图语法_模板语法_图书管理系统/web1005/dj1_touch/views.py", line 1, in <module>
    from django.shortcuts import render,HttpResponse
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.shortcuts import render,HttpResponse
import os,time
# Create your views here.

def index(request):
	return render(request,"index.html")

def login1(request):
	BASE_DIR = os.path.dirname(os.path.dirname(os.path.abspath(__file__)))
	# D:\周末5_\web1005 动态获取该网站的根目录
	return HttpResponse(BASE_DIR)

def login2(request):
	mytime = time.ctime()
	return render(request,"login.html",{'mytime':mytime} )

def login3(request):
	print(request.method)
	# 获取表单数据
	print(request.POST.get('username'))
	# {'aaa': ['1'], 'bbb': ['2']}>
	print(request.GET) # http://127.0.0.1:8001/login3/?aaa=1&bbb=2
	return HttpResponse('ok')

```

### 📖 要点讲解

- Create your views here.

- D:\周末5_\web1005 动态获取该网站的根目录

- {'aaa': ['1'], 'bbb': ['2']}>

---

## 8. __init__.py

### 💻 完整代码

```python

```

---

## 9. __init__.py

### 💻 完整代码

```python

```

---

## 10. admin.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day18_django初体验_正则表达式_正则路由url_正则路由补充_视图语法_模板语法_图书管理系统/web1005/dj5_bookProject/admin.py", line 1, in <module>
    from django.contrib import admin
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.contrib import admin

# Register your models here.

```

### 📖 要点讲解

- Register your models here.

---

## 11. apps.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day18_django初体验_正则表达式_正则路由url_正则路由补充_视图语法_模板语法_图书管理系统/web1005/dj5_bookProject/apps.py", line 1, in <module>
    from django.apps import AppConfig
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.apps import AppConfig

class Dj5BookprojectConfig(AppConfig):
    name = 'dj5_bookProject'

```

---

## 12. models.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day18_django初体验_正则表达式_正则路由url_正则路由补充_视图语法_模板语法_图书管理系统/web1005/dj5_bookProject/models.py", line 1, in <module>
    from django.db import models
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.db import models

# Create your models here.

```

### 📖 要点讲解

- Create your models here.

---

## 13. tests.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day18_django初体验_正则表达式_正则路由url_正则路由补充_视图语法_模板语法_图书管理系统/web1005/dj5_bookProject/tests.py", line 1, in <module>
    from django.test import TestCase
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.test import TestCase

# Create your tests here.

```

### 📖 要点讲解

- Create your tests here.

---

## 14. urls.py

### 📋 运行结果

```

错误：/tmp/python3_course/day18_django初体验_正则表达式_正则路由url_正则路由补充_视图语法_模板语法_图书管理系统/web1005/dj5_bookProject/urls.py:10: SyntaxWarning: invalid escape sequence '\d'
  re_path('delete/(\d+\.\d+)',views.delete) # (\d+(?:\.\d+)?)
Traceback (most recent call last):
  File "/tmp/python3_course/day18_django初体验_正则表达式_正则路由url_正则路由补充_视图语法_模板语法_图书管理系统/web1005/dj5_bookProject/urls.py", line 2, in <module>
    from django.contrib import admin
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.contrib import admin
from django.urls import path, re_path, include
from dj5_bookProject import views

urlpatterns = [

	path('index/', views.index),
	path('add/',views.add),
	re_path('delete/(\d+\.\d+)',views.delete) # (\d+(?:\.\d+)?)

]

```

---

## 15. views.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day18_django初体验_正则表达式_正则路由url_正则路由补充_视图语法_模板语法_图书管理系统/web1005/dj5_bookProject/views.py", line 1, in <module>
    from django.shortcuts import render,HttpResponse,redirect
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.shortcuts import render,HttpResponse,redirect
import time,json
# Create your views here.

def get_data():
	lst_new = []
	with open("data.json",mode="r",encoding="utf-8") as fp:
		lst = fp.readlines()
		for i in lst:
			print(i ,type(i))
			lst_new.append(json.loads(i))
	return lst_new

def index(request):
	lst = get_data()
	'''
	class Book():
		def __init__(self,title,price,publish):
			self.title = title
			self.price = price
			self.publish = publish
	book1 = Book('水浒传1',10,"清华大学出版社1")
	book2 = Book('水浒传2', 11, "清华大学出版社2")
	book3 = Book('水浒传3', 11, "清华大学出版社43")
	book4 = Book('水浒传4', 13, "清华大学出版社5")
	book5 = Book('水浒传5', 14, "清华大学出版社6")
	lst = [book1,book2,book3,book4,book5]
	'''
	return render(request,"dj5_bookProject/index.html",locals())

def add(request):
	name = 1111
	if request.method == "GET":
		return render(request,"dj5_bookProject/add.html",locals())
	elif request.method == "POST":
		title = request.POST.get("title")
		price = request.POST.get("price")
		publish = request.POST.get("publish")

		data = {'title':title,"price":price,'publish':publish,"book_id":time.time()}
		with open("data.json",mode="a+",encoding="utf-8") as fp:
			fp.write(json.dumps(data)+"\n")

		return redirect("/dj5_bookProject/index/")

def delete(request,book_id):
	'''[字典1,字典2,字典3,字典3]'''
	'''
	{"title": "1111", "price": "2222", "publish": "3333", "book_id": 1606648825.3030334}
	 <class 'str'>
	{"title": "222", "price": "222", "publish": "2222", "book_id": 1606648831.6329746}
	 <class 'str'>
	1606648825.3030334 <class 'float'> 1606648825.3030334
	1606648831.6329746 <class 'float'> 1606648825.3030334
	'''

	lst_new = get_data()
	with open("data.json",mode="w+",encoding="utf-8") as fp:
		for i in lst_new:
			print(i['book_id'] , type(i['book_id']) ,book_id ,type(book_id))
			# 如果找到的数据的id正好是传过来的id号,为字符串类型;那么该条数据不会被重新记录在文件中,等价于删除;
			if str(i['book_id']) == book_id:
				continue
			fp.write(json.dumps(i) + '\n')

	return redirect("/dj5_bookProject/index/")

```

### 📖 要点讲解

- Create your views here.

- 如果找到的数据的id正好是传过来的id号,为字符串类型;那么该条数据不会被重新记录在文件中,等价于删除;

---

## 16. __init__.py

### 💻 完整代码

```python

```

---

## 17. __init__.py

### 💻 完整代码

```python

```

---

## 18. admin.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day18_django初体验_正则表达式_正则路由url_正则路由补充_视图语法_模板语法_图书管理系统/web1005/dj4_template/admin.py", line 1, in <module>
    from django.contrib import admin
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.contrib import admin

# Register your models here.

```

### 📖 要点讲解

- Register your models here.

---

## 19. apps.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day18_django初体验_正则表达式_正则路由url_正则路由补充_视图语法_模板语法_图书管理系统/web1005/dj4_template/apps.py", line 1, in <module>
    from django.apps import AppConfig
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.apps import AppConfig

class Dj4TemplateConfig(AppConfig):
    name = 'dj4_template'

```

---

## 20. models.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day18_django初体验_正则表达式_正则路由url_正则路由补充_视图语法_模板语法_图书管理系统/web1005/dj4_template/models.py", line 1, in <module>
    from django.db import models
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.db import models

# Create your models here.

```

### 📖 要点讲解

- Create your models here.

---

## 21. tests.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day18_django初体验_正则表达式_正则路由url_正则路由补充_视图语法_模板语法_图书管理系统/web1005/dj4_template/tests.py", line 1, in <module>
    from django.test import TestCase
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.test import TestCase

# Create your tests here.

```

### 📖 要点讲解

- Create your tests here.

---

## 22. urls.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day18_django初体验_正则表达式_正则路由url_正则路由补充_视图语法_模板语法_图书管理系统/web1005/dj4_template/urls.py", line 2, in <module>
    from django.contrib import admin
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.contrib import admin
from django.urls import path, re_path
from dj4_template import views
urlpatterns = [
	path('index/', views.index),

]

```

---

## 23. views.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day18_django初体验_正则表达式_正则路由url_正则路由补充_视图语法_模板语法_图书管理系统/web1005/dj4_template/views.py", line 1, in <module>
    from django.shortcuts import render,HttpResponse
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.shortcuts import render,HttpResponse
import time,datetime
# Create your views here.
def index(request):
	# return HttpResponse('ok')
	class Person():
		def __init__(self,name,age,sex):
			self.name = name
			self.age = age
			self.sex = sex
	chenyong = Person("陈勇",80,"男性")
	zhaoqiang = Person("赵强",20,"女性")
	zhangjunwen = Person("张俊文",30,"兽性")

	# 一.变量渲染
	name = None
	age = 98
	books = ['西游记',"红楼梦","三国演义","水浒传"]
	size = 11234234234
	value = "hello world"
	pinglun = "你好啊胜多负少沙发沙发是"
	lst = [chenyong , zhaoqiang ,zhangjunwen ]
	content = "<script>alert('大坏蛋')</script>"
	now = datetime.datetime.now() # 获取日期时间;
	# dic = {'name': name, "books": books,'lst':lst,'now':now,'size':size,'value':value,"pinglun":pinglun,'content':content,"age":18}
	# locals 获取当前作用域中的所有变量;返回的是字典;里面塞满了当前作用域中的所有局部变量

	# return render(request,'dj4_template/index.html',dic)
	print(locals())
	'''
	{
		'now': datetime.datetime(2020, 11, 29, 17, 0, 28, 298763), 
		'content': "<script>alert('大坏蛋')</script>", 
		'lst': [<dj4_template.views.index.<locals>.Person object at 0x000001A5E08CCE48>, 
		<dj4_template.views.index.<locals>.Person object at 0x000001A5E08CC1D0>, <dj4_template.views.index.<locals>.Person object at 0x000001A5E0906E48>], 
		'pinglun': '你好啊胜多负少沙发沙发是', 'value': 'hello world', 'size': 11234234234, 'books': ['西游记', '红楼梦', '三国演义', '水浒传'], 
		'age': 18, 'name': None, 'zhangjunwen': <dj4_template.views.index.<locals>.Person object at 0x000001A5E0906E48>, 
		'zhaoqiang': <dj4_template.views.index.<locals>.Person object at 0x000001A5E08CC1D0>, 
		'chenyong': <dj4_template.views.index.<locals>.Person object at 0x000001A5E08CCE48>, 'Person': <class 'dj4_template.views.index.<locals>.Person'>, 
		'request': <WSGIRequest: GET '/dj4_template/index/'>
	}
	'''
	return render(request,'dj4_template/index.html',locals())

```

### 📖 要点讲解

- Create your views here.

- return HttpResponse('ok')

- dic = {'name': name, "books": books,'lst':lst,'now':now,'size':size,'value':value,"pinglun":pinglun,'content':content,"age":18}

- locals 获取当前作用域中的所有变量;返回的是字典;里面塞满了当前作用域中的所有局部变量

- return render(request,'dj4_template/index.html',dic)

---

## 24. __init__.py

### 💻 完整代码

```python

```

---

## 25. __init__.py

### 💻 完整代码

```python

```

---

## 26. admin.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day18_django初体验_正则表达式_正则路由url_正则路由补充_视图语法_模板语法_图书管理系统/web1005/dj3_views/admin.py", line 1, in <module>
    from django.contrib import admin
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.contrib import admin

# Register your models here.

```

### 📖 要点讲解

- Register your models here.

---

## 27. apps.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day18_django初体验_正则表达式_正则路由url_正则路由补充_视图语法_模板语法_图书管理系统/web1005/dj3_views/apps.py", line 1, in <module>
    from django.apps import AppConfig
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.apps import AppConfig

class Dj3ViewsConfig(AppConfig):
    name = 'dj3_views'

```

---

## 28. models.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day18_django初体验_正则表达式_正则路由url_正则路由补充_视图语法_模板语法_图书管理系统/web1005/dj3_views/models.py", line 1, in <module>
    from django.db import models
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.db import models

# Create your models here.

```

### 📖 要点讲解

- Create your models here.

---

## 29. tests.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day18_django初体验_正则表达式_正则路由url_正则路由补充_视图语法_模板语法_图书管理系统/web1005/dj3_views/tests.py", line 1, in <module>
    from django.test import TestCase
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.test import TestCase

# Create your tests here.

```

### 📖 要点讲解

- Create your tests here.

---

## 30. urls.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day18_django初体验_正则表达式_正则路由url_正则路由补充_视图语法_模板语法_图书管理系统/web1005/dj3_views/urls.py", line 2, in <module>
    from django.contrib import admin
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.contrib import admin
from django.urls import path, re_path
from dj3_views import views
urlpatterns = [
	path('login1/', views.login1),
	path("login2/", views.login2),
	path("login3/", views.login3),

]

```

---

## 31. views.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day18_django初体验_正则表达式_正则路由url_正则路由补充_视图语法_模板语法_图书管理系统/web1005/dj3_views/views.py", line 1, in <module>
    from django.shortcuts import render,HttpResponse,redirect
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.shortcuts import render,HttpResponse,redirect
import time
# Create your views here.
def login1(request):
	# return HttpResponse("ok1")

	''''render加载的模板路径 => setting => DIRS': [os.path.join(BASE_DIR, "templates")]'''
	return render(request,"login_views.html",{'mytime':time.ctime()})

def login2(request):
	# 获取请求对象
	print(request)
	# 获取请求的方法 (GET / POST)
	print(request.method)
	# 获取请求的路径
	'''/dj3_views/login2/'''
	print(request.path)
	# 获取请求的完整路径  <WSGIRequest: GET '/dj3_views/login2/?a=1&b=2'>
	request.get_full_path()

	# 通过get方法获取所有参数
	print(request.GET)
	print(request.GET.get("a"))
	print(request.GET.get("b"))
	# 通过post方法获取所有表单数据
	print(request.POST) # <QueryDict: {'username': ['wangwen'], 'pwd': ['123']}>
	print(request.POST.get("username"))
	print(request.POST.get("pwd"))

	# 获取请求体数据 (是二进制字节流)
	print(request.body) # b'username=wangwen&pwd=123456'
	# 获取请求头数据
	print(request.headers)
	print(request.headers['User-Agent'])
	print(request.headers.get('User-Agent'))
	# 判断是否是ajax发送过来的数据
	print(request.is_ajax())

	# ========================================
	if request.method == "POST":
		username = request.POST.get("username")
		pwd = request.POST.get("pwd")
		if username == "wangwen" and pwd == "123":
			return HttpResponse('登陆成功')
		else:
			return HttpResponse('登录失败')
	else:
		a = request.GET.get('a')
		b = request.GET.get('b')
		return HttpResponse('你是get请求过来的...a={},b={}'.format(a,b))

def login3(request):
	"""
		重定向是浏览器向服务端发送了2个请求实现的,
		第一次请求,服务端恢复301 或302的状态码,并且在响应头中说明location跳转的位置
		浏览器按照location响应头对应的数据进行二次请求.实现跳转
	"""
	# http://127.0.0.1:8001  /dj3_views/login1/ 跳转的路径 直接写在redirect后面
	return redirect("/dj3_views/login1/")
	# return redirect("/dj2_urls/book/2020")

```

### 📖 要点讲解

- Create your views here.

- return HttpResponse("ok1")

- 获取请求的完整路径  <WSGIRequest: GET '/dj3_views/login2/?a=1&b=2'>

- ========================================

- http://127.0.0.1:8001  /dj3_views/login1/ 跳转的路径 直接写在redirect后面

- return redirect("/dj2_urls/book/2020")

---

## 32. __init__.py

### 💻 完整代码

```python

```

---

## 33. __init__.py

### 💻 完整代码

```python

```

---

## 34. settings.py

### 💻 完整代码

```python

"""
Django settings for web1005 project.

Generated by 'django-admin startproject' using Django 2.2.

For more information on this file, see
https://docs.djangoproject.com/en/2.2/topics/settings/

For the full list of settings and their values, see
https://docs.djangoproject.com/en/2.2/ref/settings/
"""

import os

# Build paths inside the project like this: os.path.join(BASE_DIR, ...)
BASE_DIR = os.path.dirname(os.path.dirname(os.path.abspath(__file__)))

# Quick-start development settings - unsuitable for production
# See https://docs.djangoproject.com/en/2.2/howto/deployment/checklist/

# SECURITY WARNING: keep the secret key used in production secret!
SECRET_KEY = 'rahmxp8#@rphywla5$opni$vud#-e(voe$o1zn&lg*a0v9)_&2'

# SECURITY WARNING: don't run with debug turned on in production!
DEBUG = True

ALLOWED_HOSTS = []

# Application definition

INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
]

MIDDLEWARE = [
    'django.middleware.security.SecurityMiddleware',
    'django.contrib.sessions.middleware.SessionMiddleware',
    'django.middleware.common.CommonMiddleware',
    # 'django.middleware.csrf.CsrfViewMiddleware',
    'django.contrib.auth.middleware.AuthenticationMiddleware',
    'django.contrib.messages.middleware.MessageMiddleware',
    'django.middleware.clickjacking.XFrameOptionsMiddleware',
]

ROOT_URLCONF = 'web1005.urls'

TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [os.path.join(BASE_DIR, "templates")],
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]

WSGI_APPLICATION = 'web1005.wsgi.application'

# Database
# https://docs.djangoproject.com/en/2.2/ref/settings/#databases

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': os.path.join(BASE_DIR, 'db.sqlite3'),
    }
}

# Password validation
# https://docs.djangoproject.com/en/2.2/ref/settings/#auth-password-validators

AUTH_PASSWORD_VALIDATORS = [
    {
        'NAME': 'django.contrib.auth.password_validation.UserAttributeSimilarityValidator',
    },
    {
        'NAME': 'django.contrib.auth.password_validation.MinimumLengthValidator',
    },
    {
        'NAME': 'django.contrib.auth.password_validation.CommonPasswordValidator',
    },
    {
        'NAME': 'django.contrib.auth.password_validation.NumericPasswordValidator',
    },
]

# Internationalization
# https://docs.djangoproject.com/en/2.2/topics/i18n/

LANGUAGE_CODE = 'en-us'

TIME_ZONE = 'UTC'

USE_I18N = True

USE_L10N = True

USE_TZ = True

# Static files (CSS, JavaScript, Images)
# https://docs.djangoproject.com/en/2.2/howto/static-files/

STATIC_URL = '/static/'

STATICFILES_DIRS = [
    os.path.join(BASE_DIR, "static"),
]

# 自动补齐/,通过重定向实现;
# APPEND_SLASH = False

```

### 📖 要点讲解

- Build paths inside the project like this: os.path.join(BASE_DIR, ...)

- Quick-start development settings - unsuitable for production

- See https://docs.djangoproject.com/en/2.2/howto/deployment/checklist/

- SECURITY WARNING: keep the secret key used in production secret!

- SECURITY WARNING: don't run with debug turned on in production!

- Application definition

- 'django.middleware.csrf.CsrfViewMiddleware',

- https://docs.djangoproject.com/en/2.2/ref/settings/#databases

- https://docs.djangoproject.com/en/2.2/ref/settings/#auth-password-validators

- https://docs.djangoproject.com/en/2.2/topics/i18n/

- Static files (CSS, JavaScript, Images)

- https://docs.djangoproject.com/en/2.2/howto/static-files/

---

## 35. urls.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day18_django初体验_正则表达式_正则路由url_正则路由补充_视图语法_模板语法_图书管理系统/web1005/web1005/urls.py", line 16, in <module>
    from django.contrib import admin
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

"""web1005 URL Configuration

The `urlpatterns` list routes URLs to views. For more information please see:
    https://docs.djangoproject.com/en/2.2/topics/http/urls/
Examples:
Function views
    1. Add an import:  from my_app import views
    2. Add a URL to urlpatterns:  path('', views.home, name='home')
Class-based views
    1. Add an import:  from other_app.views import Home
    2. Add a URL to urlpatterns:  path('', Home.as_view(), name='home')
Including another URLconf
    1. Import the include() function: from django.urls import include, path
    2. Add a URL to urlpatterns:  path('blog/', include('blog.urls'))
"""
from django.contrib import admin
from django.urls import path,re_path,include
from dj1_touch import  views
from dj2_urls import views as v2

urlpatterns = [

	# 1.绝对匹配
    # path('admin/', admin.site.urls),
	path('',views.index),
	path('index/',views.index),
	path('login1/' , views.login1),
	path('login2/',views.login2),
	path('login3/',views.login3),
	
	# 路由分发
	path('dj2_urls/',include('dj2_urls.urls')),
	path('dj3_views/',include('dj3_views.urls')),
	path('dj4_template/',include('dj4_template.urls')),
	path('dj5_bookProject/', include('dj5_bookProject.urls')),
]

```

### 📖 要点讲解

- path('admin/', admin.site.urls),

---

## 36. wsgi.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day18_django初体验_正则表达式_正则路由url_正则路由补充_视图语法_模板语法_图书管理系统/web1005/web1005/wsgi.py", line 12, in <module>
    from django.core.wsgi import get_wsgi_application
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

"""
WSGI config for web1005 project.

It exposes the WSGI callable as a module-level variable named ``application``.

For more information on this file, see
https://docs.djangoproject.com/en/2.2/howto/deployment/wsgi/
"""

import os

from django.core.wsgi import get_wsgi_application

os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'web1005.settings')

application = get_wsgi_application()

```

---

## 37. __init__.py

### 💻 完整代码

```python

```

---

## 38. admin.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day18_django初体验_正则表达式_正则路由url_正则路由补充_视图语法_模板语法_图书管理系统/web1005/dj2_urls/admin.py", line 1, in <module>
    from django.contrib import admin
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.contrib import admin

# Register your models here.

```

### 📖 要点讲解

- Register your models here.

---

## 39. apps.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day18_django初体验_正则表达式_正则路由url_正则路由补充_视图语法_模板语法_图书管理系统/web1005/dj2_urls/apps.py", line 1, in <module>
    from django.apps import AppConfig
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.apps import AppConfig

class Dj2UrlsConfig(AppConfig):
    name = 'dj2_urls'

```

---

## 40. models.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day18_django初体验_正则表达式_正则路由url_正则路由补充_视图语法_模板语法_图书管理系统/web1005/dj2_urls/models.py", line 1, in <module>
    from django.db import models
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.db import models

# Create your models here.

```

### 📖 要点讲解

- Create your models here.

---

## 41. tests.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day18_django初体验_正则表达式_正则路由url_正则路由补充_视图语法_模板语法_图书管理系统/web1005/dj2_urls/tests.py", line 1, in <module>
    from django.test import TestCase
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.test import TestCase

# Create your tests here.

```

### 📖 要点讲解

- Create your tests here.

---

## 42. urls.py

### 📋 运行结果

```

错误：/tmp/python3_course/day18_django初体验_正则表达式_正则路由url_正则路由补充_视图语法_模板语法_图书管理系统/web1005/dj2_urls/urls.py:23: SyntaxWarning: invalid escape sequence '\d'
  re_path("book/\d{4}",v2.book_year1),
/tmp/python3_course/day18_django初体验_正则表达式_正则路由url_正则路由补充_视图语法_模板语法_图书管理系统/web1005/dj2_urls/urls.py:33: SyntaxWarning: invalid escape sequence '\d'
  re_path('^book/(?P<year>\d{4})/(?P<month>\d{1,2})/$',v2.book_year4),
Traceback (most recent call last):
  File "/tmp/python3_course/day18_django初体验_正则表达式_正则路由url_正则路由补充_视图语法_模板语法_图书管理系统/web1005/dj2_urls/urls.py", line 16, in <module>
    from django.contrib import admin
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

"""web1005 URL Configuration

The `urlpatterns` list routes URLs to views. For more information please see:
    https://docs.djangoproject.com/en/2.2/topics/http/urls/
Examples:
Function views
    1. Add an import:  from my_app import views
    2. Add a URL to urlpatterns:  path('', views.home, name='home')
Class-based views
    1. Add an import:  from other_app.views import Home
    2. Add a URL to urlpatterns:  path('', Home.as_view(), name='home')
Including another URLconf
    1. Import the include() function: from django.urls import include, path
    2. Add a URL to urlpatterns:  path('blog/', include('blog.urls'))
"""
from django.contrib import admin
from django.urls import path,re_path
from dj2_urls import views as v2

urlpatterns = [

	# 2.正则匹配  2000  2020
	re_path("book/\d{4}",v2.book_year1),

	# 3.正则匹配+ 分组
	# re_path("book/(\d{4})",v2.book_year2),

	# 4.正则匹配 + 分组 + ^$ 以..开头 以 .. 结尾
	# http://127.0.0.1:8001/sdfsdfsfsfsdf/book/2021/3
	# re_path('^book/(\d{4})/(\d{1,2})/$',v2.book_year3),
	
	# 5.正则匹配 + 命名分组 + ^$ 以..开头 以 .. 结尾
	re_path('^book/(?P<year>\d{4})/(?P<month>\d{1,2})/$',v2.book_year4),
]

```

### 📖 要点讲解

- re_path("book/(\d{4})",v2.book_year2),

- 4.正则匹配 + 分组 + ^$ 以..开头 以 .. 结尾

- http://127.0.0.1:8001/sdfsdfsfsfsdf/book/2021/3

- re_path('^book/(\d{4})/(\d{1,2})/$',v2.book_year3),

- 5.正则匹配 + 命名分组 + ^$ 以..开头 以 .. 结尾

---

## 43. views.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day18_django初体验_正则表达式_正则路由url_正则路由补充_视图语法_模板语法_图书管理系统/web1005/dj2_urls/views.py", line 1, in <module>
    from django.shortcuts import render,HttpResponse
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.shortcuts import render,HttpResponse

# Create your views here.
def book_year1(request):
	return 	HttpResponse("ok1")

def book_year2(request,year):
	# print(year)
	return 	HttpResponse(year)

def book_year3(request,month,year):
	# print(year)
	print(year)
	print(month)
	return 	HttpResponse("年份:"+year+"月份:"+month)

def book_year4(request,month,year):
	""""year=2021  monty=3 ; book_year4(month=3,year=2020)"""
	# print(year)
	print(month)
	print(year)

	# return 	HttpResponse("年份:"+year+"月份:"+month)
	return 	HttpResponse("年份:"+year+"月份:"+month)

```

### 📖 要点讲解

- Create your views here.

- return 	HttpResponse("年份:"+year+"月份:"+month)

---

## 44. __init__.py

### 💻 完整代码

```python

```

---

## 45. 1.匹配单个字符.py

### 📋 运行结果

```

['2', '3', '4', '1']
['Y', 'W', 'E', 'R', 's', 'd', 'f', '_', '&']
['s', 'a', 'd', 'f', '2', '3', '4', '_', '你', '好']
['^', '&', '*', '%', '$', '^', '$', '%']
[' ', '\t', '\t', ' ', '\r', ' ']
['1', '2', '3', '_', '*', '(']
['\n', '\n']
['\t', '\t', '\t', '\t']
['1', '2', '3']
['aab', 'abb', 'acb']
['a1b', 'a2b', 'a3b']
['a1b', 'a2b', 'a3b']
['acb', 'adb']
['acb', 'ayb', 'adb']
['aAb', 'aDb']
['aAb', 'aDb']
['aab', 'aAb', 'aWb', 'aqb', 'a1b']
['a1/b']
['a%b', 'a&b']
['a^c', 'a-c', 'a\\c']
a\c
a\b

```

### 💻 完整代码

```python

# ### 正则表达式 - 匹配单个字符
import re
"""lst = re.findall(正则表达式,字符串)"""

# (1) 预定义字符集
# \d 匹配数字
strvar = "sdjfklj234&*(&1"
lst = re.findall("\d",strvar)
print(lst)

# \D 匹配非数字
strvar = "YWERsdf78_&"
lst = re.findall("\D",strvar)
print(lst)

# \w 匹配字母或数字或下划线     (正则函数中,支持中文的匹配)
strvar = "sadf234_^&*%$^$%你好"
lst = re.findall("\w",strvar)
print(lst)

# \W 匹配非字母或数字或下划线
strvar = "sadf234_^&*%$^$%你好"
lst = re.findall("\W",strvar)
print(lst)

# \s 匹配任意的空白符 ( " "  \t  \n \r )
strvar = " 		 \r "
lst = re.findall("\s",strvar)
print(lst)

# \S 匹配任意非空白符
strvar = " 		 \r  123_*("
lst = re.findall("\S",strvar)
print(lst)

# \n 匹配一个换行符
strvar = """
今天国庆假期结束了,兄弟们满载	而归,玩的	很困,尽	快调	整.
"""
lst = re.findall(r"\n",strvar)
print(lst)

# \t 匹配一个制表符
lst = re.findall(r"\t",strvar)
print(lst)

# (2) 字符组 [] 匹配出字符组当中列举的字符(默认选一个)
lst = re.findall("[123]","a1b2c3d4")
print(lst)

# 字符组练习
print(re.findall('a[abc]b','aab abb acb adb')) # aab abb acb
print(re.findall('a[0123456789]b','a1b a2b a3b acb ayb')) # a1b a2b a3b

# 0-9 就是0123456789
print(re.findall('a[0-9]b','a1b a2b a3b acb ayb')) # a1b a2b a3b
print(re.findall('a[abcdefg]b','a1b a2b a3b acb ayb adb')) # acb adb
# a-g 就是abcdefg 小写26个字母 a-z
print(re.findall('a[a-z]b','a1b a2b a3b acb ayb adb')) # acb ayb adb

print(re.findall('a[ABCDEFG]b','a1b a2b a3b  aAb aDb aYb')) # aAb aDb
# A-G 就是ABCDEFG
print(re.findall('a[A-G]b','a1b a2b a3b  aAb aDb aYb')) # aAb aDb
# 匹配大小写字母+数字
print(re.findall('a[0-9a-zA-Z]b','a-b aab aAb aWb aqba1b'))  #aab aAb aWb aqb a1b
print(re.findall('a[0-9][*#/]b','a1/b a2b a29b a56b a456b')) #a1/b
# ^ 除了... 
print(re.findall('a[^-+*/]b',"a%b ccaa*bda&bd")) # a%b a&b

# 匹配^-\等特殊字符时 ,需要前面加上\进行转义
strvar = "a^c a-c a\c"
lst = re.findall(r"a[\^\-\\]c",strvar)
print(lst)
print(lst[-1])

# 注意点:为了防止转义,在正则表达式中或者要匹配的字符串中,无脑加r实现匹配
strvar = r"a\b"
lst = re.findall(r"a\\b",strvar)
print(lst[0])

```

### 📖 要点讲解

- \w 匹配字母或数字或下划线     (正则函数中,支持中文的匹配)

- \s 匹配任意的空白符 ( " "  \t  \n \r )

- (2) 字符组 [] 匹配出字符组当中列举的字符(默认选一个)

- a-g 就是abcdefg 小写26个字母 a-z

- 匹配^-\等特殊字符时 ,需要前面加上\进行转义

- 注意点:为了防止转义,在正则表达式中或者要匹配的字符串中,无脑加r实现匹配

---

## 46. 2.匹配多个字符.py

### 📋 运行结果

```

['ab', 'b', 'ab', 'ab', 'b', 'ab']
['ab', 'aaaaaab', 'ab']
['b', 'ab', 'aaaaaab', 'ab', 'b', 'b', 'b', 'b', 'b', 'b']
['aaab', 'ab', 'aab', 'ab', 'aab']
['aab', 'aab', 'aab']
['aaab', 'aab', 'aab']
['大哥', '大嫂', '大爷']
['大哥']
['大爷']
[]
['大哥大嫂大爷']
[]
['大哥大嫂大爷']

```

### 💻 完整代码

```python

# ### 正则表达式 - 匹配多个字符

# (1) 量词
import re
'''1) ? 匹配0个或者1个a '''
print(re.findall('a?b','abbzab abb aab'))   #ab b ab ab b ab

'''2) + 匹配1个或者多个a '''
print(re.findall('a+b','b ab aaaaaab abb')) #ab aaaaaab ab

'''3) * 匹配0个或者多个a '''
print(re.findall('a*b','b ab aaaaaab abbbbbbb')) #  b ab aaaaaab ab b b b b b b

'''4) {m,n} 匹配m个至n个a '''
# 1 <= a <= 3 
print(re.findall('a{1,3}b','aaab ab aab abbb aaz aabb')) # aaab ab aab ab aab
# {2}  代表必须匹配2个a
print(re.findall('a{2}b','aaab ab aab abbb aaz aabb')) # aab aab aab
# {2,} 代表至少匹配2个a
print(re.findall('a{2,}b','aaab ab aab abbb aaz aabb')) # aaab aab aab

"""
^ 写在在字符串的开头,表达必须以某个字符开头
$ 写在在字符串的结尾,表达必须以某个字符结尾
当使用了^ $ 代表要把该字符串看成一个整体
"""

strvar = "大哥大嫂大爷"
print(re.findall('大.',strvar))   # 大哥 大嫂 大爷
print(re.findall('^大.',strvar))  # 大哥
print(re.findall('大.$',strvar))  # 大爷
print(re.findall('^大.$',strvar)) # []
print(re.findall('^大.*?$',strvar))   # ['大哥大嫂大爷'] 
print(re.findall('^大.*?大$',strvar)) 
print(re.findall('^大.*?爷$',strvar)) # ['大哥大嫂大爷']

```

---

## 47. 3.匹配分组.py

### 📋 运行结果

```

['wusir_good', ' alex_good', ' secret男_good']
['wusir', ' alex', ' secret男']
['wusir_good', ' alex_good', ' secret男_good']
['1.3', '9.89']
['3', '4', '3', '3', '1.3', '9.89', '10']
['3', '4', '3', '3', '1.3', '9.89', '10']
z3d4pzd
<re.Match object; span=(1, 8), match='z3d4pzd'>
z3d4pzd

```

### 💻 完整代码

```python

# ### 匹配分组 ()表达整体
import re
# (1) 分组 小括号包起来的内容会优先显示
print(re.findall('.*?_good','wusir_good alex_good secret男_good'))
print(re.findall('(.*?)_good','wusir_good alex_good secret男_good'))

# (?:) 代表不优先显示分组里面的内容,只是显示正常匹配到的内容
print(re.findall('(?:.*?)_good','wusir_good alex_good secret男_good'))

# 匹配小数 
# 3.14
strvar = "3....  ....4  .3 ...3   1.3  9.89  10"
lst = re.findall(r"\d+\.\d+",strvar)
print(lst)

# 匹配小数和整数 
lst = re.findall(r"\d+\.\d+|\d+",strvar)
print(lst)

# 使用分组改造
'''findall优先显示括号里的内容,需要加上?:取消哦优先显示,按照匹配到的内容显示'''
# ?:表示 不优先显示括号里面的内容,把括号作为一个小组,一个整体;
lst = re.findall(r"\d+(?:\.\d+)?",strvar)
print(lst)

# ### 命名分组
"""
3) (?P<组名>正则表达式) 给这个组起一个名字
4) (?P=组名) 引用之前组的名字,把该组名匹配到的内容放到当前位置
"""
# 写法一 ?P<tag1>
strvar = " z3d4pzd a1b2cab "
obj = re.search(r"(?P<tag1>.*?)\d(?P<tag2>.*?)\d(.*?)\1\2",strvar)
# 按照分组匹配内容
print(obj.group())

# 写法二
strvar = " z3d4pzd a1b2cab "
obj = re.search(r"(?P<tag1>.*?)\d(?P<tag2>.*?)\d(?P<tag3>.*?)(?P=tag1)(?P=tag2)",strvar)
print(obj)
print(obj.group())

```

### 📖 要点讲解

- (1) 分组 小括号包起来的内容会优先显示

- (?:) 代表不优先显示分组里面的内容,只是显示正常匹配到的内容

- ?:表示 不优先显示括号里面的内容,把括号作为一个小组,一个整体;

---

## 48. 4.反向引用_命名分组.py

### 📋 运行结果

```

<re.Match object; span=(0, 18), match='<div>明天又要休息了</div>'>
<div>明天又要休息了</div>
('div', '明天又要休息了', '/div')
<re.Match object; span=(0, 18), match='<div>明天又要休息了</div>'>
<div>明天又要休息了</div>
('div', '明天又要休息了')
<re.Match object; span=(1, 8), match='z3d4pzd'>
z3d4pzd
('z', 'd', 'p')
<re.Match object; span=(1, 8), match='z3d4pzd'>
z3d4pzd
<re.Match object; span=(1, 8), match='z3d4pzd'>
z3d4pzd

```

### 💻 完整代码

```python

# ### 反向引用
import re
strvar = "<div>明天又要休息了</div>"
obj = re.search("<(.*?)>(.*?)<(.*?)>",strvar)
print(obj)

# 获取匹配到的内容
res1 = obj.group()
print(res1)

# 获取分组里的内容
res2 = obj.groups()
print(res2)

# 反向引用的语法 \1把第一个括号里面匹配到的内容在引用一次
obj = re.search(r"<(.*?)>(.*?)</\1>",strvar)
print(obj)
print(obj.group())
print(obj.groups())

strvar = " z3d4pzd a1b2cab "
obj = re.search(r"(.*?)\d(.*?)\d(.*?)\1\2",strvar)
print(obj)
print(obj.group())
print(obj.groups())

# ### 命名分组
"""
3) (?P<组名>正则表达式) 给这个组起一个名字
4) (?P=组名) 引用之前组的名字,把该组名匹配到的内容放到当前位置
"""
# 写法一
strvar = " z3d4pzd a1b2cab "
obj = re.search(r"(?P<tag1>.*?)\d(?P<tag2>.*?)\d(?P<tag3>.*?)\1\2",strvar)
print(obj)
print(obj.group())

# 写法二
strvar = " z3d4pzd a1b2cab "
obj = re.search(r"(?P<tag1>.*?)\d(?P<tag2>.*?)\d(?P<tag3>.*?)(?P=tag1)(?P=tag2)",strvar)
print(obj)
print(obj.group())

```

### 📖 要点讲解

- 反向引用的语法 \1把第一个括号里面匹配到的内容在引用一次

---

## 🖼️ 参考资料

![1605978413403.png](./assets/1605978413403.png)

![1605978451639.png](./assets/1605978451639.png)

![1605978501496.png](./assets/1605978501496.png)

![1605978681691.png](./assets/1605978681691.png)

![1605978818346.png](./assets/1605978818346.png)

![1606002323671.png](./assets/1606002323671.png)

![1606014445427.png](./assets/1606014445427.png)

![1606479907401.png](./assets/1606479907401.png)

![1606504886450.png](./assets/1606504886450.png)

![1606505027688.png](./assets/1606505027688.png)

![1606582664442.png](./assets/1606582664442.png)

![1606582681827.png](./assets/1606582681827.png)
