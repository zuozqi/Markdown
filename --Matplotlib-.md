---
title: Matplotlib---试试看
date: 2016年10月28日20:45:05
categories: 语言
tags: [Python,Data,Matplotlib]  
---

笔记，摘录整理自知乎“【数据可视化】之Matplotlib

matplotbib的[安装方法](http://matplotlib.org/users/installing.html)为（windows)，在命令行界面输入

```
python -m pip install -U pip setuptools
python -m pip install matplotlib
```

Matplotlib最基本的就是可以画点，假如有一堆数据，想把他们区分开，最直观的就是画成散点图，在Matplotlib中，画点的方法如下：

```python
#引入matplotlib包并简写成plt
import matplotlib.pyplot as plt

#定义几个点的x,y集合
x=[1 ,12 ,5 ,32, 3 ,15, 7 ,25 ,13 ,6 ,23 ,16] 
y=[2 ,5, 59 ,9, 3, 4, 13, 48 ,13 ,15, 18, 21]

#画散点图
plt.scatter(x,y)

#展示绘画框
plt.show()
```

通过细微的调整参数，达到一些美观的效果

```python
plt.scatter(x,y,color='red',marker='x',marksize='30')
plt.axis([0,10,0,10])
```



想画折线图的话，需要用plot

```python
#引入matplotlib包并简写成plt
import matplotlib.pyplot as plt

#定义几个点的x,y集合
x=[1 ,12 ,5 ,32, 3 ,15, 7 ,25 ,13 ,6 ,23 ,16] 
y=[2 ,5, 59 ,9, 3, 4, 13, 48 ,13 ,15, 18, 21]

#画线
plt.plot(x,y)

#展示绘画框
plt.show()
```

会**按顺序**连线，也可以设一些参数

```python
plt.plot(x,y,linestyle='--',label='picture')
```

也可以进行绘画框的划分，可以在一个图内显示两个图

```python
#引入matplotlib包并简写成plt
import matplotlib.pyplot as plt

#定义几个点的x,y集合
x=[1 ,12 ,5 ,32, 3 ,15, 7 ,25 ,13 ,6 ,23 ,16] 
y=[2 ,5, 59 ,9, 3, 4, 13, 48 ,13 ,15, 18, 21]

fig = plt.figure()  #对象化图像
p1 = fig.add_subplot(211) #划分图框
p2 = fig.add_subplot(212)

#画线
p1.plot(x,y)

#画散点图
p2.scatter(x,y)
#展示绘画框
plt.show()
```






代码积累
---

```python
import numpy as np
import matplotlib.pyplot as plt
def f(t):
	return np.exp(-t) * np.cos(2*np.pi*t)
t1 = np.arange(0.0, 5.0, 0.1)
t2 = np.arange(0.0, 5.0, 0.02)
plt.figure(1)
plt.subplot(211)
plt.plot(t1, f(t1), 'bo', t2, f(t2), 'k',alpha = 0.3)
plt.subplot(212)
plt.plot(t2, np.cos(2*np.pi*t2), 'r--')
plt.show()

```

```python

import numpy as np
import matplotlib.pyplot as plt


x = np.linspace(0, 1)
y = np.sin(4 * np.pi * x) * np.exp(-5 * x)

plt.fill(x, y, 'r')
plt.grid(True)
plt.show()

```

```python

import matplotlib.pyplot as plt

x=[1 ,12 ,5 ,32, 3 ,15, 7 ,25 ,13 ,6 ,23 ,16] 
y=[2 ,5, 59 ,9, 3, 4, 13, 48 ,13 ,15, 18, 21]
area=[50,100,60,40,80,120,135,125,225,315,75,45]
plt.scatter(x,y,s=area,color='r',alpha=0.5)

plt.show()
```

