# Day 21: day21 ajax复习 cbv执行流程 中间件part1 中间件part2 分页器语法 分页效果一 分页效果二 会话跟踪技术cookie 会话跟踪技术session

> 对应原课程：day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session

---

## 1. manage.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/2.cbv_pro/manage.py", line 10, in main
    from django.core.management import execute_from_command_line
ModuleNotFoundError: No module named 'django'

The above exception was the direct cause of the following exception:

Traceback (most recent call last):
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/2.cbv_pro/manage.py", line 21, in <module>
    main()
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/2.cbv_pro/manage.py", line 12, in main
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
    os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'cbv_pro.settings')
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
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/2.cbv_pro/app1/admin.py", line 1, in <module>
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
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/2.cbv_pro/app1/apps.py", line 1, in <module>
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
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/2.cbv_pro/app1/models.py", line 1, in <module>
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
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/2.cbv_pro/app1/tests.py", line 1, in <module>
    from django.test import TestCase
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.test import TestCase

# Create your tests here.

# 复习1
class Ceshi():
	#绑定到类的方法,自动传递类参数;
	@classmethod
	def index(cls):
		print(cls)
obj = Ceshi()
obj.index()
Ceshi.index()

# 复习2
# 通过字符串去操作类对象 或者 模块中的成员
# 反射 hasattr  getattr setattr delattr
class Ceshi():
	def get(self):
		return 1111
	def post(self):
		return 2222
obj = Ceshi()

if hasattr(obj,"get"): # 有就返回True , 反之返回False
	# func = getattr(obj,"ge111t")
	# 第三个参数的作用:为了防止报错,在不存在时,给与提醒
	func = getattr(obj, "get","抱歉,没有该方法")
	print(func)
	# print(func())

```

### 📖 要点讲解

- Create your tests here.

- 通过字符串去操作类对象 或者 模块中的成员

- 反射 hasattr  getattr setattr delattr

- func = getattr(obj,"ge111t")

- 第三个参数的作用:为了防止报错,在不存在时,给与提醒

---

## 7. views.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/2.cbv_pro/app1/views.py", line 1, in <module>
    from django.shortcuts import render,HttpResponse
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.shortcuts import render,HttpResponse
from django.views import View

# Create your views here.
# 要求:必须继承View类 -> 系统才认可当前为视图类,可以和路由捆绑;
class LoginView(View):
	"""
	# cbv
		1.方法名不能乱写 只能如下请求方法['get', 'post', 'put', 'patch', 'delete', 'head', 'options', 'trace']
		2.如果自定义dispatch , 最后落脚在父类的dispatch返回值中,前面可以自己加一些功能扩展
	"""

	def dispatch(self, request, *args, **kwargs):
		print("自定义dispatch方法,可以在这个环节写更多的代码逻辑... 扩展小功能")
		return super().dispatch(request, *args, **kwargs)

	def get(self,request):
		print("get请求方法被调用")
		return HttpResponse("GET 请求")

	def post(self,request):
		print("post请求方法被调用")
		return HttpResponse("POST 请求")

	def put(self,request):
		print("put请求方法被调用")
		return HttpResponse("put 请求")

	def patch(self,request):
		print("patch请求方法被调用")
		return HttpResponse("patch 请求")

	def delete(self,request):
		print("delete请求方法被调用")
		return HttpResponse("delete 请求")

# def func(request):
# 	if request.method == "GET":
# 			...
# 	elif request.method == "POST"
# 			...
# 	return HttpResponse('ok')

```

### 📖 要点讲解

- Create your views here.

- 要求:必须继承View类 -> 系统才认可当前为视图类,可以和路由捆绑;

- if request.method == "GET":

- elif request.method == "POST"

- return HttpResponse('ok')

---

## 8. __init__.py

### 💻 完整代码

```python

```

---

## 9. mymiddleware.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/2.cbv_pro/app1/utils/mymiddleware.py", line 11, in <module>
    from django.shortcuts import render,HttpResponse
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

