Title: 遇到的一个python的坑
Date: 2017-06-14 16:23:03
Category: python
Tags: python
Slug: python

```
:::python
def fun(arg=[]):
    arg.append('A')
    print(arg)


fun()
# ['A']

fun()
# ['A', 'A']
```


第二个
```
:::python
a = [1, 3, 4]
 
b = {"a": 7}
 
a += b

a
>>> [1, 3, 4, 'a']

```
