---
title: python-string-files
date: 2017-09-01 01:56:06
tags:
---

[toc]

#字符串与文本操作 (python-string-files)

## 字符串

> python2中的字符串是byte的有序序列
> python3中的字符串是unicode的有序序列
> 字符串是不可变的
> 字符串支持下标于切片

### 下标操作



```python
In [1]: s = 'I love Python'

In [2]: s[0]
Out[2]: 'I'

In [3]: s[-1]
Out[3]: 'n'

In [4]: s[3:8]
Out[4]: 'ove P'

In [5]: s[::-1]
Out[5]: 'nohtyP evol I'


```

* 线性结构的体现

```python
In [6]: s
Out[6]: 'I love Python'

In [7]: for i in s:
   ...:     print(i)
   ...:     
I
 
l
o
v
e
 
P
y
t
h
o
n
```

* 字符串是不可变的 (元组也不可变)

```python
In [8]: s
Out[8]: 'I love Python'

In [9]: s[1]
Out[9]: ' '

In [10]: s[1] = '_'
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-10-8ab2d301e01f> in <module>()
----> 1 s[1] = '_'

TypeError: 'str' object does not support item assignment


```

### 字符串的格式化

> print style format
> format 方法


* Print Style Format
`template % tunple 
template % dict`


```python
In [11]: 'I love %s' % ('python',)
Out[11]: 'I love python'

In [12]: 'I love %(name)s' % {'name':'python'}
Out[12]: 'I love python'
```

#### Print Styple Format Conversation

|符号|说明|
|-|-|
| %d | 整数|
| %i | 整数| 
| %o | 八进制数| 
| %x | 小写16进制整数| 
| %X | 大写16进制整数| 
| %f | 浮点数|
| %F | 浮点数| 
| %e | 小写科学计数法| 
| %E | 大写科学计数法| 
| %c | 字符，接收unicode编码或者单字符串|
| %a | 字符串，使用ascii函数转换| 
| %r | 字符串，使用repr函数转换| 
| %s | 字符串，使用str函数转换| 


* %d

```python
In [13]: '%d' % 3.4
Out[13]: '3'
```


* %E

```python
In [14]: '%E' % 0.00000000001
Out[14]: '1.000000E-11'

In [15]: '%E' % 1000000000000
Out[15]: '1.000000E+12'
```


* %g

```python
In [16]: '%g' % 0.001
Out[16]: '0.001'

In [17]: '%g' % 0.00000001
Out[17]: '1e-08'
```

#### flags

| Flag | 说明 | 
| - | - | 
| # | #代表一个数字，指定宽度，如果宽度不够，会根据一下进行填充| 
| 0 | 使用0填充，仅适用于数字| 
| . | 使用空格填充，默认为行| 
| - | 右边使用空格填充| 
| + | 填充之前增加+，仅仅对于正数|



```python
In [20]: '%10d' % 1
Out[20]: '         1'

In [21]: '%010d' % 1
Out[21]: '0000000001'
```