# ### 自定义中间件  必须继承MiddlewareMixin
"""
1.中间键里面的方法process_request , process_response 名字是固定,统一由系统调用
2.请求方法可以不返回响应体
但是响应方法必须返回响应体
3.把写好的中间价,加载到setting中的middleware中
4.中间件流程
(1).注意中间件的执行流程:请求方法中,如果直接返回响应体,会触发该中间件的响应方法,就不会把数据扔到下一个中间件了,而是直接往回走
(2).各个中间件的响应方法的返回值,永远后者替换前者;后一个中间件中的return数据替换前一个中间件的返回数据;
"""
from django.shortcuts import render,HttpResponse
from django.utils.deprecation import MiddlewareMixin
class Mdware1(MiddlewareMixin):
	def process_request(self,request):
		print("Mdware1 执行了.... ")
		# return HttpResponse("Mdware1 请求返回了111")

	def process_response(self,request,response):
		print("Mdware1 响应了....")
		print(response)
		return HttpResponse("mdware1直接返回222")
		# return response`

class Mdware2(MiddlewareMixin):
	def process_request(self,request):
		print("Mdware2 执行了.... ")
		return HttpResponse("Mdware2 请求返回了2222")

	def process_response(self,request,response):
		print("Mdware2 响应了....")
		print(response)
		# return HttpResponse("mdware1直接返回222")
		return response

```

### 📖 要点讲解

- ### 自定义中间件  必须继承MiddlewareMixin

- return HttpResponse("Mdware1 请求返回了111")

- return HttpResponse("mdware1直接返回222")

---

## 10. __init__.py

### 💻 完整代码

```python

```

---

## 11. settings.py

### 💻 完整代码

```python

"""
Django settings for cbv_pro project.

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
SECRET_KEY = 'rgkl+-cu682%0jp_+!efu9_0dde0@2!n^uwcmt45bf6*vvb)(n'

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
    # 把写好的中间件在配置文件中指定一下;
    'app1.utils.mymiddleware.Mdware1',
    'app1.utils.mymiddleware.Mdware2'
]
# from django.middleware.security import SecurityMiddleware
# from django.middleware.csrf import CsrfViewMiddleware
# from django.contrib.sessions.middleware import SessionMiddleware
# from django.contrib.auth.middleware import AuthenticationMiddleware
ROOT_URLCONF = 'cbv_pro.urls'

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

WSGI_APPLICATION = 'cbv_pro.wsgi.application'

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

```

### 📖 要点讲解

- Build paths inside the project like this: os.path.join(BASE_DIR, ...)

- Quick-start development settings - unsuitable for production

- See https://docs.djangoproject.com/en/2.2/howto/deployment/checklist/

- SECURITY WARNING: keep the secret key used in production secret!

- SECURITY WARNING: don't run with debug turned on in production!

- Application definition

- 'django.middleware.csrf.CsrfViewMiddleware',

- from django.middleware.security import SecurityMiddleware

- from django.middleware.csrf import CsrfViewMiddleware

- from django.contrib.sessions.middleware import SessionMiddleware

- from django.contrib.auth.middleware import AuthenticationMiddleware

- https://docs.djangoproject.com/en/2.2/ref/settings/#databases

- https://docs.djangoproject.com/en/2.2/ref/settings/#auth-password-validators

- https://docs.djangoproject.com/en/2.2/topics/i18n/

- Static files (CSS, JavaScript, Images)

- https://docs.djangoproject.com/en/2.2/howto/static-files/

---

## 12. urls.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/2.cbv_pro/cbv_pro/urls.py", line 16, in <module>
    from django.contrib import admin
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

"""cbv_pro URL Configuration

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
from app1.views import LoginView
urlpatterns = [
    path('admin/', admin.site.urls),
    # path('login/',views.get ) fbv
    # 语法: 视图类.as_view() 剩下的方法调用自动触发...
    path('login/',LoginView.as_view()) # cbv

]

