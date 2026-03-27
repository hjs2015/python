# Day 22: day22 drf概念 drf基本使用 序列化器 序列化器的校验功能 drf增删改查

> 对应原课程：day22_drf概念_drf基本使用_序列化器_序列化器的校验功能_drf增删改查

---

## 1. manage.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day22_drf概念_drf基本使用_序列化器_序列化器的校验功能_drf增删改查/drfdemo1/manage.py", line 10, in main
    from django.core.management import execute_from_command_line
ModuleNotFoundError: No module named 'django'

The above exception was the direct cause of the following exception:

Traceback (most recent call last):
  File "/tmp/python3_course/day22_drf概念_drf基本使用_序列化器_序列化器的校验功能_drf增删改查/drfdemo1/manage.py", line 21, in <module>
    main()
  File "/tmp/python3_course/day22_drf概念_drf基本使用_序列化器_序列化器的校验功能_drf增删改查/drfdemo1/manage.py", line 12, in main
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
    os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'drfdemo1.settings')
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
  File "/tmp/python3_course/day22_drf概念_drf基本使用_序列化器_序列化器的校验功能_drf增删改查/drfdemo1/app1/admin.py", line 1, in <module>
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
  File "/tmp/python3_course/day22_drf概念_drf基本使用_序列化器_序列化器的校验功能_drf增删改查/drfdemo1/app1/apps.py", line 1, in <module>
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

## 5. models.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day22_drf概念_drf基本使用_序列化器_序列化器的校验功能_drf增删改查/drfdemo1/app1/models.py", line 1, in <module>
    from django.db import models
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.db import models

# Create your models here.
class Student(models.Model):
    # 模型字段
    name = models.CharField(max_length=5,verbose_name="姓名")
    sex = models.BooleanField(default=1,verbose_name="性别")
    age = models.IntegerField(verbose_name="年龄")
    class_null = models.CharField(max_length=5,verbose_name="班级编号")
    description = models.TextField(max_length=1000,verbose_name="个性签名")

    # 元类Meta , 定义类的原始属性
    class Meta:
	    # 自定义表名
        db_table="tb_student"
	    # 自定义表的中文名(单数)
        verbose_name = "学生"
	    # 自定义表的中文名(复数) 默认在中文后面加s;
        verbose_name_plural = "学生"

