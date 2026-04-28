# python

## 安装管理器

```bash
# 查看已安装版本
py --list

# 查看已安装版本及安装路径
py --list-paths

# 安装指定版本
py install <tags>

# 查看默认运行版本
py --version

# 查看指定版本所安装的库
py -<tags> -m pip list

# 给指定版本安装库
py -<tags> -m pip install 库名
py -3.12 -m pip install scipy -i https://pypi.tuna.tsinghua.edu.cn/simple
```

## Pycharm快捷键

| 快捷键                    | 功能说明                                  |
| :------------------------ | :---------------------------------------- |
| Alt + Enter               | 可实现快速建参、建函数架构等。            |
| Ctrl + Alt + V            | 快捷生成参数变量，生成实例。              |
| Alt + /                   | 快捷导入模块，补齐关键字。                |
| **Ctrl + D**              | 复制本行。                                |
| **Alt + J**               | 选择相同变量名，进而可以批量编辑。        |
| **Alt + Shift + 上/下键** | 上/下移动一整行，一直按一直移。           |
| Ctrl + B                  | 函数跳转阅读。                            |
| **Ctrl + Shift + A**      | 万能搜索符，支持以下快捷操作：            |
| Ctrl + Shift + I          | 查看帮助文档。                            |
| **Ctrl + Alt + L**        | 修正/格式化：全篇格式化，符合 PEP8 规范。 |
| Ctrl + Alt + M            | 代码抽取：剥离成函数。                    |
| **Ctrl + W**              | 选中/扩展选择（通常用于逐层选中代码块）。 |


## 语法简介

变量名命名规则：

* 由数字、字母、下划线组成
* 不可以以数字开头
* 不可以是关键字

> 规范：
>
> 1.下划线 or 驼峰体
> 2.当变量名全为大写时，约定俗成为常量

```python
# 单行注释
'单行注释'
"单行注释"

"""多行注释"""
'''多行注释'''
```



## 基本数据类型

| 类型    | 描述     |
| ------- | -------- |
| int     | 整型     |
| float   | 浮点型   |
| complex | 复数     |
| str     | 字符串   |
| bool    | 布尔类型 |

> 只有空和零为False
> 空：空字符串、空字典、空列表、空元组
> 零：0 None

### 格式化字符串

#### %

```
'my name is %s.' %name
'my name is %s, I am %s years old.' %(name, age)  # 按位置传值
'I am %(age)s years old, my name is %(name)s' %{'name':name, 'age':age}  # 按key传值

# %s 以字符串输出
# %d 以整型输出
```

#### format

```
'my name is {}, I am {} years old.'.format(name, age)  # 按位传值
'my name is {0}{0}{0}, I am {1}{1}{1} years old.'.format(name, age)  # 按索引传值
'my name is {name}, I am {age} years old.'.format(name=name, age=age) # 按key传值
```

#### f

```
f'my name is {name}, I am {age} years old.
```

### 转义字符与原字符

需要在字符中使用特殊字符时，使用反斜杠 \ 转义字符

原字符 or row字符串：r 或 R

| 字符  | 描述       |
| ----- | ---------- |
| \     | 续行符     |
| \\\   | 反斜杠     |
| \\'   | 单引号     |
| \\"   | 双引号     |
| \\a   | 响铃       |
| \\b   | 退格       |
| \\000 | 空         |
| \\n   | 换行       |
| \\v   | 纵向制表符 |
| \\t   | 横向制表符 |
| \\r   | 回车       |
| \f    | 换页       |

### 函数与方法

| 函数名称  | 描述                                                         |
| --------- | ------------------------------------------------------------ |
| int()     | 只能将整数字符串转化为int<br />float转化为int会舍弃小数部分  |
| float()   | 只能将整数字符串或小数字符串转化为float<br />int转为float小数部份补零 |
| complex() | 创建复数                                                     |
| str()     | 转化为str                                                    |
| bool()    | 转化为bool                                                   |

### 进制

