---
title: python container
date: 2017-08-17 01:33:43
tags:
---
[toc]


# 内置容器 (python-container)


## 列表
> list 是最常用的线性数据结构
> list是一系列元素的有序组合
> list是可变的

### 定义列表

```python
In [1]: L = []

In [2]: L = list()

In [3]: L = [1, 2, 3]
```

### 列表常用操作

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

#### 查

* count 

```python
In [3]: L
Out[3]: [0, 1, 2, 3, 3, 4, 4, 5, 6, 7]

In [4]: L.count(3)
Out[4]: 2

In [5]: L.count(8)
Out[5]: 0
```

* index

```python
In [6]: L
Out[6]: [0, 1, 2, 3, 3, 4, 4, 5, 6, 7]

In [7]: L.index(3)
Out[7]: 3

In [8]: L.index(4)
Out[8]: 5

In [9]: L.index(8)
---------------------------------------------------------------------------
ValueError                                Traceback (most recent call last)
<ipython-input-9-4d02a661bd55> in <module>()
----> 1 L.index(8)

ValueError: 8 is not in list

```

#### 其他

* copy

```python
In [17]: L
Out[17]: [0, 1, 2, 3, 3, 4, 4, 5, 6, 7]

In [18]: L1 = L.copy()

In [19]: L2 = L

In [20]: L
Out[20]: [0, 1, 2, 3, 3, 4, 4, 5, 6, 7]

In [21]: L1
Out[21]: [0, 1, 2, 3, 3, 4, 4, 5, 6, 7]

In [22]: L2
Out[22]: [0, 1, 2, 3, 3, 4, 4, 5, 6, 7]

In [23]: id(L)
Out[23]: 4437057032

In [24]: id(L1)
Out[24]: 4436948744

In [25]: id(L2)
Out[25]: 4437057032
```


#### 下标操作及切片

```python
In [29]: L
Out[29]: [0, 1, 2, 3, 3, 4, 4, 5, 6, 7]

In [30]: L[0] = 10

In [31]: L
Out[31]: [10, 1, 2, 3, 3, 4, 4, 5, 6, 7]

In [32]: L[3:5]
Out[32]: [3, 3]

In [33]: L[:5]
Out[33]: [10, 1, 2, 3, 3]

In [34]: L[3:]
Out[34]: [3, 3, 4, 4, 5, 6, 7]

In [35]: L[:]
Out[35]: [10, 1, 2, 3, 3, 4, 4, 5, 6, 7]

In [36]: L[3: -2]
Out[36]: [3, 3, 4, 4, 5]

In [37]: L[-4:-1]
Out[37]: [4, 5, 6]

In [38]: L[2:6:2]
Out[38]: [2, 3]

In [39]: L[6:2:-1]
Out[39]: [4, 4, 3, 3]

In [40]: L[::-1]
Out[40]: [7, 6, 5, 4, 4, 3, 3, 2, 1, 10]

In [41]: L[::2]
Out[41]: [10, 2, 3, 4, 6]
```




## 元组

> 元组是不可变的结构
> 元组和列表的大多数地方相似

### 定义元组

```python
In [26]: T = ()

In [27]: T = tuple()

In [28]: T = (1, 2, 3)
```

### 元组常用操作

#### 查

* count


* index


#### 下标操作及切片


#### Packing & Unpacking


```python
In [42]: x, y = (1, 2)

In [43]: x
Out[43]: 1

In [44]: y
Out[44]: 2

In [45]: x, *y = (1, 2, 3, 4)

In [46]: x
Out[46]: 1

In [48]: y
Out[48]: [2, 3, 4]

In [49]: x, *_, y = (1, 2, 3, 4)

In [50]: x
Out[50]: 1

In [51]: y
Out[51]: 4

In [52]: _
Out[52]: [2, 3]

In [53]: x, (y, z) = (1, (2, 3))

In [54]: x
Out[54]: 1

In [55]: y
Out[55]: 2

In [56]: z
Out[56]: 3
In [68]: x = 1

In [69]: y = 2

In [70]: x, y = y, x

In [71]: x
Out[71]: 2

In [72]: y
Out[72]: 1
```

## 集合

> 集合的含义和数学上的含义相同
> 集合不是线性的
> 集合的元素是唯一的
> 集合的元素是可以hash 的


### 定义集合

```python
In [73]: s = set()

In [74]: s = set({1, 2, 3})

In [75]: s
Out[75]: {1, 2, 3}
```

### 集合常用操作

#### 增

* add

```python
In [76]: s
Out[76]: {1, 2, 3}

In [77]: s.add(4)

In [78]: s
Out[78]: {1, 2, 3, 4}

In [79]: s.add(3)
```

* update

```python
In [80]: s
Out[80]: {1, 2, 3, 4}

In [81]: s.update([3, 4, 5, 6])

In [82]: s
Out[82]: {1, 2, 3, 4, 5, 6}
```

#### 删

* remove 