"""
 path('login/',LoginView.as_view())
 ||
 path('login/',view) 内部写了闭包函数,返回view
  
as_view()

def view(request, *args, **kwargs):
    self = cls(**initkwargs)  # 拿着你传进去的类进行实例化对象;
    if hasattr(self, 'get') and not hasattr(self, 'head'):
        self.head = self.get
    self.setup(request, *args, **kwargs)
    if not hasattr(self, 'request'):
        raise AttributeError(
            "%s instance has no 'request' attribute. Did you override "
            "setup() and forget to call super()?" % cls.__name__
        )
    # 本类对象中没有dispatch方法,调用父类view的dispatch方法
    return self.dispatch(request, *args, **kwargs) # 落脚点最后返回的是dispatch这个方法的返回值

def dispatch(self, request, *args, **kwargs):
    # Try to dispatch to the right method; if a method doesn't exist,
    # defer to the error handler. Also defer to the error handler if the
    # request method isn't on the approved list.
    # if request.method == "GET" request.method == "POST" request.method == "PUT" request.method == "DELETE" .... 
    # GET => get  POST => post  DELETE => delete
    # http_method_names = ['get', 'post', 'put', 'patch', 'delete', 'head', 'options', 'trace']
    if request.method.lower() in self.http_method_names:
        handler = getattr(self, request.method.lower(), self.http_method_not_allowed)
        # 反射的是get post put ... 这些方法 ... 自定义的get post 类中方法....
    else:
        handler = self.http_method_not_allowed
    # get() post() put() 调用类中的成员 ,返回数据 ,  绑定方法的self不需要手动传递
    return handler(request, *args, **kwargs)

"""

```

### 📖 要点讲解

- path('login/',views.get ) fbv

- 语法: 视图类.as_view() 剩下的方法调用自动触发...

- 本类对象中没有dispatch方法,调用父类view的dispatch方法

- Try to dispatch to the right method; if a method doesn't exist,

- defer to the error handler. Also defer to the error handler if the

- request method isn't on the approved list.

- if request.method == "GET" request.method == "POST" request.method == "PUT" request.method == "DELETE" ....

- GET => get  POST => post  DELETE => delete

- http_method_names = ['get', 'post', 'put', 'patch', 'delete', 'head', 'options', 'trace']

- 反射的是get post put ... 这些方法 ... 自定义的get post 类中方法....

- get() post() put() 调用类中的成员 ,返回数据 ,  绑定方法的self不需要手动传递

---

## 13. wsgi.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/2.cbv_pro/cbv_pro/wsgi.py", line 12, in <module>
    from django.core.wsgi import get_wsgi_application
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

"""
WSGI config for cbv_pro project.

It exposes the WSGI callable as a module-level variable named ``application``.

For more information on this file, see
https://docs.djangoproject.com/en/2.2/howto/deployment/wsgi/
"""

import os

from django.core.wsgi import get_wsgi_application

os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'cbv_pro.settings')

application = get_wsgi_application()

```

---

## 14. manage.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/4.fenyeqi/manage.py", line 10, in main
    from django.core.management import execute_from_command_line
ModuleNotFoundError: No module named 'django'

The above exception was the direct cause of the following exception:

Traceback (most recent call last):
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/4.fenyeqi/manage.py", line 21, in <module>
    main()
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/4.fenyeqi/manage.py", line 12, in main
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
    os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'fenyeqi.settings')
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
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/4.fenyeqi/app1/admin.py", line 1, in <module>
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
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/4.fenyeqi/app1/apps.py", line 1, in <module>
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
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/4.fenyeqi/app1/models.py", line 1, in <module>
    from django.db import models
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.db import models

# django默认会为每张表添加主键,默认主键名为id
class Book(models.Model):
	title = models.CharField(max_length=50)
	# 小数保留2位,整数保留6位,一共8位
	price = models.DecimalField(max_digits=8,decimal_places=2)

