### 定义变量

在 Python 中，定义变量只需要赋值操作。语法是 ​**​`变量名 = 值`​**​  
无需像JavaScript一样使用let、var、const 关键字来定义变量

```Python
x = 10  # 整数
y = 3.14  # 浮动小数
name = "Alice"  # 字符串
is_active = True  # 布尔值
```

### 使用变量

和其他语言一样，没差

```Python
x, y = 1, 4
x = x + 5
y = x + y
xy = x + y
print(xy)
```

### 动态类型

Python 是动态类型的语言，这意味着你不需要声明变量的类型，Python 会自动根据你赋给变量的值来推断其类型。

```Python
x = 10  # x 是整数
print(x)
x = "Hello"  # 现在 x 变成字符串
print(x)  # 输出 "Hello"
```

### 常量变量

在Python中，没有原生的常量类型，所有的变量都是可以修改的。  
Python的常规约定是使用全大写字母来表示常量，以此告诉开发者这个变量的值应该保持不变。

```Python
PI = 3.14159
MAX_SIZE = 100
```

### 删除变量

在 Python 中，使用 del 关键字可以删除变量。  
使用del删除变量后，变量将无法再访问。

```Python
temp = "临时变量"
print(f"删除前: {temp}")
del temp
# print(temp)  # 错误：变量已被删除 
```

### 多变量赋值

Python支持同时给多个变量赋值，这被称为多变量赋值。  
可以使用逗号分隔的变量列表和值列表来实现。

```Python
x, y, z = 1, 2, 3
print(f"多变量赋值: x={x}, y={y}, z={z}")
```

### 链式赋值

可以将同一个值同时赋给多个变量。

```Python
a = b = c = 10
print(f"链式赋值: a={a}, b={b}, c={c}")
```

### 变量命名规则

Python变量命名需要遵循以下规则：

1. 变量名只能包含字母、数字和下划线
2. 变量名不能以数字开头
3. 变量名不能是Python关键字
4. 变量名区分大小写

```Python
my_variable = "合法"  # 下划线命名法
myVariable = "驼峰命名"  # 驼峰命名法
MY_CONSTANT = "常量"  # 常量命名（全大写）
_variable = "下划线开头"  # 私有变量（约定）
```

### 变量作用域

Python中的变量作用域分为：

1. 局部作用域（Local）：在函数内部定义的变量
2. 嵌套作用域（Enclosing）：在嵌套函数中定义的变量
3. 全局作用域（Global）：在模块级别定义的变量
4. 内置作用域（Built-in）：Python内置的变量

```Python
global_var = "全局变量"  # 全局变量

def inner_function():
    nonlocal_var = "嵌套作用域变量"  # 嵌套作用域变量
    local_var = "局部变量"  # 局部变量
    print(f"内部函数访问: {global_var}")
    print(f"内部函数访问: {nonlocal_var}")
    print(f"内部函数访问: {local_var}")

inner_function()
# print(local_var)  # 错误：无法访问局部变量
```

### 全局变量和局部变量

在函数内部修改全局变量需要使用global关键字

```Python
global_var = "原始全局变量"

def modify_global():
    global global_var  # 声明使用全局变量
    global_var = "修改后的全局变量"

print(f"修改前: {global_var}")
modify_global()
print(f"修改后: {global_var}")
```

### 变量的引用和复制

Python中的变量赋值实际上是创建了一个引用，而不是复制值  
对于可变对象（如列表、字典等），修改一个变量会影响另一个变量  
对于不可变对象（如数字、字符串等），修改会创建新的对象

```Python
# 可变对象的引用
list1 = [1, 2, 3]
list2 = list1  # list2是list1的引用
list2.append(4)
print(f"list1: {list1}")  # [1, 2, 3, 4]
print(f"list2: {list2}")  # [1, 2, 3, 4]

# 创建真正的副本
list3 = list1.copy()  # 或者 list3 = list1[:]
list3.append(5)
print(f"list1: {list1}")  # [1, 2, 3, 4]
print(f"list3: {list3}")  # [1, 2, 3, 4, 5]

# 不可变对象的引用
a = 10
b = a
b = 20
print(f"a: {a}")  # 10
print(f"b: {b}")  # 20
```