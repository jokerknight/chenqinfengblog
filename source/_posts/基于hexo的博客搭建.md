title: " 基于hexo的博客搭建"
date: 2016-10-31 14:38:00 
categories: [博客,hexo]
tags: [博客]
---


# 基于hexo的静态博客搭建
## 概念
以Hexo作为博客框架，国外通过github，国内通过码市作为托管平台的基于markdown语法的博客系统
## 关键词
* hexo
> A fast, simple & powerful blog framework, powered by Node.js. 
> 一个快速的强大的博客框架，由node.js驱动。
* github,gitcoding
> 国内和国外强大的代码托管平台
* markdown
>Markdown 是一种轻量级标记语言，它允许人们使用易读易写的纯文本格式编写文档，然后转换成格式丰富的HTML页面。 
—— 维基百科

Markdown的意义，就在于即使是门外汉，也能掌握，并且轻松获得满足感。
* git
> Git是一款免费、开源的分布式版本控制系统，用于敏捷高效地处理任何或小或大的项目 

github,与gitcoding都是基于git的社交性代码托管平台
* nodejs
> 简单的说 Node.js 就是运行在服务端的 JavaScript。
Node.js 是一个基于Chrome JavaScript 运行时建立的一个平台。
Node.js是一个事件驱动I/O服务端JavaScript环境，基于Google的V8引擎，V8引擎执行Javascript的速度非常快，性能非常好。

由于hexo是基于Node.js的，所以需要了解部分nodeJs的npm包管理机制，方便搭建hexo
* 静态博客
> 静态博客就是只支持HTML静态页面，无法使用ASP.PHP等

既然是静态页面，那怎么支持评论系统？博客数据怎么存储呢？这就需要一些外部的系统来支撑了，比如评论系统就需要"多说"这种外部系统帮你做统计，博客数据其实都是通过markdown生成了静态的html页面存储在你的本地和github等托管平台。

* DNSPod
用来做域名映射，这里需要一个小诀窍，国外网站用github做托管，国内网站用码市做托管
## 环境搭建
### 安装Node.js 
因为Hexo是一款基于Node.js的静态博客框架，所以我们还需要安装好它：
=[下载Node.js][1]
到node.js 官网下载针对自己电脑版本的最新的版本，一路安装即可。
### 安装Git
我们很经常会要用到Git以及Github，接下来，来安装Git：
=[下载Git][2]
选择合适的版本下载然后安装，我们稍后将会用上。
### Hexo
安装好Git和Node.js之后，轮到我们今天的主角登场了~先打开Git Bash，然后输入下面这条命令来安装Hexo：
`npm install hexo-cli -g`
安装之后通过
`npm -v`
来检测是否安装成功,如果出现相关版本号无报错则安装成功
接下来
#### 新建博客
在D盘新建一个叫blog的文件夹，使用git bash进入这个目录，并且初始化为我们的博客目录:
> D:
> cd blog
> hexo init

#### 写新文章
环境搭建好之后可以通过两个途径创建文章
1. `hexo new "Hello"`
2. 进入hexo init的目录中找到_post目录下新建"hello.md"文件
我们找到这个文件之后，就可以编辑自己的内容了

#### 生成静态页面
`hexo generate`
#### 预览
`hexo server` 
如果环境配置正确的话应该可以通过=[http://localhost:4000][3] 访问进行预览了

#### 配置Github

首选需要建立repository与你用户名对应的仓库，仓库名必须为【your_user_name.github.io】，固定写法

然后建立关联，我的blog在本地/Users/leopard/blog，blog是我之前建的东西也全在这里面，有：

    _config.yml    node_modules    public      source

    db.json        package.json    scaffolds  themes

现在我们需要编辑_config.yml文件来进行关联
翻到最下面，改成我这样子的,这里配置了码市与github pages的deploy渠道.

  > deploy:
  >  - type: git
  >    repo: https://github.com/jokerknight/jokerknight.github.io.git
  >    branch: master
  >  - type: git
  >    repo: https://git.coding.net/chenqinfeng/chenqinfeng.git
  >    branch: gitcafe-pages

然后执行命令：

npm install hexo-deployer-git --save

#### 发布
`hexo deploy`
访问=[http://jokerknight.github.io][4] 就可以访问刚才发布的博客了
#### 域名绑定
1. 申请域名
2. 注册DNSPOD
3. 配置映射路径
![](http://ww3.sinaimg.cn/large/9efac112gw1f9dy76bgnjj20ok090myy.jpg)
国外配置github的ip，国内配置coding的地址，这样可以加快访问速度。
#### 部署步骤
每次的部署步骤简单来说就是三个步骤
`hexo clean`
`hexo generate`
`hexo deploy`
#### 一些常用命令
hexo new"postName" #新建文章

hexo new page"pageName" #新建页面

hexo generate #生成静态页面至public目录

hexo server #开启预览访问端口（默认端口4000，'ctrl + c'关闭server）

hexo deploy #将.deploy目录部署到GitHub

hexo help # 查看帮助

hexo version #查看Hexo的版本

#### 推荐的hexo 主题

=[Cover][5]- A chic theme with facebook-like cover photo

=[Oishi][6]- A white theme based on Landscape plus and Writing.

=[Sidebar][7]- Another theme based on Light with a simple sidebar

=[TKL][8]- A responsive design theme for Hexo. 一个设计优雅的响应式主题

=[Tinnypp][9]- A clean, simple theme based on Tinny

=[Writing][10]- A small and simple hexo theme based on Light

=[Yilia][11]- Responsive and simple style 优雅简洁响应式主题，我用得就是这个。

=[Pacman voidy][12]- A theme with dynamic tagcloud and dynamic snow

#### 一些基本路径
文章在source/_posts, 文章支持Markdown语法，可以使用一些MarkDown渲染工具。
如果想修改头像可以直接在主题的_config.yml文件里面修改，友情链接，之类的都在这里。

#### Markdown语法参考链接
=[参考链接][13]



  [1]: https://nodejs.org/en/download/
  [2]: https://git-scm.com/downloads
  [3]: http://localhost:4000
  [4]: http://jokerknight.github.io
  [5]: https://github.com/daisygao/hexo-themes-cover
  [6]: https://github.com/henryhuang/oishi
  [7]: https://github.com/hardywu/hexo-theme-sidebar
  [8]: https://github.com/SuperKieran/TKL
  [9]: https://github.com/levonlin/Tinnypp
  [10]: https://github.com/yunlzheng/hexo-themes-writing
  [11]: https://github.com/litten/hexo-theme-yilia
  [12]: https://github.com/Voidly/pacman
  [13]: http://www.appinn.com/markdown/