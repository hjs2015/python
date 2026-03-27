# Day 17: day17 http协议请求报文响应报文 web升级版 web wsgi版本 django创建

> 对应原课程：day17_http协议请求报文响应报文_web升级版_web_wsgi版本_django创建

---

## 1. auth.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day17_http协议请求报文响应报文_web升级版_web_wsgi版本_django创建/web3/auth.py", line 2, in <module>
    import pymysql
ModuleNotFoundError: No module named 'pymysql'

```

### 💻 完整代码

```python

import pymysql

def check(username, pwd):
    conn = pymysql.connect(
        host='127.0.0.1',
        user='root',
        password='',
        database='django'
    )
    cursor = conn.cursor()
    sql = 'select * from userinfo where username=%s and password=%s;'
    res = cursor.execute(sql, [username, pwd])
    if res:
        return True
    else:
        return False

```

---

## 2. wsgi处理web框架.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day17_http协议请求报文响应报文_web升级版_web_wsgi版本_django创建/web3/wsgi处理web框架.py", line 8, in <module>
    from auth import check
  File "/tmp/python3_course/day17_http协议请求报文响应报文_web升级版_web_wsgi版本_django创建/web3/auth.py", line 2, in <module>
    import pymysql
ModuleNotFoundError: No module named 'pymysql'

```

### 💻 完整代码

