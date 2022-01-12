```python
def store(test_dic):
    with open("/Users/lucifer/PythonCode/log.json", "w") as f:
        json_str = json.dump(test_dic, f, ensure_ascii=False, indent=4, separators=(', ', ': ')) # 显示中文,设置缩进，分隔符进行换行格式化
        print("successful")

def openjson():
    with open("/Users/lucifer/PythonCode/log.json", 'r') as f:
        temp = json.load(f)
        print(type(temp))  # dict
        print(temp)
        print(temp['description'])
```

文件操作使用load、dump



**loads是将字符串转换成dict**

**dumps是将字典转换成str**

```python
# 将json字符串转换成字典格式
str1 = '{"name": "张三", "age": 18, "sex": "男"}'
print('这是转换后的数据：',json.loads(str1))
print('这是转换后的数据类型：',type(json.loads(str1))) # dict

# 将字典格式数据转换成json格式
dict1 = {'name': '张三', 'age': 18, 'sex': '男'}
print('这是将字典转换之后的数据：',json.dumps(dict1,ensure_ascii=False))
print('这是将字典转换之后的数据类型：',type(json.dumps(dict1,ensure_ascii=False))) # str
```

