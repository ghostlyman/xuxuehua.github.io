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

##### flags

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

#### format 方法

`template.format(*args, **kwargs) (1) (2) (3) (4)`

> template 使用{} 表示变量
> {}或{\d+} 使用*args 按顺序填充
> {key} 使用**kwargs 按key填充
> Format String Syntax


```python
In [24]: '{0}, {name}'.format('Hello', name='World')
Out[24]: 'Hello, World'
```


### 字符串常用操作

#### 字符串连接 

##### join

```python
In [26]: L
Out[26]: ['I', 'love', 'Python']

In [27]: ''.join(L)
Out[27]: 'IlovePython'

In [28]: '_'.join(L)
Out[28]: 'I_love_Python'

In [30]: L
Out[30]: ['I', 'love', 'Python']

In [31]: for i in L:
    ...:     ret += i
    ...:     ret += ''
    ...: ret
    ...: 
Out[31]: 'IlovePython'
```



#### 字符串分割

##### split

```python
In [32]: s = 'I Love Python'

In [33]: s.split()
Out[33]: ['I', 'Love', 'Python']

In [34]: s.split('o')
Out[34]: ['I L', 've Pyth', 'n']

In [37]: S
Out[37]: 'root:*:0:0:System Administrator:/var/root:/bin/sh'

In [38]: S.split(':')
Out[38]: ['root', '*', '0', '0', 'System Administrator', '/var/root', '/bin/sh']

In [39]: S.split(':')[0]
Out[39]: 'root'

In [40]: username, _ = S.split(':', 1)

In [41]: username
Out[41]: 'root'

In [42]: new_s = 'URL:http://xuxuehua.com'

In [43]: k, v = new_s.split(':', 1)

In [44]: k, v
Out[44]: ('URL', 'http://xuxuehua.com')
```

##### rsplit

```python
In [45]: new_s
Out[45]: 'URL:http://xuxuehua.com'

In [46]: new_s.rsplit(':')
Out[46]: ['URL', 'http', '//xuxuehua.com']

In [47]: new_s.rsplit(':', 1)
Out[47]: ['URL:http', '//xuxuehua.com']
```

##### splitlines

```python
In [51]: s
Out[51]: '\nI Love Python\n I love Linux either\n'

In [52]: s.splitlines()
Out[52]: ['', 'I Love Python', ' I love Linux either']

In [53]: s.splitlines(True)
Out[53]: ['\n', 'I Love Python\n', ' I love Linux either\n']

In [54]: s.splitlines(False)
Out[54]: ['', 'I Love Python', ' I love Linux either']
```

##### partition (可实现迭代操作)

```python
In [58]: s
Out[58]: 'root:*:0:0:System Administrator:/var/root:/bin/sh'

In [59]: s.partition(':')
Out[59]: ('root', ':', '*:0:0:System Administrator:/var/root:/bin/sh')

In [60]: h, _, t = s.partition(':')

In [61]: t
Out[61]: '*:0:0:System Administrator:/var/root:/bin/sh'

In [62]: h, _, t = t.partition(':')

In [63]: t
Out[63]: '0:0:System Administrator:/var/root:/bin/sh'
```

##### rpartition 

```python
In [64]: s
Out[64]: 'root:*:0:0:System Administrator:/var/root:/bin/sh'

In [65]: s.rpartition(':')
Out[65]: ('root:*:0:0:System Administrator:/var/root', ':', '/bin/sh')

In [66]: h, _, t = s.rpartition(':')

In [67]: t
Out[67]: '/bin/sh'
```


#### 字符串修改 (字符串是不可修改的，这里是返回一个新的字符串)

##### capitalize

```python
In [68]: s = 'i love python'

In [69]: s.capitalize()
Out[69]: 'I love python'
```


##### titile

```python
In [70]: s
Out[70]: 'i love python'

In [71]: s.title()
Out[71]: 'I Love Python'
```

##### upper

```python
In [72]: s
Out[72]: 'i love python'

In [73]: s.upper()
Out[73]: 'I LOVE PYTHON'
```

##### lower

```python
In [77]: S
Out[77]: 'I love python'

In [78]: S.lower()
Out[78]: 'i love python'
```

##### swapcase

```python
In [82]: S
Out[82]: 'I Love Python'

In [83]: S.swapcase()
Out[83]: 'i lOVE pYTHON'
```


##### center

```python
In [87]: s
Out[87]: 'Python'

In [88]: s.center(20)
Out[88]: '       Python       '

In [89]: s.center(20, '*')
Out[89]: '*******Python*******'
```

##### ljust

```python
In [91]: s
Out[91]: 'Python'

In [92]: s.ljust(20)
Out[92]: 'Python              '

In [93]: s.ljust(20, '*')
Out[93]: 'Python**************'
```

##### rjust

```python
In [96]: s
Out[96]: 'Python'

In [97]: s.rjust(20)
Out[97]: '              Python'

In [98]: s.rjust(20, '*')
Out[98]: '**************Python'
```

##### zfill

```python
In [103]: s
Out[103]: 'Python'

In [104]: s.zfill(10)
Out[104]: '0000Python'

In [105]: s.zfill(11)
Out[105]: '00000Python'
```

##### strip (常用于处理文本, 去除空格和换行符)

```python
In [111]: s
Out[111]: 'abc \n  '

In [112]: s.strip()
Out[112]: 'abc'
```

##### rstrip

```python
In [113]: s
Out[113]: 'abc \n  '

In [114]: s.rstrip()
Out[114]: 'abc'
```

##### lstrip

```python
In [117]: s
Out[117]: 'abc \n  '

In [118]: s.lstrip()
Out[118]: 'abc \n  '
```


#### 字符串判断

##### startswith

```python
In [124]: s
Out[124]: 'I love Python'

In [125]: s.startswith('I')
Out[125]: True

In [126]: s.startswith('l')
Out[126]: False
```

##### endswith

```python
In [127]: s
Out[127]: 'I love Python'

In [128]: s.endswith('n')
Out[128]: True

In [129]: s.endswith('o')
Out[129]: False

```

##### count

```python
In [130]: s
Out[130]: 'I love Python'

In [131]: s.count('l')
Out[131]: 1

In [132]: s.count('o')
Out[132]: 2
```

##### index  (不存在会报异常)

```python
In [135]: s
Out[135]: 'I love Python'

In [136]: s.index('o')
Out[136]: 3

In [145]: s.index('x')
---------------------------------------------------------------------------
ValueError                                Traceback (most recent call last)
<ipython-input-145-a677ba2c36a5> in <module>()
----> 1 s.index('x')

ValueError: substring not found
```

##### rindex

```python
In [137]: s
Out[137]: 'I love Python'

In [138]: s.rindex('o')
Out[138]: 11
```

##### find  (不存在返回-1)

```python
In [139]: s
Out[139]: 'I love Python'

In [140]: s.find('l')
Out[140]: 2

In [141]: s.find('o')
Out[141]: 3

In [142]: s.find('Python')
Out[142]: 7

In [143]: s.find('xuxu')
Out[143]: -1
```

##### replace (负数操作会替换所有)

```python
In [146]: s 
Out[146]: 'I love Python'

In [147]: s.replace('o', 'x')
Out[147]: 'I lxve Pythxn'

In [148]: s.replace('o', 'x', 1)
Out[148]: 'I lxve Python'

In [149]: s.replace('o', 'x', -1)
Out[149]: 'I lxve Pythxn'
```