```python

# ### 升级版web框架
"""
通过地址栏,不同的路由,访问到不同的页面;
"""

from wsgiref.simple_server import make_server
from auth import check
# environ可以取代conn的操作,内部已经封装好了
def html(environ):
	print("html 方法触发 ... ")
	with open("1.index.html" ,mode="rb") as fp:
		data = fp.read()
	return data

def css(environ):
	print("css 方法触发 ... ")
	with open("1.css.html" ,mode="rb") as fp:
		data = fp.read()
	return data

def js(environ):
	print("js 方法触发 ... ")
	with open("1.js.html" ,mode="rb") as fp:
		data = fp.read()
	return data

def login(environ):
	print("login 方法触发 ... ")
	# 获取地址栏参数
	print(environ["QUERY_STRING"]) # a=1&b=3
	# 获取请求方法
	# print(environ["REQUEST_METHOD"]) # GET
	method = environ["REQUEST_METHOD"]
	if method == "GET":
		with open("1.login.html" ,mode="rb") as fp:
			data = fp.read()
		return data
	else:
		# print(environ)
		# 获取表单内容的数据长度;
		length = int(environ.get('CONTENT_LENGTH',0)) # 16
		print(environ.get('CONTENT_LENGTH',0))  # 16
		print(environ["wsgi.input"]) # <_io.BufferedReader name=832>
		# 获取表单中所有数据
		# print(environ["wsgi.input"].read(length)) # b'username=1&pwd=2' # 16个字节
		data = environ["wsgi.input"].read(length).decode("utf-8")
		print(data , type(data))
		# data = environ["wsgi.input"] # 代码暂停再此;
		# print("表单提交的请求数据:",data)
		# return '你是post'.encode("utf-8")

		# parse_qs 将二进制数据解析成字典
		
		from urllib.parse import parse_qs
		data = parse_qs(data)
		print('格式化之后的数据',data)  #格式化之后的数据 {'username': ['aa'], 'password': ['bb']}
		
		# 获取字典中的数据
		uname = data.get('username')[0]
		pwd = data.get('pwd')[0]
		print(uname,pwd)
		""""""
		# 查询数据库中检测账号密码
		status = check(uname,pwd)
		print(status)
		if status:
			data = html(environ)
			return data
		else:
			return '账号密码不对'.encode("utf-8")
		
		return '你是post'.encode("utf-8")
		
def fav(environ):
	print("fav 方法触发 ... ")
	with open("1.fav.html" ,mode="rb") as fp:
		data = fp.read()
	return data

def application(environ,start_response):
	print("server http on port 9001 .... ")
	# 直接获取需要访问页面的路径
	path = environ["PATH_INFO"]
	print(path)

	urlpatterns = [
		("/",html),
		("/css",css),
		("/js",js),
		("/login",login),
		("/favicon.ico",fav)
	]

	for i in urlpatterns:
		if i[0] == path:
			data = i[1](environ)
			break
	else:
		data = b"404 sorry not found"

	# 必须发响应行 + 响应头
	start_response('200 ok',[ ('content-type', 'text/html;charset=UTF-8'),('bbb','112312sa') ] )
	# 响应体
	return [data]

httpd = make_server("127.0.0.1",9001,application)
httpd.serve_forever()

"""

{'ALLUSERSPROFILE': 'C:\\ProgramData', 
'APPDATA': 'C:\\Users\\pc\\AppData\\Roaming', 
'COMMONPROGRAMFILES': 'C:\\Program Files\\Common Files', 'COMMONPROGRAMFILES(X86)': 'C:\\Program Files (x86)\\Common Files', 
'COMMONPROGRAMW6432': 'C:\\Program Files\\Common Files', 'COMPUTERNAME': 'DESKTOP-OT5LRMK', 'COMSPEC': 'C:\\Windows\\system32\\cmd.exe', 
'DRIVERDATA': 'C:\\Windows\\System32\\Drivers\\DriverData', 'HOMEDRIVE': 'C:', 'HOMEPATH': '\\Users\\pc', 'IDEA_INITIAL_DIRECTORY': 'C:\\Users\\pc\\Desktop', 'LOCALAPPDATA': 'C:\\Users\\pc\\AppData\\Local', 'LOGONSERVER': '\\\\DESKTOP-OT5LRMK', 'NUMBER_OF_PROCESSORS': '4', 'ONEDRIVE': 'C:\\Users\\pc\\OneDrive', 'OS': 'Windows_NT', 'PATH': 'C:\\Windows\\system32;C:\\Windows;C:\\Windows\\System32\\Wbem;C:\\Windows\\System32\\WindowsPowerShell\\v1.0\\;C:\\Windows\\System32\\OpenSSH\\;C:\\Program Files (x86)\\Intel\\Intel(R) Management Engine Components\\DAL;C:\\Program Files\\Intel\\Intel(R) Management Engine Components\\DAL;C:\\Program Files (x86)\\NVIDIA Corporation\\PhysX\\Common;D:\\MySQL5.7\\mysql-5.7.25-winx64\\bin;C:\\Users\\pc\\AppData\\Local\\Programs\\Python\\Python36\\Scripts\\;C:\\Users\\pc\\AppData\\Local\\Programs\\Python\\Python36\\;C:\\Users\\pc\\AppData\\Local\\Microsoft\\WindowsApps;;C:\\Users\\pc\\AppData\\Local\\Programs\\Microsoft VS Code\\bin', 'PATHEXT': '.COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.MSC', 'PROCESSOR_ARCHITECTURE': 'AMD64', 'PROCESSOR_IDENTIFIER': 'Intel64 Family 6 Model 158 Stepping 9, GenuineIntel', 'PROCESSOR_LEVEL': '6', 
'PROCESSOR_REVISION': '9e09', 'PROGRAMDATA': 'C:\\ProgramData', 'PROGRAMFILES': 'C:\\Program Files', 'PROGRAMFILES(X86)': 'C:\\Program Files (x86)', 'PROGRAMW6432': 'C:\\Program Files', 'PSMODULEPATH': 'C:\\Program Files\\WindowsPowerShell\\Modules;C:\\Windows\\system32\\WindowsPowerShell\\v1.0\\Modules', 'PUBLIC': 'C:\\Users\\Public', 'PYCHARM_HOSTED': '1', 'PYTHONIOENCODING': 'UTF-8', 'PYTHONPATH': 'C:\\Users\\pc\\PycharmProjects\\pythonProject', 'PYTHONUNBUFFERED': '1', 'SESSIONNAME': 'Console', 'SYSTEMDRIVE': 'C:', 'SYSTEMROOT': 'C:\\Windows', 'TEMP': 'C:\\Users\\pc\\AppData\\Local\\Temp', 'TMP': 'C:\\Users\\pc\\AppData\\Local\\Temp', 'USERDOMAIN': 'DESKTOP-OT5LRMK', 'USERDOMAIN_ROAMINGPROFILE': 'DESKTOP-OT5LRMK', 'USERNAME': 'pc', 'USERPROFILE': 'C:\\Users\\pc', 'WINDIR': 'C:\\Windows', 'SERVER_NAME': 'DESKTOP-OT5LRMK', 'GATEWAY_INTERFACE': 'CGI/1.1', 'SERVER_PORT': '9001', 'REMOTE_HOST': '', 'CONTENT_LENGTH': '20', 'SCRIPT_NAME': '', 'SERVER_PROTOCOL': 'HTTP/1.1', 'SERVER_SOFTWARE': 'WSGIServer/0.2', 'REQUEST_METHOD': 'POST', 'PATH_INFO': '/login', 'QUERY_STRING': '', 'REMOTE_ADDR': '127.0.0.1', 'CONTENT_TYPE': 'application/x-www-form-urlencoded', 'HTTP_HOST': '127.0.0.1:9001', 'HTTP_CONNECTION': 'keep-alive', 'HTTP_CACHE_CONTROL': 'max-age=0', 'HTTP_UPGRADE_INSECURE_REQUESTS': '1', 'HTTP_ORIGIN': 'http://127.0.0.1:9001', 'HTTP_USER_AGENT': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/86.0.4240.198 Safari/537.36', 'HTTP_ACCEPT': 'text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9', 'HTTP_SEC_FETCH_SITE': 'same-origin', 'HTTP_SEC_FETCH_MODE': 'navigate', 'HTTP_SEC_FETCH_USER': '?1', 'HTTP_SEC_FETCH_DEST': 'document', 'HTTP_REFERER': 'http://127.0.0.1:9001/login', 'HTTP_ACCEPT_ENCODING': 'gzip, deflate, br', 'HTTP_ACCEPT_LANGUAGE': 'zh-TW,zh;q=0.9,en-US;q=0.8,en;q=0.7,zh-CN;q=0.6', 'wsgi.input': <_io.BufferedReader name=948>, 'wsgi.errors': <_io.TextIOWrapper name='<stderr>' mode='w' encoding='UTF-8'>, 'wsgi.version': (1, 0), 'wsgi.run_once': False, 'wsgi.url_scheme': 'http', 'wsgi.multithread': True, 'wsgi.multiprocess': False, 'wsgi.file_wrapper': <class 'wsgiref.util.FileWrapper'>}
"""

```

### 📖 要点讲解

- environ可以取代conn的操作,内部已经封装好了

- print(environ["REQUEST_METHOD"]) # GET

- print(environ["wsgi.input"].read(length)) # b'username=1&pwd=2' # 16个字节

- data = environ["wsgi.input"] # 代码暂停再此;

- print("表单提交的请求数据:",data)

- return '你是post'.encode("utf-8")

---

