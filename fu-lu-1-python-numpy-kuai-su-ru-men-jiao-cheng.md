# Python Numpy 入门教程

本教程最初由[ Justin Johnson](http://cs.stanford.edu/people/jcjohns/)由 [@LQ](https://github.com/liuqidev) 翻译整理。

在本门课程（CS231n）中， 我们将使用Python编程语言来提交所有的作业。Python就其本身而言是一门通用的编程语言，得益于众多受欢迎的开源库（numpy, scipy, matplotlib），其成为科学计算领域不可多得的强大工具。

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

```
if len\(arr\) &lt;= 1:

    return arr

pivot = arr\[len\(arr\) // 2\]

left = \[x for x in arr if x &lt; pivot\]

middle = \[x for x in arr if x == pivot\]

right = \[x for x in arr if x &gt; pivot\]

return quicksort\(left\) + middle + quicksort\(right\)
```

print\(quicksort\(\[3,6,8,10,1,2,1\]\)\)

\# 输出： "\[1, 1, 2, 3, 6, 8, 10\]"

\`\`\`

\#\#\# Python 版本

目前有两个官方支持的Python版本，一个是2.7版本，另一个是3.5的。

那么该选择哪个呢？Python 3.0 引入了很多向后不兼容的语法，所以使用Python 2.7编写的代码可能在3.5版本之下无法运行，反之亦然。

对于本门课程来说，所有代码将采用Python 3.5. \(译者注：事实上并非如此\)

你可以通过在命令行上输入以下代码来查看自己的Python 版本：

\`python --version\`.

