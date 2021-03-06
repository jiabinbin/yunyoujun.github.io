---
title: 教你如何从零开始搭建一个属于自己的网站
date: 2020-03-05 01:31:08
updated: 2020-03-05 01:31:08
tags:
  - 教程
  - Hexo
  - 分享
categories:
  - 云游的小安利
hide: true
---

> 写给想要拥有一个自己的网站但没有资金成本的小白与曾经的自己。

## 前言

虽说是网站，对于个人来说，或许一般叫作博客。
但我不希望它仅仅是一个博客，而是能够成为一个处于自己现实生活之外、自由、实验、不用畏惧他人眼光甚至可以独断专行的地方。

<!-- more -->

当然，这本质还是一个新手向教程，也许会有点科普的感觉。
我会从整体上对搭建网站的流程和使用到的技术及步骤进行介绍（因为要铺开讲，倘若包括轶事，实在太多太杂，我也会点到为止），并让你明白这个东西在网站的过程中起到什么样的作用。
但我不会就细枝末节展开叙述，譬如如何注册账号、安装时如何点击下一步。
我希望看完此篇文章后，此前对此方面知识一无所知的小白，到最后也能搭建出一个属于自己的站点。（前提是认识基础的英语单词和善用搜索引擎）

已经有所基础的同学大可跳读或者直接关闭。

> 注释处多为相关补充说明，对正常流程没有影响，若没有兴趣，可以略过。

与文章相关疑问都可在本文章的 GitHub Issues 中进行评论，其他疑问可到对应项目或文章下评论。

我会尽可能保持更新该文章所使用到的技术和做法，并随时接受勘误。

### 关键词

- Hexo
- 静态博客
- 无服务器
- GitHub Pages
- hexo-theme-yun（私货）

## 步骤

### 安装 Node.js

