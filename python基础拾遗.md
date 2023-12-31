# python基础拾遗

# 1.python之禅

在命令行通过import this可以看到python之禅

The Zen of Python, by Tim Peters

Beautiful is better than ugly.

Python程序员笃信代码可以编写得漂亮而优雅。编程是要解决问题的，设计良好、高效而漂
亮的解决方案都会让程序员心生敬意。随着你对Python的认识越来越深入，并使用它来编写越来
越多的代码，有一天也许会有人站在你后面惊呼：“哇，代码编写得真是漂亮！”

Explicit is better than implicit.

Simple is better than complex.

如果有两个解决方案，一个简单，一个复杂，但都行之有效，就选择简单的解决方案吧。这
样，你编写的代码将更容易维护，你或他人以后改进这些代码时也会更容易。

Complex is better than complicated.

现实是复杂的，有时候可能没有简单的解决方案。在这种情况下，就选择最简单可行的解决
方案吧。

Flat is better than nested.
Sparse is better than dense.
Readability counts.

即便是复杂的代码，也要让它易于理解。开发的项目涉及复杂代码时，一定要为这些代码编
写有益的注释。

Special cases aren't special enough to break the rules.
Although practicality beats purity.
Errors should never pass silently.
Unless explicitly silenced.
In the face of ambiguity, refuse the temptation to guess.
There should be one-- and preferably only one --obvious way to do it.

如果让两名Python程序员去解决同一个问题，他们提供的解决方案应大致相同。这并不是说
编程没有创意空间，而是恰恰相反！然而，大部分编程工作都是使用常见解决方案来解决简单的
小问题，但这些小问题都包含在更庞大、更有创意空间的项目中。在你的程序中，各种具体细节
对其他Python程序员来说都应易于理解。

Although that way may not be obvious at first unless you're Dutch.
Now is better than never.

你可以将余生都用来学习Python和编程的纷繁难懂之处，但这样你什么项目都完不成。不要
企图编写完美无缺的代码；先编写行之有效的代码，再决定是对其做进一步改进，还是转而去编
写新代码。

Although never is often better than *right* now.
If the implementation is hard to explain, it's a bad idea.
If the implementation is easy to explain, it may be a good idea.
Namespaces are one honking great idea -- let's do more of those!

```
美胜于丑
显式胜于隐式
简单胜于复杂
复杂胜于混乱
平铺胜于嵌套
稀疏胜于密集
可读性至关重要
特例不足以打破规则
实用性胜于纯净性
错误不应该默默传递
除非明确压制
面对模棱两可，拒绝猜测
应该有一种——最好只有一种——明显的方法来做
虽然这种方式可能一开始并不明显，除非你是荷兰人
现在总比永远好
虽然永远往往比现在立刻好
如果实现难以解释，那是个坏主意
如果实现容易解释，那可能是个好主意
```

# 2.turtle库

turtle库可用来绘制图形图案，比较典型的函数如goto() speed()等

# 3.print函数

print函数中有一个seq参数，作用是作为两个拼接字符串间的分隔符

```python
print('hello','world',sep='|',end='!\n')
```

结果：

> hello|world!

# 4.range()类

range类可以获取一系列的数，例如

```python
for i in range(3,50,6):
    print(i)
```

结果：

> 3
> 9
> 15
> 21
> 27
> 33
> 39
> 45

此代码中3为起始值，50为终止值，6为步长。前闭后开，即左边界可取到，右边界无法取到

这个类的常见用法为：

```python
@final
class range(Sequence[int]):
    @property
    def start(self) -> int: ...
    @property
    def stop(self) -> int: ...
    @property
    def step(self) -> int: ...
    @overload
    def __init__(self, __stop: SupportsIndex) -> None: ...
    @overload
    def __init__(self, __start: SupportsIndex, __stop: SupportsIndex, __step: SupportsIndex = ...) -> None: ...
    def count(self, __value: int) -> int: ...
    def index(self, __value: int) -> int: ...  # type: ignore[override]
    def __len__(self) -> int: ...
    def __eq__(self, __value: object) -> bool: ...
    def __hash__(self) -> int: ...
    def __contains__(self, __key: object) -> bool: ...
    def __iter__(self) -> Iterator[int]: ...
    @overload
    def __getitem__(self, __key: SupportsIndex) -> int: ...
    @overload
    def __getitem__(self, __key: slice) -> range: ...
    def __reversed__(self) -> Iterator[int]: ...
```

# 5.if __ name __ =  '__ main __'用法

接下来的代码只能在本模块中使用，因为只有在本模块的名字才是__ main __

# 6.cv2库   OpenCV库

python的一个计算机视觉库

## 6.1安装方法：

使用清华镜像会快很多

```bash
pip install -i https://pypi.tuna.tsinghua.edu.cn/simple opencv-python
```

## 6.2与turtle结合的脑洞

与turtle结合，读取图片然后绘制出来

代码：

```python
import turtle as t
import cv2

t.getscreen().colormode(255)
img1 = cv2.imread("""practice_day\day0909\ping.jpg""")[0: -2: 2]
img1 = cv2.imread("practice_day\da\
                  y0909\ping.jpg")[0: -2: 2]
width = len(img1[0])
height = len(img1)
t.setup(width=width / 2 + 100, height=height + 100)
t.pu()
t.goto(-width / 4 + 10, height / 2 - 10)
t.pd()
t.tracer(2000)
for k1, i in enumerate(img1):
    for j in i[::2]:
        t.pencolor((j[0], j[1], j[2]))
        t.fd(1)
    t.pu()
    t.goto(-width / 4 + 10, height / 2 - 10 - k1 - 1)
    t.pd()
t.done()
t.mainloop()


```

