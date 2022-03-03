#1 准备工作
##1.3 Python库
###1.3.1 Numpy
提供多种数据结构、算法及大部分涉及python数值计算所需的接口
- 多维数组对象
- 数组计算
- 线性代数操作、傅里叶变换
###1.3.2 pandas
提供数据结构和函数
- 处理时间序列数据和非时间序列数据
- 处理缺失数据
- 数据库的合并

#2 Python语言基础、Ipython及Jupyter notebook
##2.1 Python解释器
- 拥有TAB补全
- 可视化更强

##2.2 Ipython基础
```python
exit() #退出当前解释器
ctrl-D #退出当前解释器
ctrl-C #中断代码

b = [1,2,3]
b?          #内省，显示文档字符串
b??         #显示源代码
np.*load*?  #配合*找文件
```

###2.2.7 终端快捷键
![ipython快捷键](https://github.com/Xiao-hu-star/img/blob/main/ipython_key.jpg?raw=true)


###2.2.8 关于魔术命令
```python
%timeit 查看执行时间
```

![datetime](https://github.com/Xiao-hu-star/img/blob/main/%E9%AD%94%E6%9C%AF%E5%91%BD%E4%BB%A4.jpg?raw=true)

##2.3 Python语义基础
####2.3.1.11 可变对象和不可变对象
- 可变对象：列表、字典、Numpy数组
- 不可变：字符串、元组tuple
  
![datetime](https://github.com/Xiao-hu-star/img/blob/main/%E6%A0%87%E9%87%8F%E7%B1%BB%E5%9E%8B.jpg?raw=true)

```python
s = r'this\has\no' #r是raw简写
```

#### 2.3.2.3 UTF-8字节与Unicode
- encode
- decode

#### 2.3.2.7 日期和时间
![datetime](https://github.com/Xiao-hu-star/img/blob/main/datetime.jpg?raw=true)

#### 2.3.2.6 三元表达式
```python
value = true-expr if condition else false-expr
#等价于下式
if condition:
    value = true-expr
else:
    value = false-expr
```

#3 内建数据结构、函数及文件
##3.1 数据结构和序列
###3.1.1 元组
固定长度、不可变的序列
```python
#如果元组中一个对象可变，例如列表，则可以在内部修改：
tup = tuple(['foo',[1,2],True])
tup[1].append(3)
tup
('foo',[1,2,3],True)

(4,None,'foo') + (6,0) + ('bar')
(4,None,'foo',6,0,'bar')

# *rest
values = 1,2,3,4,5
a,b,*rest = values
a,b
(1,2)
rest
[3,4,5]

# *_
a,b,*_ = values
```

###3.1.2 列表
- list：将迭代器或者生成器转化为列表
- extend：列表中添加新的元素

###3.1.1 内建序列函数
####3.1.3.1 enumerate
遍历一个序列的同时追踪当前元素的索引
```python
for i,value in enumerate(collection)：
```

####3.1.3.2 sorted
进行排序
####3.1.3.3 zip
将元素重新配对，构成一个新列表，列表长度由最短的序列决定

###3.1.4 字典
####3.1.4.2 默认值
```python
if key in some_dict:
    value = some_dict[key]
else:
    value = default_value
#等价于
value = some_dict.get(key,default_value)
```

####3.1.4.3 有效的字典键类型
键 不可变
- hash：检查一个对象是否可以哈希化
  
###3.1.5集合
无序且元素唯一，只有键没有值的字典
![集合操作](https://github.com/Xiao-hu-star/img/blob/main/%E9%9B%86%E5%90%88%E6%93%8D%E4%BD%9C.jpg?raw=true)

###3.1.6 列表、集合和字典推导式
```python
[expr for val in collection if condition]
#等价于
result = []
for val in collection:
    if condition:
        result.append(expr)
```

####3.1.6.1 嵌套列表推导式
```python
some_tuples = [(1,2,3),(4,5,6),(7,8,9)]
flattered = [x for tup in some_tuples for x in tup]
#等价于
flattered = []
for tup in some_tuples:
    for x in tup:
        flattered.append(x)
```

###3.2.6 生成器
url:
https://www.zhihu.com/question/20829330

- 迭代器
  向python解释器生成对象的对象
```python
some_dict = {'a':1,'b':2,'c':3}
for key in some_dict:
    print(key)
#等价于
dict_iterator = iter(some_dict)
```
- 生成器
普通函数执行并一次返回单个结果，生成器则是返回一个多结果序列
生成器的好处是延迟计算，一次返回一个结果
```python
#将return替换成yield
def squares(n=10):
    print('Generating squares form 1 to {0}'.format(n**2))
    for i in range(1,n+1):
        yield i **2

#生成器表达式
gen = (x **2 for x in range(100))
gen
```

####3.2.6.2 itertools模块
用于数据算法的生成器集合

###3.2.7 错误和异常处理
```python
def attempt_float(x):
    try:
        return float(x)
    except ValueError:
        return x
```
##3.3 文件与操作系统
```python
#文件会在with代码块结束后自动关闭
with open(path) as f:
    lines = [x.rstrip() for x in f]
```
![文件模式](https://github.com/Xiao-hu-star/img/blob/main/%E6%96%87%E4%BB%B6%E6%A8%A1%E5%BC%8F.jpg?raw=true)