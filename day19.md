# Day 19: day19 pymysql模块的使用 python联表查询 orm的配置 快速实现orm的增删改查 13个查询api接口 其他查询操作 多表的添加操作

> 对应原课程：day19_pymysql模块的使用_python联表查询_orm的配置_快速实现orm的增删改查_13个查询api接口_其他查询操作_多表的添加操作

---

## 1. 作业.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day19_pymysql模块的使用_python联表查询_orm的配置_快速实现orm的增删改查_13个查询api接口_其他查询操作_多表的添加操作/作业.py", line 1, in <module>
    用orm改写图书管理系统 
    ^^^^^^^^^^^^^^^^^^^^^
NameError: name '用orm改写图书管理系统' is not defined

```

### 💻 完整代码

```python

用orm改写图书管理系统 

```

---

## 2. manage.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day19_pymysql模块的使用_python联表查询_orm的配置_快速实现orm的增删改查_13个查询api接口_其他查询操作_多表的添加操作/orm1/manage.py", line 10, in main
    from django.core.management import execute_from_command_line
ModuleNotFoundError: No module named 'django'

The above exception was the direct cause of the following exception:

Traceback (most recent call last):
  File "/tmp/python3_course/day19_pymysql模块的使用_python联表查询_orm的配置_快速实现orm的增删改查_13个查询api接口_其他查询操作_多表的添加操作/orm1/manage.py", line 21, in <module>
    main()
  File "/tmp/python3_course/day19_pymysql模块的使用_python联表查询_orm的配置_快速实现orm的增删改查_13个查询api接口_其他查询操作_多表的添加操作/orm1/manage.py", line 12, in main
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
    os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'orm1.settings')
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

## 3. __init__.py

### 💻 完整代码

```python

```

---

## 4. admin.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day19_pymysql模块的使用_python联表查询_orm的配置_快速实现orm的增删改查_13个查询api接口_其他查询操作_多表的添加操作/orm1/app1/admin.py", line 1, in <module>
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

## 5. apps.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day19_pymysql模块的使用_python联表查询_orm的配置_快速实现orm的增删改查_13个查询api接口_其他查询操作_多表的添加操作/orm1/app1/apps.py", line 1, in <module>
    from django.apps import AppConfig
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.apps import AppConfig

class App1Config(AppConfig):
    name = 'app1'

```

---

## 6. models.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day19_pymysql模块的使用_python联表查询_orm的配置_快速实现orm的增删改查_13个查询api接口_其他查询操作_多表的添加操作/orm1/app1/models.py", line 1, in <module>
    from django.db import models
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.db import models

# Create your models here.
# # 类名就是新建的表的表名,orm要求每一个表中都必须有一个主键,没有设置就自动生成一个自增主键,叫ID字段
class Book(models.Model):
	id=models.AutoField(primary_key=True)
	title = models.CharField(max_length = 32)
	pub_date = models.DateField()
	price = models.DecimalField(max_digits=8,decimal_places=2)
	publish = models.CharField(max_length=32)

	# 打印该对象时,自动触发,要求返回的数据必须是字符串 print(book)
	def __str__(self):
		return str(self.id) + self.title

```

### 📖 要点讲解

- Create your models here.

- # 类名就是新建的表的表名,orm要求每一个表中都必须有一个主键,没有设置就自动生成一个自增主键,叫ID字段

- 打印该对象时,自动触发,要求返回的数据必须是字符串 print(book)

---

## 7. tests.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day19_pymysql模块的使用_python联表查询_orm的配置_快速实现orm的增删改查_13个查询api接口_其他查询操作_多表的添加操作/orm1/app1/tests.py", line 1, in <module>
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

## 8. views.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day19_pymysql模块的使用_python联表查询_orm的配置_快速实现orm的增删改查_13个查询api接口_其他查询操作_多表的添加操作/orm1/app1/views.py", line 1, in <module>
    from django.shortcuts import render,HttpResponse
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.shortcuts import render,HttpResponse
from app1.models import Book
# Create your views here.
def add(request):
	# 添加数据方法一
	"""
	book = Book(title='西游记',price=9.91,pub_date='2020-12-13',publish="清华大学出版社")
	book.save()
	# 获取该[表对象]的成员属性;

	print(book.title)
	print(book.pub_date)
	print(book.price)
	print(book.publish)
	"""
	# 添加数据方法二
	book = Book.objects.create(title='三国',price=78,pub_date='2020-12-14',publish="南京大学出版社")
	print(book.title)
	print(book.pub_date)
	print(book.price)
	print(book.publish)
	return HttpResponse("add ok")

def select(request):
	# 1.all => 查询所有 select * from book
	data = Book.objects.all()
	print(data , type(data))
	for i in data:
		# print(i)
		print(i.id,i.title,i.price)

	# 2.filter => 按照条件进行搜索,相当于[where] select * from book where price=9.91 and publish="清华大学出版社1"  推荐
	data = Book.objects.filter(price=9.91,publish="清华大学出版社1")
	print(data , type(data))

	# 3.get 针对于单条数据的获取使用get,一般配合id使用,如果搜出的数量大于1条则报错,返回的是模型类中的表对象
	"""表对象只能有一个,记录数据对象可以有多个(queryset 里面有很多的记录数据对象(一条条的记录对象))"""
	book = Book.objects.get(id=3)
	print(book.id,book.title,book.price)
	# 如果数据大于一条会直接报错
	# book = Book.objects.get(price=9.91)
	# print(book) error
	return HttpResponse("select ok")

def delete(request):
	# 删除方法一 推荐
	''''''
	data = Book.objects.filter(id=2)
	# print(data[0].id,data[0].publish)
	# 删除数据 数据对象.delete()
	res = data.delete()
	res = res[0] # 1 0
	# print(res) # (1, {'app1.Book': 1})

	# 删除方法二 不推荐
	"""
	try:
		book = Book.objects.get(id=5)
		print(book.id)
		res = book.delete()
		print(res) # (1, {'app1.Book': 1})
		res = True
	except:
		res = False	
	"""

	status = "删除成功" if res else "删除失败"
	return HttpResponse("delete ok"+status)

def update(request):
	'''1单纯代表更新成功,0代表更新失败;'''
	# 更新方法一 即使不存在也不报错,不会中断程序
	# data = Book.objects.filter(id=7)
	# res = data.update(price=90)
	# print(res)

	res = Book.objects.filter(id=7000).update(price=90)
	print(res)

	# 更新方法二
	"""
	book = Book.objects.get(id=8) # 不存在直接报错
	book.title = "金瓶梅1"
	res = book.save()
	print(res)
	"""
	return HttpResponse("update ok")

```

### 📖 要点讲解

- Create your views here.

- 1.all => 查询所有 select * from book

- 2.filter => 按照条件进行搜索,相当于[where] select * from book where price=9.91 and publish="清华大学出版社1"  推荐

- 3.get 针对于单条数据的获取使用get,一般配合id使用,如果搜出的数量大于1条则报错,返回的是模型类中的表对象

- book = Book.objects.get(price=9.91)

- print(data[0].id,data[0].publish)

- print(res) # (1, {'app1.Book': 1})

- 更新方法一 即使不存在也不报错,不会中断程序

- data = Book.objects.filter(id=7)

- res = data.update(price=90)

---

## 9. __init__.py

### 💻 完整代码

```python

```

---

## 10. __init__.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day19_pymysql模块的使用_python联表查询_orm的配置_快速实现orm的增删改查_13个查询api接口_其他查询操作_多表的添加操作/orm1/orm1/__init__.py", line 1, in <module>
    import pymysql
ModuleNotFoundError: No module named 'pymysql'

```

### 💻 完整代码

```python

import pymysql
pymysql.install_as_MySQLdb()

```

---

## 11. settings.py

### 💻 完整代码

```python

"""
Django settings for orm1 project.

Generated by 'django-admin startproject' using Django 2.2.17.

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
SECRET_KEY = '!+mf+a9psrn1b%yl2=5!dp@61nrd2)f%2)gva*um*-t+jl5pgs'

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
    'app1.apps.App1Config'
]

MIDDLEWARE = [
    'django.middleware.security.SecurityMiddleware',
    'django.contrib.sessions.middleware.SessionMiddleware',
    'django.middleware.common.CommonMiddleware',
    'django.middleware.csrf.CsrfViewMiddleware',
    'django.contrib.auth.middleware.AuthenticationMiddleware',
    'django.contrib.messages.middleware.MessageMiddleware',
    'django.middleware.clickjacking.XFrameOptionsMiddleware',
]

ROOT_URLCONF = 'orm1.urls'

TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [],
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

WSGI_APPLICATION = 'orm1.wsgi.application'

# Database
# https://docs.djangoproject.com/en/2.2/ref/settings/#databases

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        # 'NAME': os.path.join(BASE_DIR, 'db.sqlite3'),
        'NAME':'ceshi1',
        'USER': 'root',  # 连接数据库的用户名
        'PASSWORD': '',  # 连接数据库的密码
        'HOST': '127.0.0.1',  # IP地址
        'POST': 3306,  # 端口号
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

```

### 📖 要点讲解

- Build paths inside the project like this: os.path.join(BASE_DIR, ...)

- Quick-start development settings - unsuitable for production

- See https://docs.djangoproject.com/en/2.2/howto/deployment/checklist/

- SECURITY WARNING: keep the secret key used in production secret!

- SECURITY WARNING: don't run with debug turned on in production!

- Application definition

- https://docs.djangoproject.com/en/2.2/ref/settings/#databases

- 'NAME': os.path.join(BASE_DIR, 'db.sqlite3'),

- https://docs.djangoproject.com/en/2.2/ref/settings/#auth-password-validators

- https://docs.djangoproject.com/en/2.2/topics/i18n/

- Static files (CSS, JavaScript, Images)

- https://docs.djangoproject.com/en/2.2/howto/static-files/

---

## 12. urls.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day19_pymysql模块的使用_python联表查询_orm的配置_快速实现orm的增删改查_13个查询api接口_其他查询操作_多表的添加操作/orm1/orm1/urls.py", line 16, in <module>
    from django.contrib import admin
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

"""orm1 URL Configuration

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
from django.urls import path
from app1 import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('add/',views.add),
    path('select/',views.select),
    path('delete/',views.delete),
    path('update/', views.update)
]