## 3. manage.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day17_http协议请求报文响应报文_web升级版_web_wsgi版本_django创建/web5/manage.py", line 8, in <module>
    from django.core.management import execute_from_command_line
ModuleNotFoundError: No module named 'django'

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/tmp/python3_course/day17_http协议请求报文响应报文_web升级版_web_wsgi版本_django创建/web5/manage.py", line 14, in <module>
    import django
ModuleNotFoundError: No module named 'django'

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/tmp/python3_course/day17_http协议请求报文响应报文_web升级版_web_wsgi版本_django创建/web5/manage.py", line 16, in <module>
    raise ImportError(
ImportError: Couldn't import Django. Are you sure it's installed and available on your PYTHONPATH environment variable? Did you forget to activate a virtual environment?

```

### 💻 完整代码

```python

#!/usr/bin/env python
import os
import sys

if __name__ == "__main__":
    os.environ.setdefault("DJANGO_SETTINGS_MODULE", "web5.settings")
    try:
        from django.core.management import execute_from_command_line
    except ImportError:
        # The above import may fail for some other reason. Ensure that the
        # issue is really that Django is missing to avoid masking other
        # exceptions on Python 2.
        try:
            import django
        except ImportError:
            raise ImportError(
                "Couldn't import Django. Are you sure it's installed and "
                "available on your PYTHONPATH environment variable? Did you "
                "forget to activate a virtual environment?"
            )
        raise
    execute_from_command_line(sys.argv)

```

### 📖 要点讲解

- The above import may fail for some other reason. Ensure that the

- issue is really that Django is missing to avoid masking other

- exceptions on Python 2.

---

## 4. __init__.py

### 💻 完整代码

```python

```

---

## 5. settings.py

### 💻 完整代码

```python

"""
Django settings for web5 project.

Generated by 'django-admin startproject' using Django 1.11.9.

For more information on this file, see
https://docs.djangoproject.com/en/1.11/topics/settings/

For the full list of settings and their values, see
https://docs.djangoproject.com/en/1.11/ref/settings/
"""

import os

# Build paths inside the project like this: os.path.join(BASE_DIR, ...)
BASE_DIR = os.path.dirname(os.path.dirname(os.path.abspath(__file__)))

# Quick-start development settings - unsuitable for production
# See https://docs.djangoproject.com/en/1.11/howto/deployment/checklist/

# SECURITY WARNING: keep the secret key used in production secret!
SECRET_KEY = '*qb1)%arfjyr^jz*abi2ct1@nt9-@zy3bhk^fpnmkam^y1md_w'

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

ROOT_URLCONF = 'web5.urls'

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

WSGI_APPLICATION = 'web5.wsgi.application'

# Database
# https://docs.djangoproject.com/en/1.11/ref/settings/#databases

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': os.path.join(BASE_DIR, 'db.sqlite3'),
    }
}

# Password validation
# https://docs.djangoproject.com/en/1.11/ref/settings/#auth-password-validators

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
# https://docs.djangoproject.com/en/1.11/topics/i18n/

LANGUAGE_CODE = 'en-us'

TIME_ZONE = 'UTC'

USE_I18N = True

USE_L10N = True

USE_TZ = True

# Static files (CSS, JavaScript, Images)
# https://docs.djangoproject.com/en/1.11/howto/static-files/

STATIC_URL = '/static/'

```

### 📖 要点讲解

- Build paths inside the project like this: os.path.join(BASE_DIR, ...)

- Quick-start development settings - unsuitable for production

- See https://docs.djangoproject.com/en/1.11/howto/deployment/checklist/

- SECURITY WARNING: keep the secret key used in production secret!

- SECURITY WARNING: don't run with debug turned on in production!

- Application definition

- https://docs.djangoproject.com/en/1.11/ref/settings/#databases

- https://docs.djangoproject.com/en/1.11/ref/settings/#auth-password-validators

- https://docs.djangoproject.com/en/1.11/topics/i18n/

- Static files (CSS, JavaScript, Images)

- https://docs.djangoproject.com/en/1.11/howto/static-files/

---

## 6. urls.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day17_http协议请求报文响应报文_web升级版_web_wsgi版本_django创建/web5/web5/urls.py", line 16, in <module>
    from django.conf.urls import url
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

"""web5 URL Configuration

The `urlpatterns` list routes URLs to views. For more information please see:
    https://docs.djangoproject.com/en/1.11/topics/http/urls/
Examples:
Function views
    1. Add an import:  from my_app import views
    2. Add a URL to urlpatterns:  url(r'^$', views.home, name='home')
Class-based views
    1. Add an import:  from other_app.views import Home
    2. Add a URL to urlpatterns:  url(r'^$', Home.as_view(), name='home')
Including another URLconf
    1. Import the include() function: from django.conf.urls import url, include
    2. Add a URL to urlpatterns:  url(r'^blog/', include('blog.urls'))
"""
from django.conf.urls import url
from django.contrib import admin

urlpatterns = [
    url(r'^admin/', admin.site.urls),
]

```

---

## 7. wsgi.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day17_http协议请求报文响应报文_web升级版_web_wsgi版本_django创建/web5/web5/wsgi.py", line 12, in <module>
    from django.core.wsgi import get_wsgi_application
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

"""
WSGI config for web5 project.

It exposes the WSGI callable as a module-level variable named ``application``.

For more information on this file, see
https://docs.djangoproject.com/en/1.11/howto/deployment/wsgi/
"""

import os

from django.core.wsgi import get_wsgi_application

os.environ.setdefault("DJANGO_SETTINGS_MODULE", "web5.settings")

