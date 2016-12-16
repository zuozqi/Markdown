---
title: Problems Occurred During Building Website Using Hexo and The Solutions 
date: 2016年8月21日14:38:45
categories: 工具
tags: [Hexo,Github]
---

在用`Jekyll`建站完成后，遇到了一些问题，比如
- 没学会用`Git`(但是在这就学会一点..)
- 修改配置文件要炸了
- 更换主题麻烦，如果要更换较多文件，我直接Delete Repository...十分蛋疼
- 没那么漂亮

<!-- more -->


诸如以上几点原因，在 [@春哥](http://blog.leanote.com/chilton) 的建议下，把博客迁移到了`Hexo`上

这篇教程主要参考了一下几篇文章
- [史上最详细的Hexo博客搭建图文教程](https://xuanwo.org/2015/03/26/hexo-intor/)
- [NexT官方说明文档](http://theme-next.iissnan.com/getting-started.html)
- [Hexo MathJax插件](https://unnamed42.github.io/2015-12-02-Hexo-MathJax%E6%8F%92%E4%BB%B6.html)

下面介绍一下操作的步骤
准备工作
------

首先是安装[Node.js](https://nodejs.org/dist/v4.2.3/node-v4.2.3-x64.msi)和[Git](https://github-cloud.s3.amazonaws.com/releases/23216272/84b33b96-87f5-11e5-8f91-32080286239e.exe?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAISTNZFOVBIJMK3TQ%2F20160821%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20160821T065258Z&X-Amz-Expires=300&X-Amz-Signature=835a15cab7f4c27277e81b7fa958176c848c78290e02b23290f9320ad929f411&X-Amz-SignedHeaders=host&actor_id=21128110&response-content-disposition=attachment%3B%20filename%3DGit-2.6.3-64-bit.exe&response-content-type=application%2Foctet-stream)
Git这个软件十分傲娇，后文会提到。

在安装过程中，`Node.js`一路Next安装就可以，但是在`Git`安装中，注意`PATH`选择是要选择`Use Git from the Windows Command Prompt`
![GitSetup](https://xuanwo.org/imgs/opinion/Git-path-setting.png)

检查是否安装成功的命令是(在CMD或Git Bash均可)
>git --version
>node -v
>npm -v

配置GitHub端
---
这里略过，详见[Memo for buidling a website](http://zuozqi.space/2016/08/21/backup%20for%20building%20a%20web/)

配置Hexo
---
这里配置大多是要在`Git Bash`下进行
**建议**
>找一个地方，新建一个文件夹作为站点的目录，右键`Git Bash here`完成后续操作

在命令行里输入
>npm install hexo-cli -g #在系统中安装Hexo

_Notice_ `hexo-cli` 输成 `hexo` 的话不能安装
_Notice_ <font color=red>WARN</font>是不需要管的，不出现<font color=red>FETAL</font>就可以

然后输入
>npm install hexo --save  #后续安装？不是很懂

等刷过一堆文件之后，可以用下面的代码看看安装成功没有
>hexo -v

*初始化Hexo*

下面的操作就是针对当前文件夹了。

>hexo init #在当前文件夹注入Hexo初始文件

完成这布以后，上面新建的文件夹内就有了一堆文件

然后
>npm install  #安装需要的组件

这样一个Hexo环境就布置好了，内容是初始自带的欢迎之类的文件。
如果要查看的话可以这样输入

>hexo g 

这个命令的意思是生成静态文件(Generate)，即把本地的文件渲染成可以发布的文件，但是还存在本地，没有发布到站点上去。

>hexo s

在本地服务器上查看，会提示在`http://localhost:4000/`可以查看，在浏览器打开就可以了，这个页面是初始的主题，初始的欢迎界面，不过已经很漂亮了。


`^c` 退出本地服务器，继续操作

*修改Hexo*

接下来就需要订制自己的Hexo了

在文件夹中生成的众多文件中，各个文件的作用在下面查看

_[Hexo官方文档](https://hexo.io/zh-cn/docs/configuration.html)_

*检查和Github的连接*

要配置SSH keys，输入如下代码
>cd ~./ssh  #检查本机的ssh密钥，如果没有的话就是第一次
>$ ssh-keygen -t rsa -C "user@youremail.com" #生成密钥

这样生成的SSH key存放在刚才的目录中，用记事本打开，复制其中的内容，在[此处](https://github.com/settings/keys) 添加新的密钥，复制到里面，保存就可以了。

同时，把`_config.yml`文件中的`Deployment`项修改为
```Node.js
deploy: 
  type: git
  repo: git@github.com:yourname/yourname.github.io.git
  branch: master
```

**非常重要**

需要安装 `hexo-deployer-git`

代码为
>npm install hexo-deployer-git --save

这个插件！真是坑爹！
首先，没有它的话不行，会出各种错误，反正你的网站根本部署不了，其次，安装它非常看运气！有两次安装它的时候安装过程出现了乱码(汉字)，必须重新装`Git`才能解决，如果安装过程出现乱码的话，每次`hexo d`的时候链接的自己的域名就会404，刚开始不知道真是神烦...

那么我们假定已经安装好这个插件了
>hexo d

命令把之前`hexo g`生成的静态文件部署(Deploy)到站点上

发布新的文件可以直接放到本地的`/source/_posts`文件夹中，如果新增加了文件需要`hexo g`生成一下。

还可以使用
>hexo d -g

命令，生成+部署，很方便。

这样操作完以后，就可以通过 
>XXX.github.io

来访问站点了，但是外域名还是不可以，下面设置一下。

*外域名*

把外域名解析到Github上的IP在前面的文章已经提到了，现在需要把本地和GitHub建立连接，具体的做法是：

在`source`中建立全名为`CNAME`的文件，内容为`domain.xxx`

然后`hexo d -g`，然后再`GitHub`里项目里的`Setting`里链接到自己的域名就可以了。

配置主题
---
这里主要参考各个主题的参考文档，主要提一下注意的点

- **不要作死** 不懂html就不要自己写主题...千万...
- 标题栏上的小东西

  比如Categories、Tags，需要在主题中生效，同时，还要用这个命令
 
  `hexo new page "xxx"` 

  生成一个相应文件夹和其中的`index.html`，这时候不要管！只要写文章在开头注明就可以了,`index.html`内的内容是自动生成的，

  如果没有及时更新的话，删掉根目录的`jb.json`，然后运行`hexo clean`,`hexo g`,`hexo d`，重新生成一遍网站就可以。

- `NexT`出现过语言不对的情况，需要在根目录`_confi.yml`更改语言选项为`zh.Hans`
- 大多数配置都可以在官方说明文档内查看，十分详细

设置数学公式
----

添加插件`hexo-math`就可以了，具体的操作如下

>pm install hexo-math --save

语法和`Latex`中是一致的，包括公式环境。
一个`$`是行内公式，两个`$$`是行间公式，注意特殊符号之前要加`\`转义，

网上教程的说明中有在`_config.yml`上添加一段

```Node.js
plugins:
- hexo-math
```
千万不要添加！否则`Deploy`的时候会出现错误。

插入多媒体
---
- 图片
  插入图片的方法就用Markdown本身自带的功能就可以
- 音乐 
  可以插入网易云音乐，引用下面的代码，可以在歌曲页`生成外链播放器`获取`iframe`代码下面的链接
```HTML
<center>
<iframe frameborder="no" autostart="false" border="0" marginwidth="0" marginheight="0" width=330 height=86 src="http://music.163.com/outchain/player?type=2&id=29436904&auto=1&height=66"></iframe>
</center>
```

<center>
<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width=330 height=86 src="http://music.163.com/outchain/player?type=2&id=29436904&auto=1&height=66"></iframe>
</center>
效果如上。
插入视频可以使用如下代码，在优酷视频页也选择通用代码可以获得`iframe`代码

```HTML
<iframe height=498 width=510 src="http://player.youku.com/embed/XMTY3MTU2MjY4NA==" frameborder=0 allowfullscreen></iframe>
```

<iframe height=498 width=510 src="http://player.youku.com/embed/XMTY3MTU2MjY4NA==" frameborder=0 allowfullscreen></iframe>
    
效果如上


安装过的插件
---

- [Mathjax](https://github.com/akfish/hexo-math)
- [Search](https://github.com/PaicHyperionDev/hexo-generator-search)


结语
---


真的是各种问题，要了我的小命了...
