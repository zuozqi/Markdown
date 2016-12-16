---
title: Learning Python---Data Structure 2
date: 2016年9月7日22:43:56
categories: 语言
tags: [Python,Data]  
---

Dictionary
===

Dictionary可以理解成一堆，一坨东西，和List具有线性的特点不同，Dictionary内的东西是杂乱无章的

```Python
purse = dict()
purse['money'] = 12
purse['candy'] = 3
purse['tissues'] = 75
print purse
print purse['candy']
purse['candy'] = purse['candy'] + 1
print purse
```
<!--more-->

Dictionary和List的不同点还有，Dictionary使用名称而不是数字来作为指针。(hashing)
另一种定义Dictionary的方法是：
```Python
i = { 'chuck':1,'fred':47,'jan':100}
print i
ooo = {}
print ooo
```

Dictionary十分擅长处理类似画正字求频次的问题。
```
count = dict()
ccc['csev'] = 1
ccc['dav'] = 1
print ccc
ccc['dav'] = ccc['dav'] + 1
pring ccc
```
但注意，引用DIctionary中不存在的名称会出现错误。
为解决这个问题，可以使用下列代码
```Python
counts = dict()
names = ['zhangsan','lisi','wangwu']
for name in names:
  if name not in counts:
    counts[name]=1
  else:
    counts[name] = counts[name] + 1
print counts
```

有一种函数是count.get(a.b),在函数中，a是Dictionary中指代名称的变量，b是当没有这个名称的话赋予的缺省值，可以写0，写出下面的代码

```Python
counts = dict()
names = ['zhangsan','lisi','wangwu']
for name in names:
  counts[names]=counts.get(name.0)
print counts
```
下面是一段将前面的内容结合起来的小程序，已经可以实现特定的功能了
```Python
counts = dict()
print 'Enter a line of text:'
line = raw.input("")
words = line.split()
print 'Words:',word
for word in words:
 counts[words] = counts.get(word.0) + 1
print 'Counts:', counts
```
Dictionary和list之间可以相互转换

```Python
i = { 'chuck':1,'fred':47,'jan':100}
pring list(i)
print i.values()
print i.items()
```
Python的一个有点是可以有两个迭代的变量
```Python
i = { 'chuck':1,'fred':47,'jan':100}
for a,b in i.items():
  print a ,b
```
这里，a和b分别去'i'Dictionary中的名称和值。

这里是完整的程序
```Python
name = raw_input("Enter file:")
handle = open(name,'r')
text = handle.read()
words = text.split()

counts = dict()
for word in words:
  counts[word] = counts.get(word.0) + 1

bigcount = None
bigword = None
for word,count in counts.items()
  if bigcount is None or count>bigcount:
    bigword = word
    bigcount = count

print bigword, bigcount
```

可以通过这行代码来对counts里的值进行排序
其中，d[1]为针对value排序 reverse为倒序（从大到小）
```python
dic = sorted(counts.iteritems(), key=lambda d:d[1], reverse = True)
print dic
```

Tuples
===

Tuple和List很像，但Tuple不能修改，使用时使用小括号

```Python
x = [9 , 8 ,7]
x[2] = 6
print x

z=(5, 4, 3)
z[2] = 0
#Error
```

所以，理所当然的，Tuple不能使用`sort`,`append`,`reverse`函数
详细了解Tuple可以使用哪些函数可以使用`dir()`命令来了解。

