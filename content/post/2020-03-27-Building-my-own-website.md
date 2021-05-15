---
title: 关于这个网站的诞生
date: 2020-03-27 T00:00:00+08:00
hero: "/images/fengm333.jpg"
excerpt: 使用HUGO搭建属于自己的网站！
timeToRead: 15
authors:
- lele zhu

---
前段时间看了Clfolios站上的作品集，就挺羡慕里面的设计师能有一个自己的个人网站展示作品哼哼╰(艹皿艹 )，别人有的我也得有！！！那就开搞吧\~但是我的JavaScript就真还没来得及学透彻，只靠html、CSS其实也能弄，但因为就真的太想赶紧拥有，善用搜索发现可以抄近路，感觉还蛮简单的！！于是花了三个晚上的时间，完成了方法研究、框架选择、git部署、上域名等一系列环节，成功将这个网站上线。

写篇文档记录一下，搭建的整个过程嘻嘻嘻\~

## 搭建方式

HUGO框架+Github+Netifly+aliyun

## 什么是HUGO？

根据官方文档的说法：Hugo是由Go语言实现的静态网站生成器。简单、易用、高效、易扩展、快速部署。

你可以选择站点上的喜欢的主题模板，然后根据自己的实际需要将部分的内容进行定制化修改，比如LOGO、导航栏、文本等。

那么他跟平时的建站工具有什么区别，整体下来我认为有这几个优点：速度快、成本低、灵活性强、参与感高。

* 速度快：如果只是搭建起来能本地预览，只要几行命令，十分钟以内足够了。
* 成本低：很多开源的主题，都是免费的，但部分的文档写得不是很好。
* 灵活性强：如果你有一点前端代码基础，基本上认真读文档，想改什么改什么！
* 参与感高：相较于一站式的建站工具，自己完成代码修改、部署上线就跟玩游戏通关一样更快乐\~

## **接下来就开始啦！**

### 1、 Install Hugo

在[https://github.com/gohugoio/hugo/releases](https://github.com/gohugoio/hugo/releases "hugo安装")，找到适合系统环境的版本进行下载，同时可以把GO、Git的工具一同进行安装。

![](/images/dingtalk_20210515152908.jpg)

具体的安装步骤可以参考HUGO的官方文档，安装成功后，cmd 执行hugo version 出现版本号信息意味着就是安装成功了。

```js
hugo version
```

### 2、 挑选喜欢的主题模板

移步：[https://themes.gohugo.io/](https://github.com/gohugoio/hugo/releases "hugo安装")

可以在进入相应的模板查看他的文档、Demo，点击download一般就是跳转到github相应的仓库。![](/images/dingtalk_20210515153816.jpg)

### 3、 新建一个hugo项目

打开cmd转到hugo文件夹内，执行

```js
 hugo new site [项目名]
```

PS.如果主题文档给出config文件格式是yaml，则需要加上 -f yml，否则默认生成的配置文件是toml类型。

![](/images/新建项目.gif)

这时候hugo文件夹内会出现一个新的文件夹

### 4、把主题下载到本地

```js
cd [项目名] # 进入到项目文件夹内
git clone https://github.com/... #下载主题文件
```

下载你喜欢的主题，这个地址一般在对应主题的文档里或者github上都能获取到。

![](/images/git-clone.gif)

### 5、修改config文件

接下来，需要修改一下config文件，将主题文档提供的复制下来覆盖掉本地项目文件夹内的内容，并保存。

![](/images/改配置.gif)

到这里，这个网站已经可以在本地进行预览了！

```js
hugo #生成public文件夹
hugo server  #预览项目
```

![](/images/预览.gif)

### 6、发表一篇文章

一般文章的格式都是markdown，可以看看主题的文档里有没有参考的格式，创建一个markdown文件，把格式粘贴进去，把标题、内容以及你想改的地方修改一下，保存到项目文件中的content文件夹内，再次使用上面的预览方法，就可以看到文章成功出现在页面上啦( •̀ ω •́ )y

![](/images/q5j6w-emiae.gif)

![](/images/mmz0i-pz2uj-1.gif)

### 7、通过git部署

可以将项目部署到github上，就可以通过网络来访问到这个搭建好的页面，当然这时候你需要一个github账号，注册方式就不赘述了\~如果你想用github page功能，则需要创建一个“你的用户名.github.io”的仓库（一定要这个名字，不然是不能直接打开滴）

![](/images/cangku.gif)

如果电脑上已经安装好git，就可以直接通过在 项目/public文件夹内，右键选择git bash here，然后👇

```js
git init
git add -A
git commit -am“init”
git remote add orgin https://github.com/github用户名/github用户名.github.io.git
git push -f origin master
```

成功之后就可以在github仓库看到成功git上去的文件了！！

只要访问 github用户名.github.io ，就可以在线访问网站啦！

![](/images/git.gif)

![](/images/777.gif)

**以上就是HUGO框架通用的方法。**

我这次选择的主题是：

[https://themes.gohugo.io/hugo-theme-novela/](https://themes.gohugo.io/hugo-theme-novela/ "novela主题")

这个文档提供了一种更快速的部署方式，能够一键部署到github上，后续我直接使用了netlify在线部署工具，通过github授权登录，直接将网站部署上去就ok了，注意的是需要设置好相关的参数，一般参数都会写在文档里面，跟着设置就行了。

![](/images/2.png)

部署成功后，可以进行预览\~（没部署上去，一般就是参数没设置好，多看几遍文档琢磨一下就行了）

![](/images/3.png)

部署成功后，可以进行预览，预览后觉得没问题的话，想上域名就可以在Domains上设置，域名可以在阿里云上购买，解析后，完成相关设置就ok了！

![](/images/4.png)

### 最后...

自己亲自搭一个网站还是非常有趣的！过程中虽然遇到了很多问题，比如git不上去、部署失败、找不到修改页面某些元素的方法等等，其实可以通过多看几个文档、多尝试几遍就可以解决了！因为是比较热门的开源项目，可以通过github找到也用这个项目的人，把他们的项目弄下来在本地多看几遍，对比一下就知道问题出在哪里了！！！如果过程中，出现报错，善用baidu或google都能解决的\~