---
title: hexo 迁移
tags: hexo
category: hexo
---

更换电脑时，需要对hexo 博客网站继续进行维护，这时就需要对hexo 博客网站进行迁移。

### 一.创建分支hexo

在部署hexo 博客的仓库上新建一个分支hexo,用来存放hexo 源代码。

使用如下命令，将分支上的代码克隆下来。

```
#切换到新创建的分支hexo
git checkout hexo

#克隆分支hexo的代码
git clone https://github.com/MelodyGoing/MelodyGoing.github.io.git
```

代码克隆完成后，将项目文件夹下的文件全部删除，.git文件夹除外。将hexo 博客网站的源文件复制到项目文件夹下，.deploy_git文件不需要复制，其余文件全部复制到项目文件夹下。

文件复制完成后，使用如下命令，将项目文件夹下的内容推送到hexo分支。

```
#当前分支为 hexo
git add .
git commit -m "注释"
git push
```

推送完成后，就可以在hexo 分支上看到更新的文件。注意：推送时，如果主题文件中存在.git文件，记得删除，不然推送时会报错。

### 二.新电脑上的操作

安装Node,安装Git。

将hexo分支上将源文件克隆下来

```
#克隆分支hexo的代码
git clone https://github.com/MelodyGoing/MelodyGoing.github.io.git

#安装hexo
npm install hexo

#安装依赖
npm install
```

运行hexo

```
hexo cl
hexo g
hexo s
```

访问http://localhost:40000,可以正常访问页面,说明搭建成功。

文件有更新时，先将修改的内容推送到hexo 分支上，然后再对网站进行部署。

顺序如下：

```
#1.将修改的内容更新到hexo分支上
git add .
git commit -m "注释"
git push

#2.部署网站，部署到master分支上
hexo cl
hexo g
hexo d
```

到此，hexo迁移工作已全部完成。