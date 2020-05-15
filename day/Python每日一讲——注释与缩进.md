# Python每日一讲——注释与缩进

## 注释

### **Python中的注释有单行注释和多行注释：**

* python中单行注释采用 # 开头。

```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-
# 文件名：test.py

# 第一个注释
print("Hello, Python!")  # 第二个注释
```

输出结果：

输出结果：

```
Hello, Python!
```

注释可以在语句或表达式行末：

```python
name = "Madisetti" # 这是一个注释
```

- python 中多行注释使用三个单引号(''')或三个双引号(""")。

```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-
# 文件名：test.py

'''
这是多行注释，使用单引号。
这是多行注释，使用单引号。
这是多行注释，使用单引号。
'''

"""
这是多行注释，使用双引号。
这是多行注释，使用双引号。
这是多行注释，使用双引号。
"""
```

![wps11](C:\Users\hq0749a\Desktop\learningplanv2.0\img\wps11.jpg)

## 缩进

- python最具特色的就是使用缩进来表示代码块，不需要使用大括号({})。
- 缩进的空格数是可变的，但是同一个代码块的语句必须包含相同的缩进空格数。
- 缩进强迫大家写出格式化的代码 
- 当语句以’:’结尾时，缩进的语句视为代码块 
- 约定俗成管理，4个空格为一个缩进 
- Python大小写敏感 

实例如下：

```
if True:
    print("True")
else:
    print("False")
```

- 以下代码最后一行语句缩进数的空格数不一致，会导致运行错误：

```
if True:
    print("Answer")
    print("True")
else:
    print("Answer")
  print("False")    # 缩进不一致，会导致运行错误
```

- 以上程序由于缩进不一致，执行后会出现类似以下错误：

```
 File "test.py", line 6
    print("False")    # 缩进不一致，会导致运行错误
                                      ^
IndentationError: unindent does not match any outer indentation level
```

### 多行语句

- Python 通常是一行写完一条语句，但如果语句很长，我们可以使用反斜杠()来实现多行语句，例如：

```
total = item_one + \
        item_two + \
        item_three
```

- 在 [], {}, 或 () 中的多行语句，不需要使用反斜杠()，例如：

```
total = ['item_one', 'item_two', 'item_three',
        'item_four', 'item_five']
```

### 空行

- 函数之间或类的方法之间用空行分隔，表示一段新的代码的开始。类和函数入口之间也用一行空行分隔，以突出函数入口的开始。
- 空行与代码缩进不同，空行并不是Python语法的一部分。书写时不插入空行，Python解释器运行也不会出错。但是空行的作用在于分隔两段不同功能或含义的代码，便于日后代码的维护或重构。
- 记住：空行也是程序代码的一部分。