| 进制     | 前缀  | 函数  |
| -------- | ----- | ----- |
| 二进制   | 0b/0B | bin() |
| 八进制   | 0o/0O | oct() |
| 十进制   | 默认  | int() |
| 十六进制 | 0x/0X | hex() |

### 运算符

| 分类       | 符号                              | 描述            |
| ---------- | --------------------------------- | --------------- |
| 算数运算符 | + 、-  、* 、 /  、//  、 %  、** | \\永远返回float |
| 比较运算符 | > 、< 、>= 、<= 、== 、!=         |                 |
| 逻辑运算符 | and or not                        | 存在短路逻辑    |
| 成员运算符 | in   not in                       | 字典判断的是key |

### 可变类型与不可变类型

不可变类型：value改变后，id也变

* 数字类型：int、float、complex
* 字符串类型
* bool类型



可变类型：value改变后，id不变

* 列表、元组、集合
* 字典



## 列表

> 列表存储的是值内存地址的映射与其对应的索引

### 定义

```python
# 定义列表
lst1 = []
lis2 = list((1, 2, 3))  # 传入iter

# 列表生成式
lis3  = [x for x in range(10)] 
lis4  = [[x,y] for x in range(3) for y in range(3)] # 笛卡尔积
```

### 函数与方法



## 元组

> 元组存存储的是值内存地址的映射与其对应的索引

### 定义

```python
# 定义元组
tuple1 = (,)
tuple2 = tuple([1, 2, 3])  # 传入iterable
```

### 函数与方法



## 集合

> 集合中不能存在相同元素，创建时会自动剔除相同的元素
>
> 元素类型只能是不可变类型

### 定义

```python
# 定义集合
set1 = set([1, 2, 3])
set2 = {1, 2, 3}  # 此方法不可以创建空集合

# 集合生成式
set3 = {x for x in range(10)}
```

### 函数与方法



## 字典

> 字典的key只能是不可变类型
> 字典存储的是key以及key对应的value的内存地址的映射

### 定义

```python
# 定义字典
dic1 = {1:1, 2:2, 3:3}
dic2 = dict([(1 ,1), (2, 2), (3, 3)])  # 传入iterable
dic3 = dict(a=1, b=2, c=3)

# 字典生成式
dic4 = {key:value for key,value in [[1, 2],[3, 4] , [5, 6]]}
```

### 函数与方法



## 流程控制语句

### 分支结构

```python
# 单分支结构
if 条件:
    pass

# 二分支结构
if 条件:
    pass
else:
    pass

# 多分支结构
if 条件:
    pass
elif 条件:
    pass
elif 条件:
    pass
else:
    pass

# 三元表达式
result = 真 if 条件 else 假
```

### 循环结构

```python
# break continue else

while 条件:
    pass

for i in iter:  # 遍历字典时，取的是key
    pass
```



## 文件

> 内存中固定使用unicode编码，当存入硬盘时可以指定utf-8等字符编码
>
> 
>
> 在字符前加u，强制解释器将字符串类型在内存中存为unicode码，主要在python2中使用 `a = u'abcd'`
>
> 
>
> 文件头
>
> * 指定读方式
>
> 	```python
> 	# coding: utf-8
> 	```
>
> *  指定存方式
>
> 	 ```python
> 	# encoding=utf-8
> 	```
>

### open

```python
#创建文件对象
f = open(r‘data.txt’,mode=‘rt’,encoding=‘utf-8’)
# 在linux与mac上encoding默认为utf-8
# 在window上encoding默认为gbk

# 关闭计算机系统中的文件，但并不会删除文件变量
f.close()
```

### with

```python
# with上下文管理器
# 代码块执行完毕后自动关闭文件
with open(r‘data.txt’,mode=‘rt’,encoding=‘utf-8’) as f:
    pass
with open(r‘data.txt’,mode=‘rt’,encoding=‘utf-8’) as f1,\
    open(r‘data.txt’,mode=‘rt’,encoding=‘utf-8’) as f2:
    pass
```

