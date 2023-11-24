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

说是从零开始，但是当我真的开始写这篇博客的时候，我也是发现其实还是有一些东西需要考虑的。

**需要准备好的内容:**

根据下面链接，应该基本上都能完成配置。

1. 准备一个Github账户，<https://github.com/> Sign up即可
2. 需要配置好环境，确保在命令行下能用即可
  1. Git
    * <https://git-scm.com/downloads>
    * <https://www.cnblogs.com/xueweisuoyong/p/11914045.html>
  2. nodejs
    * <https://nodejs.org/en/download> 
    * <https://www.runoob.com/nodejs/nodejs-install-setup.html>
3. 生成本地的ssh-key，上传到个人Github的setting上 
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

* 将上述的repo clone下来，然后进入该目录
* 进入这个目录，然后`npm i hexo-cli -g`

这样就完成了，检查是否完成，可以输入下下命令的命令，看下输出

```sh
hexo -v
```

* 如果输出是类似于下面这样就可以了

```bash
Sean@LAPTOP-F4VS0BRC MINGW64 /e/workspace/seanquant.github.io (master)
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

## 写新文章

* 如果想创建一个新文章，需要用到hexo new命令，也可以用hexo n缩写

```
hexo n "你的文章标题"
```

* 文章就会出现在当前目录下的`./source/_post/xxx.md`
* 当然也可以创建一个对应的文件夹，然后把这个md文件放在里面


> 更多也可以看这里 <https://oakland.github.io/2016/05/02/hexo-%E5%A6%82%E4%BD%95%E7%94%9F%E6%88%90%E4%B8%80%E7%AF%87%E6%96%B0%E7%9A%84post/>

## push到github上

* 如果是在这个电脑上第一次使用git，需要配置一下，名字跟邮箱。否则，不需要 

```bash
git config --global user.name "your name"
git config --global user.email "your email"
```

* 需要配置一下 `_config.yml`，这里放的是hexo的配置文件
  * 以后可能有变化但是关键的几个的东西是逃不掉的
  1. 改url
  ```yaml
  url: https://seanquant.github.io/
  ```
  2. 改deploy参数，这里大家都是类似。相应修改一下就行
  ```yaml
  deploy:
    type: 'git'
    repo: https://github.com/SeanQuant/seanquant.github.io.git
    branch: master
  ```

* push上就只需要(d = deploy) 配置好以后，之后就只需要下面这个命令就可以提交了。会更加简单
  * 注意，提交前最好先生成`hexo g`，有时间还可以`hexo s`本地预览一下，养成好习惯

```
hexo d
```

进行完这个操作之后，一般等个十几秒，就可以通过`seanquant.github.io`这个链接进行访问对应的博客了。



## 多设备写文章

为了实现多设备，其实很简单。就是将一些博文需要的数据，用一个新的分支进行管理


1. 如果本地文件夹下没有`.git`文件夹(可能会被隐藏)，就用`git init`将本地仓库初始化
2. `git checkout -b hexo` 创建一个hexo分支
3. 创建一个`.gitignore`文件，可以命令行创建`touch .gitnore`，也可以手动创建，里面数据是下面这样

```yaml
.DS_Store
Thumbs.db
db.json
*.log
node_modules/
public/
.deploy*/
_multiconfig.yml
```

4. 因为是有可能没有远端的的信息的因此需要添加origin

```bash
git remote add origin git@github.com:SeanQuant/seanquant.github.io.git
```

5. 提交`git push origin hexo`


6. 在github上将hexo分支设置为default分支 
  * 可以参考这个，就在setting里面 <https://docs.github.com/zh/repositories/configuring-branches-and-merges-in-your-repository/managing-branches-in-your-repository/changing-the-default-branch>
  *  为啥要这么做呢？因为每次clone默认clone default分支，你要是选的是master里面每次都需要切换分支，就会很麻烦，不如一步到位

完成这些之后，以后就可以在新设备上操作了。

### 新机器操作

假如有一个新的设备，怎么开始继续创作呢？

**前提** 同样是先保证有 git和node js，这里直接参照上面的教程安装

1. git clone 下来，比如我是`git clone git@github.com:SeanQuant/seanquant.github.io.git`
2. 进入文件夹，然后`npm i hexo-cli -g` 完成配置
3. 到这里就可以开始写了，之后还是`hexo d` 提交到github上。当然最基本的还是一样将这个目录给`git push origin hexo`这个分支上

