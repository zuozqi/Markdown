---
title: Python Fundamental --- Rice Univ. /Cousera
date: 2016年10月27日23:43:13
categories: 语言
tags: [Python,Data,Cousera]  

---


Functions
---
下面是一个例程
```python
# computing the area of a triangle
def triangle_area(base,height):
	aera = (1.0/2) * base * height
	return area
```

注意要写注释，给变量起一个合理得名字。

在定义语句（第一句）由一定要有冒号，def 后是函数名，括号里是参量，return 后是返回的值。

<!--more-->

上述语句定义一个函数，使用时：

```python
a1 = triangle_aera(3,8)
print a1
```

a1是 return 后对应的量。

上面的函数有两个输入值，一个输出值，这些都可以改变，只要方程成立。甚至可以没有输入没有输出：

```python
def hello():
	print "Hello, world"
```

注意这里没有返回值，如果令 `h=hello()` 返回值是`None`。


Event-driven Programming
---
程序是由事件驱动的，事件可以是输入的文件，或者字符串等等。

- input-- *Button* Text box
- keyboard--- key down/up
- mouse---Click drag
- timer


下面是例程

```python
#Example of a simple event-driven program

import simplegui

#event handler
def tick():
	print "tick!"

#Register handler create a timer run tick after 1000ms
timer = simplegui.creat_timer(1000, tick)

#Start timer
timer.start()
```

这段小程序会在1s后运行tick这个函数。每1s后。


Local & Global Variables
---
在函数中定义的是局部变量，在主程序中定义的是全局变量。

```python
# num1 is a global variable 
num1 = 1 
print num1

#num2 is a local variable
def fun()
	num2 = num1 + 1 
	print num2
 
 fun()
 
 # the scope of globle num1 is the whole program, 
 print num1
 
 # this line will error for num2 is not defined globle
 print num2
```


SimpleGUI
---

在写的时候可以参考下面的每一个步骤

Program Structure

- Globals (state)
- Helper Functions
- Classes
- Define event-handlers
- Creat a frame
- Register event-handlers
- Start frame & timers



```python
# simplegui template

#import the module
import simplegui

#Define global variables
counter = 0

#Define helper functions
def increment():
    global counter
    counter = counter + 1 
  
#Define event handler functions
def tick():
    increment()
    print counter
    
def buttonpress():
    increment()
    global counter = 0

#Create a frame 
frame = simplegui.create_frame('SimpleGUI Test',100,100)

#Register event handlers
timer = simplegui.create_timer(1000,tick)
frame.add_button("Click me",buttonpress)

#Start frame and timers
frame.start()
timer.start()
```

**Buttons** 

以一个计算器界面的模拟为例，添加按钮：

```python
#Starting point for calculator
import simplegui
#initialize globals
store = 12
operand = 3

#define functions tahta manipulate store and poerand 
def output():
    print "Store" , store
    print "Operand" , operand
    print ""

def swap():
    global store, operand
    store, operand = operand, store
    output()

def add():
    global store, operand 
    store = store + oprand
    output()

def sub():
    global store, oprand 
    store = store - oprand
    output()
    
frame = simplegui.create_frame("Calculator",200,200)
frame.add_button("Print",output,100)
frame.add_button("Swap",swap,100)
frame.add_button("Add",add,100)
frame.add_button("Sub",sub,100)

frame.start()
```



**Input Fields**

在输入区，回车后会激发handler

在上述程序的基础上，增加下面的内容（在def 和 frame区）：

```python
def enter(inp):
    global oprand
    operand = int(inp)
    output()
    
frame.add_input("Enter oprand",enter,100)
```

input 输入的是一串字符串，输入1，识别的是'1'。

可以通过int(),float()转换。