### 文件操作模式

| 参数 | 描述                         | 信息                                                         |
| ---- | ---------------------------- | ------------------------------------------------------------ |
| t    | 文本文件                     |                                                              |
| b    | 二进制文件                   |                                                              |
| r    | 只读模式                     | 文件不存在时报错<br />文件存在时，文件指针跳到开始位置       |
| r+   | 在只读的基础上加上写的功能   | 同r模式                                                      |
| w    | 覆盖写模式                   | 文件不存在时，创建空白文件，文件指针跳到开始位置<br />文件存在时，清空文件，文件指针跳到开始位置 |
| w+   | 在覆盖写的基础上加上读的功能 | 同w模式                                                      |
| a    | 追加模式                     | 文件不存在时，新建一个空白文件，文件指针在开始位置<br />文件存在时，文件指针跳到文件内容最后<br />即使移动文件指针，也只能在文件内容最后追加 |
| a+   | 在只追加的基础上加上读的功能 | 同a模式                                                      |
| x    | 只写模式                     | 文件存在报错，文件不存在就创建文件                           |

### 读写函数

```python
file.read()
# 将所读文件的内容从文件指针处读取到文件结尾，以字符串的格式返回
# 可以传递参数，用于指定读取多少个字节
# 若文件指针在内容的末尾则返回空字符串

file.readline()
# 每次调用读一行
# 若文件指针在内容的末尾则返回空字符串

file.readlines()
# 将所读文件的内容从文件指针处读取到文件结尾
# 返回以每一行为元素的列表；会保留结尾的换行符

file.write()
# 将写入的内容从文件指针处开始写入文件
# 返回写入文件的字符串长度

file.writelines(s:iterable[string])
# 将一个元素为字符串的序列整体写入文件

# for 循环可以按行遍历文件对象
for i in file:
    pass
```



## 函数

### 一般函数

```python
# 定义函数
def 函数名(参数1, 参数2, ...):
    '''函数说明'''
    pass
	return 返回值
# return不写或者return后面没有返回值，均默认返回None
# 函数执行return后就会结束此函数的运行
# 当函数返回多个值时，返回的类型为元组
# 定义函数不会执行函数子代码，但会检测函数子代码的语法

# 匿名函数
func = lamdba x, y: pass
```

### 参数类型

1. 位置参数

   * 可通过位置传参，也可以通过关键字传参，或者混用，位置实参必须放到关键字实参之前
   * 必须传入实参，实参和形参的位置和数量相等

2. 默认参数

   * 默认形参的值在函数定义阶段被赋值
   * 可通过位置传参，也可以通过关键字传参，或者混用，位置实参必须放到关键字实参之前
   * 可以不传入实参

3. 可变长度的形参

   * 可变长度的位置形参(\*形参名)(\*args)，class为元组
   * 可变长度的关键字形参(\**形参名)(**kwargs)，class为字典

4. 命名关键字形参

   * 限制要传入的参数名字，只能传入已命名关键字参数

   * 命名关键字参数需要一个特殊分隔符\*，后面的参数被命名为关键字参数，如果函数定义中已经有了一个可变参数，后面跟着的命名关键字参数就不再需要一个特殊分隔符*

   * 可以设置默认值

5. 特殊实参
   * 在列表（元组、字符串、字典）前加*，可以在函数位置参数传递时将列表（元组、字符串、字典）解包成位置实参
   * 在字典前加**，可以在函数关键字参数传递时将字典解包成关键字实参


> 形参顺序：
>
> 位置参数 -> 默认参数 -> *args -> 命名关键字形参 -> **kwargs

### 闭包函数与装饰器

闭函数：闭，封闭的意思，函数被封闭起来了

包函数：函数内部包含对外层函数作用域名字的引用

> 定义时嵌套函数 --> 装饰器
>
> 调用时嵌套函数 --> 递归

