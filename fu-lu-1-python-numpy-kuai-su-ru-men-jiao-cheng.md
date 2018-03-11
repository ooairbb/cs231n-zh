# Python Numpy 入门教程

本教程最初由 \[Justin Johnson\]\([http://cs.stanford.edu/people/jcjohns/\](http://cs.stanford.edu/people/jcjohns/\)\) 撰写创立。现由\[Qi \(Lewis\) Liu\]\([https://github.com/liuqidev\](https://github.com/liuqidev\)\) 翻译整理。

在本门课程（CS231n）中， 我们将使用Python编程语言来提交所有的作业。Python就其本身而言是一门通用的编程语言，得益于众多受欢迎的开源库（numpy, scipy, matplotlib），其成为科学计算领域不可多得的强大工具。

我们希望你们对于Python和numpy的使用或多或少有些经验；如果你没有这方面的经验，那么本教程就是为你而生，你可以将其视作一个速成课程，你将快速学会Python编程语言以及Python在科学计算中的使用。

可能你们中有些人之前用过Mathlab，那么我们也推荐你去看 \[numpy for Matlab users\]\([http://wiki.scipy.org/NumPy\_for\_Matlab\_Users\](http://wiki.scipy.org/NumPy_for_Matlab_Users\)\) .

你也可以找到 \[IPython notebook tutorial \]\([https://github.com/kuleshov/cs228-material/blob/master/tutorials/python/cs228-python-tutorial.ipynb\](https://github.com/kuleshov/cs228-material/blob/master/tutorials/python/cs228-python-tutorial.ipynb\)\) 早前版本的一个教程，由 \[Volodymyr Kuleshov\]\([http://web.stanford.edu/~kuleshov/\](http://web.stanford.edu/~kuleshov/\)\) 和 \[Isaac Caswell\]\([https://symsys.stanford.edu/viewing/symsysaffiliate/21335\](https://symsys.stanford.edu/viewing/symsysaffiliate/21335\)\) 撰写创立，用于先修课 \[CS 228\]\([http://cs.stanford.edu/~ermon/cs228/index.html\](http://cs.stanford.edu/~ermon/cs228/index.html\)\).

目录:

* \[Python\]\(\#python\)

  * \[基本数据类型 Basic data types\]\(\#python-basic\)

  * \[容器 Containers\]\(\#python-containers\)

    * \[列表 Lists\]\(\#python-列表s\)

    * \[字典 Dictionaries\]\(\#python-dicts\)

    * \[集合 Sets\]\(\#python-sets\)

    * \[元组 Tuples\]\(\#python-tuples\)

  * \[函数 Functions\]\(\#python-functions\)

  * \[类 Classes\]\(\#python-classes\)

* \[Numpy\]\(\#numpy\)

  * \[阵列/数组 Arrays\]\(\#numpy-arrays\)

  * \[阵列/数组索引 Array indexing\]\(\#numpy-array-indexing\)

  * \[数据类型 Datatypes\]\(\#numpy-datatypes\)

  * \[阵列/数组计算 Array math\]\(\#numpy-math\)

  * \[广播 Broadcasting\]\(\#numpy-broadcasting\)

* \[SciPy\]\(\#scipy\)

  * \[图片操作 Image operations\]\(\#scipy-image\)

  * \[MATLAB 文件\]\(\#scipy-matlab\)

  * \[点间距离\]\(\#scipy-dist\)

* \[Matplotlib\]\(\#matplotlib\)

  * \[绘图 Plotting\]\(\#matplotlib-plotting\)

  * \[子图 Subplots\]\(\#matplotlib-subplots\)

  * \[图片 Images\]\(\#matplotlib-images\)



&lt;a name='python'&gt;&lt;/a&gt;



\#\# Python



Python是一门高级的，动态类型，多参数的编程语言。Python程序被誉为“可执行的伪代码”，因为你允许你使用极少的几行代码就可以实现强大的逻辑。作为示例，下面是使用Python编写的经典快速排序实现。



\`\`\`python

def quicksort\(arr\):

    if len\(arr\) &lt;= 1:

        return arr

    pivot = arr\[len\(arr\) // 2\]

    left = \[x for x in arr if x &lt; pivot\]

    middle = \[x for x in arr if x == pivot\]

    right = \[x for x in arr if x &gt; pivot\]

    return quicksort\(left\) + middle + quicksort\(right\)



print\(quicksort\(\[3,6,8,10,1,2,1\]\)\)

\# 输出： "\[1, 1, 2, 3, 6, 8, 10\]"

\`\`\`



\#\#\# Python 版本

目前有两个官方支持的Python版本，一个是2.7版本，另一个是3.5的。



那么该选择哪个呢？Python 3.0 引入了很多向后不兼容的语法，所以使用Python 2.7编写的代码可能在3.5版本之下无法运行，反之亦然。



对于本门课程来说，所有代码将采用Python 3.5. \(译者注：事实上并非如此\)



你可以通过在命令行上输入以下代码来查看自己的Python 版本：

\`python --version\`.



&lt;a name='python-basic'&gt;&lt;/a&gt;



\#\#\# 基本数据类型



和大多数编程语言一样，Python有一些列自己的基本数据类型，包括整型，浮点型，布尔型，字符串类型。其属性和其他编程语言类似。



\*\*数字类型 Numbers:\*\* 整型和浮点型可能如你所想和其他编程语言中的用法无异。



\`\`\`python

x = 3

print\(type\(x\)\) \# 输出 "&lt;class 'int'&gt;"

print\(x\)       \# 输出 "3"

print\(x + 1\)   \# 加; 输出 "4"

print\(x - 1\)   \# 减; 输出 "2"

print\(x \* 2\)   \# 乘; 输出 "6"

print\(x \*\* 2\)  \# 幂; 输出 "9"

x += 1

print\(x\)  \# 输出 "4"

x \*= 2

print\(x\)  \# 输出 "8"

y = 2.5

print\(type\(y\)\) \# 输出 "&lt;class 'float'&gt;"

print\(y, y + 1, y \* 2, y \*\* 2\) \# 输出 "2.5 3.5 5.0 6.25"

\`\`\`

注意，和很多编程语言不一样的是，Python没有一元的增 \(\`x++\`\) 和一元减 \(\`x--\`\) 操作符。



对于更复杂的数字Python也提供了很多内置类型，具体细节参见\[这篇文档\]\(https://docs.python.org/3.5/library/stdtypes.html\#numeric-types-int-float-complex\).







\*\*布尔类型 Booleans:\*\* Python实现了所有的常用的布尔逻辑操作符，但是，不是符号（\`&&\`, \`\|\|\`, 等），取而代之的是英语单词（\`and\`,\`or\`,\`not\`,等）:



\`\`\`python

t = True

f = False

print\(type\(t\)\) \# 输出 "&lt;class 'bool'&gt;"

print\(t and f\) \# 逻辑 与; 输出 "False"

print\(t or f\)  \# 逻辑 或; 输出 "True"

print\(not t\)   \# 逻辑 非; 输出 "False"

print\(t != f\)  \# 逻辑 异或; 输出 "True"

\`\`\`



\*\*字符串类型 Strings:\*\* Python对于字符串类型有非常强大的支持性:



\`\`\`python

hello = 'hello'    \# 字符串可以使用单引号阔起来，

world = "world"    \# 也可以使用双引号; 两者完全等效

print\(hello\)       \# 输出 "hello"

print\(len\(hello\)\)  \# 字符串长度; 输出 "5"

hw = hello + ' ' + world  \# 字符串级联

print\(hw\)  \# 输出 "hello world"

hw12 = '%s %s %d' % \(hello, world, 12\)  \# sprintf 风格的字符串格式化

print\(hw12\)  \# 输出 "hello world 12"

\`\`\`



字符串对象有许多有用的方法；例如：



\`\`\`python

s = "hello"

print\(s.capitalize\(\)\)  \# 将字符串首字母大写; 输出 "Hello"

print\(s.upper\(\)\)       \# 将字符串转换成全大写; 输出 "HELLO"

print\(s.rjust\(7\)\)      \# 将字符串右对齐, 不够使用空格填充; 输出 "  hello"

print\(s.center\(7\)\)     \# 将字符串中间对其, 不够使用空白填充; 输出 " hello "

print\(s.replace\('l', '\(ell\)'\)\)  \# 将字符串中所有找到的字串使用另一个字串替换

                                \# 输出 "he\(ell\)\(ell\)o"

print\('  world '.strip\(\)\)  \# 跳过字符串首部和尾部的空字符串; 输出 "world"

\`\`\`

想查看所有的字符串内置方法的列表，看 \[这篇文档\]\(https://docs.python.org/3.5/library/stdtypes.html\#string-methods\).



&lt;a name='python-containers'&gt;&lt;/a&gt;



\#\#\# 容器 Containers

Python 中包含了好几种内置的容器类型：列表\(lists\), 字典\(dictionaries\), 集合\(sets\), 和元组\(tuples\).



&lt;a name='python-lists'&gt;&lt;/a&gt;



\#\#\#\# 列表 Lists

Python中列表\(list\) 相当于是阵列/数组\(array\), 但是Python列表是大小可变的



并且\*\*可以存储不同类型的元素 \*\*:



\`\`\`python

xs = \[3, 1, 2\]    \# 创建一个列表

print\(xs, xs\[2\]\)  \# 输出 "\[3, 1, 2\] 2"

print\(xs\[-1\]\)     \# 负的索引，将从列表的后边开始计数; 输出 "2"

xs\[2\] = 'foo'     \# 列表可以包含不同类型的元素

print\(xs\)         \# 输出 "\[3, 1, 'foo'\]"

xs.append\('bar'\)  \# 向列表中最后增加一个元素

print\(xs\)         \# 输出 "\[3, 1, 'foo', 'bar'\]"

x = xs.pop\(\)      \# 移除并返回列表中最后一个元素

print\(x, xs\)      \# 输出 "bar \[3, 1, 'foo'\]"

\`\`\`

关于列表使用凶残的细节，我不会说可以在\[这篇文档\]\(https://docs.python.org/3.5/tutorial/datastructures.html\#more-on-lists\)中找到的。



\*\*切片 Slicing:\*\*

除了每次访问列表元素的一个元素外，Python提供了一种简洁的语法来访问列表中的一部分；这种方式叫做切片：



\`\`\`python

nums = list\(range\(5\)\)     \# range 为一个内置函数，用来创建一个整型的列表

print\(nums\)               \# 输出 "\[0, 1, 2, 3, 4\]"

print\(nums\[2:4\]\)          \# 得到一个切片，元素为索引 2 到 4（开）的列表元素; 输出 "\[2, 3\]"

print\(nums\[2:\]\)           \# 得到一个切片，元素为索引 2 到 结尾的元素; 输出 "\[2, 3, 4\]"

print\(nums\[:2\]\)           \# 得到一个切片，元素为索引从开始\(0\) 到 2 \(开\)的元素; 输出 "\[0, 1\]"

print\(nums\[:\]\)            \# 得到一个切片，元素为整个列表的全部元素; 输出 "\[0, 1, 2, 3, 4\]"

print\(nums\[:-1\]\)          \# 切片的索引也可以为负值; 输出 "\[0, 1, 2, 3\]"

nums\[2:4\] = \[8, 9\]        \# 将一个列表对切片进行赋值

print\(nums\)               \# 输出 "\[0, 1, 8, 9, 4\]"

\`\`\`

我们在介绍 numpy arrays 的时候还会见到切片。



\*\*循环 Loops:\*\* 你可以像下面这样遍历列表元素:



\`\`\`python

animals = \['cat', 'dog', 'monkey'\]

for animal in animals:

    print\(animal\)

\# 输出 "cat", "dog", "monkey", 每个元素一行.

\`\`\`



如果你想在循环体中获取其中元素的索引，需要使用内置函数\`enumerate\`I：



\`\`\`python

animals = \['cat', 'dog', 'monkey'\]

for idx, animal in enumerate\(animals\):

    print\('\#%d: %s' % \(idx + 1, animal\)\)

\# 输出 "\#1: cat", "\#2: dog", "\#3: monkey", 每个输出一行

\`\`\`



\*\*列表解析 List comprehensions:\*\*

编程工程中，我梦经常需要将一种类型的数据转换成另外一种类型的数据。



下面是计算数字平方数的例子:



\`\`\`python

nums = \[0, 1, 2, 3, 4\]

squares = \[\]

for x in nums:

    squares.append\(x \*\* 2\)

print\(squares\)   \# 输出 \[0, 1, 4, 9, 16\]

\`\`\`



可以使用\*\*列表解析 list comprehension\*\*来更加优雅地完成上述任务：



\`\`\`python

nums = \[0, 1, 2, 3, 4\]

squares = \[x \*\* 2 for x in nums\]

print\(squares\)   \# 输出 \[0, 1, 4, 9, 16\]

\`\`\`



列表解析中也可以包含条件表达式：



\`\`\`python

nums = \[0, 1, 2, 3, 4\]

even\_squares = \[x \*\* 2 for x in nums if x % 2 == 0\]

print\(even\_squares\)  \# 输出 "\[0, 4, 16\]"

\`\`\`



&lt;a name='python-dicts'&gt;&lt;/a&gt;



\#\#\#\# 字典 Dictionaries

字典用来存储键值对——\(key, value\)，和Java中的\`map\` 或者Javascript中的对象类似。其用法如下：



\`\`\`python

d = {'cat': 'cute', 'dog': 'furry'}  \# 创建一个字典

print\(d\['cat'\]\)       \# 获取字典中的某项; 输出 "cute"

print\('cat' in d\)     \# 检查字典中是否有某个给定的键; 输出 "True"

d\['fish'\] = 'wet'     \# 修改字典中的某项

print\(d\['fish'\]\)      \# 输出 "wet"

\# print\(d\['monkey'\]\)  \# 键的错误，KeyError: 'monkey' 不是字典 d 中的键

print\(d.get\('monkey', 'N/A'\)\)  \# 获取到一个默认的元素; 输出 "N/A"

print\(d.get\('fish', 'N/A'\)\)    \# 获取到一个默认的元素; 输出 "wet"

del d\['fish'\]         \# 从字典中移除一个元素

print\(d.get\('fish', 'N/A'\)\) \# "fish" 不再是其中的一个键; 输出 "N/A"

\`\`\`

关于字典的更多的用法，请阅读 \[这篇文档\]\(https://docs.python.org/3.5/library/stdtypes.html\#dict\).



\*\*遍历:\*\* 字典很容易遍历其中的键:



\`\`\`python

d = {'person': 2, 'cat': 4, 'spider': 8}

for animal in d:

    legs = d\[animal\]

    print\('A %s has %d legs' % \(animal, legs\)\)

\# 输出 "A person has 2 legs", "A cat has 4 legs", "A spider has 8 legs"

\`\`\`



如果你想在遍历字典过程中，同时获取字典中的键和键对应的值，使用\`items\` 方法：



\`\`\`python

d = {'person': 2, 'cat': 4, 'spider': 8}

for animal, legs in d.items\(\):

    print\('A %s has %d legs' % \(animal, legs\)\)

\# 输出 "A person has 2 legs", "A cat has 4 legs", "A spider has 8 legs"

\`\`\`



\*\*字典解析 Dictionary comprehensions:\*\*

字典解析和列表解析类似，能够以更快的方式建立字典。例如:



\`\`\`python

nums = \[0, 1, 2, 3, 4\]

even\_num\_to\_square = {x: x \*\* 2 for x in nums if x % 2 == 0}

print\(even\_num\_to\_square\)  \# 输出 "{0: 0, 2: 4, 4: 16}"

\`\`\`



&lt;a name='python-sets'&gt;&lt;/a&gt;



\#\#\#\# 集合 Sets

集合是不同无序元素组成的集体。其基本的用法，参见下方示例：



\`\`\`python

animals = {'cat', 'dog'}

print\('cat' in animals\)   \# 检查某元素是否是集合中的元素; 输出 "True"

print\('fish' in animals\)  \# 输出 "False"

animals.add\('fish'\)       \# 向集合中增加一个元素

print\('fish' in animals\)  \# 输出 "True"

print\(len\(animals\)\)       \# 集合中元素的数量; 输出 "3"

animals.add\('cat'\)        \# 向集合中增加一个已经存在的元素

print\(len\(animals\)\)       \# 输出 "3"

animals.remove\('cat'\)     \# 从结合中移除一个元素

print\(len\(animals\)\)       \# 输出 "2"

\`\`\`



同样，如果想知道关于集合的更多用法的介绍请阅读\[这篇文档\]\(https://docs.python.org/3.5/library/stdtypes.html\#set\).





\*\*遍历:\*\*

遍历集合和遍历列表的语法相同;

但是，由于集合是无序的，所以你没办法假设你访问的集合中元素就是按照显示的顺序访问的：



\`\`\`python

animals = {'cat', 'dog', 'fish'}

for idx, animal in enumerate\(animals\):

    print\('\#%d: %s' % \(idx + 1, animal\)\)

\# 输出 "\#1: fish", "\#2: dog", "\#3: cat"

\`\`\`



\*\*集合解析 Set comprehensions:\*\*

和集合以及字典类似，你也可以使用集合解析来构建集合:



\`\`\`python

from math import sqrt

nums = {int\(sqrt\(x\)\) for x in range\(30\)}

print\(nums\)  \# 输出 "{0, 1, 2, 3, 4, 5}"

\`\`\`



&lt;a name='python-tuples'&gt;&lt;/a&gt;



\#\#\#\# 元组 Tuples

元组是值不可更改的有序列表。



元祖在很多方面和列表一样, 和列表最大的不同点就是元祖可以作为字典以及集合中的键, 而列表是不可以这样的。



下面是一个简单的示例：



\`\`\`python

d = {\(x, x + 1\): x for x in range\(10\)}  \# 创建一个带有元组键值的字典

t = \(5, 6\)        \# 创建一个元组

print\(type\(t\)\)    \# 输出 "&lt;class 'tuple'&gt;"

print\(d\[t\]\)       \# 输出 "5"

print\(d\[\(1, 2\)\]\)  \# 输出 "1"

\`\`\`

\[这个文档\]\(https://docs.python.org/3.5/tutorial/datastructures.html\#tuples-and-sequences\) 有关于元组更多的信息。



&lt;a name='python-functions'&gt;&lt;/a&gt;



\#\#\# 函数 Functions

Python 函数使用 \`def\` 关机字来构建. 举例:



\`\`\`python

def sign\(x\):

    if x &gt; 0:

        return 'positive'

    elif x &lt; 0:

        return 'negative'

    else:

        return 'zero'



for x in \[-1, 0, 1\]:

    print\(sign\(x\)\)

\# 输出 "negative", "zero", "positive"

\`\`\`



我们常常定义一些包含一些可选参数的函数，就像下面这个一样：



\`\`\`python

def hello\(name, loud=False\):

    if loud:

        print\('HELLO, %s!' % name.upper\(\)\)

    else:

        print\('Hello, %s' % name\)



hello\('Bob'\) \# 输出 "Hello, Bob"

hello\('Fred', loud=True\)  \# 输出 "HELLO, FRED!"

\`\`\`

\[这篇文档\]\(https://docs.python.org/3.5/tutorial/controlflow.html\#defining-functions\) 中有关于Python 函数的更多用法.



&lt;a name='python-classes'&gt;&lt;/a&gt;



\#\#\# 类 Classes



Python 用来定义类的语法很简单:



\`\`\`python

class Greeter\(object\):



    \# 构造器 Constructor

    def \_\_init\_\_\(self, name\):

        self.name = name  \# Create an instance variable



    \# 实例方法 Instance method

    def greet\(self, loud=False\):

        if loud:

            print\('HELLO, %s!' % self.name.upper\(\)\)

        else:

            print\('Hello, %s' % self.name\)



g = Greeter\('Fred'\)  \# 构建一个 Greeter 类的实例

g.greet\(\)            \# 调用一个实例方法; 输出 "Hello, Fred"

g.greet\(loud=True\)   \# 调用一个实例方法; 输出 "HELLO, FRED!"

\`\`\`

关于Python类，更多请阅读 \[这篇文档\]\(https://docs.python.org/3.5/tutorial/classes.html\).



