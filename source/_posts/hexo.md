---
title: hexo 搭建并配置material主题
date: 2018-05-11 17:03:23
tags: [hexo,material]
categories: 教程
---
阅读这篇文章，你将获得的知识技能有，hexo的搭建、material 主题的安装

#### 在写最前面
本文默认你已经在所使用的环境中安装了 git 、 node，如果没有请查看相关官方文档进行安装。
[git官方安装教程](https://git-scm.com/downloads)
[node官方安装教程](https://nodejs.org/zh-cn/)

#### hexo的安装

``` bash
$ npm install -g hexo-cli
```
遇到问题或了解详细信息: [点击这里](https://hexo.io/zh-cn/docs/)

#### 创建项目

安装 Hexo 完成后，请执行下列命令，Hexo 将会在指定文件夹中新建所需要的文件。
``` bash
$ hexo init <folder>
$ cd <folder>
$ npm install
```

此段借鉴hexo官方文档,更多信息请参考官方文档: [文档地址](https://hexo.io/zh-cn/docs/setup.html)

#### 自定义配置文件

项目根目录下 `_config.yml` 即为整个站点的配置文件
具体配置参数详解: [点击这里](https://hexo.io/zh-cn/docs/configuration.html)

#### 安装material主题

+ material主题下载: [下载地址](https://github.com/viosey/hexo-theme-material#download-%E4%B8%8B%E8%BD%BD)
+ material主题安装与启用: [点击这里](https://material.viosey.com/docs/#/start?id=%E5%AE%89%E8%A3%85%E3%80%8Cmaterial%E3%80%8D)
+ material主题配置: [点击这里](https://material.viosey.com/docs/#/config_basic)

#### 本地测试运行

在你完成上面的教程并按照自己的喜好自定义配置之后，我们需要本地运行，看下效果。在项目根目录运行以下命令，并用浏览器打开 http://localhost:4000 即可看到运行效果。
``` bash
$ hexo server
```

#### 部署到github

关于这一块网上有很多文章，我这边也就不赘述了，直接贴上教程地址: [用Hexo + github搭建自己的博客 --- 再也不用羡慕别人了！](https://blog.csdn.net/Hoshea_chx/article/details/78826689)

#### 写在最后

当你已经部署到github以后，就可以通过   <username\>.github.io 访问你自己的博客了,如遇到任何问题可在下方评论，很乐意帮你解决问题。