```python
# 模板一(最基础的模板)
def outer(func):
    def wrapper(*args, **kwargs):
        pass
        res = func(*args, **kwargs)
        pass
        return res
    return wrapper

# 语法糖
@outer
def function():
    pass
# 非语法糖
function = outer(function)


# 模板二(函数装饰器的完美伪装)
from functools import wraps

def outer(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        pass
        res = func(*args, **kwargs)
        pass
        return res
    return wrapper

@outer
def function():
    pass

# 模板三(带有参数的函数装饰器)
def g_outer(argment):
    def outer(func):
        def wrapper(*args, **kwargs):
            pass
            res = func(*args, **kwargs)
            pass
            return res
        return wrapper
    return outer

@g_outer('argument')
def function():
    pass
```

## 类

> 规范：类名采用驼峰体
> 自定义类默认继承object类
> 绑定方法：1.绑定给对象的方法(默认) 2.绑定给类的方法(@classmethod)
> 内置方法：会在满足条件的时候自动执行

### 面向对象

> 面向对象的特定：封装、继承、多态
>
> 
>
> 封装：
>
> * 整合
> * 隐藏属性和方法
>   * 隐藏的本质只是一种改名操作(加上一定的前缀)
>   * 隐藏属性和方法对外隐藏对内不隐藏
>   * 隐藏操作只会在类的定义阶段检查子代码语法时执行一次，之后定义的__的方法和属性并不能被隐藏
> * 目的：限制修改、减少对外复杂度
>
> 
>
> 继承：实现现实中的遗传问题
>
> 
>
> 多态：为多种类使用相同接口提供了可能
>
> * 鸭子类型实现(python推崇的多态)
> * 抽象基类(接口)实现

###  一般类

```python
class 类名(object):
    """类的说明文档"""

    # 定义类属性
    class_attribute_1 = None
    class_attribute_2 = None
    class_attribute_3 = None
    __class_attribute_4 = None  # 私有属性，将此属性隐藏，本质只是一个改名操作

    # 初始化对象独有属性的方法
    # 在创建对象时自动调用名为__init__的方法
    def __init__(self, var1, var2):
        self.var1 = var1
        self.var2 = var2
        return None  # __init__方法只可以返回None

    # len(object)时自动调用
    def __len__(self):
        pass
        return len
    
    # print(object)时自动调用
    def __str__(self):
        pass
        return str
    
    # del object时先自动调用此方法，然后删除object
    # 程序结束时，清除变量也会执行此方法
    def __del__(self):
        pass
        return None
    
    
    def __get_ca4(self): # 私有属性，将此方法隐藏，本质只是一个改名操作
        return __calss_attribute_4
    
```

### 抽象类

```python
# 抽象方法：没有函数体的方法
# 抽象类：包含抽象方法的类，抽象类的所有方法，子类都需要重写，抽象类只是提供模板
class 类名:
    def func1():
        pass
    
    def func2()
    	pass
```

### 方法重写

```python
class Father():
    def __init__():
        pass
    
class Son(Father):
    def __init__():
        # 方法一：
        Father.__init__()  # 此方法可以准确调用父类的方法
        
        # 方法二：
        super().__init__() # super()按此类的mro列表顺序查找父类，从第二个开始找
```

### 类装饰

> 自定义装饰器：使用闭包函数以及语法糖实现
>
> 内置的装饰器：
>
> * @property 将绑定方法装饰为属性(查、改、删)
> * @classmethod 类方法
> * @staticmethod 静态方法

```python
# 模板一(最基础的模板)
def outer(func):
    def wrapper(*args, **kwargs):
        pass
        res = func(*args, **kwargs)
        pass
        return res
    return wrapper

@outer
class class_name():
    pass

# 模板二(装饰器的完美伪装)
from functools import wraps

def outer(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        pass
        res = func(*args, **kwargs)
        pass
        return res
    return wrapper

@outer
class class_name():
    pass

# 模板三(带有参数的装饰器)
def g_outer(argment):
    def outer(func):
        def wrapper(*args, **kwargs):
            pass
            res = func(*args, **kwargs)
            pass
            return res
        return wrapper
    return outer

@g_outer('argument')
class class_name():
    pass

```



