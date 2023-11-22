---
title: 从零搭建个人博客-Hexo+Github
top: false
cover: false
toc: true
mathjax: true
date: 2023-04-02 16:42:10
password:
summary:
tags: [前端,]
categories: [前端,]
---


# 从零搭建个人博客-Hexo+Github

这是本博客站的第一篇博客，毫无疑问，将本次建站的完整过程记录下来，作为第一篇博客实在是非常有意义。

## 起因

在自己建站之前，我在CSDN上已经有相当大规模的浏览量了。但是，考虑到

1. 写作自由
2. 流量变现
3. 学习新技术

这三种因素，因此决定自己搭建个人博客站。

在这个过程当中，我学了相当多的技术，探索了很多中建站方案，无论是wordpress，还是个人手动造轮子等。

**但综合来看，还是觉得hexo+Github的方式最合适初次建站。**

原因如下：

1. **廉价**

一般的服务器，最便宜的海外服务器，一般都是要`50美元/年`起步的价格。这对很多初学者来说，都应该是一笔算得上是不低的开销。
但是从目前这个方案来做的话，因为服务端是放在了Github上，所以实际上是不需要花费任何钱的。

2. **效率**

相比于，其他诸如wordpress来说，很多人说着已经有很多预设好的方案，什么一键建站来着，但是实际上，背后引入了太多技术，导致了有相当多的内容需要管理了。而，很多时候，其实就是想要很简单的-- **博客好看+方便写**。至于说是像什么数据库管理，降低内存压力，提高超大规模访问容量上限等，这些我觉得对初次建站来说都是意义不大的。

3. **简洁**

由于hexo是非常轻量级的框架，虽然对于很多人来说，失去了繁杂的功能，但是我还是比较喜欢简洁化的页面。看着清新简洁的画面，实在是有一种莫名的舒适感。


## 准备工作

说是从零开始，但是当我真的开始写这篇博客的时候，我也是发现其实还是有很多东西需要考虑的。

**需要准备好的内容:**

根据下面链接，应该基本上都能完成配置。

* Github账户，<https://github.com/> Sign up即可
* 本地电脑上，安装，确保在命令行下能用即可
  * Git
    * <https://git-scm.com/downloads>
    * <https://www.cnblogs.com/xueweisuoyong/p/11914045.html>
  * nodejs
    * <https://nodejs.org/en/download> 
    * <https://www.runoob.com/nodejs/nodejs-install-setup.html>
* 生成本地的ssh-key，上传到个人Github的setting上 
  * <https://blog.csdn.net/a19990412/article/details/127839737>


## 创建一个的github.io的仓库

* 在Github上，创建一个名为`<用户名>.github.io`的仓库。
    * 这里的`<用户名>`为你Github账户的名字
    * 全部大写改成小写
    * 比如，我的Github名字是SeanQuant，这里我创建的仓库名字的就是`seanquant.github.io`
    * 设置为`Public`
* 这里的你的网站其实已经搭建好了，只不过里面的东西是空的而已。之后我们就是通过hexo的生成出来完整的网站数据最后，再部署在github上。


## 下载hexo

下面操作基本都在命令行下进行，但需要注意的是，windows推荐使用git的命令行，而不是默认的powershell，或者是cmd
不然可能会报错。

* 先创建一个文件夹，用来管理整个博客项目，包括以后写博客存放数据，比如，我放在了`D:\workplace\blogs`
* 进入这个目录，然后`npm i hexo-cli -g`

这样就完成了，检查是否完成，可以输入下下命令的命令，看下输出

```sh
hexo -v
```

* 如果输出是类似于下面这样就可以了

```bash
Sean@LAPTOP-F4VS0BRC MINGW64 /d/workplace/blogs (master)
$ hexo -v
INFO  Validating config
hexo: 6.3.0
hexo-cli: 4.3.0
os: win32 10.0.22621
node: 18.15.0
v8: 10.2.154.26-node.25
uv: 1.44.2
zlib: 1.2.13
brotli: 1.0.9
ares: 1.18.1
modules: 108
nghttp2: 1.51.0
napi: 8
llhttp: 6.0.10
uvwasi: 0.0.15
acorn: 8.8.2
simdutf: 3.1.0
undici: 5.20.0
openssl: 3.0.8+quic
cldr: 42.0
icu: 72.1
tz: 2022g
unicode: 15.0
ngtcp2: 0.8.1
nghttp3: 0.7.0
```


* 初始化网站

```
hexo init
```

* 安装必要组件


```
npm install
```

* 生成静态页面

```
hexo g
```

* 打开本地服务

```
hexo s
```

* 之后应该会输出一个链接，访问就可以了。一般来说是<http://localhost:4000/>

这样就算是完成了最基本的事情了。


## push到github上

* 如果是在这个电脑上第一次使用git，需要配置一下，名字跟邮箱。否则，不需要 

```
git config --global user.name "your name"
git config --global user.email "your email"
```