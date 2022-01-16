# Python技巧

## 语法技巧

+ 按以下写法，可快速生成相似字符串**列表**

```python
url = [
    f"http:/www.cnblogs.com/#p{page}"
    for page in range(1,50+1)
]
a = 100.
f'{a:.2f}'
```

- 生成多变量列表，并解开

列表前面加星号作用是将列表解开成两个独立的参数，传入函数，

字典前面加两个星号，是将字典解开成独立的元素作为形参。

```python
positions = [(i,j) for i in range(5) for j in range(4)]
# 生成5行4列
# [(0, 0), (0, 1), (0, 2), (0, 3), (1, 0), (1, 1), (1, 2), (1, 3), (2, 0), (2, 1), (2, 2), (2, 3), (3, 0), (3, 1), (3, 2), (3, 3), (4, 0), (4, 1), (4, 2), (4, 3)]

def add(a, b):
    return a+b

data = [4,3]
print add(*data)
#equals to print add(4, 3)
data = {'a' : 4, 'b' : 3}
print add(**data)
#equals to print add(4, 3)

```



## with用法

**with 语句**适用于对资源进行访问的场合，确保不管使用过程中是否发生异常都会**执行必要的“清理”操作，释放资源**

比如文件使用后**自动**关闭／线程中锁的自动获取和释放等。



## **Parse(解析器):**

**使用**：创建----> 添加参数------> 解析参数

```python
parser = argparse.ArgumentParser(description='Process some integers.')
parser.add_argument('integers', metavar='N', type=int, nargs='+', help='an integer for the accumulator')
parser.parse_args(['--sum', '7', '-1', '42'])
```

**ArgumentParser参数**

prog - 程序的名称（默认：sys.argv[0]）
usage - 描述程序用途的字符串（默认值：从添加到解析器的参数生成）
description - 在参数帮助文档之前显示的文本（默认值：无）
epilog - 在参数帮助文档之后显示的文本（默认值：无）
parents - 一个 ArgumentParser 对象的列表，它们的参数也应包含在内
formatter_class - 用于自定义帮助文档输出格式的类
prefix_chars - 可选参数的前缀字符集合（默认值：’-’）
fromfile_prefix_chars - 当需要从文件中读取其他参数时，用于标识文件名的前缀字符集合（默认值：None）
argument_default - 参数的全局默认值（默认值： None）
conflict_handler - 解决冲突选项的策略（通常是不必要的）
add_help - 为解析器添加一个 -h/--help 选项（默认值： True）
allow_abbrev - 如果缩写是无歧义的，则允许缩写长选项 （默认值：True）

**add_argument() 方法**

name or flags - 一个命名或者一个选项字符串的列表，例如 foo 或 -f, --foo。
action - 当参数在命令行中出现时使用的动作基本类型。
nargs - 命令行参数应当消耗的数目。
const - 被一些 action 和 nargs 选择所需求的常数。
default - 当参数未在命令行中出现时使用的值。
type - 命令行参数应当被转换成的类型。
choices - 可用的参数的容器。
required - 此命令行选项是否可省略 （仅选项可用）。
help - 一个此选项作用的简单描述。
metavar - 在使用方法消息中使用的参数值示例。
dest - 被添加到 parse_args() 所返回对象上的属性名。
————————————————
版权声明：本文为CSDN博主「quantLearner」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/The_Time_Runner/article/details/97941409



## 多线程技巧

多线程数据通信的queue.Queue

用于多线程之间、**线程安全**的数据通信

```python
import queue

q = queue.Queue()

q.put(item) # 添加元素
item = q.get() # 获取元素
# 查询状态
q.qsize()
q.empty()
q.full()
```





