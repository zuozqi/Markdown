---
title: Learning Python---Network
date: 2016年9月11日12:25:00
categories: 语言
tags: [Python,Data]  
---

Regular Expression
===

`Regular Expression` 一定程度上可以理解为程序化的语言，语素是各个符号，可以大大简化程序，所以如果能用`RE`会很酷，当然各有所好，不使用也没什么。
<!--more-->

>^   Matches the beginning of a line
$   Matches the end of the line
.   Matches any character
\s  Matches whitespace
\S  Matches any non-whitespace character
\*   Repeats a character zero or more times
\*?  Repeats a character zero or more times (non-greedy)
\+   Repeats a character one or more times
\+?  Repeats a character one or more times (non-greedy)
[aeiou] Matches a single character in the listed set
[^XYZ]  Matches a single character not in the listed set
[a-z0-9]    The set of characters can include a range
(   Indicates where string extraction is to start
)   Indicates where string extraction is to end

`RE`是依靠上面的要素组成的含义。

在使用`Regular Expression` 之前，需要导入库
`import re`

下面解释几个简单的条件：
- `^X.*` : 句首处，以X开头，后面人一个字符
- `^X-\S+` : \S为不是空格的字符，+为一次或一次以上
- `[0-9]+` : 多位数字
`re.search()` 返回的是逻辑判断，即`True` / `False`
而 `re.findall()` 
返回的是提取出来的值，行程一个List，如果没有对应值则返回空List。

Greedy Matching
---

`GM`是缺省值，意思是当寻找条件时，倾向于返回更大范围的值，例如
```Python
import re
x = 'From: Using the : character'
y = re.findall('^F.+:', x)
print y
```

输出的是 `From: Using the:`
修改方式是在+(*)后面加？
```Python
import re
x = 'From: Using the : character'
y = re.findall('^F.+?:', x)
print y
```

()
---
在输出是可以使用小括号，意思是，尽管在小括号外和内都是检索的要求，但是只输出小括号内的部分。

```Python
y = re.findall('\S+@\S+, x')
print y
y = re.findall('^From (\S+@\S+, x)')
print y
```

下面是一个提取数字的实例，能实现一下功能

- 读取文件
- 查找数字
- 输出最大值

```Python
import re
hand = open ('mbos-short.txt')
numlist = list ()
for line in hand:
    line = line.rstrip()
    stuff = re.findall('^X-DSPAM.*([0-9.]+', line)
    if len(stuff) != 1 : continue
    num = float(stuff[0])
    numlist.append(num)        

print 'Maximun:' , max(numlist)
```

Notes:
- !=1 : 因为输出的是list，所以是list内元素个数，而不是数字的长度
- [0-9.] : 数字或小数点

Network & Sockets
=== 

`Socket` 可以理解为两个应用之间的连线，通道。 类比于文件的`handle`
服务器上每一个应用都有对应的端口，其中80是最常用的，对应`Web Server`应用

链接服务器前需要先导入库
```Python
import socket
mysock= socket.socket(socket.AF_INET, socket.SOCK_STREAM)
my.sock.connet(('www.py4inf.com',80))
```

以上前两句是固定格式。

URL
---

例如网址`http://www.youtube.com/watch?v=x2Gylq59rl`, `http`代表协议，`www.youtube.com`是域名，`watch?v=x2Gylq59rl`是要访问的文件，这样表达可以清楚的看清访问的结构。

Request
---
在连接到目的服务器后，需要做`Hand Shake`,请求一个文件的写法是`GET http://www.youtube.com/watch?v=x2Gylq59rl` 就是URL地址就可以，之后要加两次回车。

例如下面这段代码

```Python 
import socket
mysock= socket.socket(socket.AF_INET, socket.SOCK_STREAM)
mysock.connect(('www.py4inf.com',80))

mysock.send('GET http://www.py4inf.com/code/romeo.txt HTTP/1.0\n\n')

while True:
    data = mysock.recv(512)
    if (len(data)<1):
        break
    print data

mysock.close()
```

以上需要注意的几点：
- `HTTP/1.0` : 使用的协议的版本
- `\n\n` : 输入后的两次回车
- `recv(512)` : 限制字符串最长为512个字符
- `mysock.close()` : 完成后关闭`Socket`

urllib
---

作为更简单的工具，可以把获取网站文件当作本地文件一样使用，如下：
```Python
import urllib
fhand= urllib.urlopen('http://www.py4inf.com/code/remeo.txt')

for line in fhand:
    print line.strip()
```

`urllib`的返回结果不包含`Header`部分

HTML
===

`Python`的一种应用是爬虫，爬虫会假装自己是浏览器，不断按目的打开网址中需要的东西，自动搜索信息。
Facebook是不允许有爬虫的，Twitter可以。
HTML作为强标记语言，可以拆分，但是有更好的方法

Beautiful Soup
---

