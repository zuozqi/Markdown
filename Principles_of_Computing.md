---
title: Principles of Computing
date: 2016年10月28日20:44:07
categories: 语言
tags: [Python,Data,Cousera]  

---


Search & Data Structures
---

**Generators**

```python
print "max in list", max ([num * 2 - 3 for num in range(7)])
print "max in gen", max (num * 2 - 3 for num in range(7))
```
上面的代码的不同在于：
第一行是生成list，然后把list传递给max，第二行直接把generator生成的传递给max,显然第二行代码更高效。

```python
# A generator function
def genfunc(limit):
    num = 0
    while num < limit:
        yield num
        num = num + 1
        
print genfunc(7)  #会错误
for num in genfunc(7):
    print num     #输出一串数字
```

上面程序中的yield，意思是，不中断程序，返回值，所以运行结果会是一串字符，从0到6，因为gen并不是具体的数字或数据，所以不能直接输出，可以把generator理解成一个生成list的函数，调用它的时候会生成一个集合的数据然后输出，但是并不用生成list占用资源。

下面一段程序可以用来区分yield和return

```python
def genfunc2(endfunc):
    num = 0
    while True:
        if endfunc(num) = True:
            return
        yield num
        num = num + 1 

 def endfc(num):
    if num == 7:
       return True
	return False
for number in genfunc2(endfn):
    print number
```

上面使用return的时候，会结束函数，而yield会返回当前值，继续进行迭代，这里，genfunc2()的参量是一个函数，endfunc只是一个代号，在本例输出是endfunc=endfc

**Stacks & Queues**

栈和队列都是存储数据的方法，栈--”先进后出“，队列--“先进先出”

```python
class Queue:
    """
    A simple implementation of a FIFO queue.
    """

    def __init__(self):
        """ 
        Initialize the queue.
        """
        self._items = []

    def __len__(self):
        """
        Return the number of items in the queue.
        """
        return len(self._items)
    
    def __iter__(self):
        """
        Create an iterator for the queue.
        """
        for item in self._items:
            yield item

    def __str__(self):
        """
        Return a string representation of the queue.
        """
        return str(self._items)

    def enqueue(self, item):
        """
        Add item to the queue.
        """        
        self._items.append(item)

    def dequeue(self):
        """
        Remove and return the least recently inserted item.
        """
        return self._items.pop(0)

    def clear(self):
        """
        Remove all items from the queue.
        """
        self._items = []  
container = Queue()

container.enqueue(1) 
container.enqueue(2)
container.enqueue(3)

print container.dequeue() 

container.enqueue(4)

print container.dequeue()
print container.dequeue()
print container.dequeue()

```

Queue的输出： 1 2 3 4 , Stack 的输出： 3 4 2 1 



**inheritance**

一个类可以继承另一个类的特性，几个有一样特性的类可以组合在一起，简洁一些

```python
class Base:
    def hello(self):
        print "hello"
        
    def message(self, msg):
        print msg
        
class Sub(Base):
    def message(self, msg):
        print "sub:", msg
        
obj = Sub()
obj.hello()
obj.message("what's going to happen")

baseobj = Base()
baseobj.hello()
baseobj.message("anothoer message")

```



```python
"""
Simple example of using inheritance.
"""

class Base:
    """
    Simple base class.
    """    
    def __init__(self, num):
        self._number = num

    def __str__(self):
        """
        Return human readable string.
        """
        return str(self._number)
        
class Sub(Base):
    """
    Simple sub class.
    """
    def __init__(self, num):
        pass
    
obj = Sub(42)
print obj
```

上面一段程序会出错，如果要初始化一个子类，要这样写，

```python
def __init__(self,num):
    Base.__init__(self, num)  #调用基函数的初始化函数
```

为什么这样没有听懂。。。（base是一个类，self是一个名词，所以不能在括号里加一个self，而要调用基函数的初始化方法，因为自己没有这个函数?。。。

**Grid Class**

```python
"""
Game of Life demo
"""

import poc_grid
import poc_gol_gui

# constants
EMPTY = 0 
FULL = 1

class GameOfLife(poc_grid.Grid):
    """
    Extend Grid class to support Game of Life
    """
    
    def update_gol(self):
        """
        Function that performs one step of the Game of Life
        """
        
        updated_grid = [[self.update_cell(row, col) \
                            for col in range(self.get_grid_width())] \
                            for row in range(self.get_grid_height())]
        
        for col in range(self.get_grid_width()):
            for row in range(self.get_grid_height()):
                if updated_grid[row][col] == EMPTY:
                    self.set_empty(row, col)
                else:
                    self.set_full(row, col)
                    

    def update_cell(self, row, col):
        """
        Function that computes the update for one cell in the Game of Life
        """
        # compute number of living neighbors
        neighbors = self.eight_neighbors(row, col)
        living_neighbors = 0
        for neighbor in neighbors:
            if not self.is_empty(neighbor[0], neighbor[1]):
                living_neighbors += 1
            
        # logic for Game of life        
        if (living_neighbors == 3) or (living_neighbors == 2 and not self.is_empty(row, col)):
            return FULL
        else:
            return EMPTY
        
# run gui        
poc_gol_gui.run_gui(GameOfLife(30, 40))

```