```python
In [84]: s
Out[84]: {1, 2, 3, 4, 5, 6}

In [85]: s.remove(1)

In [86]: s
Out[86]: {2, 3, 4, 5, 6}

In [87]: s.remove(10)
---------------------------------------------------------------------------
KeyError                                  Traceback (most recent call last)
<ipython-input-87-99f2b84d3df8> in <module>()
----> 1 s.remove(10)

KeyError: 10
```



* discard

```python
In [88]: s
Out[88]: {2, 3, 4, 5, 6}

In [89]: s.discard(3)

In [90]: s
Out[90]: {2, 4, 5, 6}

In [91]: s.discard(10)

In [92]: s
Out[92]: {2, 4, 5, 6}
```


* clear

```python
In [99]: s
Out[99]: {1, 2, 3, 4, 5, 6}

In [100]: s.clear()

In [101]: s
Out[101]: set()
```

* pop

```python
In [1]: s = set({1, 2, 3})

In [2]: s.pop()
Out[2]: 1

In [3]: s
Out[3]: {2, 3}
```


#### 集合运算

* union 

```python
In [1]: s1 = set({1, 2, 3})

In [2]: s1
Out[2]: {1, 2, 3}

In [3]: s2 = set({2, 3, 4})

In [4]: s2
Out[4]: {2, 3, 4}

In [5]: s1.union(s2)
Out[5]: {1, 2, 3, 4}

```

* intersection

```python
In [6]: s1
Out[6]: {1, 2, 3}

In [7]: s2
Out[7]: {2, 3, 4}

In [8]: s1.intersection(s2)
Out[8]: {2, 3}
```

* difference

```python
In [9]: s1
Out[9]: {1, 2, 3}

In [10]: s2
Out[10]: {2, 3, 4}

In [11]: s1.difference(s2)
Out[11]: {1}

In [15]: s2.difference(s1)
Out[15]: {4}
```


* symmetric_difference

```python
In [12]: s1
Out[12]: {1, 2, 3}

In [13]: s2
Out[13]: {2, 3, 4}

In [14]: s1.symmetric_difference(s2)
Out[14]: {1, 4}

In [16]: s2.symmetric_difference(s1)
Out[16]: {1, 4}
```


#### 集合判断

* issubset

```python
In [20]: s
Out[20]: {4, 5, 6}

In [21]: s.issubset({3, 4, 5, 6})
Out[21]: True
```


* issuperset

```python
In [22]: {0, 1, 2}.issuperset([1])
Out[22]: True

In [23]: {0, 1, 2}.issuperset([0, 1])
Out[23]: True

In [24]: {0, 1, 2}.issuperset([2, 3])
Out[24]: False

In [25]: {0, 1, 2}.issuperset(())

Out[25]: True
```

* isdisjoint

```python
In [2]: {0, 1, 2}.isdisjoint([1])
Out[2]: False

In [3]: {0, 1, 2}.isdisjoint([0, 1])
Out[3]: False

In [4]: {0, 1, 2}.isdisjoint([3, 4])
Out[4]: True

In [5]: {0, 1, 2}.isdisjoint(())
Out[5]: True
```


## 字典

> 字典是一种无序集合
> 字典是一种kv结构
> value 可以是任何对象
> key是唯一的
> key必须是可hash 对象


### 定义字典

```python
In [26]: d = {}

In [27]: d = dict()

In [28]: d = {'a':1, 'b':2}
```



### 字典的常用操作


#### key访问

```python
In [29]: d
Out[29]: {'a': 1, 'b': 2}

In [30]: d['a'] = 5

In [31]: d
Out[31]: {'a': 5, 'b': 2}

In [32]: d['c']
---------------------------------------------------------------------------
KeyError                                  Traceback (most recent call last)
<ipython-input-32-3e4d85f12902> in <module>()
----> 1 d['c']

KeyError: 'c'

In [2]: d.get('a')
Out[2]: 1

In [3]: d.get('c', 'cannot found c')
Out[3]: 'cannot found c'
```

#### keys, values, items 遍历字典

```python
In [33]: d
Out[33]: {'a': 5, 'b': 2}

In [34]: d.keys()
Out[34]: dict_keys(['a', 'b'])

In [35]: d.values()
Out[35]: dict_values([5, 2])

In [36]: d.items()
Out[36]: dict_items([('a', 5), ('b', 2)])
```


#### 删除元素

* pop

```python
In [37]: d
Out[37]: {'a': 5, 'b': 2}

In [38]: d.pop('a')
Out[38]: 5

In [39]: d
Out[39]: {'b': 2}

In [40]: d.pop('c')
---------------------------------------------------------------------------
KeyError                                  Traceback (most recent call last)
<ipython-input-40-adf338c8a0db> in <module>()
----> 1 d.pop('c')

KeyError: 'c'

In [41]: d.pop('c', True)
Out[41]: True
```


* popitem 随机删除

```python
In [44]: d
Out[44]: {'a': 1, 'b': 2}

In [45]: d.popitem()
Out[45]: ('a', 1)

In [46]: d.popitem()
Out[46]: ('b', 2)

In [47]: d
Out[47]: {}
```

* del 关键字

```python
In [4]: d
Out[4]: {'a': 1, 'b': 2}

In [5]: del d['a']

In [6]: d
Out[6]: {'b': 2}
```