```

---

## 13. wsgi.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day19_pymysql模块的使用_python联表查询_orm的配置_快速实现orm的增删改查_13个查询api接口_其他查询操作_多表的添加操作/orm1/orm1/wsgi.py", line 12, in <module>
    from django.core.wsgi import get_wsgi_application
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

"""
WSGI config for orm1 project.

It exposes the WSGI callable as a module-level variable named ``application``.

For more information on this file, see
https://docs.djangoproject.com/en/2.2/howto/deployment/wsgi/
"""

import os

from django.core.wsgi import get_wsgi_application

os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'orm1.settings')

application = get_wsgi_application()

```

---

## 14. manage.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day19_pymysql模块的使用_python联表查询_orm的配置_快速实现orm的增删改查_13个查询api接口_其他查询操作_多表的添加操作/orm2/manage.py", line 10, in main
    from django.core.management import execute_from_command_line
ModuleNotFoundError: No module named 'django'

The above exception was the direct cause of the following exception:

Traceback (most recent call last):
  File "/tmp/python3_course/day19_pymysql模块的使用_python联表查询_orm的配置_快速实现orm的增删改查_13个查询api接口_其他查询操作_多表的添加操作/orm2/manage.py", line 21, in <module>
    main()
  File "/tmp/python3_course/day19_pymysql模块的使用_python联表查询_orm的配置_快速实现orm的增删改查_13个查询api接口_其他查询操作_多表的添加操作/orm2/manage.py", line 12, in main
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
    os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'orm2.settings')
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

## 15. __init__.py

### 💻 完整代码

```python

```

---

## 16. admin.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day19_pymysql模块的使用_python联表查询_orm的配置_快速实现orm的增删改查_13个查询api接口_其他查询操作_多表的添加操作/orm2/app1/admin.py", line 1, in <module>
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

## 17. apps.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day19_pymysql模块的使用_python联表查询_orm的配置_快速实现orm的增删改查_13个查询api接口_其他查询操作_多表的添加操作/orm2/app1/apps.py", line 1, in <module>
    from django.apps import AppConfig
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.apps import AppConfig

class App1Config(AppConfig):
    name = 'app1'

```

---

## 18. models.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day19_pymysql模块的使用_python联表查询_orm的配置_快速实现orm的增删改查_13个查询api接口_其他查询操作_多表的添加操作/orm2/app1/models.py", line 1, in <module>
    from django.db import models
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.db import models

# Create your models here.

# # 类名就是新建的表的表名,orm要求每一个表中都必须有一个主键,没有设置就自动生成一个自增主键,叫ID字段
class Book(models.Model):
	id=models.AutoField(primary_key=True)
	title = models.CharField(max_length = 32)
	pub_date = models.DateField()
	price = models.DecimalField(max_digits=8,decimal_places=2)
	publish = models.CharField(max_length=32)

	# 打印该对象时,自动触发,要求返回的数据必须是字符串 print(book)
	def __str__(self):
		return str(self.id) + self.title

```

### 📖 要点讲解

- Create your models here.

- # 类名就是新建的表的表名,orm要求每一个表中都必须有一个主键,没有设置就自动生成一个自增主键,叫ID字段

- 打印该对象时,自动触发,要求返回的数据必须是字符串 print(book)

---

## 19. tests.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day19_pymysql模块的使用_python联表查询_orm的配置_快速实现orm的增删改查_13个查询api接口_其他查询操作_多表的添加操作/orm2/app1/tests.py", line 1, in <module>
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

## 20. views.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day19_pymysql模块的使用_python联表查询_orm的配置_快速实现orm的增删改查_13个查询api接口_其他查询操作_多表的添加操作/orm2/app1/views.py", line 1, in <module>
    from django.shortcuts import render,HttpResponse
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.shortcuts import render,HttpResponse
from app1.models import Book
# Create your views here.
def select(request):
	# 1.all 查询所有数据
	data = Book.objects.all()
	print(data)

	# 2.count 获取数据总数 select count(*) from book
	res = data.count()
	print(res)

	# 3.first: 返回的第一条数据对象
	res = data.first()
	print(res)
	print(res.id,res.title)

	# 4.last: 返回的最后一个数据对象
	res = data.last()
	print(res.id)

	# 5.order_by 排序(正序)  order by id asc
	data = Book.objects.order_by('id')
	print(data)

	# 6.order_by 排序(倒序) reverse  order by id desc 推荐;
	data = Book.objects.order_by('id').reverse()
	print(data)

	# 扩展写法 [可以在排序的字段前面加上-,表达倒序] 不推荐;
	data = Book.objects.order_by('-id')
	print(data)

	# 7.filter 按条件查询[相当于where] 返回的queryset对象
	data = Book.objects.filter(price=81).order_by("-id")
	# select * from book where price=81 order by id desc
	for i in data.order_by("-id"):
		print(i.id)
	print(data[0].id,"<=====>")

	# 8.exists():  如果QuerySet包含数据，就返回True，否则返回False
	data = Book.objects.filter(id=10)
	res = data.exists()
	print(res)

	# 9.get 返回一个模型类对象 [等价于表对象]
	# data = Book.objects.get(id=100000) # error 找不到或者找到多条数据都会报错;
	# print(data)

	# 10.exclude: 排除符合条件的对象,返回的依然是queryset对象 [表达不等于,除了的概念]
	data = Book.objects.exclude(id=10) # select * from book where id != 10
	print(data)

	# 11.values 查找某个字段值,返回字典
	data = Book.objects.filter(price=78).values("id","title")
	print(data)

	# 12.values_list 查找某个字段值,返回元组
	data = Book.objects.filter(price=78).values_list("id","title")
	print(data)

	# 13.distinct 去重 select distinct(price) from app1_book
	data = Book.objects.all().values("price").distinct()
	print(data)

	# 链式操作(连贯操作)
	# select "id","title" from book where price = 78 order by id desc
	data = Book.objects.filter(price=78).values("id","title").order_by("id").reverse()
	print(data)
	return HttpResponse("select ok")

def select2(request):
	# 范围查询
	# in  => __in
	# select * from book where price in (78,79,90)
	data = Book.objects.filter(price__in=[78,79,90])
	print(data,1)

	# >   => __gt
	# select * from book where price > 79
	data = Book.objects.filter(price__gt=79)
	print(data,2)

	# >=  => __gte
	# select * from book where price >= 79
	data = Book.objects.filter(price__gte=79)
	print(data,3)

	# <   => __lt
	# select * from book where price < 79
	data = Book.objects.filter(price__lt=79)
	print(data,4)

	# <=  => __lte
	data = Book.objects.filter(price__lte=79)
	print(data,5)

	# between .. and .. =>  __range=[100,200]
	# select * from book where price between 100 and 200;
	data = Book.objects.filter(price__range=[100,200])
	print(data,6)

	# like模糊查询
	# __contains="金"
	# like => __contains="金"
	#  select * from book where title like "%瓶%";
	data = Book.objects.filter(title__contains="瓶")
	print(data,7)

	# like(忽略大小写)
	# __icontains="a"
	data = Book.objects.filter(title__icontains="ab")
	print(data,8)

	# __startswith="aa" 以..开头
	data = Book.objects.filter(title__startswith="三")
	print(data,9)

	# __endswith="bb"   以..结尾
	data = Book.objects.filter(title__endswith="5")
	print(data,10)

	# 针对于date类型
	data = Book.objects.filter(id=10).values("pub_date")
	print(data[0]["pub_date"],11)

	# select * from book where year(pub_date) = 2021
	data = Book.objects.filter(pub_date__year = 2021 )
	data = Book.objects.filter(pub_date__month=12)
	data = Book.objects.filter(pub_date__day=14)
	print(data , 12)
	# __year  过滤日期字段的年份
	# __month 过滤日期字段的月份
	# __day   过滤日期字段的日

	# 扩展 正则匹配 mysql可以使用正则 但是不好事,效率低,查询速度低下,不建议使用;了解
	data = Book.objects.filter(title__regex="^金.*$")
	# print(data,11)
	return HttpResponse("select2 ok")

```

### 📖 要点讲解

- Create your views here.

- 2.count 获取数据总数 select count(*) from book

- 5.order_by 排序(正序)  order by id asc

- 6.order_by 排序(倒序) reverse  order by id desc 推荐;

- 扩展写法 [可以在排序的字段前面加上-,表达倒序] 不推荐;

- 7.filter 按条件查询[相当于where] 返回的queryset对象

- select * from book where price=81 order by id desc

- 8.exists():  如果QuerySet包含数据，就返回True，否则返回False

- 9.get 返回一个模型类对象 [等价于表对象]

- data = Book.objects.get(id=100000) # error 找不到或者找到多条数据都会报错;

- 10.exclude: 排除符合条件的对象,返回的依然是queryset对象 [表达不等于,除了的概念]

- 11.values 查找某个字段值,返回字典

- 12.values_list 查找某个字段值,返回元组

- 13.distinct 去重 select distinct(price) from app1_book

- select "id","title" from book where price = 78 order by id desc

- select * from book where price in (78,79,90)

- select * from book where price > 79

- select * from book where price >= 79

- select * from book where price < 79

- between .. and .. =>  __range=[100,200]

- select * from book where price between 100 and 200;

- like => __contains="金"

- select * from book where title like "%瓶%";

- __startswith="aa" 以..开头

- __endswith="bb"   以..结尾

- select * from book where year(pub_date) = 2021

- 扩展 正则匹配 mysql可以使用正则 但是不好事,效率低,查询速度低下,不建议使用;了解

---

## 21. __init__.py

### 💻 完整代码

```python

