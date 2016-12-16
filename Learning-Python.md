---
title: Learning Python---Data Structure
date: 2016年9月4日22:21:58
categories: 语言
tags: [Python,Data]  
---

String
===

`+` means concatenance

```python
str1 = "Hello"
str2 = "there"
Hey = str1 +str2
print Hey
Hi = str1 + " " + str2  /* for a space. */
```
<!--more-->

To get lower letters or upper letters

```python
greet = Hey.lower()
great = Hey.upper()
print greet, great
```

If the type is string you can't just calculate, the right way is 

`x = int(str3) + 1`

This is same when using `raw_input`

`A = len(fruit) ` to get the length of the string.

IN
---

```python
fruit = "banana"
for letter in fruit
  if letter = ="a"
    count =count + 1
print count
```
To lookup the "a"s number in "banana".

Another way is

```python
fruit = "banana"
index = 0
while index < len(fruit)
  if letter == "a"
    count = count + 1
  index = index + 1
print count
```

The first method is significantly easy.

IN is also used as a logical expression

` "n" in "banana" ` you will get `TRUE`

And,you can use IN like this

```python
if "ana" in "banana"
print "found ana !"
```

The `find` function is used like

```
pos = find.fruit('na')
print pos  /* show the 'n's position in the string. */
a = find.fruit('aa')
print a # -1 means NULL.
```

Slicing 
---

To select a series of concerate string

```python
s = "I Love You"
print s[0:5]  /* up to 5, but not including 5; */
print s[6:20]
print s[5:]
```

---

You can get help by doing this

```python
hy = "hello world"
type(hy)  /* get the type of hy; */
dir(hy)  /* list what you can do to the type of hy; */
```

You can also go to the [online document](http://docs.python.org/2/library/stdtypes.html#string-methods)

Replace
---

The function will search and replace.

```python
greet = "Hello Qi"
nstr = greet.replace('Qi','Ye')
print nstr
```

Strip
---
`lstrip` ,`rstrip` ,`strip` remove the whitespace on left, right or both.


Parsing Example
---

We want to extract a piece of data from a line.
(Email)

> From stephen.marquard @uct.ac.za Sat Jan 5 09:14:16 2008

For example, the domain name.

```python
data = "From stephen.marquard @uct.ac.za Sat Jan 5 09:14:16 2008"
atpos = data.find('@')
print atpos
sppos = data.find(' ',atpos) /* start at 'atpos' ; */
print sppos
host = data [atpos+1:sppos] /* not include '@' ; */
print host
```

File
===

Open
---

open() returns a "file handle"
e.g.

```python
handle = open(filename,mode)
fhand = open ('mbox','r')
print fhand
```
r means reading. The filename is a string.
open() will not read the data instantly, it just create a connection.

If you are openning a file, it needs to be put in the same folder.

\n
---
New line character

```python
stuff= "x\ny"
print stuff
len(stuff)
```

it will be 3.

Read
---

A file handle open for read can be treated as a sequence of strings. We can use for & in to handle.
 ```python
fhand = open ('mbox.txt')
count = 0
for line in fhand 
  count = count + 1

print 'Line count ' , count
```
To read the whole file
```python
fhand = open('mbox.txt')
inp= fhand.read()
print len(inp)
```

When the file is not big, this method can read the whole file into memory.

Search
---

Use if to print lines that meet criteria.

```python
fhand = open('mbox.txt')
for line in fhand:
  if line.startwith('From:')
    print line
```

Oops: The lines printed will have a \n from file and a \n from print function. To solve this, we change the code to this.

```python
fhand = open('mbox.txt')
for line in fhand
  line = line.rstrip()
  if line.startwith('From')
    print line
```

The \n are treated as white space.

Continue
---
Continue can skip the line that are not interesting.

```python
fhand = open('mbox.txt')
for line in fhand
  line = line.rstrip()
  if not '@hust.edu.cn' in line:
    continue
  print line
```
When numbers of files are being operating, try this code

```python
fname = raw_input('Enter the file name: ')
try
  fhand = open(fname)
except
  print 'File cannot be openned', fname
  exit()
count = 0
for line in fhand:
  if line.startwith('Subject')
    count = count + 1
print 'There are ', count, 'subject lines in ',fname
```

try this ` line = line.rstrip().upper()`

Lists
===

A list is a variable contains many values.(collection)
```python
a=[1, 2, 4]
friends=['Josrph','Glenn','Sally']
b=['red', 2, [1, 2]]
c=[]
```
Use loops

```python
friends=['A','B','C']
for friend in friends:
  print 'Happy new year', friend

print 'Done!'
```

inside list, every value has a sub, `friend[1]` for example.

lists can be changed every piece.
```python
A=[1,2,3]
A[1]=1
print A
```

length
---

```python
a=[1,[a,b],3]
print len(a)
```

the result will be 3.

Range
---
 Range returns a list if numbers starting from 0.
```python
print range(4)
[0,1,2,3]
```
so see the example before.

```python
friends=['A','B','C']
for friend in friends:
  print 'Happy new year', friend

print 'Done!'
```

can be writen as

```python
friends=['A','B','C']
for i in range(len(friends)):
  print 'Happy new year', friends[i]

print 'Done!'
```

Cincatenate
---

Use `+` too.

Slicing
---

```python
t = [1,2,3,4,5]
print t[1:3]
[2,3]
```

up to but not included.

Scratch
---
use append to add new element at the end of list

```python
stuff=list()
stuff.append=('boom')
stuff.append=('shakalaka')
print stuff
['boom','shakalaka']
```
Find
---
Use in to see weather a element is in a list
```python
some=[1,2,3,4]
9 in some
20 not in some
```

Sort
---

```python
friends=['Adam','Cathy','Bob']
print friends.sort()
```

sort() means "Sort yourself"

Functions
---

`len(), max(), min(), sum()/len()`

above shows the built in functions of Lists.

Split
---
Split breaks a string into parts produces a list if strings. By doing this, we can access a single word ib a line.

```python
abc='What the fuck'
stuff=abc.split()
print stuff
print len(stuff)
for w in stuff:
  print w
```

You can specify the character used to split the text

```python
line= 'first;second;thirs'
stuff=line.split(';')
print stuff
```

Using split, we can extract single word from a particular line.


```python
fhand = open('mbox.txt')
for line in fhand 
  line=line.rstrip()
  if not line.startwith('From:'):
    continue
  words=line.spilt()
  print words[2]
```

*Double Split*

You can extract even smaller pieces of information.

```python
words=line.split()
email=words[1]
pieces=email.split('@')
print pieces[1]
```