```

### 📖 要点讲解

- django默认会为每张表添加主键,默认主键名为id

---

## 19. tests.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/4.fenyeqi/app1/tests.py", line 1, in <module>
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
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/4.fenyeqi/app1/views.py", line 1, in <module>
    from django.shortcuts import render,HttpResponse
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.shortcuts import render,HttpResponse
import time
from app1.models import Book

# 引入分页期功能
from django.core.paginator import Paginator

def add(request):
	# 1.批量添加数据
	"""
	# 方法一
	startime = time.time()
	# 插入了1000次
	for i in range(1000):
		Book.objects.create(title='book'+str(i) , price = i ** 2)
	endtime = time.time()
	print(endtime - startime) # 1.99
	"""
	# 方法二
	startime = time.time()
	lst = []
	for i in range(100):
		book = Book(title='book'+str(i) , price = i ** 2)
		lst.append(book)
	# bulk_create(列表容器) 批量添加数据 , 直插入了一次
	Book.objects.bulk_create(lst)
	endtime = time.time()
	print(endtime - startime) # 0.08572745323181152
	return HttpResponse("ok")

def index(request):
	# 语法    分页器对象 = Paginator(参数1:数据列表  参数2:一页显示几条)
	paginator = Paginator(  [1,2,3,4,5,6,7,8,9,10] , 3 )

	# 分页的成员属性
	# 1.数据总个数
	print(paginator.count)     #10
	# 2.页码数
	print(paginator.num_pages) # 4
	# 3.页码范围,返回range对象
	print(paginator.page_range) # range(1, 5)

	# 分页的成员方法
	# 4.获取第几页的数据 => 返回的是页面对象
	page = paginator.page(3)
	print(page,"<=========111=====>")
	# 5.查看含有下一页,返回True or False
	print(page.has_next()) # True
	# 6.返回下一页页码
	print(page.next_page_number())  # 4 如果已经没有下一页了,直接报错
	# 7.查看含有上一页,返回True or False
	print(page.has_previous()) # True
	# 8.返回上一页页码
	print(page.previous_page_number()) # 2
	# 9.获取改页码所有数据
	print(page.object_list) # [7, 8, 9]

	return HttpResponse("ok")

def index2(request):
	# 获取地址栏传过来的页面值 [通过地址栏传参,知道当前页码是多少页]
	current_num= int(request.GET.get("page",1))  #i 默认获取不到为1页
	print(current_num , type(current_num),"<==============>")

	book_lst = Book.objects.all()
	# 按照5条一页进行数据分页
	paginator = Paginator(book_lst, 5)
	print(book_lst)
	# 找到当前yemi8an对应的数据
	page = paginator.page(current_num)
	print(page, "<=========222=====>")
	# page对象可以直接迭代
	# for i in page:
	# 	print(i)
	# page 当前页面数,current_num当前页面是几
	return render(request,"index.html",{"page":page,"paginator":paginator,"current_num":current_num})

def index3(request):
	# 获取地址栏传过来的页面值 [通过地址栏传参,知道当前页码是多少页]
	current_num= int(request.GET.get("page",1))  #i 默认获取不到为1页
	print(current_num , type(current_num),"<==============>")
	book_lst = Book.objects.all()
	# 按照5条一页进行数据分页
	paginator = Paginator(book_lst, 5)
	print(book_lst)
	# 找到当前yemi8an对应的数据
	page = paginator.page(current_num)

	# ### 控制页码范围
	if paginator.num_pages > 11:
		# 大于最大页
		if current_num + 5 > paginator.num_pages:
			# range(开始值[往前减去10条],最大值40+1) = 11条
			page_range = range(paginator.num_pages - 10,paginator.num_pages + 1)
		# 小于最小页
		elif current_num - 5 < 1:
			page_range = range(1,12)
		# 通过range,卡死页码范围.
		else:
			page_range = range(current_num-5,current_num+5+1)
	else:
		# 返回页码范围
		page_range = paginator.page_range

	return render(request,"index2.html",{"page":page,"paginator":paginator,"current_num":current_num , "page_range":page_range})
# 1 2 3 4 5  6  7 8 9 10 11 12 13 .... 40
# 38 + 5 => 43 > 40
#
# 3 - 5 => -2 < 1
# range(1,12)

```

### 📖 要点讲解

- bulk_create(列表容器) 批量添加数据 , 直插入了一次