```

---

## 22. __init__.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day19_pymysql模块的使用_python联表查询_orm的配置_快速实现orm的增删改查_13个查询api接口_其他查询操作_多表的添加操作/orm2/orm2/__init__.py", line 1, in <module>
    import pymysql
ModuleNotFoundError: No module named 'pymysql'

```

### 💻 完整代码

```python

import pymysql
pymysql.install_as_MySQLdb()

```

---

## 23. settings.py

### 💻 完整代码

```python

"""
Django settings for orm2 project.

Generated by 'django-admin startproject' using Django 2.2.17.

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
SECRET_KEY = '9g=fi#+zujs*@8u9i3#yt_l)2ar*zf08x0wul4^*d2pxe%021-'

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
    'app1.apps.App1Config'
]

MIDDLEWARE = [
    'django.middleware.security.SecurityMiddleware',
    'django.contrib.sessions.middleware.SessionMiddleware',
    'django.middleware.common.CommonMiddleware',
    'django.middleware.csrf.CsrfViewMiddleware',
    'django.contrib.auth.middleware.AuthenticationMiddleware',
    'django.contrib.messages.middleware.MessageMiddleware',
    'django.middleware.clickjacking.XFrameOptionsMiddleware',
]

ROOT_URLCONF = 'orm2.urls'

TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [],
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

WSGI_APPLICATION = 'orm2.wsgi.application'

# Database
# https://docs.djangoproject.com/en/2.2/ref/settings/#databases

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        # 'NAME': os.path.join(BASE_DIR, 'db.sqlite3'),
        'NAME':'ceshi2',
        'USER': 'root',  # 连接数据库的用户名
        'PASSWORD': '',  # 连接数据库的密码
        'HOST': '127.0.0.1',  # IP地址
        'POST': 3306,  # 端口号
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

```

### 📖 要点讲解

- Build paths inside the project like this: os.path.join(BASE_DIR, ...)

- Quick-start development settings - unsuitable for production

- See https://docs.djangoproject.com/en/2.2/howto/deployment/checklist/

- SECURITY WARNING: keep the secret key used in production secret!

- SECURITY WARNING: don't run with debug turned on in production!

- Application definition

- https://docs.djangoproject.com/en/2.2/ref/settings/#databases

- 'NAME': os.path.join(BASE_DIR, 'db.sqlite3'),

- https://docs.djangoproject.com/en/2.2/ref/settings/#auth-password-validators

- https://docs.djangoproject.com/en/2.2/topics/i18n/

- Static files (CSS, JavaScript, Images)

- https://docs.djangoproject.com/en/2.2/howto/static-files/

---

## 24. urls.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day19_pymysql模块的使用_python联表查询_orm的配置_快速实现orm的增删改查_13个查询api接口_其他查询操作_多表的添加操作/orm2/orm2/urls.py", line 16, in <module>
    from django.contrib import admin
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

"""orm2 URL Configuration

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
from django.urls import path
from app1 import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('select/',views.select),
    path('select2/',views.select2)
]

```

---

## 25. wsgi.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day19_pymysql模块的使用_python联表查询_orm的配置_快速实现orm的增删改查_13个查询api接口_其他查询操作_多表的添加操作/orm2/orm2/wsgi.py", line 12, in <module>
    from django.core.wsgi import get_wsgi_application
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

"""
WSGI config for orm2 project.

It exposes the WSGI callable as a module-level variable named ``application``.

For more information on this file, see
https://docs.djangoproject.com/en/2.2/howto/deployment/wsgi/
"""

import os

from django.core.wsgi import get_wsgi_application

os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'orm2.settings')

application = get_wsgi_application()

```

---

## 26. manage.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day19_pymysql模块的使用_python联表查询_orm的配置_快速实现orm的增删改查_13个查询api接口_其他查询操作_多表的添加操作/orm3/manage.py", line 10, in main
    from django.core.management import execute_from_command_line
ModuleNotFoundError: No module named 'django'

The above exception was the direct cause of the following exception:

Traceback (most recent call last):
  File "/tmp/python3_course/day19_pymysql模块的使用_python联表查询_orm的配置_快速实现orm的增删改查_13个查询api接口_其他查询操作_多表的添加操作/orm3/manage.py", line 21, in <module>
    main()
  File "/tmp/python3_course/day19_pymysql模块的使用_python联表查询_orm的配置_快速实现orm的增删改查_13个查询api接口_其他查询操作_多表的添加操作/orm3/manage.py", line 12, in main
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
    os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'orm3.settings')
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

## 27. __init__.py

### 💻 完整代码

```python

```

---

## 28. admin.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day19_pymysql模块的使用_python联表查询_orm的配置_快速实现orm的增删改查_13个查询api接口_其他查询操作_多表的添加操作/orm3/app1/admin.py", line 1, in <module>
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

## 29. apps.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day19_pymysql模块的使用_python联表查询_orm的配置_快速实现orm的增删改查_13个查询api接口_其他查询操作_多表的添加操作/orm3/app1/apps.py", line 1, in <module>
    from django.apps import AppConfig
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.apps import AppConfig

class App1Config(AppConfig):
    name = 'app1'

```

---

## 30. models.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day19_pymysql模块的使用_python联表查询_orm的配置_快速实现orm的增删改查_13个查询api接口_其他查询操作_多表的添加操作/orm3/app1/models.py", line 1, in <module>
    from django.db import models
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.db import models

# Create your models here.

class Book(models.Model):
	title = models.CharField(max_length=30)
	price = models.DecimalField(max_digits=8,decimal_places=2)
	pub_date = models.DateField()
	# 一对多 => on_delete=models.CASCADE 联级删除 ,关联Publish这个表的主键
	"""关联字段,系统会自动在字段名后面加上id"""
	publisher = models.ForeignKey("Publish",on_delete=models.CASCADE)

	# 多对多 => ManyToManyField,系统会自动创建多堆多关系表 , 只需要写入表名即可;
	authors = models.ManyToManyField("Author")

class Publish(models.Model):
	name = models.CharField(max_length=30)
	email = models.CharField(max_length=30)
	addr = models.CharField(max_length=30)

class Author(models.Model):
	name = models.CharField(max_length=30)
	tel =  models.CharField(max_length=30)
	# 一对一 => 用Author里面的ad关联AuthorDetail中的主键;
	ad = models.OneToOneField("AuthorDetail",on_delete=models.CASCADE)

class AuthorDetail(models.Model):
	addr = models.CharField(max_length=30)
	gf = models.CharField(max_length=30)

# django 自动可以为用户创建多对多关系表
# class Book2Author(models.Model):
# 	bookid = ...
# 	authorid = ...

"""
多堆多 或者 一对一 ,关联字段放在哪张表都可以
但是一对多,必须放在多的那张表上;
"""

```

### 📖 要点讲解

- Create your models here.

- 一对多 => on_delete=models.CASCADE 联级删除 ,关联Publish这个表的主键

- 多对多 => ManyToManyField,系统会自动创建多堆多关系表 , 只需要写入表名即可;

- 一对一 => 用Author里面的ad关联AuthorDetail中的主键;

- django 自动可以为用户创建多对多关系表

- class Book2Author(models.Model):

---

## 31. tests.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day19_pymysql模块的使用_python联表查询_orm的配置_快速实现orm的增删改查_13个查询api接口_其他查询操作_多表的添加操作/orm3/app1/tests.py", line 1, in <module>
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

## 32. views.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day19_pymysql模块的使用_python联表查询_orm的配置_快速实现orm的增删改查_13个查询api接口_其他查询操作_多表的添加操作/orm3/app1/views.py", line 1, in <module>
    from django.shortcuts import render,HttpResponse
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.shortcuts import render,HttpResponse
from app1.models import Book,Publish,Author,AuthorDetail
# Create your views here.
def add(request):
	# 单表添加数据
	# book = Publish.objects.create(name='清华大学出版社',email="111@qq.com",addr="深圳")
	# print(book)

	# 一对多添加数据方式1
	data = Book.objects.create(title="三国",price=111,pub_date="2020-10-10",publisher_id=2)
	print(data.id,data.title)

	# 一对多条件数据方式2
	"""
	pub_data = Publish.objects.filter(name="清华大学出版社")[0]
	print(pub_data) # id =1 的那条数据对象  和 publisher 直接绑定
	data = Book.objects.create(title="水壶",price=222,pub_date="2020-10-11",publisher=pub_data)
	"""

	# 绑定多对多关系表 方法一

	"""默认主键都是id ,如果不确定自己的主键名称叫什么,可以无脑写pk,让系统给你找主键;"""
	data = Book.objects.get(pk=6)
	"""
	alex = Author.objects.get(pk=1)
	wusir = Author.objects.get(pk=2)
	# data.authors 数据.外键名 => 找的是多堆多的第三张关系表; add是添加数据
	data.authors.add(alex,wusir)
	"""
	# 绑定多对多关系表 方法二
	# data.authors.add(1,2)
	# data.authors.add(*[1,2]) # data.authors.add(1,2)

	# 多堆垛的解绑(移除操作)  移除外键为1的数据和外键为2的数据
	# data.authors.remove(1,2)

	# 清除所有外键数据
	# data.authors.clear()

	# 数据的重置 删+加
	data.authors.set([1,2])

	return HttpResponse("ok11")

```

### 📖 要点讲解

- Create your views here.

- book = Publish.objects.create(name='清华大学出版社',email="111@qq.com",addr="深圳")

- data.authors 数据.外键名 => 找的是多堆多的第三张关系表; add是添加数据

- data.authors.add(1,2)

- data.authors.add(*[1,2]) # data.authors.add(1,2)

- 多堆垛的解绑(移除操作)  移除外键为1的数据和外键为2的数据

- data.authors.remove(1,2)

---

## 33. __init__.py

### 💻 完整代码

```python

```

---

## 34. __init__.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day19_pymysql模块的使用_python联表查询_orm的配置_快速实现orm的增删改查_13个查询api接口_其他查询操作_多表的添加操作/orm3/orm3/__init__.py", line 1, in <module>
    import pymysql
ModuleNotFoundError: No module named 'pymysql'

```

### 💻 完整代码

```python

import pymysql
pymysql.install_as_MySQLdb()

```

---

## 35. settings.py

### 💻 完整代码

```python

"""
Django settings for orm3 project.