# 7.字符串

## 7.1字符串换行的方法

- 在换行处用斜杠结尾。此方法也可用于非字符串的代码换行

```python
def F_to_C(F):
   return \
   (F-32)/1.8
```

- 将字符串用三个引号包裹

## 7.2chr()方法

将数字转为对应字符

```python
print(chr(98))
```

结果：

> b

## 7.3ord()方法

将字符转为对应字符串

```python
print(ord('a'))
```

结果：

> 97

## 7.4len()

求字符串元素数量

## 7.5title()

将每一个单词首字母大写

```python
print("nigle walter".title())
```

结果：

> Nigle Walter

注意空格的使用

## 7.6upper() lower() isupper() islower()

 将所有单词大写或者小写  判断当前是不是全都大写或者全都小写

## 7.7startswith() endswith()

判断字符串是否以参数开头或者结尾

## 7.8转义字符

如果不想让\起到转义字符串的作用，可以在字符串最前面加上字母r

```python
print("测\t试")
print(r"测\t试")
```

## 7.9 find(str)函数

查找子串所在位置,查找不到返回-1

## 7.10 isdigit()函数

判断字符串是否由数字组成

## 7.11 isalnum()

判断字符串是否由数字和字母组成

## 7.12 strip()

去除字符串左右两侧空格

## 7.13格式化输出字符串

```python
a = 10
b = 30.2
print(f"{a}*{b}={a*b}")
```

结果：

> 10*30.2=302.0



# 8.命名要求

## 8.1PEP8对受保护的实例属性和私有实例属性的命名要求

> - 用小写字母拼写，多个单词用下划线连接。
> - 受保护的实例属性用单个下划线开头。
> - 私有的实例属性用两个下划线开头。

# 9.运算符

## 9.1 **用法

两个*的意思是求指数

```python
print(3**4)
```

结果：

> 81

## 9.2除法

除法是使用两个斜杠 //

```python
def is_primenumber(num):
    # 素数不能为1
    if num == 1:
        return False
    for i in range(2,num//2):#注意此处的除法
        if num%i==0:
            return False
    return True

print(is_primenumber(3))
```

# 10.函数

## 10.1可变参数

在参数名前面的*表示其是一个可变参数，可变参数args的类型为tuple

```python
def add(*args):
    total = 0
    for val in args:
        total += val
    return total

print(add(3,6,9,2))
```

# 11.作用域

## 11.1作用域关系

python查找变量是，会按照“局部作用域”、“嵌套作用域”、“全局作用域”和“内置作用域”的顺序来查找。因此如果一个局部作用域与全局作用域同名，会优先使用局部作用域。内置作用域是指python内置的标识符，例如print int等

## 11.2global关键字

可以指示某个变量来自全局作用域

## 11.3nolocal关键字

可以指示某个变量来自嵌套作用域

## 11.4全局变量

全局变量要减少使用，因为1.作用域和影响过于广泛，可能会发生意料之外的修改和使用。2.生命周期更长，导致长时间无法被垃圾回收。3.降低代码之间的耦合度。

## 11.5闭包

# 12.列表list

## 12.1求列表元素数量

len()

## 12.2遍历列表

三种方式

### 用下标遍历

```python
list1 = ['1',2,3.1]
for index in range(len(list1)):
    print(list1[index])
```

### 用元素遍历

```python
for item in list1:
    print(item)
```

### 同时根据下标和元素遍历

```python
for index,item in enumerate(list1):
    print(f"{index}:{item}")
```

## 12.3 删除指定位置元素

pop(index)

## 12.4切片

### 反向切片

```python
print(f"反向切片：{list1[::-1]}")
```

结果：

> 反向切片：[3.1, 2, '1']

## 12.5 sorted与sort

sorted不会修改原始列表，sort会修改原始列表

```python
list1 = ['orange', 'apple', 'zoo', 'internationalization', 'blueberry']
list2 = sorted(list1)
print(list1)#['orange', 'apple', 'zoo', 'internationalization', 'blueberry']
print(list2)#['apple', 'blueberry', 'internationalization', 'orange', 'zoo']
list1.sort()
print(list1)#['apple', 'blueberry', 'internationalization', 'orange', 'zoo']
```

## 12.6生成式语法与生成器

```python
# 生成式语法
f = [x for x in range(1,10)]
print(f)
print(sys.getsizeof(f))#占用内存更多，因为元素以及准备就绪
# 生成器
f = (x for x in range(1,10))
print(f)
print(sys.getsizeof(f))#占用内存较少  基本固定在64
for item in  f:
    print(item)
```

下面这个例子较难：

```python
# 生成式语法
f = [x + y for x in 'ABCDE' for y in '1234567']
print(f)
print(sys.getsizeof(f))
# 生成器
f = (x + y for x in 'ABCDE' for y in '1234567')
print(f)
print(sys.getsizeof(f))
for item in  f:
    print(item)
```



# 13.系统相关

## 13.1查看对象内存占用

sys.getsizeof(f)   f为对象

# 14.面向对象

## 14.1私有属性与保护属性

__ 开头的为私有属性，其他类无法访问。访问方法为在前面拼接下划线加类名

```python
class Test:
    def __init__(self) -> None:
        self.__foo = 'foo'
    
    def __bar(self):
        print(self.__foo)

def main():
    test = Test()
    print(test.__foo)#无法获取foo
    print(test._Test__foo)#前面拼接下划线加类名后，即可实现获取该属性名
    test.__bar()
    test._Test__bar()

if __name__ == '__main__':
    main()
```

_ 开头的为受保护属性，其他类可以访问，起到了一个提醒的效果