- 语法    分页器对象 = Paginator(参数1:数据列表  参数2:一页显示几条)

- 4.获取第几页的数据 => 返回的是页面对象

- 5.查看含有下一页,返回True or False

- 7.查看含有上一页,返回True or False

- 获取地址栏传过来的页面值 [通过地址栏传参,知道当前页码是多少页]

- page 当前页面数,current_num当前页面是几

- 获取地址栏传过来的页面值 [通过地址栏传参,知道当前页码是多少页]

- range(开始值[往前减去10条],最大值40+1) = 11条

- 1 2 3 4 5  6  7 8 9 10 11 12 13 .... 40

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
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/4.fenyeqi/fenyeqi/__init__.py", line 1, in <module>
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
Django settings for fenyeqi project.

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
SECRET_KEY = '4us1v4ahfe4#c9-wz!82r6dew6sype3v7)dd-dx71rneh3j-9+'

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
    # 'django.middleware.csrf.CsrfViewMiddleware',
    'django.contrib.auth.middleware.AuthenticationMiddleware',
    'django.contrib.messages.middleware.MessageMiddleware',
    'django.middleware.clickjacking.XFrameOptionsMiddleware',
]

ROOT_URLCONF = 'fenyeqi.urls'

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

WSGI_APPLICATION = 'fenyeqi.wsgi.application'

# Database
# https://docs.djangoproject.com/en/2.2/ref/settings/#databases

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        # 'NAME': os.path.join(BASE_DIR, 'db.sqlite3'),
        'NAME':'ceshi100',
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
LOGGING = {
    'version': 1,
    'disable_existing_loggers': False,
    'handlers': {
        'console':{
            'level':'DEBUG',
            'class':'logging.StreamHandler',
        },
    },
    'loggers': {
        'django.db.backends': {
            'handlers': ['console'],
            'propagate': True,
            'level':'DEBUG',
        },
    }
}

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

## 24. urls.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/4.fenyeqi/fenyeqi/urls.py", line 16, in <module>
    from django.contrib import admin
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

"""fenyeqi URL Configuration

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
    path('index/',views.index),
    path("index2/",views.index2),
    path("index3/",views.index3)
]

```

---

## 25. wsgi.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/4.fenyeqi/fenyeqi/wsgi.py", line 12, in <module>
    from django.core.wsgi import get_wsgi_application
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

"""
WSGI config for fenyeqi project.

It exposes the WSGI callable as a module-level variable named ``application``.

For more information on this file, see
https://docs.djangoproject.com/en/2.2/howto/deployment/wsgi/
"""

import os

from django.core.wsgi import get_wsgi_application

os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'fenyeqi.settings')

application = get_wsgi_application()

```

---

## 26. manage.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/1.booksys/manage.py", line 10, in main
    from django.core.management import execute_from_command_line
ModuleNotFoundError: No module named 'django'

The above exception was the direct cause of the following exception:

Traceback (most recent call last):
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/1.booksys/manage.py", line 21, in <module>
    main()
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/1.booksys/manage.py", line 12, in main
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
    os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'booksys.settings')
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

## 28. settings.py

### 💻 完整代码

```python

"""
Django settings for booksys project.

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
SECRET_KEY = '0$wnhj92w-c&f!lcuwn_3hqu4xo4$yh4m(-h&-xdrz3gbi&d3q'

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
    'django.middleware.csrf.CsrfViewMiddleware',
    'django.contrib.auth.middleware.AuthenticationMiddleware',
    'django.contrib.messages.middleware.MessageMiddleware',
    'django.middleware.clickjacking.XFrameOptionsMiddleware',
]

ROOT_URLCONF = 'booksys.urls'

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

WSGI_APPLICATION = 'booksys.wsgi.application'

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