```

### 📖 要点讲解

- Create your models here.

- 自定义表的中文名(复数) 默认在中文后面加s;

---

## 6. tests.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day22_drf概念_drf基本使用_序列化器_序列化器的校验功能_drf增删改查/drfdemo1/app1/tests.py", line 1, in <module>
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
  File "/tmp/python3_course/day22_drf概念_drf基本使用_序列化器_序列化器的校验功能_drf增删改查/drfdemo1/app1/views.py", line 1, in <module>
    from django.shortcuts import render,HttpResponse
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.shortcuts import render,HttpResponse

# Create your views here.
# cbv  fbv
from django.views import View
from app1.models import Student
# from django.core import serializers
from rest_framework import serializers
from rest_framework.response import Response
from django.http import JsonResponse

# drf 组件需要继承APIView
from rest_framework.views import APIView

# cbv
"""
class StudentView(View):
	# 查询
	def get(self,request):
		data = Student.objects.all()
		# 语法: serialize(格式,数据) => 进行序列化
		res = serializers.serialize("json",data)
		print(res,type(res),"<==============>")
		return HttpResponse("ok")

	# 添加
	def post(self,request):
		# 获取字段信息
		tup = Student._meta.fields
		print(tup)
		# 获取字段别名
		name = tup[1].verbose_name
		print(name)
		# 获取表名
		print(Student._meta.db_table)
		# 获取表的中文名
		print(Student._meta.verbose_name)
		print(Student._meta.verbose_name_plural)
		return HttpResponse("post")

	# 修改
	def put(self,request):
		return HttpResponse("put")

	# 删除
	def delete(self,request):
		return HttpResponse("delete")
"""

# drf

# 自定义序列化器
"""
csrf防止跨站伪造攻击
1.drf可以自动帮助我们处理csrf发送过来的数据,不需要额外做注释
"""
class StudentSerializer(serializers.Serializer):
	# 对单个字段的校验 validate_字段名
	def validate_name(self,value): # value 是接过来的数据
		if value == "abc":
			raise serializers.ValidationError("不让起这个名字~")
		return value

	# 多个字段校验
	def validate(self,attrs):
		name = attrs["name"]
		class_null = attrs["class_null"]
		if len(name) > len(class_null):
			raise serializers.ValidationError("名字太长了")
		print(name,"<=============>")
		print(attrs , "<==========>")
		return attrs

	name = serializers.CharField(max_length=5)
	sex = serializers.BooleanField(default=1)
	age = serializers.IntegerField()
	class_null = serializers.CharField(max_length=5)
	# required=False 非必须字段
	description = serializers.CharField(max_length=1000,required=False)

class StudentView(APIView):
	# 查询所有数据
	def get(self,request):
		# 1.一条数据的序列化方法 [一个模型类对象]
		"""
		data = Student.objects.get(id=1)
		print(data)
		ss = StudentSerializer(instance=data)
		res = ss.data
		print(res , type(res))
		return Response(res)
		"""
		# 2.多条数据的序列化方法 [queryset]
		""""""
		data = Student.objects.all()
		print(data)
		ss = StudentSerializer(instance=data,many=True)
		# print(ss.data,type(ss.data),"<======>")
		return Response(ss.data)

		# 3.可以额外序列化更多数据,通过context关键字指定
		"""
		data = Student.objects.all()
		ss = StudentSerializer(instance=data,many=True,context={"aaazzzbb":234})
		print(ss)
		res = ss.context
		print(res , type(res))
		
		# return Response(ss.data)
		# 如果是字典,可以直接返回,如果是列表,需要指定safe=False
		return JsonResponse(ss.context)
		# return JsonResponse(ss.data,safe=False)
		"""		
		return Response({})

	# 插入数据
	def post(self,request):
		print(request.GET , "<GET>")
		print(request.POST,"<POST>")
		print(request.data,"<DATA>")

		"""
		# 反序列化(收数据)
		# instance=(写要序列化的数据)  data=(写要反序列化的数据)
		ss = StudentSerializer(data=request.data)
		# print(ss.data)
		# 检测数据是否校验成功
		print(ss.is_valid())
		# 获取错误的原因
		print(ss.errors)
		# 获取正确数据
		print(ss.validated_data)
		"""
		ss = StudentSerializer(data=request.data)
		if ss.is_valid():
			data = Student.objects.create(**ss.validated_data)
			print(data)
			# 序列化 (发数据)
			ss2 = StudentSerializer(instance=data)
			return Response(ss2.data)
		else:
			return Response(ss.errors)

		return HttpResponse("post2")

# drf 的 api接口
class StudentDetailView(APIView):

	# 查询单条数据
	def get(self,request,pk):
		# 如果只是单独的模型类对象,可以直接序列化,如果是queryset必须加上many=True
		data = Student.objects.filter(pk=pk)
		print(data)
		ss = StudentSerializer(instance=data,many=True)
		return Response(ss.data)

	# 修改单条数据
	def put(self,request,pk):
		print(request.GET , "<GET>")
		print(request.POST,"<POST>")
		print(request.data,"<DATA>")
		# {'name': '王文', 'sex': 1, 'age': 8, 'class_null': '周末5期'}
		ss = StudentSerializer(data=request.data)
		if ss.is_valid():
			data = Student.objects.filter(pk=pk)
			print(ss.validated_data)
			res = data.update(**ss.validated_data)

			# 对修改成功的数据进行序列化返回给请求的客户端
			# 重新搜索当前数据
			data = Student.objects.filter(pk=pk)
			ss2 = StudentSerializer(instance=data,many=True)
			return Response(ss2.data)
		else:
			return Response(ss.errors)

	# 删除单条数据
	def delete(self,request,pk):
		data = Student.objects.filter(pk=pk)
		res = data.delete()
		# print(res)# (1, {'app1.Student': 1})
		dic = {"status":"删除成功"} if res[0] else {"status":"删除失败"}
		return Response(dic)

```

### 📖 要点讲解

- Create your views here.

- from django.core import serializers

- 语法: serialize(格式,数据) => 进行序列化

- 对单个字段的校验 validate_字段名

- 1.一条数据的序列化方法 [一个模型类对象]

- 2.多条数据的序列化方法 [queryset]

- print(ss.data,type(ss.data),"<======>")

- 3.可以额外序列化更多数据,通过context关键字指定

- return Response(ss.data)

- 如果是字典,可以直接返回,如果是列表,需要指定safe=False

- return JsonResponse(ss.data,safe=False)

- instance=(写要序列化的数据)  data=(写要反序列化的数据)

- 如果只是单独的模型类对象,可以直接序列化,如果是queryset必须加上many=True

- {'name': '王文', 'sex': 1, 'age': 8, 'class_null': '周末5期'}

- 对修改成功的数据进行序列化返回给请求的客户端

- print(res)# (1, {'app1.Student': 1})

---

## 8. __init__.py

### 💻 完整代码

```python

```

---

## 9. __init__.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day22_drf概念_drf基本使用_序列化器_序列化器的校验功能_drf增删改查/drfdemo1/drfdemo1/__init__.py", line 1, in <module>
    import pymysql
ModuleNotFoundError: No module named 'pymysql'

```

### 💻 完整代码

```python

import pymysql
pymysql.install_as_MySQLdb()