Generated by 'django-admin startproject' using Django 2.2.17.

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
SECRET_KEY = '451bjn*)$o(3t=mhi-mk=6kl9+@b!e7!q1a1#**6f6%qric$%4'

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
    'app1.apps.App1Config',
]

MIDDLEWARE = [
    'django.middleware.security.SecurityMiddleware',
    'django.contrib.sessions.middleware.SessionMiddleware',
    'django.middleware.common.CommonMiddleware',
    'django.middleware.csrf.CsrfViewMiddleware',
    'django.contrib.auth.middleware.AuthenticationMiddleware',
    'django.contrib.messages.middleware.MessageMiddleware',
    'django.middleware.clickjacking.XFrameOptionsMiddleware',
]

ROOT_URLCONF = 'orm3.urls'

TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [],
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

WSGI_APPLICATION = 'orm3.wsgi.application'

# Database
# https://docs.djangoproject.com/en/2.2/ref/settings/#databases

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        # 'NAME': os.path.join(BASE_DIR, 'db.sqlite3'),
        'NAME':'ceshi3',
        'USER': 'root',  # 连接数据库的用户名
        'PASSWORD': '',  # 连接数据库的密码
        'HOST': '127.0.0.1',  # IP地址
        'POST': 3306,  # 端口号
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

```

### 📖 要点讲解

- Build paths inside the project like this: os.path.join(BASE_DIR, ...)

- Quick-start development settings - unsuitable for production

- See https://docs.djangoproject.com/en/2.2/howto/deployment/checklist/

- SECURITY WARNING: keep the secret key used in production secret!

- SECURITY WARNING: don't run with debug turned on in production!

- Application definition

- https://docs.djangoproject.com/en/2.2/ref/settings/#databases

- 'NAME': os.path.join(BASE_DIR, 'db.sqlite3'),

- https://docs.djangoproject.com/en/2.2/ref/settings/#auth-password-validators

- https://docs.djangoproject.com/en/2.2/topics/i18n/

- Static files (CSS, JavaScript, Images)

- https://docs.djangoproject.com/en/2.2/howto/static-files/

---

## 36. urls.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day19_pymysql模块的使用_python联表查询_orm的配置_快速实现orm的增删改查_13个查询api接口_其他查询操作_多表的添加操作/orm3/orm3/urls.py", line 16, in <module>
    from django.contrib import admin
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

"""orm3 URL Configuration

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
from django.urls import path
from app1 import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('add/',views.add)
]

```

---

## 37. wsgi.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day19_pymysql模块的使用_python联表查询_orm的配置_快速实现orm的增删改查_13个查询api接口_其他查询操作_多表的添加操作/orm3/orm3/wsgi.py", line 12, in <module>
    from django.core.wsgi import get_wsgi_application
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

"""
WSGI config for orm3 project.

It exposes the WSGI callable as a module-level variable named ``application``.

For more information on this file, see
https://docs.djangoproject.com/en/2.2/howto/deployment/wsgi/
"""

import os

from django.core.wsgi import get_wsgi_application

os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'orm3.settings')

application = get_wsgi_application()

```

---

## 38. 联表查询_子查询.py

### 📋 运行结果

```

错误：  File "/tmp/python3_course/day19_pymysql模块的使用_python联表查询_orm的配置_快速实现orm的增删改查_13个查询api接口_其他查询操作_多表的添加操作/复习扩展mysql/扩展/联表查询_子查询.py", line 7
    1、查询所有的课程的名称以及对应的任课老师姓名
     ^
SyntaxError: invalid character '、' (U+3001)

```

### 💻 完整代码

```python

五张表之间的关系
class <=> student   关联: class_id
teacher <=> course  关联: teacher_id
score <=> student   关联: student.sid <=> score.student_id
score <=> course    关联: score.course_id <=> course.cid   

1、查询所有的课程的名称以及对应的任课老师姓名
# where
select
	teacher.tname,course.cname
from 
	teacher,course
where
	teacher.tid = course.teacher_id
	
# inner join 
select
	teacher.tname,course.cname
from 
	teacher inner join course on teacher.tid = course.teacher_id

2、查询学生表中男女生各有多少人
select 
	gender,count(*)
from 
	student
group by
	gender
	
3、查询物理成绩等于100的学生的姓名

# where
select
	student.sname
from 
	student,course,score
where
	student.sid = score.student_id
	and
	course.cid = score.course_id
	and
	score.num = 100
	and
	course.cname = "物理"
	
# inner join  as起一个别名
select
	st.sname 
from 
	student as st inner join score as sc on st.sid = sc.student_id
	inner join course as cr on cr.cid = sc.course_id
where 
	sc.num = 100
	and
	cr.cname = '物理'

4、查询平均成绩大于八十分的同学的姓名和平均成绩
"""group by 身后的字段,按照什么分类就搜索这个表的字段,
这个表的其他字段因为没有被分类,不能直接作为搜索字段"""
# 1.给学生id做一下分类,查看一下对应的分数
select 
	score.student_id,score.num
from
	score
group by
	score.student_id,score.num

# 2.按照当前的分类,做二次条件筛选,要成绩大于80的条件
select 
	score.student_id
from
	score
group by
	score.student_id
having 
	avg(score.num) > 80
	
# 3.在额外拼接一个student表,查询对应的学生姓名
select 
	score.student_id , student.sname
from
	score,student
where 
	score.student_id = student.sid
group by
	score.student_id
having 
	avg(score.num) > 80
	
5、查询所有学生的学号，姓名，选课数，总成绩
select 
	score.student_id,count(*)
from 
	score
group by 
	score.student_id

# 1.以实际的学生id为参考标准,统计选课数量
select 
	student.sid,count(score.course_id)
from 
	score right join student on score.student_id = student.sid
group by 
	student.sid

# 2.总成绩 sum
select 
	student.sid,sum(score.num)
from 
	score right join student on score.student_id = student.sid
group by 
	student.sid

# 3.拼接一下
select 
	student.sid,sum(score.num),count(score.course_id),student.sname
from 
	score right join student on score.student_id = student.sid
group by 
	student.sid

```

### 📖 要点讲解

- 1.给学生id做一下分类,查看一下对应的分数

- 2.按照当前的分类,做二次条件筛选,要成绩大于80的条件

- 3.在额外拼接一个student表,查询对应的学生姓名

- 1.以实际的学生id为参考标准,统计选课数量

---

## 39. 0001_initial.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day19_pymysql模块的使用_python联表查询_orm的配置_快速实现orm的增删改查_13个查询api接口_其他查询操作_多表的添加操作/orm1/app1/migrations/0001_initial.py", line 3, in <module>
    from django.db import migrations, models
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

# Generated by Django 2.2.17 on 2020-12-13 06:47

from django.db import migrations, models

class Migration(migrations.Migration):

    initial = True

    dependencies = [
    ]

    operations = [
        migrations.CreateModel(
            name='Book',
            fields=[
                ('id', models.AutoField(primary_key=True, serialize=False)),
                ('title', models.CharField(max_length=32)),
                ('pub_date', models.DateField()),
                ('price', models.DecimalField(decimal_places=2, max_digits=8)),
                ('publish', models.CharField(max_length=32)),
            ],
        ),
    ]

```

### 📖 要点讲解

- Generated by Django 2.2.17 on 2020-12-13 06:47

---

## 40. 0001_initial.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day19_pymysql模块的使用_python联表查询_orm的配置_快速实现orm的增删改查_13个查询api接口_其他查询操作_多表的添加操作/orm2/app1/migrations/0001_initial.py", line 3, in <module>
    from django.db import migrations, models
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

# Generated by Django 2.2.17 on 2020-12-13 08:26

from django.db import migrations, models

class Migration(migrations.Migration):

    initial = True

    dependencies = [
    ]

    operations = [
        migrations.CreateModel(
            name='Book',
            fields=[
                ('id', models.AutoField(primary_key=True, serialize=False)),
                ('title', models.CharField(max_length=32)),
                ('pub_date', models.DateField()),
                ('price', models.DecimalField(decimal_places=2, max_digits=8)),
                ('publish', models.CharField(max_length=32)),
            ],
        ),
    ]

```

### 📖 要点讲解

- Generated by Django 2.2.17 on 2020-12-13 08:26

---

## 41. 0001_initial.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day19_pymysql模块的使用_python联表查询_orm的配置_快速实现orm的增删改查_13个查询api接口_其他查询操作_多表的添加操作/orm3/app1/migrations/0001_initial.py", line 3, in <module>
    from django.db import migrations, models
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

# Generated by Django 2.2.17 on 2020-12-13 10:33

from django.db import migrations, models
import django.db.models.deletion

class Migration(migrations.Migration):

    initial = True

    dependencies = [
    ]

    operations = [
        migrations.CreateModel(
            name='Author',
            fields=[
                ('id', models.AutoField(auto_created=True, primary_key=True, serialize=False, verbose_name='ID')),
                ('name', models.CharField(max_length=30)),
                ('tel', models.CharField(max_length=30)),
            ],
        ),
        migrations.CreateModel(
            name='AuthorDetail',
            fields=[
                ('id', models.AutoField(auto_created=True, primary_key=True, serialize=False, verbose_name='ID')),
                ('addr', models.CharField(max_length=30)),
                ('gf', models.CharField(max_length=30)),
            ],
        ),
        migrations.CreateModel(
            name='Publish',
            fields=[
                ('id', models.AutoField(auto_created=True, primary_key=True, serialize=False, verbose_name='ID')),
                ('name', models.CharField(max_length=30)),
                ('email', models.CharField(max_length=30)),
                ('addr', models.CharField(max_length=30)),
            ],
        ),
        migrations.CreateModel(
            name='Book',
            fields=[
                ('id', models.AutoField(auto_created=True, primary_key=True, serialize=False, verbose_name='ID')),
                ('title', models.CharField(max_length=30)),
                ('price', models.DecimalField(decimal_places=2, max_digits=8)),
                ('pub_date', models.DateField()),
                ('authors', models.ManyToManyField(to='app1.Author')),
                ('publisher', models.ForeignKey(on_delete=django.db.models.deletion.CASCADE, to='app1.Publish')),
            ],
        ),
        migrations.AddField(
            model_name='author',
            name='ad',
            field=models.OneToOneField(on_delete=django.db.models.deletion.CASCADE, to='app1.AuthorDetail'),
        ),
    ]

```