application = get_wsgi_application()

```

---

## 8. __init__.py

### 💻 完整代码

```python

```

---

## 9. admin.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day17_http协议请求报文响应报文_web升级版_web_wsgi版本_django创建/web5/app1/admin.py", line 1, in <module>
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

## 10. apps.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day17_http协议请求报文响应报文_web升级版_web_wsgi版本_django创建/web5/app1/apps.py", line 1, in <module>
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

## 11. models.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day17_http协议请求报文响应报文_web升级版_web_wsgi版本_django创建/web5/app1/models.py", line 1, in <module>
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

## 12. tests.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day17_http协议请求报文响应报文_web升级版_web_wsgi版本_django创建/web5/app1/tests.py", line 1, in <module>
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

## 13. views.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day17_http协议请求报文响应报文_web升级版_web_wsgi版本_django创建/web5/app1/views.py", line 1, in <module>
    from django.shortcuts import render
ModuleNotFoundError: No module named 'django'

```

### 💻 完整代码

```python

from django.shortcuts import render

# Create your views here.

```

### 📖 要点讲解

- Create your views here.

---

## 14. __init__.py

### 💻 完整代码

```python

```

---

## 15. manage.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day17_http协议请求报文响应报文_web升级版_web_wsgi版本_django创建/web4/manage.py", line 2, in <module>
    from xiangmu.wsgi import run
  File "/tmp/python3_course/day17_http协议请求报文响应报文_web升级版_web_wsgi版本_django创建/web4/xiangmu/wsgi.py", line 1, in <module>
    from .urls import urlpatterns
  File "/tmp/python3_course/day17_http协议请求报文响应报文_web升级版_web_wsgi版本_django创建/web4/xiangmu/urls.py", line 1, in <module>
    from app import views
  File "/tmp/python3_course/day17_http协议请求报文响应报文_web升级版_web_wsgi版本_django创建/web4/app/views.py", line 2, in <module>
    from app.auth import check
  File "/tmp/python3_course/day17_http协议请求报文响应报文_web升级版_web_wsgi版本_django创建/web4/app/auth.py", line 1, in <module>
    import pymysql
ModuleNotFoundError: No module named 'pymysql'

```

### 💻 完整代码

```python

from app.models import UserInfo
from xiangmu.wsgi import run

# ### sys.argv 执行脚本时,可以动态获取后面的参数
import sys
args = sys.argv
print(args)   #['manage.py', 'migrate']
# print(args[1])

# 执行migrate创建数据表
if args[1] == 'migrate':
   obj = UserInfo()
   obj.create_model()
# 执行runserver启动网站
elif args[1] == 'runserver':
     ip = args[2] # args[2] ip地址
     port = int(args[3]) # args[3] 端口
     print(ip,port)
     # print(type(port))
     run(ip, port)

# python manage.py runserver 127.0.0.1 8001
"""
"""

```

### 📖 要点讲解

- ### sys.argv 执行脚本时,可以动态获取后面的参数

- python manage.py runserver 127.0.0.1 8001

---

## 16. auth.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day17_http协议请求报文响应报文_web升级版_web_wsgi版本_django创建/web4/app/auth.py", line 1, in <module>
    import pymysql
ModuleNotFoundError: No module named 'pymysql'

```

### 💻 完整代码

```python

import pymysql

def check(username, pwd):
    conn = pymysql.connect(
		host='127.0.0.1',
		user='root',
		password='',
		database='django',
		charset='utf8'
    )
    cursor = conn.cursor()
    sql = 'select * from userinfo where username=%s and password=%s;'
    res = cursor.execute(sql, [username, pwd])
    if res:
        return True
    else:
        return False

```

---

## 17. models.py

### 💻 完整代码

```python

class UserInfo:

    def create_model(self):
        import pymysql
        conn = pymysql.connect(
            host='127.0.0.1',
            user='root',
            password='',
            database='django',
            charset='utf8'
        )
		# 创建游标对象是为了对数据库实现增删改查;
        cursor = conn.cursor()

        sql = '''
            create table userinfo(id int primary key auto_increment, username char(10), password char(10));
        '''
		# 执行sql语句
        cursor.execute(sql)
		# 提交数据
        conn.commit()

```

---

## 18. views.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day17_http协议请求报文响应报文_web升级版_web_wsgi版本_django创建/web4/app/views.py", line 2, in <module>
    from app.auth import check
ModuleNotFoundError: No module named 'app'

```

### 💻 完整代码

```python

import time
from app.auth import check
from jinja2 import Template

def home(environ):

	msg = {'name': 'zhangsan', 'hobby': ['吃饭', '睡觉', '打豆豆']}
	# with open('./templates/index.html', 'rb') as f:
	#     data = f.read()
	with open('./templates/index.html', 'r', encoding='utf-8') as f:
		data = f.read()

	# 加载模板
	t = Template(data)
	# 替换数据
	res = t.render(msg)
	# 返回字节流
	return res.encode('utf-8')

def html(environ):
    current_time = str(time.time())

    with open('./templates/home.html', 'r', encoding='utf-8') as f:
        data = f.read()
    data = data.replace('xxoo', current_time).encode('utf-8')
    return data

def css(environ):
    with open('./templates/home.html', 'rb') as f:
        data = f.read()
    return data

def js(environ):
    with open('./templates/home.html', 'rb') as f:
        data = f.read()
    return data

from urllib.parse import parse_qs

