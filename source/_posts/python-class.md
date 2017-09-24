---
title: python class
date: 2017-09-25 00:27:19
tags:
---




[TOC]

# 面向对象

> 编程范式指软件工程中的一种方法学
> 常见的编程范式： OOP， FP， PP， IP
> 通常没中语言都会提倡一些范式，也有语言支持多种范式
> python是一种多范式到语言，但对OOP支持最好

## OOP (Object Oriented Programming) 基本哲学

> 世界是由对象组成的
> 对象具有运动规律和内部状态
> 对象之间的相互作用和通讯构成世界


### 对象的特性

> 唯一性： 世界上没有两片相同的树叶（每个对象都有自己唯一的内存）
> 分类性： 分类是对现实世界的抽象


### OOP的三大特征

> 继承
> 多态： 相同的操作在不同的对象表现不同
> 封装

### 面向对象的本质

> 面向对象是对数据和行为的封装
> 但有时候，数据仅仅是数据，方法仅仅是方法

### 数据及行为封装

```python
class Door():
    def __init__(self, number, status):
        self.number = number
        self.status = status
        
    def open(self):
        self.status = 'opening'
        
    def close(self):
        self.status = 'closed'
        
door1 = Door(1, 'closed')
```



## 类的定义

```python
class ClassName:
    pass

# 等价于

class ClassName(object):
    pass
```

## 方法定义 

```python
class ClassName:
    def method_name(self):
        pass
```

### 构造方法

```python
class ClassName:
    def __init__(self):
        pass
```

## 实例化

* init 只是初始化类变量的作用

```python
class A:
    def __init__(self, x):
        self.x = x

# 实例化
a = A(5)

# 绑定实力变量
print(a.x)
>>>
5
```

### 实例类型

```python
class A:
    # 通常不建议使用并修改(高手另说)
    def __new__(cls, *args, **kwargs):
        print('call __new__')
        print(type(cls))
        return object.__new__(cls)

    def __init__(self, x):
        print('call __init__')
        # self 是实例本身
        print(type(self))
        self.x = x

a = A(5)
>>>
call __new__
<class 'type'>
call __init__
<class '__main__.A'>
```

#### 传入位置参数

```python
class A:
    def __init__(self, x=5):
        #这里不由形式参数x决定，由abcd决定
        self.abcd = x

a1 = A(5)
a2 = A()
a3 = A(8)
print(a1.abcd)
print(a2.abcd)
print(a3.abcd)
>>>
5
5
8
```


## 封装

* 封装只能在类的内部访问

```python
class A:
    def __init__(self, x):
        self.__value = x

    def __add(self):
        self.__value += i

    def get_value(self):
        return self.__value

    def __increase(self):
        self.__add(1)

a = A(5)
print(a.get_value())
print(a.__value)
>>>
5
Traceback (most recent call last):
  File "/Users/xhxu/python/python3/test/3.py", line 17, in <module>
    print(a.__value)
AttributeError: 'A' object has no attribute '__value'
```



### 访问控制

```python

```


### 类变量

* 类变量对所有的实例都是可见的，可以共享，且初值都是一样的

```python
class A:
    val = 3
    def __init__(self, x):
        self.x = 3

a1 = A(5)
print(a1.val)

a2 = A(9)
print(a2.val)

a1.val += 1
print(a1.val)
>>>
3
3
4
```

#### 私有类变量

* 私有类变量不能被实例访问

```python
class A:
    __value = 3
    def get_value(self):
        return self.__value

a = A()
print(a.get_value())
print(a.__value)
>>>
Traceback (most recent call last):
3
  File "/Users/xhxu/python/python3/test/3.py", line 8, in <module>
    print(a.__value)
AttributeError: 'A' object has no attribute '__value'
```


### 类方法

* 类方法传递类本身， 可以访问私有的类变量

```python
class A:
    __val = 3

    @classmethod
    def get_val(cls):
        return cls.__val

a = A()

print(a.get_val())
print(A.get_val())
>>>
3
3
```

#### 静态方法

* 不可以访问私有变量

```python
class A:
    __value = 3

    @staticmethod
    def print_value():
        print(__value)

a = A()

print(a.print_value())
print(A.print_value())
>>>
Traceback (most recent call last):
  File "/Users/xhxu/python/python3/test/3.py", line 10, in <module>
    print(a.print_value())
  File "/Users/xhxu/python/python3/test/3.py", line 6, in print_value
    print(__value)
NameError: name '_A__value' is not defined
```



