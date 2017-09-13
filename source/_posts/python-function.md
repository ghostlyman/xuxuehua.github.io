---
title: python-function
date: 2017-09-05 23:28:56
tags:
---



[toc]

# 函数

## 函数特点

> 函数是组织好的，可重复使用，实现单一功能的代码段
> 函数有输入（参数）和输出（返回值）
> Python中，函数是一等对象

### 函数定义 

```python
def fn():
    pass
```

### 函数参数

> 非默认非可变参数，可变位置参数，可变关键字参数
> 默认参数不要和可变参数放在一起


```python
def add(x, y):
    return x + y

print(add(3, 4))
>>>
7
```

* 参数引用 (在函数体内赋值，不会影响外部变量)

```python
x = 1
y = 2

def swap(x, y):
    x, y = y, x

swap(x, y)
print(x, y)
>>>
1 2
```

* 直传递

```python
L = [1, 2, 3]

def append(item):
    L.append(item)

append(4)
print(L)
>>>
[1, 2, 3, 4]
```

#### 位置参数 

> 位置参数，通过参数传递的位置来决定

```python
def add(x, y):
    print('x = {0}'.format(x))
    print('y = {0}'.format(y))
    return x + y

print(add(1, 2))
>>>
x = 1
y = 2
3
```

#### 关键字参数

> 关键字参数，通过参数名称来决定

```python
def add(x, y):
    print('x = {0}'.format(x))
    print('y = {0}'.format(y))
    return x + y

print(add(y=2, x=1))
>>>
x = 1
y = 2
3
```

#### 位置，关键字参数混合使用

* 位置参数和关键字参数是在调用的时候决定的

```python
def add(x, y):
    print('x = {0}'.format(x))
    print('y = {0}'.format(y))
    return x + y

print(add(1, y=2))
>>>
x = 1
y = 2
3
```

* 关键字参数必须在位置参数之后

```python
def add(x, y):
    print('x = {0}'.format(x))
    print('y = {0}'.format(y))
    return x + y

print(add(x=1, 2))
>>>
  File "/Users/xhxu/python/python3/test/1.py", line 6
    print(add(x=1, 2))
                  ^
SyntaxError: positional argument follows keyword argument
```

#### 默认参数

* 默认的参数可以被覆盖掉

```python
def inc(x, i=1):
    return x + i

print(inc(5))
print(inc(5, 2))
>>>
6
7
```

#### 可变参数 (可变位置参数)

> 函数定义时，参数名前加\*代表次参数是可变的位置参数
> 函数调用是，参数列表封装成一个元组传递给args

* 使用列表的调用方法

```python
def sum(L):
    ret = 0
    for x in L:
        ret += x
    return ret

print(sum([1, 2, 3, 4, 5]))
>>>
15
```

* 使用可变参数的调用方法 (调用参数的时候，自动组装成元组)

```python
def sum(*args):
    ret = 0
    for x in args:
        ret += x
    return ret

print(sum(1, 2, 3, 4, 5))
>>>
16
```

#### 关键字参数 (可变关键字参数)

* 使用可变关键字参数  (调用参数的时候，自动组装成字典)

```python
def print_info(**kwargs):
    for k, v in kwargs.items():
        print('{0} -> {1}'.format(k, v))

print(print_info(a=1, b=2))
>>>
b -> 2
a -> 1
```

* 调用的时候, 会决定参数是位置参数还是关键字参数

```python
def print_info(**kwargs):
    for k, v in kwargs.items():
        print('{0} -> {1}'.format(k, v))

print_info(1, 2, 3)
>>>
  File "/Users/xhxu/python/python3/test/1.py", line 5, in <module>
    print_info(1, 2, 3)
TypeError: print_info() takes 0 positional arguments but 3 were given
```

#### 可变参数和关键字参数混合使用

```python
def print_info(*args, **kwargs):
    for x in args:
        print(x)
    for k, v in kwargs.items():
        print('{0} -> {1}'.format(k, v))

print_info(1, 2, 3, a=4, b=5)
>>>
1
2
3
a -> 4
b -> 5
```