def login(environ):
	print(environ)
	# 获取请求的参数
	# print(environ['QUERY_STRING'])  # username=a
	# 获取请求的方法
	method = environ['REQUEST_METHOD']
	if method == 'GET':
		with open('./templates/login.html', 'rb') as f:
			data = f.read()
		return data
	else:
		print(environ)
		content_length = int(environ.get('CONTENT_LENGTH',0))
		# 获取表单post发送的数据
		data = environ['wsgi.input'].read(content_length).decode('utf-8')
		print('请求数据为', data)   #请求数据为 b'username=asdf&password=asdf
		# parse_qs 将二进制数据解析成字典
		data = parse_qs(data)
		print('格式化之后的数据',data)  #格式化之后的数据 {'username': ['aa'], 'password': ['bb']}
		# 获取字典中的数据
		uname = data.get('username')[0]
		pwd = data.get('password')[0]
		print(uname,pwd)
		# 查询数据库中检测账号密码
		status = check(uname,pwd)
		print(status)
		if status:
			data = html(environ)
			return data
		else:
			return '账号密码不对'.encode("utf-8")

```

### 📖 要点讲解

- with open('./templates/index.html', 'rb') as f:

- print(environ['QUERY_STRING'])  # username=a

---

## 19. urls.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day17_http协议请求报文响应报文_web升级版_web_wsgi版本_django创建/web4/xiangmu/urls.py", line 1, in <module>
    from app import views
ModuleNotFoundError: No module named 'app'

```

### 💻 完整代码

```python

from app import views
urlpatterns = [
	("/",views.html),
    ('/home', views.home),
    ('/login', views.login),
    ('/js', views.js),
    ('/css', views.css)
]

```

---

## 20. wsgi.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day17_http协议请求报文响应报文_web升级版_web_wsgi版本_django创建/web4/xiangmu/wsgi.py", line 1, in <module>
    from .urls import urlpatterns
ImportError: attempted relative import with no known parent package

```

### 💻 完整代码

```python

from .urls import urlpatterns
from wsgiref.simple_server import make_server

def run(ip, port):
	def application(environ, start_response):
		print('Serving HTTP on port 8001...')
		path = environ['PATH_INFO']
		for url in urlpatterns:
			if url[0] == path:
				data = url[1](environ)
				print(data,"<111222333>")
				break
		else:
			data =  b'404 page not found'
		start_response( '200 OK', [ ('Content-Type', 'text/html;charset=utf-8'),('a', '1') ]  )
		return [data]

	httpd = make_server(ip, port, application)
	httpd.serve_forever()

```

---

## 21. 1.wsgi基本使用.py

### 📋 运行结果

```

执行超时（可能是交互式程序）

```

### 💻 完整代码

```python

# ### wsgi  (web server gateway interface)
"""
网站整体执行顺序:
    浏览器发送一个http请求
    服务器接收请求,生成html文档
    服务器把文档内容作为http响应体发送给浏览器
    浏览器收到http响应之后,从响应体中获取数据,渲染页面
    
网页服务端包含而部分内容:
    (1) 收发数据的逻辑:
        通过WSGI的收发数据接口(内部使用socket完成的)
        代码以 socket + python为主
    (2) 网站的业务逻辑:
        代码以 前端 + python 为主
        
wsgiref 遵循wsgi接口,是python内置模块
    参数: environ           => 接受http请求信息(请求报文),值是字典dict
    参数: start_response    => 发送http响应信息(响应报文),是函数
"""

from wsgiref.simple_server import make_server
""""""
# 自定义应用函数 
"""响应体无论键或者值必须是字符串"""
def application(environ,start_response):
    print(environ)
    # 获取路径
    print(environ["PATH_INFO"])
    # 获取参数
    print(eviron["QUERY_STRING"])
    data = b'<h1>1234345</h1>'
    # start_response用来发送响应行 + 响应头
    """如果是html,内容类型必须加上,有时可能无法解析,当成字符串执行;"""
    start_response('200 ok',[ ('content-type', 'text/html'),('bbb','112312sa') ] )
    return [data]

# def application(environ, start_response):
    # start_response('200 OK', [('Content-Type', 'text/html')])
    # return [b'<h1>Hello, web!</h1>']
    
# 语法 make_server(ip地址,端口号,执行的应用函数)
httpd = make_server("127.0.0.1",9000,application)
# 开始时时监听http请求
httpd.serve_forever()

