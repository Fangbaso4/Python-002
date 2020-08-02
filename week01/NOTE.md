# 学习笔记

---

## 预习周

**why python** 

### python 特点

- 学习曲线平缓
- 高级编程语言，更接近人的思考过程
- 既支持面向过程又支持面向对象
- 第三方模块多
- 支持跨平台
- python应用领域广泛

### 体系化学习python

#### 1. 学会搜索

- google
- stack overflow
- GitHub 搜索帮助：
  - in:readme python
  - https://docs.github.com/en/github/searching-for-information-on-github

- 《提问的智慧》：[ https://github.com/ryanhanwu/How-To-Ask-Questions-The-Smart-Way/blob/master/README-zh_CN.md](https://github.com/ryanhanwu/How-To-Ask-Questions-The-Smart-Way/blob/master/README-zh_CN.md)

- Python 3.7.7 官方文档：[ https://docs.python.org/zh-cn/3.7/](https://docs.python.org/zh-cn/3.7/)

#### 2. 风格指引：

- PEP8：[ https://www.python.org/dev/peps/pep-0008/](https://www.python.org/dev/peps/pep-0008/) 

- Google Python Style Guides：[ http://google.github.io/styleguide/pyguide.html](http://google.github.io/styleguide/pyguide.html)

### 环境变量配置

#### python安装

- Python 安装包下载地址 https://www.python.org/downloads/

- 安装方法 https://docs.python.org/zh-cn/3.7/using/windows.html

- 查看版本： `python -V`

- 查找python 命令具体所在的位置： `which python` windows下使用`where python`

- 找到不同python 版本的位置，加入系统环境变量：

  `echo $PATH` 在打印出的路径前面添加其他版本的python路径，然后赋值给PATH

  即`export PATH=/新python 版本路径:$PATH`

  再次执行python时，会默认使用前面的版本。

  长期进行保存可写在系统环境配置文件中：/etc/bashrc

  如果是非管理员权限，使用 ` sudo vim /etc/bashrc ` 进行编辑。修改配置文件后，重启依然生效。

  

### 第三方库的安装

pip 命令，`pip -V`查看版本，如果是python2 的直接使用pip ,如果是pyton3 使用pip3 命令。

`python -m pip install --upgrade pip` 升级pip版本

`pip3 install requests` 提示success 即为安装成功

在python 中执行 `import requests`未报错，进一步验证安装成功。 

#### 配置pip源

**常用 pip 源地址**

- 豆瓣：[ https://pypi.doubanio.com/simple/](https://pypi.doubanio.com/simple/)
- 清华：[ https://mirrors.tuna.tsinghua.edu.cn/help/pypi/](https://mirrors.tuna.tsinghua.edu.cn/help/pypi/)
- 中科大：[ https://pypi.mirrors.ustc.edu.cn/simple/](https://pypi.mirrors.ustc.edu.cn/simple/)
- 阿里云：[ https://mirrors.aliyun.com/pypi/simple/](https://mirrors.aliyun.com/pypi/simple/)

**临时替换**

`pip install -i https://pypi.tuna.tsinghua.edu.cn/simple 要安装的包名`

**永久替换**

`pip install pip -U`

`pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple`

**freeze**

python 环境迁移，不用一个个再重新安装第三方软件包

A环境生成环境文件：

`pip3 freeze > requirements.txt`

B环境导入：

`pip3 install -r requirements.txt`

### 配置venv虚拟环境

在你指定的路径下执行`python3 -m venv venv1`就创建了名为venv1的虚拟环境。

进入虚拟环境：`source venv1/bin/activate` windows 使用：`venv1\Scripts\activate.bat`

各个虚拟环境之前是独立的，方便进行开发、尝试。

### IDE(集成开发环境)

linux vi 

win/mac ：VS code 、Pycharm

提示安装pylint

Python-autopep8 语法规范检测

左下角显示当前使用的python版本，点击可进行切换。

### 基础语法概览

终端交互模式，直接输入变量名回车可获得变量值。（ctrl+l 可清空终端展示内容

- 使用help(xxx) 查询使用方法
- type(XXX) 得到变量的类型
- dir() 查看当前环境中有哪些变量已经被使用

#### 数据类型

##### 数值类型：

**整数**：1、-6、6666 整数无大小限制，受限于内存

**浮点数**: 1.3

**复数**: 1+3j 2.3+4.5j

**布尔值**:True  False

**数值运算**: `+ - * /  //整数除法 %求模 **求幂`

**支持数学函数**，math库：

##### 字符串 string:

可以使用不同的引号引起来，在python 中使用不同的引号引起来是没有差别的。

字符串中包含单引号时，使用双引号或者三引号。

##### 列表 list

- 类似C语言中的数组。
- 但python列表中可以包含字符串、数字等基本的数据类型，且支持对列表的内置函数（`len max min`），也支持对列表本身的方法（`append count extend index insert pop remove reverse sort`）

- 列表可通过下标进行访问`x[1]`，也可以逆向访问`x[-1]` 

##### 元组 tuple

- 元组与列表类似，一旦创建不可修改
- 支持操作符、内置函数
- 本身方法只能支持两个 `count index` 
- 列表和元组很类似，但列表无法替代元组，比如哈希算法中的 key，需要使用不可变的类型。

##### 字典 dict

- 字典本质是 key 和 value 组成的哈希表
- key 只能是数值、字符串、元组 （哈希表的key 不可变）
- 本身方法支持`copy get  items keys values update`

##### 集合 set

- 由基本对象组合的无序集，具有唯一性

- 可以使用集合的唯一性，对列表进行去重

  ```python
  set1=set([1,2,3,4,3,2,1])
  print(set)
  ```

#### 流程控制：

##### **流程控制中的真值、假值：**

**假值**： False  0  零值None  空（列表、字典、字符串） 

**真值：** 其他值  

##### if

```python
#代码块与缩进 使用缩进来区分语句块
x = 1
if x < 10:
    y = 1
elif x > 10:
    y = 2
else:
    y = 3
	z = 4
```

##### while

```python
#支持 break continue
x = 2
y = 1
while x > y:
    pass
```

##### for

```python
#支持break continue
#for in 类型 一种迭代的形式
for i in z:
    print(i)
```



定义函数 `def `定义类 `class` 

定义的方式不是唯一的，以上是两种简单的方式。

#### 函数

```python
#面向过程：
def func1(x,y):
    return x + y
print(func1(12,18))
```

```python
#面向对象：
class DemoClassName:
    def __init__(self,x,y):
        self.x = x
        self.y = y
    def add(self):
        return self.x + self.y
```

### 老师分享的学习链接：

#### **Python 基础语法。**

- Python 标准语法：[ https://docs.python.org/zh-cn/3.7/tutorial/index.html](https://docs.python.org/zh-cn/3.7/tutorial/index.html)
- Python 内置函数：[ https://docs.python.org/zh-cn/3.7/library/functions.html](https://docs.python.org/zh-cn/3.7/library/functions.html)
- Python 内置类型：[ https://docs.python.org/zh-cn/3.7/library/stdtypes.html](https://docs.python.org/zh-cn/3.7/library/stdtypes.html)
- Python 数据类型：[ https://docs.python.org/zh-cn/3.7/library/datatypes.html](https://docs.python.org/zh-cn/3.7/library/datatypes.html)
- Python 标准库：[ https://docs.python.org/zh-cn/3.7/library/index.html](https://docs.python.org/zh-cn/3.7/library/index.html)
- Python 计算器使用：[ https://docs.python.org/zh-cn/3.7/tutorial/introduction.html](https://docs.python.org/zh-cn/3.7/tutorial/introduction.html)
- Python 数据结构：[ https://docs.python.org/zh-cn/3.7/tutorial/datastructures.html](https://docs.python.org/zh-cn/3.7/tutorial/datastructures.html)
- Python 其他流程控制工具 :[ https://docs.python.org/zh-cn/3.7/tutorial/controlflow.html](https://docs.python.org/zh-cn/3.7/tutorial/controlflow.html)
- Python 中的类：[ https://docs.python.org/zh-cn/3.7/tutorial/classes.html](https://docs.python.org/zh-cn/3.7/tutorial/classes.html)
- Python 定义函数：[ https://docs.python.org/zh-cn/3.7/tutorial/controlflow.html#defining-functions](https://docs.python.org/zh-cn/3.7/tutorial/controlflow.html#defining-functions)

#### **HTML（超文本标记语言）基础**

- HTML 标准语法：[ https://developer.mozilla.org/zh-CN/docs/Web/HTML](https://developer.mozilla.org/zh-CN/docs/Web/HTML)
- HTML 元素参考：[ https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element)
- HTML 属性参考：[ https://developer.mozilla.org/zh-CN/docs/Web/HTML/Attributes](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Attributes)
- HTML 全局属性：[ https://developer.mozilla.org/zh-CN/docs/Web/HTML/Global_attributes](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Global_attributes)
- HTML 链接类型：[ https://developer.mozilla.org/zh-CN/docs/Web/HTML/Link_types](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Link_types)