### 📖 要点讲解

- Generated by Django 2.2.17 on 2020-12-13 10:33

---

## 42. 1.笔记.py

### 📋 运行结果

```

错误：  File "/tmp/python3_course/day19_pymysql模块的使用_python联表查询_orm的配置_快速实现orm的增删改查_13个查询api接口_其他查询操作_多表的添加操作/复习扩展mysql/复习/1.笔记.py", line 3
    d:  -> 切换到d盘
        ^^
SyntaxError: invalid syntax

```

### 💻 完整代码

```python

# ### 安装mysql => 通过超级管理员打开cmd黑窗口
# 切换路径
d:  -> 切换到d盘
dir -> 看一下盘符里面有什么
cd MySQL5.7
cd mysql-5.7.25-winx64
cd bin
# 执行命令
mysqld --initialize-insecure --user=mysql
mysqld install
# 启动mysql
net start mysql
# mysql>  安装成功 !!

# windows (启动或者关闭数据库,必须在超级管理员的身份下才能执行)
net start mysql
net stop mysql

# ### part1 
数据库: 关系型数据库 非关系型数据库
关系型数据库 : mysql , oracle , sql server
(把数据存储在文件,有行有列这样的结构表里,支持复杂的sql查询和事务处理)

非关系型数据库 : redis mongodb
(把数据存储在内存,以键值对这样的结构进行存储,没有关系表结构,读取速度较快)

# 存储引擎 (数据的存储方式)
innodb : 支持事务处理 , 行级锁 , 外键
myisam : 表级锁
	事务处理: 操作多条sql语句时,必须全部成功,才能最终提交数据,否则默认回滚,恢复到原来的状态;
	表级锁 : 有一个线程在操作文件,其他线程需要等待,不能同一时间多个用户修改同一个表文件
	行级锁 : 多个线程操作同一个数据表文件,只单独锁定要修改的这一行,可以支持多线程的并发修改;
	外键   : 把多个表通过关联字段连接在一起,要改全改,要删全删.

# ### part2 
# 登录数据库
mysql -u(用户名) -p(密码) -h(ip地址,默认本地) 
mysql -uroot -p (默认连接的本地数据库 127.0.0.1 <=> localhost )
mysql -uroot -p -h 14.215.177.38 (远程连接数据库)

# 退出 
exit;

# 授权用户登录到mysql数据库中
grant 权限 on 数据库.表 to "用户名"@"ip地址" identified by "密码"
"""
权限
all  代表所有权限
select 查看数据库权限
insert 插入数据库权限
update 修改数据库权限
delete 删除数据库权限
...
* 代表所有数据库,所有表
% 所有的ip都可以
"""
grant all on *.* to "ceshi12345"@"%" identified by "12345";
# 刷新权限,立刻生效
flush privileges

# mysql设置密码
# 查看当前登录的用户是谁
select user();
# 设置当前用户的密码
set password = password("33445566")
# 去除密码
set password = password("")

# ###part3.数据库的增删改查 (必须掌握)
# (1)操作数据库(文件夹)
增
	# 创建db数据库,设置字符集为utf8
	create database db1 charset utf8;

查:
	# 显示所有的数据库
	show databases;
	# 查看建库语句
	show create database db1; # CREATE DATABASE `db2` /*!40100 DEFAULT CHARACTER SET utf8 */ |

改:
	# 更改数据库的字符集
	alter database db1 charset gbk;
删:
	# 删除数据库db1
	drop database db1;

# (2)操作数据表(文件)
+-------+---------+------+-----+---------+-------+
| Field | Type    | Null | Key | Default | Extra |
+-------+---------+------+-----+---------+-------+
| id    | int(11) | YES  |     | NULL    |       |
| name  | char(1) | YES  |     | NULL    |       |
+-------+---------+------+-----+---------+-------+
use 数据库 (创建表之前需要先选择数据库)
增
	"""int 整数类型  char 字符串类型 enum 枚举类型"""
	create table t1(id int , name char);

查:
	# 显示所有数据表
	show tables
	# 查看表结构
	desc t1;
	# 查看建表语句
	show create table t1;
	# 垂直显示内容
	show create table t1\G 
	"""
	CREATE TABLE `t2` (
	  `id` int(11) DEFAULT NULL,
	  `name` char(1) DEFAULT NULL
	) ENGINE=InnoDB DEFAULT CHARSET=utf8
	"""
改:
	# modify 专门用来修改数据类型 , 指定char类型长度为4
	alter table t2 modify name char(4);
	# change 连名带类型一起改掉
	alter table t2 change name name666 char(1);
	# add 添加字段
	alter table t2 add sex enum("男性","女性");
	# drop 删除字段
	alter table t2 drop name666;
	# rename 更改表名
	alter table t2 rename t3;

删:
	# 删除表t3
	drop table t3;

# (3) 操作记录: (实例文件里面的内容)
增:
	# 一次插入一条数据
	insert into t1(id,name) values(1,"a");
	# 一次插入多条数据
	insert into t1(id,name) values(2,"b") ,(3,"c"),(4,"d");
	# 可以不指定具体某字段插入数据,但是要保证一一对应
	insert into t1 values(5,"e");
	# 可以具体指定某个字段进行插入
	insert into t1(id) values(6)
查:
	# 查询所有
	select * from t1;
	select id from t1;
	select t1.name from t1;
	# 查询当前数据库
	select database();
改:
	# update 表名 set 字段=值 where 条件
	update t1 set name = "z" where id = 1;
	# 不加条件该表所有
	update t1 set name = "z";
删:
	# 指定id删除
	delete from t1 where id = 1;
	# 删除所有
	delete from t1;
	# 重置表 (删除数据 + 重置id)
	truncate table t1;

# 事务处理
# 开始事务
begin;
# 修改数据
update t1 set name="c" where id = 1
# 回滚到初始状态
rollback;
# 最后提交数据
commit

# ### part4 数据类型
# 整型
tinyint: 1个字节 有符号(-128 ~ 127) 无符号 (0~255) unsigned 小整数
int    : 4个字节 有符号(-21亿 ~ 21亿作用) 无符号 (0~42亿) unsigned 大整数,范围更大
	
	create table t1(id int  ,sex tinyint);
	insert into t1 values(4200000000,1); error
	insert into t1 values(100,299); error
	insert into t1 values(1,0); 
	
# 浮点型
float(255,30)  单精度
double(255,30) 双精度
decimal(65,30) 金钱类型
	# float(5,2) 小数点后保留2为,整体长度是5位
	create table t2(f1 float(5,2),f2 double(5,2),f3 decimal(5,2))
	insert into t2 values(1.45678,1.45678,1.45678);
	
	# float和double比较,double小数位保留的更多,decimal默认只保留整数,存在四舍五入.
	create table t3(f1 float,f2 double,f3 decimal);
	insert into t3 values(12345.6789123488888888888,12345.6789123488888888888,12345.6789123488888888888);

	# 总长度是5,小数点最多保留2位,整数部分最多保留3位.
	create table t4(f1 float(5,2));
	insert into t4 values(123.456789);
	insert into t4 values(12345.456789); error
	insert into t4 values(12.456789);
	
# 字符串
char(11)    : 定长,固定开辟11个长度大小的空间 (手机号,身份证)
varchar(11) : 变长,动态开辟最大11个长度空间   (姓名,评论)
text        : 存大文本,(论文,小说 ... )
	# char(4) varchar(4) 代表字符的个数不能超过4个
	# char 最大不超过255个字符.varchar 最大不超过21845个字符
	# 有时不确定varchar是多少个字符上线,可以先写255个在调;
	create table t5(c char(4),v varchar(4),t text);
	insert into t5 values("你好啊啊","你好啊啊","sfsdfsd");
	insert into t5 values("你好啊啊","你好啊啊2","sfsdfsd");
	
# 时间类型 
"""select now() 获取的是当前的时间"""
date     YYYY-MM-DD  年月日 (出生日期)
time     HH:MM:SS    时分秒 (竞速比赛)
year     YYYY        年份   (红酒的制造年份)
datetime YYYY-MM-DD HH:MM:SS 年月日时分秒 (登录,注册,下单,退款时间)
	create table t6(d date ,t time , y year ,dt datetime);
	insert into t6 values("2020-09-20","14:46:50","2020","2020-09-20 14:46:50");
	# 默认以当前时间进行更新;
	insert into t6 values(now(),now(),now(),now());

timestamp YYYYMMDDHHMMSS 时间戳 系统自动更新时间戳,(修改数据,自动进行更新,用于标注最后一次修改时间)
	create table t7(dt datetime,ts timestamp);
	insert into t7 values(null,null);
	insert into t7 values(20200920144650,20200920144650);
	
# 枚举类型 enum  集合类型 set
enum 枚举 从一组数据当中选一个 (一般用在性别)
set  集合 从一组数据当中选多个 (一般用在爱好)
create table t8(
	id int unsigned,
	name varchar(10),
	money float(5,3),
	sex enum("man","woman"),
	hobby set("睡觉","吃饭","打豆豆")
);

# 枚举选一个,集合选多个(之间用逗号隔开)
insert into  t8(id,name,money,sex,hobby) values(1,'王文',3.123456,"man","睡觉,吃饭")
# 集合可以自动去重
insert into  t8(id,name,money,sex,hobby) values(1,'王文',3.123456,"man","睡觉,吃饭,吃饭,吃饭")

# ### part5 约束
"""字段名  字段类型  字段约束 => 创建表"""
unsigned     : 无符号整型
not null     : 不能为空
default      : 设置默认值
unique       : 唯一约束,数据唯一不重复
primary key  : 主键 , 唯一并且不能为空,辨别单条数据的唯一性
auto_increment: 自增加一
foreign key  : 外键,把多张表通过一个字段关联在一起,形成联级更新,联级删除效果

# unsigned     : 无符号整型
create table t1(id int unsigned );
insert into t1 values(-100); error
insert into t1 values(100);

# not null     : 不能为空
create table t2(id int unsigned not null , name varchar(255) );
insert into t2 values(1,"abc");
insert into t2(name) values("abc"); error

# default      : 设置默认值
create table t3(id int unsigned not null , name varchar(255) default "张俊文" );
insert into t3 values(11,null);
insert into t3(id) values(12);

# unique       : 唯一约束,数据唯一不重复 (唯一索引)
"""索引: 相当于字典首页的目录,可以快速定位到要查找的数据,加快查询速度"""
"""UNI 唯一索引 或者唯一约束 ,不能重复,但可以是多个null值"""
create table t4(id int unique , name varchar(255) default "张俊文" );
insert into t4(id ) values(1);
insert into t4(id ) values(1); error 1这个值重复
insert into t4(id ) values(null); 正确
insert into t4(id ) values(null); 正确

# primary key  : 主键 , 唯一并且不能为空,辨别单条数据的唯一性
"""PRI 主键 或者 主键索引, 一个表中,默认单个字段里只能有一个主键,不存在多个字段多个主键"""
create table t5(id int primary key  , name varchar(255) default "张俊文" );
insert into t5(id ) values(1);
insert into t5(id ) values(2);
insert into t5(id ) values(null); error

# auto_increment: 自增加一 (一般配合主键或者unique使用)
create table t6(id int primary key auto_increment , name varchar(255) default "张俊文" );
insert into t6(id) values(1);
insert into t6(id) values(null);
insert into t6(id) values(null);
insert into t6(id) values(null);

# 删除所有 (保留id)
delete from t6;
# 重置表 (删除数据 + 重置id)
truncate table t6;

# foreign key  : 外键,把多张表通过一个字段关联在一起,形成联级更新,联级删除效果
"""外键的要求:所关联另外一张表的字段至少具有唯一性"""
字段1 字段2 ...... 字段30(公司法人代表)
                     
student
	id name    age  classname sex  family    friend   time parent .... 
	1  wangwen 16   python5   男性 一家三口  绿巨人1990  马化腾

	2  lisi    17   python5   男性 一家三口  绿巨人1990  马化腾

	3  wangwu  18   python5   男性 一家三口  绿巨人1990  马化腾

student1
	id name    age  classid
	1  wangwen 16   1  
	2  lisi    17   2
	3  wangwu  18   1

class1
	id  classname
	1   python5
	2   python6
	3   python7

# foreign key(关联字段) references
"""如果被关联的字段是有符号的,那么主动关联的字段也需要有符号,要保证符号类型一致"""
create table class111(id int unsigned,classname varchar(255));

# 设置id变成unique
alter table class1 add unique(id);
desc class1;

create table student111(
	id int primary key auto_increment,
	name varchar(255),
	age tinyint unsigned,
	classid int unsigned,foreign key(classid) references class111(id)
);

# 插入数据
insert into class111 values(1,"python5"),(2,"python6"),(3,"python7");
insert into student111 values(null,"wangwen",16,1),(null,"lisi",17,2),(null,"wangwu",18,1);

# 如果是被修饰成外键,当前字段只有在无任何数据关联的情况下,才能够进行修改或者删除
delete from class111 where id = 1 error 
# 必须把其他关联的数据都删掉,才可以删掉对应的班级
delete from student111 where classid = 1;

"""
联级更新 : on update cascade
联级删除 : on delete cascade
"""
create table class222(id int unsigned,classname varchar(255));

# 设置id变成unique
alter table class222 add unique(id);
desc class222;

create table student222(
	id int primary key auto_increment,
	name varchar(255),
	age tinyint unsigned,
	classid int unsigned,
	foreign key(classid) references class222(id) on update cascade on delete cascade
	
);

# 插入数据
insert into class222 values(1,"python5"),(2,"python6"),(3,"python7");
insert into student222 values(null,"wangwen",16,1),(null,"lisi",17,2),(null,"wangwu",18,1);

# 联级删除
#delete from class222 where id = 1
# 联级更新
# update class222 set id = 20 where classname="python6"

# ### part6 表与表之间的关系
(1) 一对一 : 身份证 和 姓名
(2) 一对多 : 一个班级对应多个学生
(3) 多对多 : 一个作者可以写多本书,一本书可以被多个作者完成
			 一个学科可以被多个学生学习,一个学生可以学习多个学科

xueke (表1)
id name
1  math
2  english
3  wuli

student(表2)
id  name
1   wangwen
2   zhangsan
3   lisi

relation (表3 关系表)
"""可以吧xid和sid设置关联字段,关联xueke.id 以及  student.id 
把xid 和 sid 设置成外键,实现联级删除或者联级更新
"""
xid  sid
1    1
1    2
1    3
2    1
2    2
2    3
3    1 
3    2
3    3

"""
# 总结:
1.添加/删除 not null 约束
	alter table 表名 modify 别名 类型
	
2.添加/删除 unique 唯一索引
	alter table 表名 add unique(id);
	alter table 表名 drop  索引名
	
3.添加/删除 primary key 主键
	alter table 表名 add primary key(id)
	alter table 表名 drop primary key

4. 添加/删除froeign key 外键
	show create table student2\G 查看外键名
	alter table student2 drop foreign key 外键名字 `student2_ibfk_1`
	alter table student2 add foreign key(clas_id) references class2(id)
"""

```

