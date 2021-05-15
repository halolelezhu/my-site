---
title: 关于这个网站的诞生
date: 2020-03-20
hero: "/images/hero-2.jpg"
excerpt: With the growing community interest in Gatsby, we hope to create more resources
  that make it easier for anyone to grasp the power of this incredible tool.
timeToRead: 4
authors:
- lele zhu


---
前段时间看了Clfolios的作品集，就挺羡慕里面的设计师能有一个自己的个人网站展示作品哼哼╰(艹皿艹 )，别人有的我也得有！！！那就开搞吧~但是我的Javascript就真还没来得及学透彻，只靠html、CSS其实也能弄，但因为就真的太想赶紧拥有，善用搜索发现可以抄近路，感觉还蛮简单的！！于是花了三个晚上的时间，完成了方法研究、框架选择、git部署、上域名等一系列环节，成功将这个网站上线。
写篇文档记录一下，搭建的整个过程嘻嘻嘻~





## 搭建方式
HUGO框架+Github+Netifly

## 什么是HUGO？

根据官方文档的说法：Hugo是由Go语言实现的静态网站生成器。简单、易用、高效、易扩展、快速部署。
你可以选择站点上的喜欢的主题模板，然后根据自己的实际需要将部分的内容进行定制化修改，比如LOGO、导航栏、文本等。
那么他跟平时的建站工具有什么区别，整体下来我认为有这几个优点：速度快、成本低、灵活性强、参与感高。

- 速度快：如果只是搭建起来能本地预览，只要几行命令，十分钟以内足够了。 
- 成本低：很多开源的主题，都是免费的，但部分的文档写得不是很好。
- 灵活性强：如果你有一点前端代码基础，基本上认真读文档，想改什么改什么！
- 参与感高：相较于一站式的建站工具，自己完成代码修改、部署上线就跟玩游戏通关一样更快乐~


### Step 1 Install Hugo

During the Bootstrap sequence, which occurs every time you run \$ gatsby develop, there are about 20 events that fire ranging from validating your gatsby-config.js to building the data schemas and pages for your site. For example, the Bootstrap sequence is where Gatsby will create pages. If you want an in depth look of all 20 Bootstrap steps Swyx shared a fantastic Gist that goes into more detail.

### Step 2 挑选喜欢的主题模板

The Build sequence is very similar to the Bootstrap sequence, except it’s run with production optimizations and will output static files ready for deployment. Think of it as building your React application in production mode vs development.

### Step 3 新建一个hugo项目
打开cmd转到hugo文件夹内，执行
```js
hugo new site [项目名]
```

PS.如果主题文档给出config文件格式是yaml，则需要加上 -f yml，否则默认生成的配置文件是toml类型。

这时候hugo文件夹内会出现一个新的文件夹

### Step 3 把主题下载到本地
```js
cd[项目名] 进入到项目文件夹内
git clone https://github.com/...
```

下载你喜欢的主题，这个地址一般在对应主题的文档里或者github上都能获取到。 

### Step 4 修改config文件
接下来，需要修改一下config文件，将主题文档提供的复制下来覆盖掉本地项目文件夹内的内容，并保存。

到这里，这个网站已经可以在本地进行预览了！
```js
Hugo
hugo server 
```
What are the Gatsby specific files for?
gatsby-config.js
A place to put all your site configurations such as plugins, metadata, and polyfills. This file is the blueprint of your application and is where Gatsby really shines with its plugin system. When you run $ gatsby develop or $ gatsby build gatsby-config.js is the first file to be read and validated.

Most of your time spent in gatsby-config.js will likely revolve around source plugins, image plugins, offline support, styling options, and site metadata.

gatsby-node.js
Gatsby runs a Node process when you develop or build your website and uses Webpack under the hood to spin up a development server with hot reloading. During the Node process Gatsby will load plugins, check the cache, bootstrap the website, build the data schema, create pages, and deal with some configuration and data management.

Everything that occurs during the Bootstrap and Build sequences occurs in gatsby-node.js. This means it’s the perfect place to create pages dynamically based off data from a source plugin or modify Gatsby’s Webpack or Babel configs.

For example, if you want to move some files manually, such as a Netlify \_redirects file, a good place to do it is in your gatsby-node.js file at the onPostBuild lifecycle hook.

From experience, most of my time has revolved around handling data and building pages in gatsby-node.js. This file quickly becomes the piping of your entire website.

## Examples of gatsby-node.js hooks:

- createPages
- onCreateBabelConfig
- onCreateWebpackConfig
- onPostBuild
- gatsby-ssr.js

When you think Server Side Rendering you think of a server that takes in requests and dynamically builds pages and sends it to the client. Gatsby doesn’t do that, but it does server side render — it generates all the pages during build time.

Naturally, gatsby-ssr.js allows developers to hook into that lifecycle. In my experience, most use cases revolve around injecting CSS, HTML, or Redux state information into the generated output. For example, if you need to insert third party scripts such as Analytics Tracking or a Pixel it can be done on the onRenderBody gatsby-ssr.js hook.

## Examples of gatsby-ssr.js hooks:

- onPreRenderHTML
- onRenderBody
- replaceRenderer
- gatsby-browser.js

Gatsby is a static site that loads a dynamic application after initial load, which means you get the benefits of a static site in a web application. gatsby-browser.js provides convenient hooks to deal with app loading, route updates, service worker updates, scroll positioning, and more.

Everything that occurs after your static site has loaded can be hooked in gatsby-browser.js. For apps that I’ve built, gatsby-browser.js was mostly used for keeping track of routes, scroll positioning, and sending analytics events.

## Examples of gatsby-browser.js hooks:

- onClientEntry
- onRouteUpdate
- onServiceWorkerInstalled
- registerServiceWorker
- shouldUpdateScroll

## Conclusion

Gatsby is built with React at its core and shares a common API pattern, the lifecycle. This lifecycle gives developers access to key moments in their website’s process through specific hooks. For example, adding analytics can be achieved through the Browser lifecycle hook onClientEntry. Gatsby reserves specific filenames as an entry point to access every lifecycle; these files are named gatsby-node.js, gatsby-ssr.js and gatsby-browser.js.

Without the Gatsby lifecycle, it would be impossible to customize and modify your project beyond the base configuration, leaving developers with a rigid and poor developer experience. This power and flexibility has helped us build amazing web projects for clients like Hopper!

Gatsby is a staple within our engineering process at Narative, helping us help our clients build the products they’ve always dreamed of, and the ones they’re yet to dream up.