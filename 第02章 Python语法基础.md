> 《利用Python进行数据分析》这本书并不是以学习Python编程为主，所以只是用了两章的篇幅简单介绍了Python的基础知识，但对知识的梳理很好。如果想完整学习Python，入门Python的书有不少，推荐这几本《Python编程：从入门到实践》（这本书读前10章就够了）、《Python Cookbook》（进阶书，全书都写得很好，还可以当宝典用）、《流畅的Python》（更进阶的书）。
> 
> 学习Python最好的方式是用IPython、Jupyter notebook，或使用**PyCharm**结合**Miniconda**。PyCharm的代码配色方案非常漂亮，而Miniconda非常适合来做虚拟环境，两者结合如虎添翼。


***

![Python数分三·第2章](https://upload-images.jianshu.io/upload_images/7178691-6cceb7b444f10592.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


***

# 2.1 Python解释器

运行Python解释器很便捷，在终端里输入`python`就进入了Python解释器。如果要输出文本“Hello world”，则使用`print`语句`print("Hello world")`。

![](https://upload-images.jianshu.io/upload_images/7178691-064ef74035777532.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

将`print("Hello world")`保存为Python脚本文件`hello_world.py`。

```python
# hello_world.py
print("Hello world")
```

运行该脚本的方法是在终端里，执行命令`python hello_world.py`。




## 2.2 IPython基础

IPython也是解释器，但增加了许多功能，最明显的是有行号。在终端里输入`ipython`，进入IPython解释器。如果要在IPython中运行`py`脚本，命令是`%run hello_world.py`
```python
$ ipython
Python 3.10.4 | packaged by conda-forge | (main, Mar 24 2022, 17:38:57)
Type 'copyright', 'credits' or 'license' for more information
IPython 7.31.1 -- An enhanced Interactive Python. Type '?' for help.

In [1]: %run hello_world.py
Hello world

In [2]:
```

IPython在代码美化上下了很大功夫，尤其是代码对齐、自动换行、面向对象，并且还有许多好用的命令。

在IPython中，打印对象不必使用`print`命令，只需输入对象就成了。

```python
$ ipython
Python 3.10.4 | packaged by conda-forge | (main, Mar 24 2022, 17:38:57)
Type 'copyright', 'credits' or 'license' for more information
IPython 7.31.1 -- An enhanced Interactive Python. Type '?' for help.

In [1]: a = 5

In [2]: a
Out[2]: 5
```

再尝试一个复杂点的对象，使用NumPy生成一组随机数字：

```python
In [5]: import numpy as np

In [6]: data = [np.random.standard_normal() for i in range(7)]

In [7]: data
Out[7]: 
[-0.20470765948471295,
 0.47894333805754824,
 -0.5194387150567381,
 -0.55573030434749,
 1.9657805725027142,
 1.3934058329729904,
 0.09290787674371767]
```

和IPython配套的是Jupyter notebook。进入Jupyter notebook的方法是在终端中输入命令`jupyter notebook`：

``` python
$ jupyter notebook
[I 15:20:52.739 NotebookApp] Serving notebooks from local directory:
/home/wesm/code/pydata-book
[I 15:20:52.739 NotebookApp] 0 active kernels
[I 15:20:52.739 NotebookApp] The Jupyter Notebook is running at:
http://localhost:8888/?token=0a77b52fefe52ab83e3c35dff8de121e4bb443a63f2d...
[I 15:20:52.740 NotebookApp] Use Control-C to stop this server and shut down
all kernels (twice to skip confirmation).
Created new window in existing browser session.
    To access the notebook, open this file in a browser:
        file:///home/wesm/.local/share/jupyter/runtime/nbserver-185259-open.html
    Or copy and paste one of these URLs:
        http://localhost:8888/?token=0a77b52fefe52ab83e3c35dff8de121e4...
     or http://127.0.0.1:8888/?token=0a77b52fefe52ab83e3c35dff8de121e4...
```

Jupyter会自动打开默认的浏览器（除非用参数`--no-browser`指定不打开浏览器）。或者，可以在启动notebook之后手动打开网页，对于上面的例子，地址是最后的几行URL。

![](https://upload-images.jianshu.io/upload_images/7178691-16184460be253460.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

单击“New”，选择“Python3”，就可以新建笔记本。在代码框中输入`print('Hello, World!')`，按Shift-Enter执行代码。保存和重新加载笔记本也很简单，笔记本文件的后缀为`.ipynb`。

![](https://upload-images.jianshu.io/upload_images/7178691-f1ec13f39f246563.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### Tab补全

IPython具有Tab补全和代码提示功能。

```python
# 使用Tab补充变量名
In [1]: an_apple = 27

In [2]: an_example = 42

In [3]: an<Tab>
an_apple   an_example  any
```

```python
# 使用Tab补充变量的方法
In [3]: b = [1, 2, 3]

In [4]: b.<Tab>
append()  count()   insert()  reverse()
clear()   extend()  pop()     sort()
copy()    index()   remove()
```

```python
# 使用Tab补充模块的方法
In [1]: import datetime

In [2]: datetime.<Tab>
date          MAXYEAR       timedelta
datetime      MINYEAR       timezone
datetime_CAPI time          tzinfo
```

Jupyter notebook中也支持<Tab>补全

![](https://upload-images.jianshu.io/upload_images/7178691-4ae77d65f8ae5ad9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 自省

在对象前后使用问号（?），可以显示对象的信息：

```python
In [1]: b = [1, 2, 3]

In [2]: b?
Type:        list
String form: [1, 2, 3]
Length:      3
Docstring:
Built-in mutable sequence.

If no argument is given, the constructor creates a new empty list.
The argument must be an iterable if specified.

In [3]: print?
Docstring:
print(value, ..., sep=' ', end='\n', file=sys.stdout, flush=False)

Prints the values to a stream, or to sys.stdout by default.
Optional keyword arguments:
file:  a file-like object (stream); defaults to the current sys.stdout.
sep:   string inserted between values, default a space.
end:   string appended after the last value, default a newline.
flush: whether to forcibly flush the stream.
Type:      builtin_function_or_method
```

## 2.3 Python语法基础

#### 缩进

区别于其他编程语言，Python分行是使用缩进。

```python
for x in array:
    if x < pivot:
        less.append(x)
    else:
        greater.append(x)
```

#### 万物皆对象

Python中的标量、字符串、数据结构、函数、类、模块等都是对象，可以使用`type(*)`方法查看其对象信息。

#### 注释

Python在代码行开头使用`#`进行注释。快捷方法是`Ctrl+/`。

```python
results = []
for line in file_handle:
    # keep the empty lines for now
    # if len(line) == 0:
    #   continue
    results.append(line.replace("foo", "bar"))
```

#### 函数和方法

可以用圆括号调用函数，传入零个或若干参数，可以选择将返回值赋值给一个变量，也可以不赋值：

```python
result = f(x, y, z)
g()
```

几乎Python中的每个对象都有内部函数，称作方法（method），可以用来访问对象内部的内容。可以用下面的语句调用：

```python
obj.some_method(x, y, z)
```

函数可以使用位置（positional）和关键字（keyword）参数：

```python
result = f(a, b, c, d=5, e="foo")
```

#### 变量和参数

当在Python中为变量（或命名）赋值，可以在等号右边创建对这个变量的引用。在使用中，考虑一个整数列表：

```python
In [8]: a = [1, 2, 3]
```

假设将`a`赋值给一个新变量`b`：

```python
In [9]: b = a

In [10]: b
Out[10]: [1, 2, 3]
```

在Python中，`a`和`b`实际上是引用了同一个对象，即原有列表`[1, 2, 3]`（如图2-5所示的引用模型）。为了验证，可以先在`a`中添加一个元素，然后检查b：

```python
In [11]: a.append(4)

In [12]: b
Out[12]: [1, 2, 3, 4]
```

![图2-5 对同一对象的双重引用](https://upload-images.jianshu.io/upload_images/7178691-b4b1051a8fd9c2e1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

当你将对象作为参数传递给函数时，新的局域变量创建了对原始对象的引用，而不是复制。如果在函数里将一个新对象绑定到一个变量，这个操作不会影响到该函数（即函数圆括号以内的部分）以外“范围”的同名变量。因此，可以修改可变参数的内部值。假设有以下函数：

```python
In [13]: def append_element(some_list, element):
 ....: some_list.append(element)
```

然后有：

```python
In [14]: data = [1, 2, 3]

In [15]: append_element(data, 4)

In [16]: data
Out[16]: [1, 2, 3, 4]
```

#### 动态引用，强类型

Python中的对象不涉及固有类型（在Java等语言中，当声明变量时，同时需要声明变量的类型，称其为变量的固有类型），通过引用，变量可以引用不同类型的对象。下面的代码是没有问题的：

```python
In [17]: a = 5

In [18]: type(a)
Out[18]: int

In [19]: a = "foo"

In [20]: type(a)
Out[20]: str
```

变量是在特殊命名空间中的对象名；类型信息保存在对象自身中。但Python是“类型化语言”，如下所示：

```python
In [21]: "5" + 5
---------------------------------------------------------------------------
TypeError Traceback (most recent call last)
<ipython-input-21-7fe5aa79f268> in <module>
----> 1 "5" + 5
TypeError: can only concatenate str (not "int") to str
```

知道对象的类型很重要，最好能让函数可以处理多种类型的输入。使用`isinstance`函数，可以检查对象是否为特定类型的实例：

```python
In [26]: a = 5

In [27]: isinstance(a, int)
Out[27]: True
```

`isinstance`可以接收包含类型的元组作为参数，检查对象类型是否在类型元组中：

```python
In [28]: a = 5; b = 4.5

In [29]: isinstance(a, (int, float))
Out[29]: True

In [30]: isinstance(b, (int, float))
Out[30]: True
```

#### 属性和方法

Python的对象通常都有属性（存储在对象“内部”的其他Python对象）和方法（与对象关联的函数，可以访问对象的内部数据）。二者可以通过`obj.attribute_name`访问：

```python
In [1]: a = "foo"

In [2]: a.<Press Tab>
capitalize() index() isspace() removesuffix() startswith()
casefold() isprintable() istitle() replace() strip()
center() isalnum() isupper() rfind() swapcase()
count() isalpha() join() rindex() title()
encode() isascii() ljust() rjust() translate()
endswith() isdecimal() lower() rpartition()
expandtabs() isdigit() lstrip() rsplit()
find() isidentifier() maketrans() rstrip()
format() islower() partition() split()
format_map() isnumeric() removeprefix() splitlines()
```

也可以用`getattr`函数，通过名字访问属性和方法：

```python
In [32]: getattr(a, "split")
Out[32]: <function str.split(sep=None, maxsplit=-1)>
```

#### 鸭子类型

通常情况下，用户可能不关心对象的类型，只关心对象是否具有某些方法或特性。这通常称为鸭子类型（duck typing），源自“走起来像鸭子、叫起来像鸭子，那么它就是鸭子”的说法。例如，可以通过验证对象是否遵循迭代器协议（iterator protocol），验证它是否是可迭代的。对于许多对象，这意味着该对象有一个`__iter__`“魔术方法”，但使用`iter`函数来验证是更好的办法：

```python
In [33]: def isiterable(obj):
 ....: try:
 ....: iter(obj)
 ....: return True
 ....: except TypeError: # not iterable
 ....: return False
```

对于字符串以及大多数Python集合类型，该函数会返回`True`：

```python
In [34]: isiterable("a string")
Out[34]: True

In [35]: isiterable([1, 2, 3])
Out[35]: True

In [36]: isiterable(5)
Out[36]: False
```

#### 引入

在Python中，模块就是具有`.py`扩展名且包含Python代码的文件。假设有以下模块：

```python
# some_module.py
PI = 3.14159

def f(x):
    return x + 2

def g(a, b):
    return a + b
```

如果想从同路径下的另一个文件访问`some_module.py`中定义的变量和函数，可以：

```python
import some_module
result = some_module.f(5)
pi = some_module.PI
```

或者：

```python
from some_module import g, PI
result = g(5, PI)
```

使用`as`关键字，可以给引入的模块起不同的变量名：

```python
import some_module as sm
from some_module import PI as pi, g as gf

r1 = sm.f(pi)
r2 = gf(6, pi)
```

#### 二元运算符和比较运算符

Python中大部分二元数学运算和比较运算跟其他编程语言的数学语法很相似：

```python
In [37]: 5 - 7
Out[37]: -2

In [38]: 12 + 21.5
Out[38]: 33.5

In [39]: 5 <= 2
Out[39]: False
```

表2-1列出了所有可用的二元运算符。

![](https://upload-images.jianshu.io/upload_images/7178691-1a45bb5f9eb9df3c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

要判断两个变量是否引用同一个对象，可以使用`is`关键字。`is not`可以判断两个对象是不同的：

```python
In [40]: a = [1, 2, 3]

In [41]: b = a

In [42]: c = list(a)

In [43]: a is b
Out[43]: True

In [44]: a is not c
Out[44]: True
```

因为`list`函数总是创建一个新的Python列表（即复制），我们可以断定`c`是不同于`a`的。`is`关键字与`==`运算符不同，如下所示：

```python
In [45]: a == c
Out[45]: True
```

`is`和`is not`常用来判断变量是否为`None`，因为`None`的实例是唯一的：

```python
In [46]: a = None

In [47]: a is None
Out[47]: True
```

#### 可变与不可变对象

Python中的许多对象，例如列表、字典、NumPy数组，以及用户定义的类型（类），都是可变对象。这意味着可以修改这些对象或其包含的值：

```python
In [48]: a_list = ["foo", 2, [4, 5]]

In [49]: a_list[2] = (3, 4)

In [50]: a_list
Out[50]: ['foo', 2, (3, 4)]
```

另外，例如字符串和元组，是不可变对象，即不能修改其内部数据：

```python
In [51]: a_tuple = (3, 5, (4, 5))
In [52]: a_tuple[1] = "four"
---------------------------------------------------------------------------
TypeError Traceback (most recent call last)
<ipython-input-52-cd2a018a7529> in <module>
----> 1 a_tuple[1] = "four"
TypeError: 'tuple' object does not support item assignment
```

### 2.3.2 标量类型

Python有为数不多的内置类型，用于处理数值数据、字符串、布尔值（`True`或`False`），以及日期时间。这些“单值”类型有时被称为标量类型（scalar type），本书中称其为标量（scalar）。表2-2列出了主要的标量。日期和时间处理会单独讨论，因为它们是标准库的`datetime`模块提供的。

![](https://upload-images.jianshu.io/upload_images/7178691-620cea396daa098c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### 数值类型

Python的主要数值类型是`int`和`float`。`int`可以存储任意大的数：

```python
In [53]: ival = 17239871

In [54]: ival ** 6
Out[54]: 26254519291092456596965462913230729701102721
```

浮点数使用Python的`float`类型表示。每个浮点数底层都是双精度（64位）的值。浮点数也可以用科学计数法表示：

```python
In [55]: fval = 7.243

In [56]: fval2 = 6.78e-5
```

整数除法如果不能得到完整的整数，会自动将结果转换为浮点数：

```python
In [57]: 3 / 2
Out[57]: 1.5
```

要使用C语言风格的整除（即如果不是完整的整数，则删除小数部分），可以使用底除运算符`//`：

```python
In [58]: 3 // 2
Out[58]: 1
```

####  字符串

可以用单引号`'`或双引号`"`创建字符串常量：

```python
a = 'one way of writing a string'
b = "another way"
```

对于换行的多行字符串，可以使用三引号，`'''`或`"""`都行：

```python
c = """
This is a longer string that
spans multiple lines
"""
```

字符串`c`实际包含四行文本，`"""`后和`lines`后的换行符都是包含在字符串中的。可以用`count`方法计算`c`中的换行符：

```python
In [60]: c.count("\n")
Out[60]: 3
```

Python的字符串是不可变的，不能修改字符串：

```python
In [61]: a = "this is a string"
In [62]: a[10] = "f"
---------------------------------------------------------------------------
TypeError Traceback (most recent call last)
<ipython-input-62-3b2d95f10db4> in <module>
----> 1 a[10] = "f"
TypeError: 'str' object does not support item assignment
```

如果需要修改字符串，必须用函数或方法创建一个新的字符串，例如使用字符串的`replace`方法：

```python
In [63]: b = a.replace("string", "longer string")

In [64]: b
Out[64]: 'this is a longer string'
```

使用`str`函数，许多Python对象可以转化为字符串：

```python
In [66]: a = 5.6

In [67]: s = str(a)

In [68]: print(s)
5.6
```

字符串是Unicode字符的序列，因此可以像其他序列一样处理，比如列表和元组：

```python
In [69]: s = "python"

In [70]: list(s)
Out[70]: ['p', 'y', 't', 'h', 'o', 'n']

In [71]: s[:3]
Out[71]: 'pyt'
```

语法`s[:3]`被称作切片（slicing），适用于多种Python序列。后面会更详细地介绍，本书中广泛使用了切片。

反斜杠`\`是转义字符，用来表示特殊字符，比如换行符`\n`或Unicode字符。要写一个包含反斜杠的字符串，需要进行转义：

```python
In [72]: s = "12\\34"

In [73]: print(s)
12\34
```

如果字符串中包含许多反斜杠，但没有特殊字符，做起来就很麻烦。可以在字符串前面加一个前缀字符`r`，表明该字符串是原生字符串：

```python
In [74]: s = r"this\has\no\special\characters"

In [75]: s
Out[75]: 'this\\has\\no\\special\\characters'
```

r表示原生（raw）。

将两个字符串合并，会产生一个新的字符串：

```python
In [76]: a = "this is the first half "

In [77]: b = "and this is the second half"

In [78]: a + b
Out[78]: 'this is the first half and this is the second half'
```

Python 3.6中引入了一个新功能，即f-字符串（f-string）（即格式化字符串（formatted string）的缩写），用其创建格式化字符串更为简单。要创建f-字符串，就在字符串的前方加上字符f。在字符串中，Python表达式需要放在尖括号中，用于将表达式替换为格式化字符串。

```python
In [81]: amount = 10

In [82]: rate = 88.46

In [83]: currency = "Pesos"

In [84]: result = f"{amount} {currency} is worth US${amount / rate}"
```

可以在每个表达式的后面添加格式说明符，语法和之前的字符串模板相同：

```python
In [85]: f"{amount} {currency} is worth US${amount / rate:.2f}"
Out[85]: '10 Pesos is worth US$0.11'
```

#### 字节和Unicode

在当前的Python中（例如，Python 3.0及以上版本），Unicode成为了一级的字符串类型，可以更兼容地处理ASCII和非ASCII文本。在早期的Python版本中，字符串都是字节，不使用Unicode编码。假如知道字符的编码，可以将其转化为Unicode。看一个例子：

```python
In [86]: val = "español"

In [87]: val
Out[87]: 'español'
```

可以用`encode`方法将这个Unicode字符串转换为UTF-8字节：

```python
In [88]: val_utf8 = val.encode("utf-8")

In [89]: val_utf8
Out[89]: b'espa\xc3\xb1ol'

In [90]: type(val_utf8)
Out[90]: bytes
```

假如知道一个字节对象的Unicode编码，用`decode`方法可以解码：

```python
In [91]: val_utf8.decode("utf-8")
Out[91]: 'español'
```

#### 布尔值

Python中的两个布尔值写作`True`和`False`。比较运算和其他条件表达式的结果为`True`和`False`。布尔值可以与`and`和`or`关键字结合使用：

```python
In [95]: True and True
Out[95]: True

In [96]: False or True
Out[96]: True
```

布尔值转换为数字时，`False`变为0，`True`变为1：

```python
In [97]: int(False)
Out[97]: 0

In [98]: int(True)
Out[98]: 1
```

关键字`not`会翻转布尔值，即`True`变为`False`，反之亦然：

```python
In [99]: a = True

In [100]: b = False

In [101]: not a
Out[101]: False

In [102]: not b
Out[102]: True
```

#### 类型转换

`str`、`bool`、`int`和`float`类型同时也是函数，可以将其他数据转换为对应的类型：

```python
In [103]: s = "3.14159"

In [104]: fval = float(s)

In [105]: type(fval)
Out[105]: float

In [106]: int(fval)
Out[106]: 3

In [107]: bool(fval)
Out[107]: True

In [108]: bool(0)
Out[108]: False
```

#### None

`None`是Python的空值类型。

```python
In [109]: a = None

In [110]: a is None
Out[110]: True

In [111]: b = 5

In [112]: b is not None
Out[112]: True
```

`None`也常常作为函数参数的默认值：

```python
def add_and_maybe_multiply(a, b, c=None):
    result = a + b
    if c is not None:
        result = result * c
    return result
```

#### 日期和时间

Python内置的`datetime`模块提供了`datetime`、`date`和`time`类型。`datetime`类型结合了`date`和`time`二者存储的信息，是最常使用的：

```python
In [113]: from datetime import datetime, date, time

In [114]: dt = datetime(2011, 10, 29, 20, 30, 21)

In [115]: dt.day
Out[115]: 29

In [116]: dt.minute
Out[116]: 30
```

对于`datetime`实例，可以用`date`和`time`方法分别提取出`date`和`time`对象：

```python
In [117]: dt.date()
Out[117]: datetime.date(2011, 10, 29)

In [118]: dt.time()
Out[118]: datetime.time(20, 30, 21)
```

`strftime`方法可以将`datetime`格式化为字符串：

```python
In [119]: dt.strftime("%Y-%m-%d %H:%M")
Out[119]: '2011-10-29 20:30'
```

`strptime`函数可以将字符串转换（解析）成`datetime`对象：

```python
In [120]: datetime.strptime("20091031", "%Y%m%d")
Out[120]: datetime.datetime(2009, 10, 31, 0, 0)
```

### 2.3.3 控制流

和其他编程语言一样，Python有若干内置的关键字进行条件逻辑、循环和其他控制流（control flow）操作。

#### if、elif和else

`if`语句是最广为人知的控制流语句之一。它检查一个条件，如果为`True`，则执行后面的语句：

```python
x = -5
if x < 0:
    print("It's negative")
```

`if`语句后面可以跟一个或多个`elif`代码块，如果所有条件都是`False`时，还可以添加一个`else`代码块：

```python
if x < 0:
    print("It's negative")
elif x == 0:
    print("Equal to zero")
elif 0 < x < 5:
    print("Positive but smaller than 5")
else:
    print("Positive and larger than or equal to 5")
```

如果某个条件为`True`，后面的elif代码块就不会被执行。当使用`and`和`or`时，复合条件语句是从左到右执行，并且会发生“短路”：

```python
In [130]: a = 5; b = 7

In [131]: c = 8; d = 4

In [132]: if a < b or c > d:
 .....: print("Made it")
Made it
```

#### for循环

for循环是在集合（例如列表或元组）或迭代器中进行迭代。可以用`continue`使for循环提前进入下一次迭代，跳过剩下的部分。看下面这个例子，将列表中的整数相加，跳过`None`值：

```python
sequence = [1, 2, None, 4, None, 5]
total = 0
for value in sequence:
    if value is None:
        continue
    total += value
```

可以用`break`关键字跳出for循环。下面的代码将列表中各元素相加，直到遇到5：

```python
sequence = [1, 2, 0, 4, 6, 5, 2, 1]
total_until_5 = 0
for value in sequence:
    if value == 5:
        break
    total_until_5 += value
```

#### While循环

while循环指定了条件和代码快，当条件为`False`或用`break`退出循环，代码才会退出：

```python
x = 256
total = 0
while x > 0:
    if total > 500:
        break
    total += x
    x = x // 2
```

#### pass

`pass`是Python中的“无操作”（或“什么都不做”）语句。它用于不执行任何操作的代码块（或作为未完成代码的占位符）；之所以需要它，是因为Python使用缩进界定代码块：

```python
if x < 0:
    print("negative!")
elif x == 0:
    # TODO: put something smart here
    pass
else:
    print("positive!")
```

#### range

`range`函数生成一个均匀分布的整数序列：

```python
In [135]: range(10)
Out[135]: range(0, 10)

In [136]: list(range(10))
Out[136]: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

`range`的三个参数是起点、终点、步进，其中步进值可以是负数：

```python
In [137]: list(range(0, 20, 2))
Out[137]: [0, 2, 4, 6, 8, 10, 12, 14, 16, 18]

In [138]: list(range(5, 0, -1))
Out[138]: [5, 4, 3, 2, 1]
```

## 2.4总结

本章简要介绍了Python的基础语法概念，以及IPython和Jupyter编程环境。下一章中，我会介绍许多内置的数据类型、函数、输入-输出方法，这些内容将贯穿本书剩余章节。