### 📖 要点讲解

- ### 安装mysql => 通过超级管理员打开cmd黑窗口

- windows (启动或者关闭数据库,必须在超级管理员的身份下才能执行)

- ###part3.数据库的增删改查 (必须掌握)

- modify 专门用来修改数据类型 , 指定char类型长度为4

- (3) 操作记录: (实例文件里面的内容)

- 可以不指定具体某字段插入数据,但是要保证一一对应

- update 表名 set 字段=值 where 条件

- float(5,2) 小数点后保留2为,整体长度是5位

- float和double比较,double小数位保留的更多,decimal默认只保留整数,存在四舍五入.

- 总长度是5,小数点最多保留2位,整数部分最多保留3位.

- char(4) varchar(4) 代表字符的个数不能超过4个

- char 最大不超过255个字符.varchar 最大不超过21845个字符

- 有时不确定varchar是多少个字符上线,可以先写255个在调;

- unique       : 唯一约束,数据唯一不重复 (唯一索引)

- primary key  : 主键 , 唯一并且不能为空,辨别单条数据的唯一性

- auto_increment: 自增加一 (一般配合主键或者unique使用)

- foreign key  : 外键,把多张表通过一个字段关联在一起,形成联级更新,联级删除效果

- foreign key(关联字段) references

- 如果是被修饰成外键,当前字段只有在无任何数据关联的情况下,才能够进行修改或者删除

- 必须把其他关联的数据都删掉,才可以删掉对应的班级

- delete from class222 where id = 1

- update class222 set id = 20 where classname="python6"

---

## 43. 1.python操作mysql.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day19_pymysql模块的使用_python联表查询_orm的配置_快速实现orm的增删改查_13个查询api接口_其他查询操作_多表的添加操作/复习扩展mysql/扩展/1.python操作mysql.py", line 2, in <module>
    import pymysql
ModuleNotFoundError: No module named 'pymysql'

```

### 💻 完整代码

```python

# ### python 操作mysql 
import pymysql

# ### 1.基本语法
""""""
# (1) 创建连接对象 host user password database 这四个参数必写
conn = pymysql.connect( host="127.0.0.1" , user="root" , password="123456" , database="db003" , charset="utf8" , port=3306 )
# (2) 创建游标对象 (用来操作数据库的增删改查)
cursor = conn.cursor()
print(cursor)
# (3) 执行sql语句
sql = "select * from employee"
# 执行查询语句返回的总条数
res = cursor.execute(sql)
print(res) 
# (4) 获取数据 fetchone 获取一条数据
# 返回的是元组,里面包含的是第一条的完整数据
res = cursor.fetchone()
print(res)
res = cursor.fetchone()
print(res)
res = cursor.fetchone()
print(res)
# (5) 释放游标对象
cursor.close()
# (6) 释放连接对象
conn.close()

# ### 2.创建/删除 表操作
# conn = pymysql.connect(host="127.0.0.1",user="root",password="123456",database="db003")
# cursor = conn.cursor()

# 1.创建一张表
sql = """
create table t1(
id int unsigned primary key auto_increment,
first_name varchar(255) not null,
last_name varchar(255) not null,
sex tinyint not null,
age tinyint unsigned not null,
money float
);
"""
# res = cursor.execute(sql)
# print(res) # 无意义返回值

# 2.查询表结构
"""
sql = "desc t1"
res = cursor.execute(sql)
print(res) # 返回的是字段的个数
res = cursor.fetchone()
print(res)
res = cursor.fetchone()
print(res)
res = cursor.fetchone()
print(res)
"""
# 3.删除表
"""
try:
	sql = "drop table t1"
	res = cursor.execute(sql)
	print(res) # 无意义返回值
except:
	pass
"""

# ### 3.事务处理
"""pymysql 默认开启事务的,所有增删改的数据必须提交,否则默认回滚;rollback"""
conn = pymysql.connect(host="127.0.0.1",user="root",password="123456",database="db003")
cursor = conn.cursor()
sql1 = "begin"
sql2 = "update employee set emp_name='程咬钻石' where id = 18 "
sql3 = "commit"

res1 = cursor.execute(sql1)
res1 = cursor.execute(sql2)
res1 = cursor.execute(sql3)
# 一般在查询的时候,通过fetchone来获取结果
res1 = cursor.fetchone()
print(res1)

