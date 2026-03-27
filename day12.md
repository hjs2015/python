# Day 12: day12 ceshi1 认识html 常用标签 锚点图片表格 table属性音视频标签 自定义flask的路由展现表单 INPUT span div列表超链接a 表格 表格表单

> 对应原课程：day12_ceshi1_认识html_常用标签_锚点图片表格_table属性音视频标签_自定义flask的路由展现表单_INPUT_span_div列表超链接a_表格_表格表单

---

## 1. app.py

### 📋 运行结果

```

错误：Traceback (most recent call last):
  File "/tmp/python3_course/day12_ceshi1_认识html_常用标签_锚点图片表格_table属性音视频标签_自定义flask的路由展现表单_INPUT_span_div列表超链接a_表格_表格表单/代码/表单操作/app.py", line 1, in <module>
    from flask import Flask , render_template , request , redirect
ModuleNotFoundError: No module named 'flask'

```

### 💻 完整代码

```python

from flask import Flask , render_template , request , redirect
"""安装flask  pip3 install flask"""
print(__name__)

# (1) 实例化一个flask的应用对象
app = Flask(__name__)

# (2) 定义路由(url)
""" The return type must be a string, dict, tuple"""
@app.route("/")
def index():
	return "<h1 style='color:red'>服务器运转正常~ flask已经启动~</h1>"
	# return 1233 error

@app.route('/ceshi1')
def func():
	# 获取访问的方法(get , post)
	print(request.method  ,  "<====================>") # GET
	strvar = """
<!DOCTYPE HTML>
<html>

<head>
	<meta charset="utf-8" />
</head>

<body>

	<!-- 
	action 表示吧数据提交给哪个地址进行处理
	method 表示数据以哪种方式进行提交
		get  显示提交数据(参数在地址栏上,参数大小2k~8k左右)
		post 隐式提交数据(参数不在地址上,参数大小没有限制)
		
	input 行内块状元素
	-->
	<form action="" method="get">
		账号:<input type="text" name="username" value="" />
		<br />
		密码:<input type="password" name="username" value="" />
		<br />
		<input type="submit" value="登录" style="color:red;background-color:yellow;" />
	</form>

</body>

</html>

	# return strvar
	"""
	
	"""
	# render_template 操作过程;  文件夹的名称必须是templates
	with open("./templates/1.form表单.html" mode="rb") as fp:
		res = fp.read()
	return res.decode()
	"""
	return render_template("1.form表单.html")
	
	# return strvar

# get方法提交到 http://127.0.0.1:9008/ceshi2 地址 (路由默认以GET方法接收数据)
@app.route('/ceshi2',methods=("GET",))
def func2():
	"""	"""
	if request.method == "GET":
		return "ok,就是我 GET"
	
# post方法提交到 http://127.0.0.1:9008/ceshi2 地址	
@app.route('/ceshi2',methods=("POST",))
def func3():
	if request.method == "POST":
	
		# to_dict 把响应的数据转换成字典
		dic = request.values.to_dict()
		return dic

		# return "ok,就是我 post"

@app.route('/ceshi3',methods=("GET",))
def func4():
	if request.method == "GET":
		return render_template("2.单选框_复选框_下拉框.html")
		
@app.route('/ceshi4',methods=("POST",))
def func5():
	if request.method == "POST":
		# 获取表单对应的数据,通过to_dict转化成字典,但无法获取到复选框的所有内容
		# return request.values.to_dict()
		# 获取复选框时,使用getlist方法,但是返回时需要字典,借助enumerate间接变成字典
		# print(request.values.getlist("hobby"))
		return dict(  enumerate(request.values.getlist("hobby"))  )

@app.route('/ceshi5',methods=("POST","GET"))
def func6():
	if request.method == "GET":
		return render_template("3.文件上传.html")
		
	if request.method == "POST":
		# 获取上传图片的数据信息
		tupian_obj = request.files.get("myfiles")
		# 获取上传文件的名字
		print(tupian_obj.filename)
		# 保存上传的数据
		tupian_obj.save(  tupian_obj.filename  ) # 按照这个名字保存数据
		print(request.values.to_dict)
		# return request.values.to_dict()
		
		strvar = """
		恭喜你上传成功,3秒后自动跳转到百度!!!
		<meta http-equiv="refresh" content="0;url=http://www.baidu.com" />		
		"""
		# return strvar
		
		# redirect 重定向
		# return redirect("http://www.baidu.com")
		# return redirect("/ceshi2")
		
# (3) 启动服务
app.run(host="127.0.0.1" ,port=9008,debug=True)

```

### 📖 要点讲解

- render_template 操作过程;  文件夹的名称必须是templates

- get方法提交到 http://127.0.0.1:9008/ceshi2 地址 (路由默认以GET方法接收数据)

- post方法提交到 http://127.0.0.1:9008/ceshi2 地址

- 获取表单对应的数据,通过to_dict转化成字典,但无法获取到复选框的所有内容

- return request.values.to_dict()

- 获取复选框时,使用getlist方法,但是返回时需要字典,借助enumerate间接变成字典

- print(request.values.getlist("hobby"))

- return request.values.to_dict()

- return redirect("http://www.baidu.com")

- return redirect("/ceshi2")

---

## 🖼️ 参考资料

![b_s.png](./assets/b_s.png)

![zhouxingchi.jpg](./assets/zhouxingchi.jpg)

![表格.png](./assets/表格.png)

![页面结构-1577532950523.png](./assets/页面结构-1577532950523.png)

![页面结构.png](./assets/页面结构.png)

![作业1.png](./assets/作业1.png)

![作业2.png](./assets/作业2.png)
