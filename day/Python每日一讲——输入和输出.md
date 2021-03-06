# Python每日一讲——输入和输出

## input()输入

- input()的小括号中放入的是，提示信息，用来在获取数据之前给用户的一个简单提示
- input()在从键盘获取了数据以后，会存放到等号右边的变量中
- input()会把用户输入的任何值都作为字符串来对待
- 注意：在python2中还有一个raw_input()输入，但到python3中没有了

```
#!/usr/bin/python3

str = input("请输入：");
print("你输入的内容是: ", str)
```

- 这会产生如下的对应着输入的结果：

```
请输入：Hello Python!
你输入的内容是:  Hello Python!
```

## Print()输出：

- print 默认输出是换行的，如果要实现不换行需要在变量末尾加上 end=""：

```python
#!/usr/bin/python3

x = "a"
y = "b"
# 换行输出
print(x)
print(y)

print('---------')
# 不换行输出
print(x, end=" ")
print(y, end=" ")
print()

# 同时输出多个变量
print(x, y)
```

 ## 扩展——格式化输出

什么叫格式化输出？
数据按照某种特殊的要求输出

假如输入一个整数，希望整数按照十六进制，八进制输出，如果输入一个小数，希望小数保留后面2位数然后输出，或者以科学计数法的方式来输出小数。字符串的输出希望在十个格子内输出，或者左对齐，居中等等

说白了，就是为了显示的更美观，更方便看

### **基本格式化输出：%**

如下实例：

```python
print "My name is %s and weight is %d kg!" % ('Zara', 21) 

输出结果为
My name is Zara and weight is 21 kg!
```

### python 字符串格式化符号:

| %c   | 格式化字符及其ASCII码                |
| ---- | ------------------------------------ |
| %s   | 格式化字符串                         |
| %d   | 格式化整数                           |
| %u   | 格式化无符号整型                     |
| %o   | 格式化无符号八进制数                 |
| %x   | 格式化无符号十六进制数               |
| %X   | 格式化无符号十六进制数（大写）       |
| %f   | 格式化浮点数字，可指定小数点后的精度 |
| %e   | 用科学计数法格式化浮点数             |
| %E   | 作用同%e，用科学计数法格式化浮点数   |
| %g   | %f和%e的简写                         |
| %G   | %F 和 %E 的简写                      |
| %p   | 用十六进制数格式化变量的地址         |

### 格式化操作符辅助指令:

| *     | 定义宽度或者小数点精度                                       |
| ----- | ------------------------------------------------------------ |
| -     | 用做左对齐                                                   |
| +     | 在正数前面显示加号( + )                                      |
| <sp>  | 在正数前面显示空格                                           |
| #     | 在八进制数前面显示零('0')，在十六进制前面显示'0x'或者'0X'(取决于用的是'x'还是'X') |
| 0     | 显示的数字前面填充'0'而不是默认的空格                        |
| %     | '%%'输出一个单一的'%'                                        |
| (var) | 映射变量(字典参数)                                           |
| m.n.  | m 是显示的最小总宽度,n 是小数点后的位数(如果可用的话)        |

- 格式化字符串的函数 str.format()，它增强了字符串格式化的功能。
- 基本语法是通过 {} 和 : 来代替以前的 % 。

```
>>>"{} {}".format("hello", "world")    # 不设置指定位置，按默认顺序
'hello world'

>>> "{0} {1}".format("hello", "world")  # 设置指定位置
'hello world'

>>> "{1} {0} {1}".format("hello", "world")  # 设置指定位置
'world hello world'

>>> print("网站名：{name}, 地址 {url}".format(name="百度", url="www.baidu.com")) #指定参数名
'网站名：百度, 地址 www.baidu.com'


>>>site = {"name": "百度", "url": "www.baidu.com"}
>>>print("网站名：{name}, 地址 {url}".format(**site)) # 通过字典设置参数
'网站名：百度, 地址 www.baidu.com' 

>>>my_list = ['百度', 'www.baidu.com']
>>>print("网站名：{0[0]}, 地址 {0[1]}".format(my_list))  # "0" 是必须的 通过列表索引设置参数
'网站名：百度, 地址 www.baidu.com'

>>> print("{:.2f}".format(3.1415926)); #数字格式化
3.14
```

| 数字       |                             格式                             | 输出                 | 描述                         |
| :--------- | :----------------------------------------------------------: | -------------------- | ---------------------------- |
| 3.1415926  |                            {:.2f}                            | 3.14                 | 保留小数点后两位             |
| 3.1415926  |                           {:+.2f}                            | +3.14                | 带符号保留小数点后两位       |
| -1         |                           {:+.2f}                            | -1.00                | 带符号保留小数点后两位       |
| 2.71828    |                            {:.0f}                            | 3                    | 不带小数                     |
| 5          |                           {:0>2d}                            | 05                   | 数字补零 (填充左边, 宽度为2) |
| 5          |                           {:x<4d}                            | 5xxx                 | 数字补x (填充右边, 宽度为4)  |
| 10         |                           {:x<4d}                            | 10xx                 | 数字补x (填充右边, 宽度为4)  |
| 1000000    |                             {:,}                             | 1,000,000            | 以逗号分隔的数字格式         |
| 0.25       |                            {:.2%}                            | 25.00%               | 百分比格式                   |
| 1000000000 |                            {:.2e}                            | 1.00e+09             | 指数记法                     |
| 13         |                            {:10d}                            | 13                   | 右对齐 (默认, 宽度为10)      |
| 13         |                           {:<10d}                            | 13                   | 左对齐 (宽度为10)            |
| 13         |                           {:^10d}                            | 13                   | 中间对齐 (宽度为10)          |
| 11         | '{:b}'.format(11) '{:d}'.format(11) '{:o}'.format(11) '{:x}'.format(11) '{:#x}'.format(11) '{:#X}'.format(11) | 1011 11 13 b 0xb 0XB | 进制                         |

### Python3.6.x新格式

Python3.6.x 开始支持一种新的字符串格式化方式，官方称为Formatted String Literals,其含义与字符串对象的format()方法类似，但形式更加简洁

```python
name='Dong'
age=39
print(f'My name is {name},and I am {age} years old.')

My name is Dong,and I am 39 years old.
```

