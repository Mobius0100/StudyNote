## 背景

程序中难以避免需要写配置文件来控制参数，之前在 Python 中使用参数的方法包括两种：

- 将参数写在 Python 文件 `config.py` 中，这样好处是可以直接导入这个 `config.py` 中的参数，但是通用性不太好；
- 命令行输入参数，使用 `argsparse` 或者 `click` 等模块，但是在大型项目中一般不会在命令行手动输入参数；

因此，需要一个统一的撰写配置文件规范而且配置文件较为通用且易读，有没有解决方案呢？答案是有的，目前介绍一种配置文件规范 **YAML 语言**。



## 简介

1.yaml [ˈjæməl]: Yet Another Markup Language ：另一种标记语言。yaml 是专门用来写配置文件的语言，非常简洁和强大,之前用ini也能写配置文件，看了yaml后，发现这个更直观，更方便，有点类似于json格式

2.yaml基本语法规则：

- 大小写敏感
- 使用缩进表示层级关系
- 缩进时不允许使用Tab键，只允许使用空格。
- 缩进的空格数目不重要，只要相同层级的元素左侧对齐即可
- \#表示注释，从这个字符一直到行尾，都会被解析器忽略，这个和python的注释一样

3.yaml支持的数据结构有三种：

- 对象：键值对的集合，又称为映射（mapping）/ 哈希（hashes） / 字典（dictionary）
- 数组：一组按次序排列的值，又称为序列（sequence） / 列表（list）
- 纯量（scalars）：单个的、不可再分的值。字符串、布尔值、整数、浮点数、Null、时间、日期



## 使用方法

**安装** pip install pyyaml

**导入** import yaml

```yaml
# 注释：list嵌套dict

- user: admin1
  psw: '123456'

- user: admin2
  psw: '111111'

- user: admin3
  psw: '222222'
  
# 注释： dict嵌套list
nub1:
    - admin1
    - '123456'
nb2:
    - admin2
    - '111111'
nb3:
    - admin3
    - '222222'
```