cursor.close()
conn.close()

```

### 📖 要点讲解

- (1) 创建连接对象 host user password database 这四个参数必写

- (2) 创建游标对象 (用来操作数据库的增删改查)

- (4) 获取数据 fetchone 获取一条数据

- 返回的是元组,里面包含的是第一条的完整数据

- conn = pymysql.connect(host="127.0.0.1",user="root",password="123456",database="db003")

- cursor = conn.cursor()

- res = cursor.execute(sql)

- 一般在查询的时候,通过fetchone来获取结果

---

## 44. 2.笔记.py

### 📋 运行结果

```

错误：  File "/tmp/python3_course/day19_pymysql模块的使用_python联表查询_orm的配置_快速实现orm的增删改查_13个查询api接口_其他查询操作_多表的添加操作/复习扩展mysql/复习/2.笔记.py", line 48
    9.concat(参数1,参数2,参数3) 连接在一起(类似于os.path.join)
     ^
SyntaxError: invalid decimal literal

```

### 💻 完整代码

```python

# ### 1.单表查询
select  .. from .. where .. group by .. having .. order by .. limit ..

# 1.where 子句 : 对数据按照条件筛选
	"""
		1.符号: = > >= < <= != <> (不等于)
		2.between .. and  在两者之间[小值,大值] 
		3.is用来判断是否是null
		4.in   => in(值1,值2,值3...) 在当前括号里划定范围
	    5.like 模糊查询 %是通配符 _是通配符
			like "%a"  匹配以a结尾的任意长度字符串
			like "a%"  匹配以a开头的任意长度字符串
			like "%a%" 匹配含有a字符的任意长度字符串
			like "_a"  匹配以a结尾的2个长度的字符串
			like "a__" 匹配以a开头的共3个长度的字符串
		6.and or not 通过逻辑拼接条件
	"""
	
	1.查询部门是sale的所有员工姓名
	select emp_name from employee where post = "sale";
	
	2.找teacher部门,并且收入大于10000
	select * from employee where post="teacher" and salary > 10000;
	
	3.收入在10000~20000之间的所有姓名和收入
	select emp_name ,salary  from employee where salary between 10000 and 20000
	
	4.收入不在10000~20000之间的所有姓名和收入
	select emp_name ,salary  from employee where salary not  between 10000 and 20000
	
	5.找部门评论为null的数据 (必须用is来判断)
	select * from employee where post_comment = null; error 无数据 null是关键字需要用is来判断
	select * from employee where post_comment is null;
	
	6.找3000 3500 4000收入的员工姓名
	select emp_name,salary from employee where salary in (3000,3500,4000);
	select emp_name,salary from employee where salary  = 3000 or salary = 3500 or salary = 4000;
	
	7.找不在3000 3500 4000收入的员工姓名
	select emp_name,salary from employee where salary not in (3000,3500,4000);
	
	8.找a开头的名字
	# 必须是a开头,后面字符个数,种类都不限制
	select emp_name from employee where emp_name like "a%";
	# 必须是金结尾,前面字符个数是2个
	select emp_name from employee where emp_name like "__金";
	
	9.concat(参数1,参数2,参数3) 连接在一起(类似于os.path.join)
	select concat("姓名:",emp_name,"薪水",salary) from employee;
	
# 2.group by 分类,分组
	"""
	group by + 字段 按照当前这个字段分类
	按照什么分类,就搜索什么字段
	group_concat 对分类的内容进行数据拼接
	"""
	select sex from employee group by sex;
	select group_concat(emp_name) from employee group by sex;
	
	# 聚合函数
		# count 统计计数
		select count(*) from employee;
		# max   统计最大值
		select max(salary) from employee;
		# min   统计最小值
		select min(salary) from employee;
		# sum   统计总和
		select sum(salary) from employee;
		# avg   统计平均值
		select avg(salary) from employee;
	
	# 分组 + 聚合函数一起使用
	# 求各部门的平均薪资
	select post,avg(salary) from employee group by post;
	# 求各部门的最大薪资
	select post,max(salary) from employee group by post;
	
# 3.having 在分类完数据之后,进行数据的二次过滤.一般配合group by一起使用
	
	1.查询各岗位平均薪资大于10000以上的岗位名、平均工资
	select post,avg(salary) from employee group by post having avg(salary) > 10000;
	# as 就是起别名
	select post,avg(salary) as avg from employee group by post having avg(salary) > 10000;
	
# 4.order by 按照什么字段排序
+----+------------+--------+-----+------------+-----------------------------------------+--------------+------------+--------+-----------+
| id | emp_name   | sex    | age | hire_date  | post                                    | post_comment | salary     | office | depart_id |
+----+------------+--------+-----+------------+-----------------------------------------+--------------+------------+--------+-----------+
|  1 | egon       | male   |  18 | 2017-03-01 | 老男孩驻沙河办事处外交大使              | NULL         |    7300.33 |    401 |         1 |
|  2 | alex       | male   |  78 | 2015-03-02 | teacher                                 | NULL         | 1000000.31 |    401 |         1 |
|  3 | wupeiqi    | male   |  81 | 2013-03-05 | teacher                                 | NULL         |    8300.00 |    401 |         1 |
|  4 | yuanhao    | male   |  73 | 2014-07-01 | teacher                                 | NULL         |    3500.00 |    401 |         1 |
|  5 | liwenzhou  | male   |  28 | 2012-11-01 | teacher                                 | NULL         |    2100.00 |    401 |         1 |
|  6 | jingliyang | female |  18 | 2011-02-11 | teacher                                 | NULL         |    9000.00 |    401 |         1 |
|  7 | jinxin     | male   |  18 | 1900-03-01 | teacher                                 | NULL         |   30000.00 |    401 |         1 |
|  8 | 成龙       | male   |  48 | 2010-11-11 | teacher                                 | NULL         |   10000.00 |    401 |         1 |
|  9 | 歪歪       | female |  48 | 2015-03-11 | sale                                    | NULL         |    3000.13 |    402 |         2 |
| 10 | 丫丫       | female |  38 | 2010-11-01 | sale                                    | NULL         |    2000.35 |    402 |         2 |
| 11 | 丁丁       | female |  18 | 2011-03-12 | sale                                    | NULL         |    1000.37 |    402 |         2 |
| 12 | 星星       | female |  18 | 2016-05-13 | sale                                    | NULL         |    3000.29 |    402 |         2 |
| 13 | 格格       | female |  28 | 2017-01-27 | sale                                    | NULL         |    4000.33 |    402 |         2 |
| 14 | 张野       | male   |  28 | 2016-03-11 | operation                               | NULL         |   10000.13 |    403 |         3 |
| 15 | 程咬金     | male   |  18 | 1997-03-12 | operation                               | NULL         |   20000.00 |    403 |         3 |
| 16 | 程咬银     | female |  18 | 2013-03-11 | operation                               | NULL         |   19000.00 |    403 |         3 |
| 17 | 程咬铜     | male   |  18 | 2015-04-11 | operation                               | NULL         |   18000.00 |    403 |         3 |
| 18 | 程咬铁     | female |  18 | 2014-05-12 | operation                               | NULL         |   17000.00 |    403 |         3 |
+----+------------+--------+-----+------------+-----------------------------------------+--------------+------------+--------+-----------+
	# 默认升序,从小到大 asc
	# 1.把teacher部门的所有员工,按照年龄从小到大排序 asc
	select * from employee where post = "teacher" order by age ;
	select * from employee where post = "teacher" order by age asc;
	# 2.把teacher部门的所有员工,按照年龄从大到小排序 desc
	select * from employee where post = "teacher" order by age desc;
	# 3.在年龄倒序排列之后,在按照入职日期进行升序排序
	select * from employee where post = "teacher" order by age desc , hire_date asc;
	
# 5.limit 限制查询的条数(一般用于做分页)
	# 1. 只查询一条数据
	select * from employee limit 1;
	# 2.limit m,n  m代表从第几条开始搜 , n代表搜索几条 如果m=0,代表从第一条开始
	select * from employee limit 0,5
	select * from employee limit 5,5
	select * from employee limit 10,5
	
# ### 2.多表之间的查询
	# (1) 内联 (inner join ) : 将两表或者多表拼接在一起进行查询,要求必须双方都共有的数据可以联合
	语法: select 字段 from 表1 inner join 表2 on 必要关联的字段
	多表: select 字段 from 表1 inner join 表2 on 必要关联的字段 inner join 表3 on 必要关联的字段 inner join ... 

	# 内联查询 (双方都存在的数据才能联合)
	select * from employee inner join department on employee.dep_id = department.id
	# 用as 起别名
	select * from employee as e inner join department as d on e.dep_id = d.id;
	select * from employee,department where employee.dep_id = department.id #( 默认where 是内联查询)
	# as 本身都可以省略
	select * from employee e,department d where e.dep_id = d.id 
	
	# (2) 外联
		1.左联接 (left join)  : 以左表为主,右表为辅,完整查询左表所有数据,右表对不上的数据补null
			select * from employee left join department on employee.dep_id = department.id
		2.右联接 (right join) : 以右表为主,左表为辅,完整查询右表所有数据,左表对不上的数据补null
			select * from employee right join department on employee.dep_id = department.id
		3.全联接 (union)
			select * from employee left join department on employee.dep_id = department.id
			union
			select * from employee right join department on employee.dep_id = department.id
	
```

### 📖 要点讲解

- 1.where 子句 : 对数据按照条件筛选

- 3.having 在分类完数据之后,进行数据的二次过滤.一般配合group by一起使用

- 1.把teacher部门的所有员工,按照年龄从小到大排序 asc

- 2.把teacher部门的所有员工,按照年龄从大到小排序 desc

- 3.在年龄倒序排列之后,在按照入职日期进行升序排序

- 5.limit 限制查询的条数(一般用于做分页)

- 2.limit m,n  m代表从第几条开始搜 , n代表搜索几条 如果m=0,代表从第一条开始

- (1) 内联 (inner join ) : 将两表或者多表拼接在一起进行查询,要求必须双方都共有的数据可以联合

---

## 45. 2.sql注入攻击.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day19_pymysql模块的使用_python联表查询_orm的配置_快速实现orm的增删改查_13个查询api接口_其他查询操作_多表的添加操作/复习扩展mysql/扩展/2.sql注入攻击.py", line 2, in <module>
    import pymysql
ModuleNotFoundError: No module named 'pymysql'

```