```

---

## 10. settings.py

### 💻 完整代码

```python

"""
Django settings for drfdemo1 project.

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
SECRET_KEY = '#3d8vuu63+(5s74-ymd-u(&23vw!%3!q0uad%eo(8=vzamy0_$'

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
    "app1",
    "rest_framework"
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

ROOT_URLCONF = 'drfdemo1.urls'

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

WSGI_APPLICATION = 'drfdemo1.wsgi.application'

# Database
# https://docs.djangoproject.com/en/2.2/ref/settings/#databases

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        # 'NAME': os.path.join(BASE_DIR, 'db.sqlite3'),
        'NAME':'drfdemo',
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

- 'django.middleware.csrf.CsrfViewMiddleware',

- https://docs.djangoproject.com/en/2.2/ref/settings/#databases

- 'NAME': os.path.join(BASE_DIR, 'db.sqlite3'),

- https://docs.djangoproject.com/en/2.2/ref/settings/#auth-password-validators

- https://docs.djangoproject.com/en/2.2/topics/i18n/

- Static files (CSS, JavaScript, Images)

- https://docs.djangoproject.com/en/2.2/howto/static-files/

---

## 11. urls.py

### 📋 运行结果

```

错误：/tmp/python3_course/day22_drf概念_drf基本使用_序列化器_序列化器的校验功能_drf增删改查/drfdemo1/drfdemo1/urls.py:25: SyntaxWarning: invalid escape sequence '\d'
  re_path('^index/(\d+)/$',views.StudentDetailView.as_view())
Traceback (most recent call last):
  File "/tmp/python3_course/day22_drf概念_drf基本使用_序列化器_序列化器的校验功能_drf增删改查/drfdemo1/drfdemo1/urls.py", line 16, in <module>
    from django.contrib import admin
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

"""drfdemo1 URL Configuration

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
from django.urls import path , re_path
from app1 import views

urlpatterns = [
    path('admin/', admin.site.urls),
    # cbv / drf
    path('index/',views.StudentView.as_view()),
    re_path('^index/(\d+)/$',views.StudentDetailView.as_view())
]

```

---

## 12. wsgi.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day22_drf概念_drf基本使用_序列化器_序列化器的校验功能_drf增删改查/drfdemo1/drfdemo1/wsgi.py", line 12, in <module>
    from django.core.wsgi import get_wsgi_application
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

"""
WSGI config for drfdemo1 project.

It exposes the WSGI callable as a module-level variable named ``application``.

For more information on this file, see
https://docs.djangoproject.com/en/2.2/howto/deployment/wsgi/
"""

import os

from django.core.wsgi import get_wsgi_application

os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'drfdemo1.settings')

application = get_wsgi_application()

```

---

## 13. 0001_initial.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day22_drf概念_drf基本使用_序列化器_序列化器的校验功能_drf增删改查/drfdemo1/app1/migrations/0001_initial.py", line 3, in <module>
    from django.db import migrations, models
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

# Generated by Django 2.2.17 on 2021-01-10 03:33

from django.db import migrations, models

class Migration(migrations.Migration):

    initial = True

    dependencies = [
    ]

    operations = [
        migrations.CreateModel(
            name='Student',
            fields=[
                ('id', models.AutoField(auto_created=True, primary_key=True, serialize=False, verbose_name='ID')),
                ('name', models.CharField(max_length=5, verbose_name='姓名')),
                ('sex', models.BooleanField(default=1, verbose_name='性别')),
                ('age', models.IntegerField(verbose_name='年龄')),
                ('class_null', models.CharField(max_length=5, verbose_name='班级编号')),
                ('description', models.TextField(max_length=1000, verbose_name='个性签名')),
            ],
            options={
                'verbose_name': '学生',
                'verbose_name_plural': '学生',
                'db_table': 'tb_student',
            },
        ),
    ]

```

### 📖 要点讲解

- Generated by Django 2.2.17 on 2021-01-10 03:33

---

## 🖼️ 参考资料

![1607695795818.png](./assets/1607695795818.png)

![1607695810080.png](./assets/1607695810080.png)

![1607695842134.png](./assets/1607695842134.png)

![1607695993385.png](./assets/1607695993385.png)

![1607696464062.png](./assets/1607696464062.png)

![1607806325895.png](./assets/1607806325895.png)

![1609030497976.png](./assets/1609030497976.png)

![1609030508660.png](./assets/1609030508660.png)

![1610188783535.png](./assets/1610188783535.png)

![1610188858300.png](./assets/1610188858300.png)

![1610188876535.png](./assets/1610188876535.png)

![1610189091054.png](./assets/1610189091054.png)

![1610191837496.png](./assets/1610191837496.png)

![1610192342344.png](./assets/1610192342344.png)

![1610193851313.png](./assets/1610193851313.png)

![1610195413513.png](./assets/1610195413513.png)
