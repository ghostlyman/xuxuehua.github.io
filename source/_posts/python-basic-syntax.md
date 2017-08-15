---
title:  Python 基础语法
---

[toc]

# Python 基础语法



## Hello World

```python
In [2]: print('Hello World')
Hello World
```



## 变量 

> 即解释器中的一段内存引用
> Python 中，变量都是引用



## 数据类型

> Python 是强类型的动态语言
> 数据类型是对用来约束数据
> 原始类型和复合类型

*  强类型特点
```python
In [3]: 1 + 'abc'
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-3-aab9e8ede4f7> in <module>()
----> 1 1 + 'abc'

TypeError: unsupported operand type(s) for +: 'int' and 'str'
```

* 弱类型特点
```javascript
1 + "abc"
"1abc"
```

### 原始类型
* int,  fload, byte

### 复合类型
> 由其他原始类型组合起来的类型

* list, dict 

## 运算符

### 算数运算符
* \+ \- \* / 
* \% \** // 

### 位运算符
*  & |  ^ 
* 左移 << 
* 右移动 >>


### 比较运算符
* ==
* !=
* >
* <
* >=
* <=
*

### 逻辑运算符
* and or not

> 逻辑运算的短路功能


### 其他运算符
* a = b 赋值
* a in b 成员
* a not in b 成员
* a is b ( 比较的元素ID ）
* a is not b


## 表达式
* a and (1+2) < 3
* a if a > 0 else 0 

### 表达式与优先级
* 一元高于二元
* 数值高于逻辑
* 算术高于位运算
* 乘除高于加减
* 拿不准加括号解决


## 程序结构 

### 顺序结构
* 绝大部分编程语言的默认结构
* 按照书写顺序依次执行


### 分支结构

> if 语句

```python
In [10]: if True:
    ...:     print('True')
    ...:     
True
```

> else 语句

```python
In [12]: a = 4 

In [13]: if a > 0:
    ...:     a = 5
    ...: else:
    ...:     a = 0
    ...:     

In [14]: a
Out[14]: 5
```

> elif 语句

```python
a = 4
if a > 5:
    print('a > 5')
elif a > 0:
    print('a > 0')
else:
    print('a < 0')
>>>
a > 0
```

### 循环结构

> while 语句
> - 循环执行， 知道条件不满足，退出循环

```python
a = 4
while a > 0:
    print(a)
    a -= 1
>>>
4
3
2
1
```

> for 语句
> 遍历某个可迭代对象的所有元素，循环体不应该修改迭代器

```python
for item in iterator:
    block
```


### range 函数
> range 函数产生一个生成器，通常用于控制循环次数


* 对于python3， python2 返回的是一个list， 如果range函数的取值很大，会对内存造成很大影响

```python 
In [6]: sys.version
Out[6]: '2.7.13 (default, Apr 20 2017, 15:32:43) \n[GCC 4.2.1 Compatible Apple LLVM 8.1.0 (clang-802.0.38)]'

In [7]: range(10)
Out[7]: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

---

In [2]: sys.version
Out[2]: '3.5.3 (default, Apr 20 2017, 15:39:30) \n[GCC 4.2.1 Compatible Apple LLVM 8.1.0 (clang-802.0.38)]'

In [3]: range(10)
Out[3]: range(0, 10)
```

* range函数和list方法

```python
In [4]: list(range(0, 10))
Out[4]: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

In [5]: list(range(0, 10, 2))
Out[5]: [0, 2, 4, 6, 8]

In [6]: list(range(10, 0))
Out[6]: []

In [7]: list(range(0, 10, -1))
Out[7]: []
```

### break 语句
> 跳出当前循环

```python
for x in range(3):
    print(x)
    for i in range(5):
        print('\t %d' % i)
        if i > 2:
            break
>>>
0
	 0
	 1
	 2
	 3
1
	 0
	 1
	 2
	 3
2
	 0
	 1
	 2
	 3
```

### continue 子句
> 只能出现在循环结构中
> 用于跳过此次迭代对剩余操作

```python
for x in range(10):
    if x % 2 == 0:
        continue
    print(x)
>>>
1
3
5
7
9
```

### else 子句

> 循环结构的else子句是Python特有的，用于表示一个循环是未经break子句跳出

```python
for x in range(10):
    if x > 1:
        break
    print(x)
else:
    print('###')
>>>
0
1
```

```python
for x in range(0, 10, 2):
    if x % 2 != 0:
        break
else:
    print('OK')
>>>
OK
```



## 内置容器


### 列表
> list 是最常用的线性数据结构
> list是一系列元素的有序组合
> list是可变的

#### 定义列表

```python
In [1]: L = []

In [2]: L = list()

In [3]: L = [1, 2, 3]
```

#### 增
* append 
```python
In [4]: L 
Out[4]: [1, 2, 3]

In [5]: L.append(4)

In [6]: L
Out[6]: [1, 2, 3, 4]
```

* extend 
```python
In [9]: L = [1, 2, 3, 4]

In [10]: L.extend([5, 6, 7])

In [11]: L
Out[11]: [1, 2, 3, 4, 5, 6, 7]
```


* insert
```python
In [11]: L
Out[11]: [1, 2, 3, 4, 5, 6, 7]

In [12]: L.insert(0, 0)

In [13]: L
Out[13]: [0, 1, 2, 3, 4, 5, 6, 7]
```

#### 删
* remove
```python
In [15]: L
Out[15]: [0, 1, 2, 3, 4, 5, 6, 7]

In [16]: L.remove(3)

In [17]: L
Out[17]: [0, 1, 2, 4, 5, 6, 7]
```

* pop
```python
In [18]: L
Out[18]: [0, 1, 2, 4, 5, 6, 7]

In [19]: L.pop(0)
Out[19]: 0

In [20]: L
Out[20]: [1, 2, 4, 5, 6, 7]
```

* clear
```python
In [21]: L
Out[21]: [1, 2, 4, 5, 6, 7]

In [22]: L.clear()

In [23]: L
Out[23]: []
```

#### 改

* reverse
```python
In [26]: L
Out[26]: [0, 1, 2, 3, 4, 3, 4, 5, 6, 7]

In [27]: L.reverse()

In [28]: L
Out[28]: [7, 6, 5, 4, 3, 4, 3, 2, 1, 0]
```

* sort
```python
In [28]: L
Out[28]: [7, 6, 5, 4, 3, 4, 3, 2, 1, 0]

In [29]: L.sort()

In [30]: L
Out[30]: [0, 1, 2, 3, 3, 4, 4, 5, 6, 7]

In [30]: L
Out[30]: [0, 1, 2, 3, 3, 4, 4, 5, 6, 7]

In [31]: L.sort(reverse=True)

In [32]: L
Out[32]: [7, 6, 5, 4, 4, 3, 3, 2, 1, 0]
```

* 