"""
{'ALLUSERSPROFILE': 'C:\\ProgramData', 'APPDATA': 'C:\\Users\\pc\\AppData\\Roaming', 'COMMONPROGRAMFILES': 'C:\\Program Files\\Common Files', 'COMMONPROGRAMFILES(X86)': 'C:\\Program Files (x86)\\Common Files', 'COMMONPROGRAMW6432': 'C:\\Program Files\\Common Files', 'COMPUTERNAME': 'DESKTOP-OT5LRMK', 'COMSPEC': 'C:\\Windows\\system32\\cmd.exe', 'DRIVERDATA': 'C:\\Windows\\System32\\Drivers\\DriverData', 'HOMEDRIVE': 'C:', 'HOMEPATH': '\\Users\\pc', 'IDEA_INITIAL_DIRECTORY': 'C:\\Users\\pc\\Desktop', 'LOCALAPPDATA': 'C:\\Users\\pc\\AppData\\Local', 'LOGONSERVER': '\\\\DESKTOP-OT5LRMK', 'NUMBER_OF_PROCESSORS': '4', 'ONEDRIVE': 'C:\\Users\\pc\\OneDrive', 'OS': 'Windows_NT', 'PATH': 'C:\\Windows\\system32;C:\\Windows;C:\\Windows\\System32\\Wbem;C:\\Windows\\System32\\WindowsPowerShell\\v1.0\\;C:\\Windows\\System32\\OpenSSH\\;C:\\Program Files (x86)\\Intel\\Intel(R) Management Engine Components\\DAL;C:\\Program Files\\Intel\\Intel(R) Management Engine Components\\DAL;C:\\Program Files (x86)\\NVIDIA Corporation\\PhysX\\Common;D:\\MySQL5.7\\mysql-5.7.25-winx64\\bin;C:\\Users\\pc\\AppData\\Local\\Programs\\Python\\Python36\\Scripts\\;C:\\Users\\pc\\AppData\\Local\\Programs\\Python\\Python36\\;C:\\Users\\pc\\AppData\\Local\\Microsoft\\WindowsApps;;C:\\Users\\pc\\AppData\\Local\\Programs\\Microsoft VS Code\\bin', 'PATHEXT': '.COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.MSC', 'PROCESSOR_ARCHITECTURE': 'AMD64', 'PROCESSOR_IDENTIFIER': 'Intel64 Family 6 Model 158 Stepping 9, GenuineIntel', 'PROCESSOR_LEVEL': '6', 'PROCESSOR_REVISION': '9e09', 'PROGRAMDATA': 'C:\\ProgramData', 'PROGRAMFILES': 'C:\\Program Files', 'PROGRAMFILES(X86)': 'C:\\Program Files (x86)', 'PROGRAMW6432': 'C:\\Program Files', 'PSMODULEPATH': 'C:\\Program Files\\WindowsPowerShell\\Modules;C:\\Windows\\system32\\WindowsPowerShell\\v1.0\\Modules', 'PUBLIC': 'C:\\Users\\Public', 'PYCHARM_HOSTED': '1', 'PYTHONIOENCODING': 'UTF-8', 'PYTHONPATH': 'C:\\Users\\pc\\PycharmProjects\\pythonProject', 'PYTHONUNBUFFERED': '1', 'SESSIONNAME': 'Console', 'SYSTEMDRIVE': 'C:', 'SYSTEMROOT': 'C:\\Windows', 'TEMP': 'C:\\Users\\pc\\AppData\\Local\\Temp', 'TMP': 'C:\\Users\\pc\\AppData\\Local\\Temp', 'USERDOMAIN': 'DESKTOP-OT5LRMK', 'USERDOMAIN_ROAMINGPROFILE': 'DESKTOP-OT5LRMK', 'USERNAME': 'pc', 'USERPROFILE': 'C:\\Users\\pc', 'WINDIR': 'C:\\Windows', 'SERVER_NAME': 'DESKTOP-OT5LRMK', 'GATEWAY_INTERFACE': 'CGI/1.1', 'SERVER_PORT': '9000', 'REMOTE_HOST': '', 'CONTENT_LENGTH': '', 'SCRIPT_NAME': '', 'SERVER_PROTOCOL': 'HTTP/1.1', 'SERVER_SOFTWARE': 'WSGIServer/0.2', 'REQUEST_METHOD': 'GET', 'PATH_INFO': '/', 'QUERY_STRING': '', 'REMOTE_ADDR': '127.0.0.1', 'CONTENT_TYPE': 'text/plain', 'HTTP_HOST': '127.0.0.1:9000', 'HTTP_CONNECTION': 'keep-alive', 'HTTP_CACHE_CONTROL': 'max-age=0', 'HTTP_UPGRADE_INSECURE_REQUESTS': '1', 'HTTP_USER_AGENT': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/86.0.4240.198 Safari/537.36', 'HTTP_ACCEPT': 'text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9', 'HTTP_SEC_FETCH_SITE': 'none', 'HTTP_SEC_FETCH_MODE': 'navigate', 'HTTP_SEC_FETCH_USER': '?1', 'HTTP_SEC_FETCH_DEST': 'document', 'HTTP_ACCEPT_ENCODING': 'gzip, deflate, br', 'HTTP_ACCEPT_LANGUAGE': 'zh-TW,zh;q=0.9,en-US;q=0.8,en;q=0.7,zh-CN;q=0.6', 'wsgi.input': <_io.BufferedReader name=828>, 'wsgi.errors': <_io.TextIOWrapper name='<stderr>' mode='w' encoding='UTF-8'>, 'wsgi.version': (1, 0), 'wsgi.run_once': False, 'wsgi.url_scheme': 'http', 'wsgi.multithread': True, 'wsgi.multiprocess': False, 'wsgi.file_wrapper': <class 'wsgiref.util.FileWrapper'>}

{'ALLUSERSPROFILE': 'C:\\ProgramData', 'APPDATA': 'C:\\Users\\pc\\AppData\\Roaming', 'COMMONPROGRAMFILES': 'C:\\Program Files\\Common Files', 'COMMONPROGRAMFILES(X86)': 'C:\\Program Files (x86)\\Common Files', 'COMMONPROGRAMW6432': 'C:\\Program Files\\Common Files', 'COMPUTERNAME': 'DESKTOP-OT5LRMK', 'COMSPEC': 'C:\\Windows\\system32\\cmd.exe', 'DRIVERDATA': 'C:\\Windows\\System32\\Drivers\\DriverData', 'HOMEDRIVE': 'C:', 'HOMEPATH': '\\Users\\pc', 'IDEA_INITIAL_DIRECTORY': 'C:\\Users\\pc\\Desktop', 'LOCALAPPDATA': 'C:\\Users\\pc\\AppData\\Local', 'LOGONSERVER': '\\\\DESKTOP-OT5LRMK', 'NUMBER_OF_PROCESSORS': '4', 'ONEDRIVE': 'C:\\Users\\pc\\OneDrive', 'OS': 'Windows_NT', 'PATH': 'C:\\Windows\\system32;C:\\Windows;C:\\Windows\\System32\\Wbem;C:\\Windows\\System32\\WindowsPowerShell\\v1.0\\;C:\\Windows\\System32\\OpenSSH\\;C:\\Program Files (x86)\\Intel\\Intel(R) Management Engine Components\\DAL;C:\\Program Files\\Intel\\Intel(R) Management Engine Components\\DAL;C:\\Program Files (x86)\\NVIDIA Corporation\\PhysX\\Common;D:\\MySQL5.7\\mysql-5.7.25-winx64\\bin;C:\\Users\\pc\\AppData\\Local\\Programs\\Python\\Python36\\Scripts\\;C:\\Users\\pc\\AppData\\Local\\Programs\\Python\\Python36\\;C:\\Users\\pc\\AppData\\Local\\Microsoft\\WindowsApps;;C:\\Users\\pc\\AppData\\Local\\Programs\\Microsoft VS Code\\bin', 'PATHEXT': '.COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.MSC', 'PROCESSOR_ARCHITECTURE': 'AMD64', 'PROCESSOR_IDENTIFIER': 'Intel64 Family 6 Model 158 Stepping 9, GenuineIntel', 'PROCESSOR_LEVEL': '6', 'PROCESSOR_REVISION': '9e09', 'PROGRAMDATA': 'C:\\ProgramData', 'PROGRAMFILES': 'C:\\Program Files', 'PROGRAMFILES(X86)': 'C:\\Program Files (x86)', 'PROGRAMW6432': 'C:\\Program Files', 'PSMODULEPATH': 'C:\\Program Files\\WindowsPowerShell\\Modules;C:\\Windows\\system32\\WindowsPowerShell\\v1.0\\Modules', 'PUBLIC': 'C:\\Users\\Public', 'PYCHARM_HOSTED': '1', 'PYTHONIOENCODING': 'UTF-8', 'PYTHONPATH': 'C:\\Users\\pc\\PycharmProjects\\pythonProject', 'PYTHONUNBUFFERED': '1', 'SESSIONNAME': 'Console', 'SYSTEMDRIVE': 'C:', 'SYSTEMROOT': 'C:\\Windows', 'TEMP': 'C:\\Users\\pc\\AppData\\Local\\Temp', 'TMP': 'C:\\Users\\pc\\AppData\\Local\\Temp', 'USERDOMAIN': 'DESKTOP-OT5LRMK', 'USERDOMAIN_ROAMINGPROFILE': 'DESKTOP-OT5LRMK', 'USERNAME': 'pc', 'USERPROFILE': 'C:\\Users\\pc', 'WINDIR': 'C:\\Windows', 'SERVER_NAME': 'DESKTOP-OT5LRMK', 'GATEWAY_INTERFACE': 'CGI/1.1', 'SERVER_PORT': '9000', 'REMOTE_HOST': '', 'CONTENT_LENGTH': '', 'SCRIPT_NAME': '', 'SERVER_PROTOCOL': 'HTTP/1.1', 'SERVER_SOFTWARE': 'WSGIServer/0.2', 'REQUEST_METHOD': 'GET', 'PATH_INFO': '/abcdefg', 'QUERY_STRING': 'a=1&b=2', 'REMOTE_ADDR': '127.0.0.1', 'CONTENT_TYPE': 'text/plain', 'HTTP_HOST': '127.0.0.1:9000', 'HTTP_CONNECTION': 'keep-alive', 'HTTP_CACHE_CONTROL': 'max-age=0', 'HTTP_UPGRADE_INSECURE_REQUESTS': '1', 'HTTP_USER_AGENT': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/86.0.4240.198 Safari/537.36', 'HTTP_ACCEPT': 'text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9', 'HTTP_SEC_FETCH_SITE': 'none', 'HTTP_SEC_FETCH_MODE': 'navigate', 'HTTP_SEC_FETCH_USER': '?1', 'HTTP_SEC_FETCH_DEST': 'document', 'HTTP_ACCEPT_ENCODING': 'gzip, deflate, br', 'HTTP_ACCEPT_LANGUAGE': 'zh-TW,zh;q=0.9,en-US;q=0.8,en;q=0.7,zh-CN;q=0.6', 'wsgi.input': <_io.BufferedReader name=844>, 'wsgi.errors': <_io.TextIOWrapper name='<stderr>' mode='w' encoding='UTF-8'>, 'wsgi.version': (1, 0), 'wsgi.run_once': False, 'wsgi.url_scheme': 'http', 'wsgi.multithread': True, 'wsgi.multiprocess': False, 'wsgi.file_wrapper': <class 'wsgiref.util.FileWrapper'>}
/abcdefg

"""