#### 可变参数和非可变参数

```python
def print_info(x, y, *args, **kwargs):
    print('x = {0}'.format(x))
    print('y = {0}'.format(y))
    for x in args:
        print(x)
    for k, v in kwargs.items():
        print('{0} -> {1}'.format(k, v))

print_info(1, 2, 3, 4, 5, 6, a=7, b=8)
>>>
x = 1
y = 2
3
4
5
6
b -> 8
a -> 7
```

### 参数解包

#### 位置参数解包

```python
def add(x, y):
    print('x = {0}'.format(x))
    print('y = {0}'.format(y))
    return x + y

L = [1, 2]
print(add(*L))
>>>
x = 1
y = 2
3
```

#### 关键字参数解包

```python
def add(x, y):
    print('x = {0}'.format(x))
    print('y = {0}'.format(y))
    return x + y

d = {'x': 1, 'y': 2}
print(add(**d))
>>>
x = 1
y = 2
3
```


## 高阶函数

> 将另一个函数作为变量传递进来


```python
def sort(cmp, *args):
    ret = []
    for item in args:
        for i, v in enumerate(ret):
            if cmp(item, v):
                ret.insert(i, item)
                break
        else:
            ret.append(item)
    return ret

def cmp1(x, y):
    return x >= y

def cmp2(x, y):
    return x <= y

print(sort(cmp1, 3, 2, 1, 5))
print(sort(cmp2, 3, 1, 2, 5))
>>>
[5, 3, 2, 1]
[1, 2, 3, 5]
```

```python
def left_fold(fn, *args):
    it = iter(args)
    ret = next(it)
    for x in it:
        ret = fn(ret, x)
    return ret

def add(x, y):
    return x + y

print(left_fold(add, 1, 2, 3, 4))
>>>
10
```

### filter 高阶函数

```python
def bigger(x):
    if x > 5:
        return True
    return False

print(list(filter(bigger, range(10))))
>>>
[6, 7, 8, 9]
```

### map 高阶函数

```python
def inc(x):
    return x + 1

print(list(map(inc, [1, 2, 3, 4])))
>>>
[2, 3, 4, 5]
```

### 函数作为返回值

```python
def make_inc(f=1):
    print(f)
    def inc(x):
        return x + f
    return inc

inc1 = make_inc(1)
print(inc1(5))
inc2 = make_inc(2)
print(inc2(5))
>>>
6
7
```







## 生成器

> 最主要作用是交替执行，保存现场
> yield 可以实现协程（即在用户空间协作完成，无需进入内核空间）
> yield 可以暂停当前现场


### 生成器是可以迭代的

> 每个函数的生命周期是从被调用开始，到返回结束,下一次再进入此函数就得重新开始。但一添加yield就并非如此了，每次遇到yield，它会返回一个值给调用者，而后当前函数就暂停了(而非退出)，接着把控制权交还给调用者。
> yield就相当于return，只不过，return而结束当前函数，但yield会暂停，即保存现场。于是，下一次调用这个函数，是从上一次保存的状态继续进行，而非从头。


```python
def iterator(x):
    i=0
    while i < 5:
       yield i
       i += 1

print(iterator(5))

for i in iterator(5):
    print(i)
>>>
<generator object iterator at 0x1029f0d58>
0
1
2
3
4
```

```python
def iterator(x):
    i=0
    while i < 5:
        yield i
        i += 1
   
def main(): 
    for i in iterator(5):
        print(i)

main()
>>>
0
1
2
3
4
```


```python
def iterator():
    L = [1, 2, 3, 4, 5]
    yield from L

for x in iterator():
    print(x)
>>>
1
2
3
4
5
```

* 求积数

```python
def fn(x):
    ret = 1
    for i in range(1, x+1):
        ret *= i
        yield ret

for x in fn(5):
    print(x)
>>>
1
2
6
24
120
```