## 异常处理

```python
try:
    pass

except TypeError as doc:  # 将捕获的异常信息传入doc 
    # 出现TypeError时执行
    pass

except (Exception, NameError) as doc: # <=> except:
    # 捕获所有异常
    pass

else:
    # try的子代码块没有出现异常时执行
    pass

finally:
    # 无论try的子代码块有没有出现异常，都会执行
    pass
```



## 迭代器与生成器

> 可迭代对象：内置有\__iter__()方法
>
> 迭代器对象：内置有\_\_next\_\_()方法和\_\_iter\_\_方法
>
> 生成器 generator ：自定义的迭代器

```python
# yield 表达式
def fuc():
    pass
    y = yield 值1  # y 用于接收send()的参数
    pass
    y = yield 值2

res = func()  # 迭代器对象

# res.send(None) <=> next(res) <=> res.__next__()

# 生成器表达式
# (expression for item in iterable if condition)
l = [1, 2, 3, 4, 5]
generator = (x for x in l)
```



## 名称空间与作用域

### 名称空间


1. 内置名称空间：
    * Python解释器内置的变量名
    * Python解释器启动时，内置名称空间被创建。Python解释器关闭时，内置名称空间被销毁
2. 全局名称空间：
    * Python文件（模块）内定义的变量名，包括函数名、类名、模块名
    * 只要不是函数内部定义的变量名，也不是内置的变量名，剩下的就都属于全局名称空间的变量名
    * 在Python文件执行之前产生，Python文件运行完毕后销毁
3. 局部名称空间：
    * 函数内部定义的变量名，包括函数的参数
    * 在函数调用时产生，函数调用结束后销毁

4. 名称空间查找的优先级
    * 局部名称空间>全局名称空间>内置名称空间
    * 查找名称时，先查找所处的名称空间，然后找比所在名称空间优先级低的名称空间
    * 查找名称时，不会查找比所在名称空间优先级高的和同级但不同的名称空间
    * 名称空间的查找顺序是以定义阶段为基准，即变量名在哪个空间执行的定义，它就在那个空间，与调用空间无关

>非官方的名称空间定义：LEGB；（B：built-in；G：global；E：enclosing；L：local；）

### 作用域

1. 全局作用域
   * 包括内置名称空间、全局名称空间
   * 特点：全局存活、局部有效
2. 局部作用域
   * 包括局部名称空间
   * 临时存活、局部有效
3. 不同名称空间相互改值
   * 如果想要在局部名称空间（LE）中改全局名称空间（G）中的不可变类型的值，需要在局部名称空间（LE）中在改值之前用global声明
   * 如果想要在此局部名称空间（L）中改外层的局部名称空间（E）的不可变类型的值，需要在此局部名称空间（L）中在改值之前用nonlocal声明；



## 正则表达式

 

## 内置函数与方法

```python
id()  # 获取变量内存地址的映射值
type()  # 获取变量的类型
input()  # input()函数可以忽略输入的\n
print()  # 输出内容
```



## 第三方库

> 模块：一系列功能的集合体，例如Python文件 <=> 文件
>
> 包：把文件夹作为模块使用，文件夹中必须有\__init__.py <=> 文件夹
>
> 
>
> ​     组成       组成
>
> 模块 ------> 包 ------> 库

```python
# 当且仅当首次导入模块(包)时，会运行此模块(包)，导入包时，运行的是包中的__init__模块

# import：主模块(运行的py文件)与模块(包)之间的名称空间是独立开的
import 库名
import 库名 as 别名

# from import 会将函数等的变量名导入主模块的名称空间
from 库名 import 函数/属性/*
from 库名 import 函数/属性/* as 别名
```



### copy模块

```python
import copy

copy.copy()  # 浅拷贝
copy.deepcopy()  # 深拷贝
```