```

### 📖 要点讲解

- Build paths inside the project like this: os.path.join(BASE_DIR, ...)

- Quick-start development settings - unsuitable for production

- See https://docs.djangoproject.com/en/2.2/howto/deployment/checklist/

- SECURITY WARNING: keep the secret key used in production secret!

- SECURITY WARNING: don't run with debug turned on in production!

- Application definition

- https://docs.djangoproject.com/en/2.2/ref/settings/#databases

- https://docs.djangoproject.com/en/2.2/ref/settings/#auth-password-validators

- https://docs.djangoproject.com/en/2.2/topics/i18n/

- Static files (CSS, JavaScript, Images)

- https://docs.djangoproject.com/en/2.2/howto/static-files/

---

## 29. urls.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/1.booksys/booksys/urls.py", line 16, in <module>
    from django.contrib import admin
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

"""booksys URL Configuration

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
    path('',views.index),
    path('book/',views.select_all)
]

```

---

## 30. wsgi.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/1.booksys/booksys/wsgi.py", line 12, in <module>
    from django.core.wsgi import get_wsgi_application
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

"""
WSGI config for booksys project.

It exposes the WSGI callable as a module-level variable named ``application``.

For more information on this file, see
https://docs.djangoproject.com/en/2.2/howto/deployment/wsgi/
"""

import os

from django.core.wsgi import get_wsgi_application

os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'booksys.settings')

application = get_wsgi_application()

```

---

## 31. __init__.py

### 💻 完整代码

```python

```

---

## 32. admin.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/1.booksys/app1/admin.py", line 1, in <module>
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

## 33. apps.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/1.booksys/app1/apps.py", line 1, in <module>
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

## 34. models.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/1.booksys/app1/models.py", line 1, in <module>
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

## 35. tests.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/1.booksys/app1/tests.py", line 1, in <module>
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

## 36. views.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/1.booksys/app1/views.py", line 1, in <module>
    from django.shortcuts import render,HttpResponse
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.shortcuts import render,HttpResponse
import json
# Create your views here.
def index(request):
	# return HttpResponse("ok")
	return render(request,"index.html")

def select_all(request):
	data = [
		{'title':"金瓶梅","price":10,"publish":"清华大学出版社"},
		{'title':"舒克和贝塔","price":20,"publish":"北京大学出版社"}
	]
	# ajax请求时,需要返回json格式的字符串
	return HttpResponse(json.dumps(data))

```

### 📖 要点讲解

- Create your views here.

- return HttpResponse("ok")

- ajax请求时,需要返回json格式的字符串

---

## 37. __init__.py

### 💻 完整代码

```python

```

---

## 38. manage.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/6.session/manage.py", line 10, in main
    from django.core.management import execute_from_command_line
ModuleNotFoundError: No module named 'django'

The above exception was the direct cause of the following exception:

Traceback (most recent call last):
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/6.session/manage.py", line 21, in <module>
    main()
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/6.session/manage.py", line 12, in main
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
    os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'session.settings')
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

## 39. __init__.py

### 💻 完整代码

```python

```

---

## 40. admin.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/6.session/app1/admin.py", line 1, in <module>
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

## 41. apps.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/6.session/app1/apps.py", line 1, in <module>
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

## 42. models.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/6.session/app1/models.py", line 1, in <module>
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

## 43. tests.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/6.session/app1/tests.py", line 1, in <module>
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

## 44. views.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/6.session/app1/views.py", line 1, in <module>
    from django.shortcuts import render,HttpResponse,redirect
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.shortcuts import render,HttpResponse,redirect

# Create your views here.
def login(request):
	if request.method == "GET":
		# return HttpResponse('ok')
		return render(request,"login.html")
	elif request.method == "POST":
		user = request.POST.get("user")
		pwd = request.POST.get("pwd")
		if user == "wangwen" and pwd == "111":
			"""
				(1) 生成一个session_id 作为键 (一个随机字符串) e98xho04o8drexvdgij17tzjyhzab1jg 系统自己写
				(2) 存放在客户端浏览器一份, response.set_cookie("session_id","键名") 系统自己写
				相当于给浏览器一把下一次取件的钥匙,通过session_id来取件 
				(3) 存放在服务端数据库一份,在django_session 表中添加记录 系统自己写
				session_key    session_data   expire_date
				键名            数据           过期时间		
			"""
			# 存储session的写法
			request.session["is_login"] = True
			request.session["user"] = "wangwen"
			return HttpResponse("验证成功")
		else:
			return HttpResponse("验证失败")