```

### 📖 要点讲解

- ### wsgi  (web server gateway interface)

- start_response用来发送响应行 + 响应头

- def application(environ, start_response):

- start_response('200 OK', [('Content-Type', 'text/html')])

- return [b'<h1>Hello, web!</h1>']

- 语法 make_server(ip地址,端口号,执行的应用函数)

---

## 22. 1.基础班web框架.py

### 📋 运行结果

```

执行超时（可能是交互式程序）

```

### 💻 完整代码

```python

"""
软件: b/s 浏览器/服务端  c/s 客户端/服务端
网络世界书局传输遵循osi网络七层模型 : 应表会 -> 应用层 传网数物
在这个模型中的每一层都有各式各样的不同的规则,也叫做协议

比如: http    是应用层协议,规范书局要按照什么样的格式封装
      tcp/udp 是传输层协议,规范什么样的方式进行书局传输
      ip      是网络层协议,规范以什么样的版本寻址
http : 超文本传输协议,基于tcp/ip协议簇
       http协议特点属于一个无状态的短链接,请求与响应必须成对;
       
在浏览器和服务器之间,通过地址栏
利用socket这个工具进行收发数据.互相传输数据报文(请求报文,响应报文)

wsgi
"""

# ###1.基础班web框架
import socket
sk = socket.socket()
sk.bind( ("127.0.0.1",8000) )
sk.listen()

