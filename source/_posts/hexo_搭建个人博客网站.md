---
title: hexo 搭建个人博客网站
tags: hexo
---

### 1.环境搭建

​	安装[Node.js](http://nodejs.cn/)

​	安装[Git]()

### 2.hexo 安装与配置

#### 	hexo安装

> ```
> npm install hexo
> ```

#### 	hexo 初始化

> ```
> hexo init "你的文件夹名"
> ```

  初始化之后，文件目录如下图:

<img src="C:\Users\11072\Pictures\Saved Pictures\hexo 文件目录结构图.png" alt="hexo 文件目录结构图" style="zoom: 80%;" />

#### 	启动 hexo

> ```
> hexo g
> hexo s
> ```

![](C:\Users\11072\Pictures\Saved Pictures\微信截图_20200308210306.png)

​	访问 [http://localhost:4000] ,在本地运行hexo

### 3.hexo 部署到GitHub

#### 	创建gitHub账号

#### 	创建gitHub仓库

 	仓库名为:<u>yourUsername.github.io</u>

<img src="C:\Users\11072\Pictures\Saved Pictures\微信截图_20200308211301.png" style="zoom:67%;" />

1. 复制刚刚新建的https连接:`https://github.com/yourUsername/yourUsername.github.io.git`(仓库地址)

2. 打开你hexo目录下的`_config.yml`

3. 设置deploy信息,如:

   > ```
   > deploy:
   >   type: git
   >   repository: https://github.com/yourUsername/yourUsername.github.io.git
   >   branch: master
   > ```

   #### 设置SSH key

   ##### 	检验是否已存在key，执行命令

   > ```
   > cd ~
   > cd  .ssh
   > ```

   ##### 	添加一个 SSH key

   ​	执行命令(已有key的可以跳过步骤2):

   > ```
   > $ ssh-keygen -t rsa -C "your_email@mail.com"
   > 
   > ##  t 指定密钥类型，默认是 rsa ，可以省略。 -C 设置注释文字，比如邮箱或其他。
   > ```

   然后会提示你 `Enter Enter file in which to save the key (/c/Users/you/.ssh/id_rsa): [Press enter`,这里是输入一个文件名用来保存ssh key,也可以什么都不输,会使用默认的`id_rsa.pub` 和 `id_dsa.pub`

   回车之后,需要输入两次密码(该密码是你push文件的时候要输入的密码，而不是github的密码)
   输入密码之后,看见如下显示信息,添加SSH key成功。

   #### Github 设置 SSH key

   登录github,点击`Settings`,然后点击 `SSH keys` ,在这个页面你可以管理你所有的ssh keys
   然后点击`Add SSH key`
   用文本编辑器打开刚刚添加的key文件`id_rsa.pub`,复制里面的所有的内容
   回到github页面,将复制的内容粘贴到刚刚那个页面的key对应的文本框里面,title 可以随便填写。

   #### 测试ssh key 是否添加成功

   在命令行输入:

   ```
   $ ssh -T git@github.com
   ```

   会出现一段警告代码,输入yes回车,然后会要求你输入刚刚设置的密码

   到此SSH key就设置完毕了

   ### 4.部署到Github

   打开命令窗口,回到你的hexo博客目录下,如别执行如下命令:

   > ```
   > hexo generate
   > hexo deploy
   > ```

   等待命令执行完毕后,可以查看代码是否已提交到github上,然后在浏览器输入yourUsername.github.io就可以访问了

   ### 5.新建页面

   > ```
   > $ hexo new page 'pageName'
   > ```

   执行命令后可以在你本地的`/source` 目录下看见以为你新增页面名为名的文件夹

   ### 6.显示页面

   打开文件后可以对`index.md` 进行编辑.然后打开`/themes/jacman`目录下的`_config.yml`文件(自己正在使用的主题),
   添加刚刚新增的页面:

   > ```
   > menu:
   >   首页: /
   >   统计: /archives
   >   关于: /about
   >   pageName: /pageName ##前面的pageName可以自定义,后面的pageName必须写刚刚新增的页面名称
   > ```

   ### 7.安装主题

   ```
   $ git clone https://github.com/JamesPan/hexo-theme-icarus.git themes/icarus
   ```

   #### 更换主题

   首先下载主题,然后打开根目录下的 `_cinfig.yml` ,修改 `theme: 要更换的主题名`

   



