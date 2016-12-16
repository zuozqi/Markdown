---
title: Memo For Buidling a Website  
date: "2016年8月21日01:25:31" 
categories: 工具
tags: [Github,Jekyll]  
---
总体的步骤
===
- 注册域名
- 申请github账户
- 进行解析
- 在账户里新建项目
- 项目设置
- Jekyll设置
<!-- more -->

这种方法的优点：

*不需要操心空间的问题，解析以后就不用管了，十分十分方便。*

---



注册域名
===

这里是在[阿里云](https://account.aliyun.com/)上购买的，选择了.space作为顶级域名，首先是因为有个人空间的含义，然而最重要的是因为他很便宜，首年只需要 ~~￥5~~,买了两年花了19块大洋，也就一顿外卖的价钱。

在阿里云上买域名还是很方便的，而且不需要通过实名认证，像“用作自己没事瞎搞搞”这种目的，是很契合的。
![yuming](https://raw.githubusercontent.com/zuozqi/MDPhotos/master/yuming.png)

申请github账户
===

这里只需要在[github](https://github.com/)上注册一个免费帐户就好，付费账户多的隐私现在还用不到，我这里也没有什么要隐藏起来的，~~还是贪便宜......~~

于是就有了自己的主页，这里如果想摆腾摆腾，弄得漂亮一点的话又是一个工作日...但是鉴于目的是建站，所以这里先略过不表。

![gzy](https://raw.githubusercontent.com/zuozqi/MDPhotos/master/gihubzy.png)

进行解析
===

之所以说阿里云方便，是它提供一个免费版的云解析，具体有什么限制还没有了解，但是是可以解析成功的，而且访问量、速度什么的，我 _并不是很在意_，所以这个版本就足够用了。

![jiexi](https://raw.githubusercontent.com/zuozqi/MDPhotos/master/jiexi.png)

解析式，在Github Pages帮助文档里，在[
Tips for configuring an A record with your DNS provider ](http://willingtobe.com/tips-for-configuring-an-a-record-with-your-dns-provider) 有提到，创建一个A记录指向 192.30.252.153/154 即可，这里我选择的是前者。

![jlz](https://raw.githubusercontent.com/zuozqi/MDPhotos/master/jiluzhi.png)

这样解析就搞定了，当访问域名时指向的就是上面那个IP，不过现在还没有内容，不要着急。

在账户里新建项目
===
在github账号主页的右上角的 '+' 里可以新建一个项目，**注意**如果新建的项目全称为 `username.github.io`的话，那么这个就会被当作这个用户的主页，也就是说如果生成页面的话，访问 username.github.io 的话，会被定向到这个项目下的页面。 当然别的项目也可以有自己的页面，不过初步想法是，这个页面当作主页，其他的项目的页面作为那个项目具体介绍的页面，把项目的地址放在主页的Project栏目里，当作二级页面。

**注意**需要勾选` Initialize this repository with a README`，要不生成的项目，，看不懂。。

![xm](https://raw.githubusercontent.com/zuozqi/MDPhotos/master/new.png)

这样就有了一个Github仓库，在仓库里可以放各种文件，当然包括建立博客需要的文件。

![ck](https://raw.githubusercontent.com/zuozqi/MDPhotos/master/repo.png)

项目设置
===

在项目页面的右上角会有`Setting`按钮，点击进入项目的设置界面，这里需要配置的是`Github Pages`这个栏。

在`Custom domain`中，可以添加自己的域名，这里把之前注册好并解析完成的域名填上去，点击`Save`,等待一会，就完成了，这样你的域名会指向当前项目的主页，但现在项目依然没有主页，需要进行下一步补充内容。

但需要 **注意** 的是，现在还不要在Setting里点 `Launch automatic page generator` 这个按钮，因为这种方法最后生成页面是不依赖这个的，如果点了，自动生成的页面将不是Jekyll里所产生的。

![setting](https://raw.githubusercontent.com/zuozqi/MDPhotos/master/setting.png)

Jekyll设置
===
在[JekyllThemes](http://jekyllthemes.org/) 选择自己喜欢的主题，下载后解压，在项目右上角同样有`Upload`这个按钮，点击后上传文件夹里的文件，然后在仓库里可以看到这些文件。

![Jekyll](https://raw.githubusercontent.com/zuozqi/MDPhotos/master/bank.png)

在打包好的主题中的`README.MD`中都有说明，这里补充几点 _重要_的。

-  `_config.yml` 
	在这个文件中，可以设置站点的标题，说明，联系方式等等，文件中都有明确的标识。还有一些诸如Google Analytics，Disqus之类我并不知道干什么的选项，这一个文件可以设置的有很多，可以以后钻研一下。
-  `CNAME`
	在这个文件中显示的是指向的域名
-  `_posts `文件夹
	在这个文件夹中，每增加一个`.md`文件，就会在主页上显示一篇博文，需要注意的是，博文的名字需要时'yy-mm-dd-Theme'，否则的话不会显示
-  `about.md`, `projects.md`
	这两个文件是主页上的两个栏目，可以在里面写一些个人简介，还有放一些自己做过的项目的链接，比较直观。
- `other` 
	其他的在各个主题介绍里有一些个性化的设置，可以看一下。

---

配置完成后，就可以访问域名然后直接看到有Jekyll生成的网站了！积累干货，想换主题的时候只需要保存'_posts','about.md','projects.md'三个文件里的内容，然后清空这个项目，再下新的主题就可以了（或者直接替换相应的文件）。