while True:
    conn , addr = sk.accept()
    # 1.服务端接受浏览器的请求报文数据
    from_brower_msg = conn.recv(1024)
    print(from_brower_msg)
    
    # 2.服务端向客户端发送响应的报文数据
    # (1).发送 响应行
    # conn.send(b'HTTP/1.1 200 okk\r\n\r\n\r\n')
    # conn.send(b'HTTP/1.1 200 okk\n\n\n')
    
    # (2) 响应行 + 响应头
    # conn.send(b'HTTP/1.1 200 okk\r\na:1\r\n\r\n')
    # conn.send(b'HTTP/1.1 200 okk\r\na:1\r\nb:2\r\n\r\n')
    
    # (3) 响应行 + 响应头 + 响应体
    # 响应行+响应头 (如果没有响应头,直接空格即可)
    conn.send(b'HTTP/1.1 200 okk\r\na:1')
    # 换行
    conn.send(b'\r\n\r\n')
    # 响应体
    with open("1.index.html","rb") as fp:
        data = fp.read()
    conn.send(data)
    conn.close()
sk.close()

"""
b'GET / HTTP/1.1\r\nHost: 127.0.0.1:8000\r\nConnection: keep-alive\r\nUpgrade-Insecure-Requests: 1\r\nUser-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/86.0.4240.198 Safari/537.36\r\nAccept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9\r\nSec-Fetch-Site: none\r\nSec-Fetch-Mode: navigate\r\nSec-Fetch-User: ?1\r\nSec-Fetch-Dest: document\r\nAccept-Encoding: gzip, deflate, br\r\nAccept-Language: zh-TW,zh;q=0.9,en-US;q=0.8,en;q=0.7,zh-CN;q=0.6\r\n\r\n'
"""

```

### 📖 要点讲解

- conn.send(b'HTTP/1.1 200 okk\r\n\r\n\r\n')

- conn.send(b'HTTP/1.1 200 okk\n\n\n')

- conn.send(b'HTTP/1.1 200 okk\r\na:1\r\n\r\n')

- conn.send(b'HTTP/1.1 200 okk\r\na:1\r\nb:2\r\n\r\n')

- 响应行+响应头 (如果没有响应头,直接空格即可)

---

## 23. 2.升级版web框架.py

### 📋 运行结果

```

执行超时（可能是交互式程序）

```

### 💻 完整代码

```python

# ### 升级版web框架
"""
通过地址栏,不同的路由,访问到不同的页面;
"""
import socket

sk= socket.socket()
sk.bind( ("127.0.0.1",8001) )
sk.listen()

def html(conn):
    print("html 方法触发 ... ")
    with open("1.index.html" ,mode="rb") as fp:
        data = fp.read()
    conn.send(data)
    conn.close()
def css(conn):
    print("css 方法触发 ... ")
    with open("1.css.html" ,mode="rb") as fp:
        data = fp.read()
    conn.send(data)
    conn.close()

def js(conn):
    print("js 方法触发 ... ")
    with open("1.js.html" ,mode="rb") as fp:
        data = fp.read()
    conn.send(data)
    conn.close()

def login(conn):
    print("login 方法触发 ... ")
    with open("1.login.html" ,mode="rb") as fp:
        data = fp.read()
    conn.send(data)
    conn.close()
def fav(conn):
    print("fav 方法触发 ... ")
    with open("1.fav.html" ,mode="rb") as fp:
        data = fp.read()
    conn.send(data)
    conn.close()

# 匹配路由地址(url地址)
urlpatterns = [
    ("/",html),
    ("/css",css),
    ("/js",js),
    ("/login",login),
    ("/favicon.ico",fav)
]

while True:
    conn,addr = sk.accept()
    from_browser_msg = conn.recv(1024)
    print(from_browser_msg,"1")
    # 把字节流通过decode 反解成字符串
    res = from_browser_msg.decode("utf-8")
    print(res , type(res),"2")
    path = res.split(" ")[1]
    print(path,"3") #\abc
    
    # 发送响应行
    conn.send(b'HTTP/1.1 200 ok\r\n \r\n\r\n')
    # 找对应的访问路径
    for i in urlpatterns:
        if i[0] == path:
            # 加载对应路径中的页面
            i[1](conn)

sk.close()
    
```

---

## 🖼️ 参考资料

![1605978413403.png](./assets/1605978413403.png)

![1605978451639.png](./assets/1605978451639.png)

![1605978501496.png](./assets/1605978501496.png)

![1605978681691.png](./assets/1605978681691.png)

![1605978818346.png](./assets/1605978818346.png)

![1606002323671.png](./assets/1606002323671.png)

![1606014445427.png](./assets/1606014445427.png)

![2.jpg](./assets/2.jpg)