> **什么是 Node.js ？**  
> 这得从什么是 JS 说起，JS 也就是 JavaScript。（为什么有种从盘古开天辟地开始的感觉）没错，JavaScript 就是网页的盘古。JavaScript 是一种编程语言，我们所见到的网页中的交互和逻辑处理几乎都是由 JavaScript 完成。  
> JavaScript 语法简单，易学易用。（当然也请不要小瞧它，虽然它入门门槛低，但上限同样也很高。包括但不限于实现网站前后端，手机桌面应用程序，机器学习，计算机图形学等。）
> 在 Node.js 诞生前，JavaScript 都运行于浏览器端。也就是说，它是鱼，浏览器是装满了水的水缸。
> 2008 年，Chrome V8 诞生。2009 年，Node.js 诞生。并成为 GitHub 早期最著名的开源项目。GitHub 可能大家已有所了解，后续再说。  
> Node.js 便是一个基于 Chrome V8 引擎的 JavaScript 运行环境。（当年第一次看到这句话时，我也一脸懵逼。）按照我的理解，JavaScript 是鱼，Chrome V8 就是抽水机，Node.js 则把这台抽水机也装在你电脑上。于是你的电脑也有了 Node.js 这个和浏览器相似的水缸，也可以在里面运行 JavaScript 了！  
> 当然 Node.js 和浏览器端还是因为自身定位和一些历史原因而有些许区别的，不再展开。  
> [Node.js | 百度百科](https://baike.baidu.com/item/node.js/7567977)  
> [JavaScript | MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript)

[下载｜ Node.js](https://nodejs.org/zh-cn/)

建议下载**长期支持版**而非**当前发布版**（因为是最新版，所以容易出现一些奇妙的 bug）。

全部默认下一步进行安装。

Windows 打开命令提示符，macOS 打开终端。（= =，这个不会就请百度吧。）
Linux 用户右上角关闭本标签页。

后续如提到输入命令，均默认指打开终端进行输入。

输入 `node --version`，如果得到的版本号与你方才安装的一致，那么 Node.js 就已经成功安装。

### Git 与 GitHub

#### 安装 Git

> Visual Studio Code，简称 VS Code。
> 目前最为强大的编辑器，轻量且快速。（~~宇宙第一编辑器~~）
> 注意：它并不是我们常常听到的 VS，VS 常常指的是 Visual Studio，是一个功能强大的 IDE（集成开发环境），体积也相比 VS Code 都要大上一个量级。

在此之前，我建议你先安装 [VS Code](https://code.visualstudio.com/)。因为安装 Git Bash 时，可以设置 VS Code 作为默认编辑器。

> Git 是一个开源的分布式版本控制系统，由 Linus Torvalds（同时也是 Linux 的作者）为了管理 Linux 开发而开发。
> 简而言之，是一个版本管理工具。譬如设计师设计好了第三版的海报，客户却说还是要第一版吧，这时便可以通过 Git 快速回退到最初的版本。
> 你只需要把每次更改的状态（Git 会自动进行检测，你只要掌握基础的几条命令就可以了）告诉 Git，而不需要每个版本都保存一份压缩包，既方便也能大大节约空间。
> （当然这主要只对代码文本起作用，因为 Git 的本质是记录各行代码的增减，倘若是像视频、海报这类二进制文件来说便体现不出丝毫优势了。当然想要应对这种场景还有 [Git LFS](https://git-lfs.github.com/)。）

下载 [Git](https://git-scm.com/) 并安装（如果国内速度太慢，可以试试[这里](https://pc.qq.com/detail/13/detail_22693.html)）

macOS 用户可以下载官网的安装包进行安装，也可以直接安装 App Store 的 Xcode（附带会安装 Git，但是比较大）。

> 类似的工具还有：SVN。但始终更推荐 Git，因为它功能更为强大且它的背后还有更强大的生态：GitHub。

#### 注册 GitHub

> GitHub 一听便与 Git 有所渊源。`Git` 在英文中是懒人、饭桶之意。`Hub` 则是中心、集线器的意思。譬如 USB 集线器就是 USB Hub。所以 GitHub 就是饭桶中心（~~大雾~~）。  
> GitHub 是全世界最大的开源项目与代码托管平台，也是众多开发者的交流场所。~~还是全球最大的同性交友网站~~。
> 而代码托管本身用到的正是上文提到的 Git 技术。

注册 [GitHub](https://github.com/) 账号。（虽然都是英文，但不必畏惧，也并不会造成使用障碍，只要记得最常用的选项含义即可，以及善用手头的翻译软件。）

> 注意：注册时的英文用户名将成为你可以使用的免费域名前缀。

登录 GitHub。

> 为什么要用 GitHub？
> 对于平民玩家来说，在初次尝试建立自己的网站时，也许并不会有闲钱或者说决心来购买自己的服务器与域名。
> 而 GitHub 则提供了 [GitHub Pages](https://pages.github.com/) 这一服务。
> 用户们可以利用这一服务，部署自己的静态站点。

点击右上角的 `+` -> `New repository` 新建仓库。

![QQ20200305-221806@2x.png](https://i.loli.net/2020/03/05/pDZtlgQsLTb9k13.png)

> 我这里因为已经有同名仓库，所以提示了重复。

仓库名称务必为 `你的用户名.github.io`，用户名是英文，大小写无所谓，但建议统一小写。（因为你会发现时常切换大小写很麻烦）

> 为什么必须这个作为仓库名？
> GitHub Pages 服务的命名规范，同时它也将成为你的专属域名。当然，你也可以购置自己的专属域名并用它来提供内容。

点击 `Create repository`。

### 安装 Hexo

[Hexo](https://hexo.io)

- GitHub: <http://github.com/hexojs/hexo>
- [官方文档](https://hexo.io/zh-cn/docs/index.html)（直接参考文档也是一个不错的选择）

> **为嘛使用 Hexo ？**
> Hexo 是一个快速、简洁而强大的博客框架，基于 Node.js，同样托管于 GitHub 之上。生态中拥有众多插件主题。你可以基于它快速生成一些静态页面。
> 你可以使用别人的各种主题与插件，也可以自己定制开发想要的功能。
> **为什么不是...?**
> 其他常用的博客框架还有 [WordPress](https://wordpress.org/)，[typecho](http://typecho.org/)等，但这些往往都需要购置自己的服务器，而无法静态化地部署到 GitHub Pages 上。（当然，相应的功能和灵活性也大大提升。）
> 静态网站生成器还有 [Vuepress](https://vuepress.vuejs.org/)，[Gatsby](https://www.gatsbyjs.org/)等。但这些多是为了写文档而量身定制的，你也可以使用它们，但是相较 Hexo 的博客定位，它们关于博客的插件和主题以及解决办法会少得多。
> [Hugo](https://gohugo.io/) 提供的功能与 Hexo 几乎相同，不过它是基于 GO 语言。日后你想对自己的网站进行自定义，即便是 Hugo，你编写前端的交互仍旧需要使用 JavaScrip，所以选择基于 JavaScript 的 Hexo 可以降低学习成本。（你若对 GO 有兴趣，仍然可以尝试使用 Hugo，但本教程将不会针对 Hugo 进行展开。）
> 所以对于新手来说，使用 Hexo 作为起始点，不失为一个好选择。（当然如果你有钱租服务器，就可以考虑考虑 WordPress）

在终端中输入以下命令：

```sh
npm install hexo-cli -g
# 如果安装失败，可能是没有权限，可以尝试头部加上 sudo 重新执行
# sudo npm install hexo-cli -g
```

> `npm` 是随 Node.js 一起被安装的包管理工具，你可以理解成 Node.js 自带的应用商店。
> `install` 自然是安装。
> `hexo-cli` 则是 `hexo` 的终端工具，可以帮助你生成一些模版文件，之后再用到。
> `-g` 代表的是全局安装。也就是在任何地方都可以使用，否则会只能在安装的目录下使用。

此时，请先通过 `cd` 进入你本地电脑打算存储网站代码的文件夹目录。（或者右键文件夹 Git Bash Here）

> [cd | DOS 命令](https://baike.baidu.com/item/cd/3516393)  
> [cd （LINUXSHELL 命令）](https://baike.baidu.com/item/cd/3516411)

譬如：

> 注意：这里是你自定义的目录，请不要复制粘贴

```sh
# '#' 字符后的文字代表注释，不需要输入
# Windows
cd C:\Users\YunYou\Documents\GitHub\
# macOS
# cd /Users/yunyou/github/
```

接下来输入：

```sh
hexo init 你的名字.github.io
```

> `hexo` 正是因为我们之前安装了 `hexo-cli` 这一个包，所以我们可以在终端中使用 `hexo` 这一命令。
> `init` 初始化博客的模版文件。后面跟的是你要新建的文件夹，最好和你此前新建的仓库名一致。

```sh
# 进入你的博客文件夹
cd 你的名字.github.io
# 默认安装所有 `package.json` 文件中提到的包
npm install
# 你也可以缩写成 hexo s
hexo server
```

`server` 代表开启本地的 Hexo 服务器，这时你就可以打开浏览器，在地址栏中输入 `localhost:4000` 就可以看到本地的网页了。

按 `Ctrl + C` 终端服务器的运行。

至此，基础的模版页面便已经搭建好了。

#### 使用 Hexo 主题

Hexo 默认提供的是 [hexo-theme-landscape](https://github.com/hexojs/hexo-theme-landscape) 主题。
默认主题样式简单，功能较少。所以大多数人并不会使用默认主题。

这里将示范如何使用我自己开发的主题 [hexo-theme-yun](https://github.com/YunYouJun/hexo-theme-yun)（\_(:з」∠)\_ 顺带求 Star）。
你可以前往 [云游君的小站](https://www.yunyoujun.cn) 查看示例效果。

当然，你也可以在 [Themes | Hexo](https://hexo.io/themes/) 发现更多有趣美丽的主题。使用方法大致相同。
当你具备一定开发能力时，你可以开发属于自己的主题，或者为 hexo-theme-yun 提交 [PR](https://github.com/YunYouJun/hexo-theme-yun/pulls) 添加你想要的功能。

- [hexo-theme-yun - GitHub](https://github.com/YunYouJun/hexo-theme-yun)
- [hexo-theme-yun 使用文档](https://yun.yunyoujun.cn)：更详细的配置进阶指南。
- [示例效果](https://www.yunyoujun.cn)

##### 下载 Hexo 主题

进入终端（确保路径处于你此前使用 Hexo 初始化好的文件夹目录下，后简称为 `Hexo 目录`），输入以下命令。

> 实际上你也可以直接在 VS Code 中使用终端。

```sh
git clone https://github.com/YunYouJun/hexo-theme-yun themes/yun
```

> 这里便使用到了我们此前安装的 Git，`git clone` 即代表克隆（也就是复制的作用）我的主题（托管于 GitHub，链接便是主题所在的地址），`themes/yun` 则代表放在你 Hexo 文件夹下的 `themes/yun` 文件夹里（没有该文件夹会自动新建）。

##### 编辑 Hexo 配置

> 右键文件夹使用 VS Code 打开，或者进入 VS Code 打开你存储网站的文件夹。此后操作都将默认你已处于该工作目录下。

在你此前通过 Hexo 初始化生成的文件目录下，会存在一个 `_config.yml` 文件。

> `yml` 是 [YAML](https://baike.baidu.com/item/YAML/1067697) 文件的后缀名，YAML 是 "YAML Ain't a Markup Language"（YAML 不是一种标记语言） 的缩写，但它实际上还是一种标记语言。你可以将其理解为存储数据的一种文本格式，这也是其诞生的目的。 如果你听说过 JSON，那你就更能明白它是干什么的了。

它是 Hexo 的配置文件，关于各配置选项的意义你可以查看 [配置 | Hexo](https://hexo.io/zh-cn/docs/configuration)。

在 `_config.yml` 中找到 `theme` 这个字段，将其后的 `landscape` 修改为 `yun`。

```yml
theme: yun
```

> pug 是一种模板引擎，可以渲染为 HTML 字符串。类似的还有 ejs，swig 等，语法和设计理念有所不同。
> stylus 是一种 CSS 预处理器，可以渲染为 CSS。类似的还有 scss，less，同样只是语法和设计理念有所差异。

由于我的主题使用了 pug 和 stylus，而 Hexo 自带的一般是 ejs 与 stylus，所以你可能还需要输入以下命令安装渲染器。

```sh
npm install hexo-render-pug hexo-renderer-stylus
```

这时再像此前那般使用 `hexo server` 重新启动服务器，你就可以看到一个不一样的主题风格的页面了。

##### 自定义主题配置

当启动时，会使用主题的默认配置。但这不一定是你想要的。
所以你可以对主题进行一些自定义。

主题的配置文件放在 `themes/yun/_config.yml` 文件中。
且慢，你最好不要直接修改主题的默认配置。倘若日后主题升级更新了怎么办吗，难道还要重新配置一遍吗？

最好的解决方案就是新建 `source/_data/yun.yml`。（若 `source/_data` 目录不存在，请新建）

本主题将自定义配置与默认配置进行合并，因此你只需要在 `yun.yml` 文件中自定义你需要的配置即可，其余仍将自动采用默认配置。

譬如我们需要更换头像。在 `yun.yml` 中填写。

> 你可以在 `source` 文件夹下新建 `images` 文件夹，用来存储你的图片。
> 也可以使用 [SM.MS](https://sm.ms/) 上传你的图片文件，获取在线链接。

```yml
avatar:
  url: /images/avatar.jpg # 你的头像图片地址
  rounded: true
  opacity: 1
```

更换主题色彩，比如换成黑色，黑色的十六进制颜色代码是 `#000000`。

```yml
colors:
  primary: "#000000"
```

这时你的主题色调就会变为黑色。

这只是一个配置项的简单示例，更多配置你可以参考我的[主题文档](https://yun.yunyoujun.cn) 或直接在 `theme/yun/_config.yml` 中查看，并根据自己的需要进行配置。

### 生成静态文件

至今我们的工作都是在本地进行，想必你也很想放到线上与小伙伴们分享。
这便轮到了 GitHub Pages 的出场，不过 GitHub Pages 只支持纯静态文件。

所以我们需要使用以下命令先来生成站点的静态文件。

```sh
# 如果进行多次生成，为了避免受错误缓存影响，最好使用 hexo clean 先清除一遍。
hexo generate
# 缩写为 hexo g
```

此时你的文件夹目录下会出现 `public` 这个文件夹，里面存放的就是你站点的静态文件。

### 与远程仓库建立关联

接下来我们将本地的仓库与此前在 GitHub 上建立的仓库建立关联。

```sh
git init # 初始化 Git 仓库，只需要执行一次即可
```

在将其部署到 GitHub Pages 上之前，我们最好先建立一个分支。

> 什么是分支？
> Git 提供了版本管理功能，其中还有一个分支功能，你现在可以简单地将其理解为平行世界。

`你的名字.github.io` 部署后，GitHub Pages 将默认使用你的 master 分支作为静态文件部署。
所以我们最好新建一个 hexo 分支（命名无所谓）用来存储 Hexo 地源代码，master 分支则用来存储部署后的静态文件。

```sh
git checkout -b hexo
```

这时便成功建立了一个 hexo 分支。（此后的工作都将在 hexo 分支下进行）

你可以通过 `git branch -v` 来查看当前有哪些分支，使用 `git branch 分支名` 来切换到哦对应的分支。

> [Git 学习笔记](https://www.yunyoujun.cn/note/git-learn-note/)

### 部署

为了更方便的部署到 GitHub Pages，Hexo 提供了 `hexo-deployer-git` 插件。

老规矩，安装。

```sh
npm install hexo-deployer-git
```

在 `_config.yml` 中配置。

```yml
deploy:
  type: git
  repo: 你此前新建的仓库的链接 # 比如：https://github.com/YunYouJun/yunyoujun.github.io
  branch: master # 默认使用 master 分支
  message: Update Hexo Static Content # 你可以自定义此次部署更新的说明
```

保存，部署！

> 第一次可能需要你输入用户名与密码。
> 密码输入的时候不会出现 \*\*\*，不要害怕，已经输入进去了。

```sh
hexo deploy
```

等待完成后，打开网址 `https://你的名字.github.io` 就能看到你的线上网站了。

> 使用 https，http 可能无法正常打开。HTTPS 是多了安全加密的 HTTP，Chrome 浏览器已经默认会显示 `http` 链接为不安全。
> 为了安全，建议开启强制 https 跳转。`项目地址页面 -> Settings -> Options -> GitHub Pages -> Enforce HTTPS`。（翻到下面）
> 此时，http 网址会自动重定向到 https

## FAQ

### 视频？

没有视频，一是懒，二是文字更利于更新勘误。

以及文章中将会频繁出现参考链接，更方便使用。

### 如何绑定你的自定义域名？

<!-- 在 `Hexo` 分支下新建 `CNAME` 文件（没有后缀名）。

内容填写你的域名即可。 -->

---

To Be Continued.

<!-- Q.E.D. -->
