# Python Numpy 入门教程

本教程最初由 \[Justin Johnson\]\([http://cs.stanford.edu/people/jcjohns/\](http://cs.stanford.edu/people/jcjohns/%29%29 撰写创立。现由[Qi %28Lewis\) Liu\]\([https://github.com/liuqidev\](https://github.com/liuqidev%29\) 翻译整理。

在本门课程（CS231n）中， 我们将使用Python编程语言来提交所有的作业。Python就其本身而言是一门通用的编程语言，得益于众多受欢迎的开源库（numpy, scipy, matplotlib），其成为科学计算领域不可多得的强大工具。

我们希望你们对于Python和numpy的使用或多或少有些经验；如果你没有这方面的经验，那么本教程就是为你而生，你可以将其视作一个速成课程，你将快速学会Python编程语言以及Python在科学计算中的使用。

可能你们中有些人之前用过Mathlab，那么我们也推荐你去看 \[numpy for Matlab users\]\([http://wiki.scipy.org/NumPy\_for\_Matlab\_Users\](http://wiki.scipy.org/NumPy_for_Matlab_Users%29\) .

你也可以找到 \[IPython notebook tutorial \]\([https://github.com/kuleshov/cs228-material/blob/master/tutorials/python/cs228-python-tutorial.ipynb\](https://github.com/kuleshov/cs228-material/blob/master/tutorials/python/cs228-python-tutorial.ipynb%29\) 早前版本的一个教程，由 \[Volodymyr Kuleshov\]\([http://web.stanford.edu/~kuleshov/\](http://web.stanford.edu/~kuleshov/%29\) 和 \[Isaac Caswell\]\([https://symsys.stanford.edu/viewing/symsysaffiliate/21335\](https://symsys.stanford.edu/viewing/symsysaffiliate/21335%29\) 撰写创立，用于先修课 \[CS 228\]\([http://cs.stanford.edu/~ermon/cs228/index.html\](http://cs.stanford.edu/~ermon/cs228/index.html%29\).

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



