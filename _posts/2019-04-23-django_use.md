---
layout: post
title: Django使用
---

## Windows

### 创建虚拟环境（单独的一个虚拟环境，便于管理django所依赖的python库）（python3.6, django2.0， ）

    python -m venv C:\python-django

### 激活虚拟环境

    C:\python-django\Scripts\activate
    (python-django) C:\Users\Liuwt>

### 目录结构

    templates目录：存放html文件
    manage.py：django项目管理文件
    settings.py：主配置文件
    urls.py：URL路由文件
    wsgi.py：网络通讯接口文件

### 生成APP
每个django项目中可以包含多个APP，相当于一个大型项目中的分系统、子模块、功能部件等，相互之间比较独立，各APP共享项目资源。

    python manage.py startapp aaa

### urls.py
路由都在urls文件里，将浏览器输入的url映射到相应的业务处理逻辑。urls编写方法和业务处理逻辑都在对应APP的views.py文件里：  

urls.py: 

    from aaa import views
    path("index/", views.index),

views.py:

    from django.shortcuts import HttpResponse
    def index(request):                      # request封装了用户请求的所有内容
        return HttpResponse("Htllo, world")  # 不能直接返回字符串，必须由这个类封装起来

### urls相关问题集

    1. urls匹配正则时要用re_path
    2. 将根目录的urls重定位到app的urls，path("HMS/", include('HMS.urls'))，然后将路由匹配写到app的urls.py中即可
  
### 将web服务运行起来

    python manage.py runserver 127.0.0.1:8000

### 返回html文件
在相应APP的templates下创建要返回的html文件，在views中返回：    

    return render(request, "html文件",)   

用render方法来渲染（打包），render是django提供的方法和规则，request为固定参数。
  
    return render(request, "html文件", {"data":user_list})  

render第三个参数是后台返回给浏览器的数据，data是自定义的指针名字，会被对应的html文件引用。

### 静态资源文件
新建一个static目录，将前端的静态文件放到这个目录中，为了让django找到目录，需要对settings.py进行配置：

    STATIC_URL = '/static/' 

这个指的是引用指针，不是具体的目录，可以改成想要的任何名字，但是在html文件中必须和它对应。

添加固定的全局变量名：

    STATICFILES_DIRS = (os.path.join(BASE_DIR, 'static'),)  

'static'与静态文件目录的名字对应，和html的引用无关。  

### django跨站保护机制  
伪装来自受信任用户的请求来利用受信任的网站完成攻击。当直接写一个form表单提交数据时会被误认为是跨站请求。  
直接注释掉settings MIDDLEWARE中的django.middleware.csrf.CsrfViewMiddleware
  
### 注册APP
在settings中的INSTALLED_APPS中添加APP的名字。

### 数据库创建字段
models.py中添加字段名

### 创建数据库的表

    python manage.py makemigrations
    python manage.py migrate

### 更改sqlite为mysql

    pip install pymysql

    __init__.py:

    import pymysql
    pymysql.install_as_MySQLdb()

### pycharm指定django版本
建项目时勾选Inherit global site-packages，则项目默认应用系统内的django版本。  
或者File——Setting——project:项目名———project interpreter——双击django——勾选Specify——选择版本。

### pycharm中自带数据库
右边Database中新建直连mysql，然后就可以直接在pycharm界面中操作数据库啦！

### 生成requirements.txt

    pip freeze > requirements.txt  

### 安装requirements.txt  

    pip install -r requirements.txt

### 使用Vue，前后端分离

    使用vue.js进行前端渲染，就放弃了Django内置的模型引擎；  
    Django继续负责对Model的管理和操作；  
    Django的view，将负责返回vue的入口文件，成为api-view，返回JSON响应；  
    Django的urls.py将负责后端路由，指向vue入口文件和api；  
    vue负责前端试图逻辑，以及前端路由；