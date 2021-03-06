
# 第三章 Python语言的数据类型
本章介绍Python语言的基本数据类型（数值、字符串、布尔类型）以及Python所特有的列表、元组、字典等数据类型。

## 3.1 Python语言的基本数据类型
Python语言的基本数据类型包括数值类型、布尔类型、字符串类型，其中数值类型又包括整数类型和浮点数类型。

| 类型名称| 实例|
| -----  | ----- |
| 整数 | `-100` |
| 浮点数 | `3.1416` |
| 字符串 | `'hello'` |
| 布尔型 | `True, False`|
<center>表3-1 Python语言的基本数据类型</center>

### 3.1.1 数值类型
数值类型包括整型、浮点型、长整型和复数型，这里只介绍我们经常使用的整型和浮点型。
- 整型（Integers）
例如，我们可以进行整型数据的加减乘除、整除、取余以及幂运算等，如下代码所示（#后面的文字为Python的注释）：


```python
#加法
2 + 2
```




    4




```python
#减法
10 - 3
```




    7




```python
#乘法
3 * 4
```




    12




```python
#除法
12 / 5
```




    2.4




```python
#整除
12 // 5
```




    2




```python
#取余
14 % 5
```




    4




```python
#幂运算
2 ** 3
```




    8



整型数字的最大最小值：
在 32 位系统中，一个整型 4 个字节，最小值 `-2,147,483,648`，最大值 `2,147,483,647`。
在 64 位系统中，一个整型 8 个字节，最小值 `-9,223,372,036,854,775,808`，最大值 `9,223,372,036,854,775,807`。  
我们可以用sys包中的maxsize来查看本机所能表示的最大整数。


```python
import sys
sys.maxsize
```




    9223372036854775807



- 浮点数（Floating Point Numbers）  
浮点数的运算和整数类似。


```python
#浮点数减法
3.4 - 3.2
```




    0.19999999999999973



注意看 3.4 - 3.2 的结果并不是我们预期的0.2，这是因为浮点数本身储存方式引起的，浮点数本身会存在一点误差。


```python
#浮点数除法
12.0 / 5.0
```




    2.4




```python
#浮点数幂运算
2.5 ** 3.5
```




    24.705294220065465



同样的，我们可以用sys包中float_info.max查看本机浮点数的最大值。


```python
sys.float_info.max
```




    1.7976931348623157e+308



除了上述标准的算术运算之外，还有一些常用的运算可以用于数值类型的数据，例如四舍五入、求绝对值等。这些运算可以通过Python内置的函数来完成。


```python
#绝对值函数abs
print(abs(-2.75))
#取整函数int
print(int(2.75))
#四舍五入函数round
print(round(2.75,1))
```

    2.75
    2
    2.8
    

### 变量赋值
Python 中的变量赋值不需要类型声明。每个变量在内存中创建，都包括变量的标识，名称和数据这些信息。每个变量在使用前都必须赋值，变量赋值以后该变量才会被创建。  
Python使用<变量名>=<表达式>的方式对变量进行赋值。等号（=）运算符左边是一个变量名,等号（=）运算符右边是存储在变量中的值。  
在 Python 里，变量名标识符由字母、数字、下划线组成，但不能以数字开头且区分大小写。  
例如，下面的代码将两个数值分别赋值给a、b两个变量，并把相加的结果赋值给变量c并打印。


```python
a = 10
b = 20
c = a + b
print(c)
```

    30
    

也可以为多个变量同时赋值，例如：


```python
a = b = 10
print(a,b)
```

    10 10
    


```python
a,b = 10,20
print(a,b)
```

    10 20
    

### 3.1.3 布尔类型（Boolean Data Type）
布尔型可以看成特殊的二值变量，其取值为True和False，例如：


```python
flag = True
print(flag)
```

    True
    

可以用布尔表达式构建布尔型变量，例如：


```python
x = 5
flag = x > 1 & x <= 5
print(flag)
```

    True
    

常用的比较符号包括：
<, >, <=, >=, ==, !=
分别代表小于、大于、小于等于、大于等于、等于、不等于。  


### 3.1.4 字符串类型

字符串是字符构成的一个序列。Python中的字符串可以是单引号或者双引号包围的一个字符序列，起始和末尾的引号必须是一致的（要么两个双引号，要么两个单引号）。使用双引号定义字符串时，单引号可以出现在字符串中，但双引号不能；同样的，使用单引号定义字符串时，双引号可以是字符串的一部分，但单引号不可以。以下是一些字符串的例子，用print函数打印出来。


```python
print("Hello,world!")
print("She isn't a student")
print('我说："早安，先生"')
```

    Hello,world!
    She isn't a student
    我说："早安，先生"
    

变量也可以赋值为字符串，例如：


```python
s = "Hello,Python"
print(s)
```

    Hello,Python
    

前面说过，字符串是字符组成的一个序列，这个序列中每个字符的位置可以使用数字0，1，2，3...来标识，这就是字符的索引。字符串中的第一个字符对应索引0而不是1，那么最后一个字符对应的索引就是字符串长度（字符串中字符的个数）减1。在Python中也可以用-1来表示字符串中最后一个字符的索引，用-2表示倒数第二个字符的索引，依此类推。在Python中我们用中括号中包含数字来表示字符串的索引，例如：


```python
s = "Hello,Python"
print(s[0],s[6],s[-1])
```

    H P n
    

截取字符串中某一段连续的字符，称为子字符串或字符串的切片。Python中字符串的切片操作采用n:m形式的索引,表示字符串从索引n开始到索引m（不包括m）的一个子序列，省略n表示从头开始，省略m表示直到末尾。例如：


```python
s = "Hello,Python"
print(s[2:8])
print(s[-5:-2])
print(s[2:])
print(s[:8])
```

    llo,Py
    yth
    llo,Python
    Hello,Py
    

字符串之间可以使用加法和乘法运算，只是和数值类型的加法和乘法不同。字符串的加法表示字符串之间的连接，而字符串和一个数字n相乘则表示将该字符串重复n次，例如下面的代码：


```python
s = "Hello," + "world!"
print(s)
print(s*3)
```

    Hello,world!
    Hello,world!Hello,world!Hello,world!
    

Python是一种面向对象的语言，面向对象的语言中一个必不可少的元素就是方法，而字符串是对象的一种，所以有很多可用的方法。

跟很多语言一样，Python使用以下形式来调用方法：

    对象.方法(参数)


```python
s = "Hello," + "world!"
#求字符串的长度
print(len(s))
#将字符串全部转为大写
print(s.upper())
#将字符串全部转为小写
print(s.lower())
```

    12
    HELLO,WORLD!
    hello,world!
    

### 3.1.5 类型转换
Python中简单的数据转换主要在整型、浮点型和字符串之间进行，采用Python的内置函数int、float和str完成，如下代码所示：


```python
#浮点型数据取整
a = int(123.45)
print(a)
#字符串转换成数值
b = float("123.45")
print(b)
#数值转换成字符串
c = str(123.45)
print(c)
#输出以上三个变量的类型
print(type(a),type(b),type(c))
```

    123
    123.45
    123.45
    <class 'int'> <class 'float'> <class 'str'>
    

## 3.2 列表类型


```python

```