def index(request):
	# 获取session的相关数据
	is_login = request.session.get("is_login")
	user = request.session.get("user")
	"""
	(1) 浏览器拿着cookie中存放的session_id去服务端取数据, session_id = request.COOKIES.get("session_id")
	(2) 在django_session表中,查看下该键名对应的过期时间是否到期
	(3) ok的话,获取到该键对应的session_data,进而取出里面的数据	
	"""
	print(is_login)
	print(user)
	if is_login:
		return render(request,"index.html",{"user":user})
	else:
		return redirect('/login/')

def loginout(request):
	# 清除服务端的session 删除的是当前的sessionid在数据库储存的那一条自己的记录
	request.session.flush()
	return redirect('/login/')

```

### 📖 要点讲解

- Create your views here.

- return HttpResponse('ok')

- 清除服务端的session 删除的是当前的sessionid在数据库储存的那一条自己的记录

---

## 45. __init__.py

### 💻 完整代码

```python

```

---

## 46. __init__.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/6.session/session/__init__.py", line 1, in <module>
    import pymysql
ModuleNotFoundError: No module named 'pymysql'

```

### 💻 完整代码

```python

import pymysql
pymysql.install_as_MySQLdb()

```

---

## 47. settings.py

### 💻 完整代码

```python

"""
Django settings for session project.

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
SECRET_KEY = '7!c@es=uth@qr4vjcn1k)%m8rz7-3%myg8-4*lpws(w(=$6ln_'

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
    # 'django.middleware.csrf.CsrfViewMiddleware',
    'django.contrib.auth.middleware.AuthenticationMiddleware',
    'django.contrib.messages.middleware.MessageMiddleware',
    'django.middleware.clickjacking.XFrameOptionsMiddleware',
]

ROOT_URLCONF = 'session.urls'

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

WSGI_APPLICATION = 'session.wsgi.application'

# Database
# https://docs.djangoproject.com/en/2.2/ref/settings/#databases

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        # 'NAME': os.path.join(BASE_DIR, 'db.sqlite3'),
        'NAME':'db200',
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

## 48. urls.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/6.session/session/urls.py", line 16, in <module>
    from django.contrib import admin
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

"""session URL Configuration

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
    path('login/',views.login),
    path('index/',views.index),
    path('loginout/',views.loginout),
]

```

---

## 49. wsgi.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/6.session/session/wsgi.py", line 12, in <module>
    from django.core.wsgi import get_wsgi_application
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

"""
WSGI config for session project.

It exposes the WSGI callable as a module-level variable named ``application``.

For more information on this file, see
https://docs.djangoproject.com/en/2.2/howto/deployment/wsgi/
"""

import os

from django.core.wsgi import get_wsgi_application

os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'session.settings')

application = get_wsgi_application()

```

---

## 50. manage.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/5.cookie/manage.py", line 10, in main
    from django.core.management import execute_from_command_line
ModuleNotFoundError: No module named 'django'

The above exception was the direct cause of the following exception:

Traceback (most recent call last):
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/5.cookie/manage.py", line 21, in <module>
    main()
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/5.cookie/manage.py", line 12, in main
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
    os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'cookie.settings')
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

## 51. __init__.py

### 💻 完整代码

```python

