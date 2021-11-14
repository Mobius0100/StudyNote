# Python技巧

按以下写法，可快速生成相似字符串列表

```python
url = [
    f"http:/www.cnblogs.com/#p{page}"
    for page in range(1,50+1)
]
```