[Beautiful Soup](http://www.crummy.com/software/BeautifulSoup)是一个python文件，当需要使用的时候，把他放在和代码同目录的路径中。

```Python
import urllib
from BeautifulSoup import *

url = raw_input('Enter -')

html = urllib.urlopen(url).read()
soup = BeautifulSoup(html)

tags = soup('a')

for tag in tags
    print tag.get('href', None)
```

需要注意的是
- Soup返回的不是List也不是DIctionary，而是一堆数据，询问他，他给你回复
- tags对应的是`<a>...</a>`这个标签，`.get`中是读取`href`中的value

XML
---

在`Python`和`Java`之间有互相传递数据的方式，叫`Wire Protocol`
在本地将自己语言的代码`Serialize`，成为中间格式，然后在目的地`De-serialize`成为另一种语言，就完成了语言的相互传递
这种中间格式有`XML`,`JSON`

XML: eXtensible Markup Language
这种语言比较繁琐，但是处理文档的时候优势比较明显，例如`.pptx`，x就代表XML,其中的例如加粗，斜体都是通过XML标记来实现的。
XML中有`Complex Element`,`Simple Element`,其中`CE`中包含`SE`，结构为树状。
一般的标记为`<name attribute='...'>value</name>`,也有一种结构是`<name />`为自闭型标签。
XML Schema是XML的标准，是各方商定的，规定XML是否有效，有固定的格式，也是互相交换的标准，其中`XSD`是常用的标准

XML示例：
```XML
<person>
    <name>Chuck</name>
    <phone type="intl">
        + 1 734 303 4456
    </phone>
    <email hide="yes" />
```

相应的，Python内置了处理XML的库，具体的方法如下

```Python
import xml.etree.ElementTree as ET
input = '''<stuff>
        <users>
            <user x="2">
                <id>001</id>
                <name>Chuck</name>
            </user>
            <user x="7">
                <id>009</id>
                <name>Brent</name>
            </user>
        </users>
    </stuff>'''

    stuff = ET.fromstring(input)
    lst = stuff.findall('users/user')
    print 'User count:' ,len(lst)
    for item in lst:
        print 'Name', item.find('name').text
        print 'id', item.find('id').text
        print 'Attribute', item.get("x")
```

可见，XML语言操作起来比较麻烦，而且取值的时候不是很直观。

JSON
---

JavaScript Object Notation
`JSON`看起来像`Java`和`Python`,是很好的数据结构，非常自然。

```JSON
{
    "name" : "Chuck",
    "phone" : {
        "type" : "intl"
        "number" : "+1 734 303 4456"
    },
    "email" : {
        "hide":"yes"
    }
}
```

可见，`JSON`中没有`Attributes`，都是以`Value`形式出现，所以比较直观。
`JSON`只返回两种值，一种是`List`,另一种是`Dictionary`，这就使他的应用性大大提高，返回的可以直接用，如下：

```Python
import json
input = '''[
{
    "id" : "001",
    "x" : "2",
    "name" : "Chuck"
},
{
    "id" : "009",
    "x" : "7",
    "name" : "Broat"
}
]'''

info = json.loads(input)
print 'User counts', len(info)
for item in info:
    print 'Name', item['name']
    print 'Id', item['id']
    print 'Attribute', item['x']
```

需要注意的是
- `[]`括起来的说明是`list`，里面有两个`Object`，在这里是两个人，每个人(`Item`)是一个`Object`,人里面有各个属性，`id`,`x`...
- 这里引用每个`item`就是一个`Dictionary`,引用非常方便，后面例子体现的更好。

所以，`JSON`表现的更直观，`XML`可能有能力更清楚一些

APIs
---

服务器上有各种服务，也有自己的标准，当你访问服务器数据的时候，他可以规定你怎么访问，你要按照他的标准填写自己的要求。

Service Layer: 将自己的数据转换成通用数据，反之亦然。 相同标准可以直接传递。

Geocoding API (Google)
---

访问谷歌的API，返回JSON文件
```Python
import urllib
import json

serviceurl = 'https://maps.googleapis.com/maps/api/geocode/json?'

while True:
    address = raw_input ('Enter Location: ')
    if len(address) < 1 : break

    url = serviceurl + urllib.urlencode({'sensor':'false','address':address})
    print 'Retrieving', url
    uh = urllib.urlopen(url)
    data = uh.read()
    print 'Retrieved', len(data),'characters'

    print data

    js = json.loads(str(data))

    print json.dumps(js, indent = 4)

    lat = js["results"][0]["geometry"]["location"]["lat"]
    lng = js["results"][0]["geometry"]["location"]["lng"]
    print 'lat',lat,'lng',lng

    location = js["results"][0]["formatted_address"]
    print location
```

需要注意的是：
- `urlencode`是将输入转成浏览器可以识别的代码，不需要知道细节
- `js["result"][0]`中的0是因为，返回的是dictionary，[0]是result列表中第一个元素，具体的应该查看返回的json文件。
- Goolge的API是免费使用的，但有次数限制，其他的不一定可以，要先查看。