### 💻 完整代码

```python

# ### sql 注入攻击
import pymysql
# (1) sql注入的现象
''' 现象:绕开账号密码登录成功 '''
''''''
user = input("请输入您的用户名>>>")
pwd  = input("请输入您的密码>>>")

conn = pymysql.connect(host="127.0.0.1" , user="root" , password="123456",database="db005")
cursor = conn.cursor()
sql1 = """
create table usr_pwd(
id int unsigned primary key auto_increment,
username varchar(255) not null,
password varchar(255) not null
)
"""
sql2 = "select * from usr_pwd where username='%s' and password='%s' " % (user,pwd)
print(sql2)
res = cursor.execute(sql2)
print(res) # 1查到成功 0没查到失败
# res=cursor.fetchone()
"""
select * from usr_pwd where username='2222' or 4=4 -- aaa' and password='' 
相当于 : select * from usr_pwd where 10=10; 绕开了账户和密码的判断 -- 代表的是注释;
"""
if res:
	print("登录成功")
else:
	print("登录失败")

cursor.close()
conn.close()

# (2) 预处理机制
""" 在执行sql语句之前,提前对sql语句中出现的字符进行过滤优化,避免sql注入攻击 """
""" execute( sql , (参数1,参数2,参数3 .... ) ) execute2个参数默认开启预处理机制 """
""" 填写 234234' or 100=100 -- sdfsdfsdfsdf  尝试攻击  """

user = input("请输入您的用户名>>>")
pwd  = input("请输入您的密码>>>")

conn = pymysql.connect(host="127.0.0.1" , user="root" , password="123456",database="db005")
cursor = conn.cursor()
sql = "select * from usr_pwd where username=%s and password=%s"
res = cursor.execute( sql , (user,pwd)  )
print(res)

print(    "登录成功"  if res else "登录失败"    )

cursor.close()
conn.close()

```

### 📖 要点讲解

- res=cursor.fetchone()

---

## 46. 3.python操作mysql增删改查.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day19_pymysql模块的使用_python联表查询_orm的配置_快速实现orm的增删改查_13个查询api接口_其他查询操作_多表的添加操作/复习扩展mysql/扩展/3.python操作mysql增删改查.py", line 2, in <module>
    import pymysql
ModuleNotFoundError: No module named 'pymysql'

```

### 💻 完整代码

```python

# ### python 操作mysql 数据库 (增删改查)
import pymysql
"""
	python 操作mysql增删改时,默认是开启事务的,
	必须最后commit提交数据,才能产生变化
	
	提交数据: commit 
	默认回滚: rollback
	
"""

conn = pymysql.connect(host="127.0.0.1",user="root",password="123456",database="db005")
# 默认获取查询结果时是元组,可以设置返回字典;  cursor=pymysql.cursors.DictCursor
cursor = conn.cursor(cursor=pymysql.cursors.DictCursor)

# 执行对mysql 的操作

# 1.增
"""
sql = "insert into t1(first_name,last_name,sex,age,money) values(%s,%s,%s,%s,%s)"
# (1) 一次插入一条
res = cursor.execute( sql , ("孙","健",0,15,20000)  )
print(res) # 1
# 获取最后插入这条数据的id号
print(cursor.lastrowid)

# (2) 一次插入多条
res = cursor.executemany(  sql , [  ("安","晓东",0,18,30000) , ("刘","玉波",1,20,50000) ,("张","光旭",0,80,60000) , ("李","是元",0,10,10) , ("高","大奥",1,20,80000)   ]   )
print(res) # 返回插入的条数
# 插入5条数据中的第一条数据的id
print(cursor.lastrowid)
# 获取最后一个数据的id
sql = "select id from t1 order by id desc limit 1"
res = cursor.execute(sql)
print(res)
# 获取结果,返回元组
res = cursor.fetchone()
print(res["id"])
# 默认元组 : (57, '高', '大奥', 1, 20, 80000.0)
# 返回字典 : {'id': 51, 'first_name': '高', 'last_name': '大奥', 'sex': 1, 'age': 20, 'money': 80000.0}
"""

# 2.删
"""
sql = "delete from t1 where id in (%s,%s,%s)"
res = cursor.execute(sql , (3,4,5) )
print(res) # 返回的是3,代表删除了3条

if res:
	print("删除成功")
else:
	print("删除失败")
"""

# 3.改
"""
sql = "update t1 set first_name = '王' where id = %s"
sql = "update t1 set first_name = '王' where id in (%s,%s,%s,%s)"
res = cursor.execute(sql , (6,7,8,9))
print(res) # 返回的是4,代表修改了4条

if res:
	print("修改成功")
else:
	print("修改失败")
"""

# 4.查
"""
fetchone  获取一条
fetchmany 获取多条
fetchall  获取所有
"""	

sql = "select * from t1"
res = cursor.execute(sql)
print(res) # 针对于查询语句来说,返回的res是总条数;

# (1) fetchone 获取一条
res = cursor.fetchone()
print(res)
res = cursor.fetchone()
print(res)

# (2) fetchmany 获取多条
res = cursor.fetchmany() # 默认获取的是一条数据,返回列表,里面里面是一组一组的字典;
data = cursor.fetchmany(3)
print(data)
"""
[
	{'id': 9, 'first_name': '王', 'last_name': '是元', 'sex': 0, 'age': 10, 'money': 10.0}, 
	{'id': 10, 'first_name': '孙', 'last_name': '健', 'sex': 0, 'age': 15, 'money': 20000.0}, 
	{'id': 11, 'first_name': '安', 'last_name': '晓东', 'sex': 0, 'age': 18, 'money': 30000.0}
]
"""
for row in data:
	first_name = row["first_name"]
	last_name = row["last_name"]
	sex = row["sex"]
	if sex == 0:
		sex = "男性"
	else:
		sex = "女性"
	age = row["age"]
	money = row["money"]
	strvar = "姓:{},名:{},性别:{},年龄:{},收入:{}".format(first_name,last_name,sex,age,money)
print(strvar)

# (3) fetchall 获取所有
# data = cursor.fetchall()
# print(data)

# (4) 自定义搜索查询的位置
print("<==================>")
# 1.相对滚动 relative
"""相对于上一次查询的位置往前移动(负数),或者往后移动(正数)"""
"""
cursor.scroll(-1,mode="relative")
# cursor.scroll(5,mode="relative")
res = cursor.fetchone()
print(res)
"""
# 2.绝对滚动 absolute
"""永远从数据的开头起始位置进行移动,不能向前滚"""
cursor.scroll(0,mode="absolute")
res = cursor.fetchone()
print(res)

conn.commit()
cursor.close()
conn.close()

```

### 📖 要点讲解

- ### python 操作mysql 数据库 (增删改查)

- 默认获取查询结果时是元组,可以设置返回字典;  cursor=pymysql.cursors.DictCursor

- 默认元组 : (57, '高', '大奥', 1, 20, 80000.0)

- 返回字典 : {'id': 51, 'first_name': '高', 'last_name': '大奥', 'sex': 1, 'age': 20, 'money': 80000.0}

- data = cursor.fetchall()

- cursor.scroll(5,mode="relative")

---

## 47. 4.导入导出_更改编码集.py

### 📋 运行结果

```

错误：  File "/tmp/python3_course/day19_pymysql模块的使用_python联表查询_orm的配置_快速实现orm的增删改查_13个查询api接口_其他查询操作_多表的添加操作/复习扩展mysql/扩展/4.导入导出_更改编码集.py", line 6
    3.mysqldump -uroot -p db001 > db001.sql
     ^
SyntaxError: invalid decimal literal

```

### 💻 完整代码

```python

# ### (1) 导入导出 不要加分号
导出数据库
1.退出mysql
2.选择要导出的默认路径
3.mysqldump -uroot -p db001 > db001.sql

导入数据库
1.登录到mysql之后
2.创建新的数据库
3.source 路径+文件

# ### (2) 配置linux下的编码集
!includedir  /etc/mysql/conf.d/       客户端的修改
# 设置mysql客户端默认字符集
default-character-set=utf8
!includedir  /etc/mysql/mysql.conf.d/ 服务端的修改
# 服务端使用的字符集默认为8比特编码的latin1字符集
character-set-server=utf8

service mysql restart

```

### 📖 要点讲解

- 服务端使用的字符集默认为8比特编码的latin1字符集

---

## 🖼️ 参考资料

![django运作流程.png](./assets/django运作流程.png)

![orm图.png](./assets/orm图.png)

![联表语句写法.png](./assets/联表语句写法.png)

![1607695795818.png](./assets/1607695795818.png)

![1607695810080.png](./assets/1607695810080.png)

![1607695842134.png](./assets/1607695842134.png)

![1607695993385.png](./assets/1607695993385.png)

![1607696464062.png](./assets/1607696464062.png)

![1607806325895.png](./assets/1607806325895.png)

![1560401672936.png](./assets/1560401672936.png)

![1560401690571.png](./assets/1560401690571.png)

![1560401702657.png](./assets/1560401702657.png)

![1560401713280.png](./assets/1560401713280.png)

![1560401726064.png](./assets/1560401726064.png)

![1560401741798.png](./assets/1560401741798.png)

![1560401751508.png](./assets/1560401751508.png)

![1560559430738.png](./assets/1560559430738.png)

![1560559452665.png](./assets/1560559452665.png)

![1560559463455.png](./assets/1560559463455.png)

![1560559471782.png](./assets/1560559471782.png)

![表结构(1).png](./assets/表结构(1).png)

![表结构.png](./assets/表结构.png)
