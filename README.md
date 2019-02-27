# 搭建开发环境
开发环境：
~~~
windows 10（64位）
Python版本 3.7.2（64位）
Django版本 1.10.6
~~~
建议尽可能与开发环境保持一致，避免一些不必要的麻烦。推荐Python版本为3.4或以上，Django版本号必须为1.10.x。
&nbsp;     

## 一、安装python

Windows 下安装 Python 非常简单，去 Python 官方网站找到 Python 3 的下载地址，根据你的系统选择 32 位或者 64 位的安装包，下载好后双击安装即可。

安装完后检测 Python 是否可以正常运行。在命令行输入 python -v ，如果输出了 Python 的版本号，说明 Python 已安装成功。
~~~
C:\Users\qianqi>python -V
Python 3.7.2
~~~
如果提示命令未找到，而你又确定已经安装了 Python，多半是因为没有把 Python 添加到环境变量。可搜索如何把 Python 添加到环境变量的相关教程，将安装的Python 添加到环境变量即可。

 
## 二、使用虚拟环境 Virtualenv

强烈推荐在 Virtualenv 下进行 Django 的开发。Virtualenv 是一个 Python 工具，使用它可以创建一个独立的 Python 环境。

为什么要使用 Virtualenv 呢？举个例子，假设你已经在系统中安装了 Python，并且在阅读此教程前你已经进行过一些 Django 的学习，但那时候安装的 Django 还是 1.8 版本。我们教程使用的是最新版的 Django 1.10.6 版本，你可能不愿意删除掉旧版的 Django 1.8，因为那可能导致你以前的项目无法运行。既想让原本项目在 Django 1.8 环境下运行，又想再安装 Django 1.10.6 来开启本教程的项目，怎么办呢？使用 Virtualenv 就能够完美解决这个问题。

Virtualenv 帮我们从系统的 Python 环境中克隆一个全新的 Python 环境出来，这个环境独立于原来的 Python 环境。我们可以在这个新克隆的环境下安装 Django 1.10.6，并且在这个新环境下运行我们的新项目。

Virtualenv 的使用非常简单，首先安装 Virtualenv，打开命令行工具，输入 pip install virtualenv 命令即可安装 Virtualenv。
~~~
C:\Users\qianqi>pip install virtualenv
~~~
安装成功后就可以开始创建虚拟环境，指定一个你喜欢的目录，Virtualenv 会把这个新的虚拟环境装到你指定目录下。例如我把它装到 D:\qianq\ 目录下，并将虚拟环境命名为 blogproject_env（也可以取任何你喜欢的名字）。在命令栏运行如下命令：
~~~
C:\Users\qianqi>virtualenv D:\qianq\blogproject_env
~~~
虚拟环境已经创建好了，我们需要激活这个环境，运行 blogproject_env\Scripts\ 目录下的 activate 程序激活它：
~~~
C:\Users\qianqi>D:\qianq\blogproject_env\Scripts\activate
(blogproject_env) C:\Users\qianqi>
~~~

## 三、安装Django

Django 的官方文档对 如何安装 Django 给出了详细且明确的指导，不过我们目前用不上这些，只需使用 pip 命令就可以解决问题。
~~~
(blogproject_env) C:\Users\qianqi>pip install django==1.10.6
~~~
我们用 django==1.10.6 来安装指定的 Django 版本以保证和教程中的一致。如果直接 pip install django 的话有可能安装最新的 Django 发行版本，而不是 Django 1.10.6。

注意命名提示符前的 (blogproject_env) 以确保你始终处在虚拟环境中，如果不小心退出了虚拟环境，先按上面的步骤重新进入再安装 Django。

测试一下安装是否成功，先在命令行输入 python 以打开 Python 自带的命令栏，然后输入 import django，如果没有报错就说明 Django 安装成功。通过运行 print(django.get_version()) 打印出 Django 的版本号，确保安装了正确版本的 Django。
~~~
(blogproject_env) C:\Users\qianqi>python
Python 3.7.2 (tags/v3.7.2:9a3ffc0492, Dec 23 2018, 23:09:28) [MSC v.1916 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> import django
>>> print(django.get_version())
1.10.6
>>>
~~~

## 四、运行项目

首先根据上述步骤激活虚拟环境，运行 D:\qianq\blogproject_env\Scripts\activate 激活它：
~~~
C:\Users\qianqi>D:\qianq\blogproject_env\Scripts\activate
(blogproject_env) C:\Users\qianqi>
~~~
注意：虚拟环境激活成功的标志就是前面带有(blogproject_env)

然后进入博客项目manage.py所在目录，运行manage.py文件：
~~~
(blogproject_env) C:\Users\qianqi>d:
(blogproject_env) D:\>cd D:\Pycharm-workSpace\blogproject\Django-Blog
(blogproject_env) D:\Pycharm-workSpace\blogproject\Django-Blog>
(blogproject_env) D:\Pycharm-workSpace\blogproject\Django-Blog>python manage.py runserver
Performing system checks...

System check identified no issues (0 silenced).
February 27, 2019 - 15:17:03
Django version 1.10.6, using settings 'blogproject.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CTRL-BREAK.
~~~

最后在网页上输入 http://127.0.0.1:8000/ 就可以看到本项目了！