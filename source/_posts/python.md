# Python 基础语法

---

## Hello World

```ipython
In [2]: print('Hello World')
Hello World
```

---

## 变量 

> 即解释器中的一段内存引用
> Python 中，变量都是引用

---

## 数据类型

* Python 是强类型的动态语言
* 数据类型是对用来约束数据
* 原始类型和复合类型

### 强类型
```ipython
In [3]: 1 + 'abc'
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-3-aab9e8ede4f7> in <module>()
----> 1 1 + 'abc'

TypeError: unsupported operand type(s) for +: 'int' and 'str'
```

### 弱类型
```javascript
1 + "abc"
"1abc"
```

### 原始类型
* int,  fload, byte

### 复合类型
> 由其他原始类型组合起来的类型

* list, dict 


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


### 表达式
* a and (1+2) < 3
* a if a > 0 else 0 

### 表达式与优先级
* 一元高于二元
* 数值高于逻辑
* 算术高于位运算
* 乘除高于加减
* 拿不准加括号解决