```

---

## 52. admin.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/5.cookie/app1/admin.py", line 1, in <module>
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

## 53. apps.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/5.cookie/app1/apps.py", line 1, in <module>
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

## 54. models.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/5.cookie/app1/models.py", line 1, in <module>
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

## 55. tests.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/5.cookie/app1/tests.py", line 1, in <module>
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

## 56. views.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/5.cookie/app1/views.py", line 1, in <module>
    from django.shortcuts import render,HttpResponse,redirect
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.shortcuts import render,HttpResponse,redirect

# Create your views here.
def index(request):

	# 获取cookie  键为is_login的值
	is_login = request.COOKIES.get("is_login")
	if is_login == "wangwen":
		return render(request,"index.html",{"user":"wangwen"})
	else:
		return redirect("/login/")

def login(request):
	if request.method == "GET":

		# 直接删除cookie
		response = render(request, "login.html")
		response.delete_cookie("is_login")
		return response

	elif request.method == "POST":
		user = request.POST.get("user")
		pwd = request.POST.get("pwd")
		if user == "wangwen" and  pwd == "111":
			response  = HttpResponse("登陆成功")
			# 如果能够登陆成功,就把该数据记录到浏览器的cookie中
			# 把数据存储在浏览器的cookie文件中   ,  响应对象.set_cookie(键,值,过期时间[单位是秒])
			response.set_cookie("is_login","wangwen",3600)
			return response
		else:
			return HttpResponse("登陆失败")

```

### 📖 要点讲解

- Create your views here.

- 获取cookie  键为is_login的值

- 如果能够登陆成功,就把该数据记录到浏览器的cookie中

- 把数据存储在浏览器的cookie文件中   ,  响应对象.set_cookie(键,值,过期时间[单位是秒])

---

## 57. __init__.py

### 💻 完整代码

```python

```

---

## 58. __init__.py

### 💻 完整代码

```python

```

---

## 59. settings.py

### 💻 完整代码

```python

"""
Django settings for cookie project.

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
SECRET_KEY = '_uhzdvdw@q7!o3x73s&ckx7tbqadsfmf2+1ix1-*#5+3y+^g$6'

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

ROOT_URLCONF = 'cookie.urls'

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

WSGI_APPLICATION = 'cookie.wsgi.application'

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

## 60. urls.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/5.cookie/cookie/urls.py", line 16, in <module>
    from django.contrib import admin
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

"""cookie URL Configuration

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
    path('index/',views.index),
    path('login/',views.login)
]

```

---

## 61. wsgi.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/5.cookie/cookie/wsgi.py", line 12, in <module>
    from django.core.wsgi import get_wsgi_application
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

"""
WSGI config for cookie project.

It exposes the WSGI callable as a module-level variable named ``application``.

For more information on this file, see
https://docs.djangoproject.com/en/2.2/howto/deployment/wsgi/
"""

import os

from django.core.wsgi import get_wsgi_application

os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'cookie.settings')

application = get_wsgi_application()

```

---

## 62. 0001_initial.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day21_ajax复习_cbv执行流程_中间件part1_中间件part2_分页器语法_分页效果一_分页效果二_会话跟踪技术cookie_会话跟踪技术session/4.fenyeqi/app1/migrations/0001_initial.py", line 3, in <module>
    from django.db import migrations, models
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

# Generated by Django 2.2.17 on 2020-12-27 06:48

from django.db import migrations, models

class Migration(migrations.Migration):

    initial = True

    dependencies = [
    ]

    operations = [
        migrations.CreateModel(
            name='Book',
            fields=[
                ('id', models.AutoField(auto_created=True, primary_key=True, serialize=False, verbose_name='ID')),
                ('title', models.CharField(max_length=50)),
                ('price', models.DecimalField(decimal_places=2, max_digits=8)),
            ],
        ),
    ]

```

### 📖 要点讲解

- Generated by Django 2.2.17 on 2020-12-27 06:48

---

## 🖼️ 参考资料

![cookie_session.png](./assets/cookie_session.png)

![中间件执行流程.png](./assets/中间件执行流程.png)

![中间件执行流程2.png](./assets/中间件执行流程2.png)

![中间件执行流程4.png](./assets/中间件执行流程4.png)

![执行流程2.png](./assets/执行流程2.png)

![流程.png](./assets/流程.png)

![1607695795818.png](./assets/1607695795818.png)

![1607695810080.png](./assets/1607695810080.png)

![1607695842134.png](./assets/1607695842134.png)

![1607695993385.png](./assets/1607695993385.png)

![1607696464062.png](./assets/1607696464062.png)

![1607806325895.png](./assets/1607806325895.png)

![1609030497976.png](./assets/1609030497976.png)

![1609030508660.png](./assets/1609030508660.png)
