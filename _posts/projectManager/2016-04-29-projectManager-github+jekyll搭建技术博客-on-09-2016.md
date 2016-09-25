##### 一、 准备工作

**创建本地与github的远程访问**  

> 本地的git与github进行远程访问时，对于用户的控制可以采用用户名/密码认证和RSA认证两种方式。本文中使用RSA方式进行认证，因此需要在本地生成公钥并放置在远程的Github中，从而使用“无密码登录”的方式进行认证。

- 安装git，从程序目录打开 "Git Bash" 

- 键入命令：`ssh-keygen -t rsa -C "email@email.com"`，其中"email@email.com"是github账号
- 提醒你输入key的名称，输入如id_rsa

- 在gitbash中进入`.ssh`目录：C:\Documents and Settings\Administrator\，发现该目录下产生两个文件：id_rsa和id_rsa.pub，操作如下图所示：

![](http://odpb4zgu7.bkt.clouddn.com/markdown/image/youdaogit2.png)

![](http://odpb4zgu7.bkt.clouddn.com/markdown/image/youdaogit3.png)

- 把上述步骤中生成的密钥文件复制到C:\Documents and Settings\Administrator\.ssh\ 目 录下。

- 执行 `vim id_rsa.pub`，复制内容，在github.com的网站上到ssh密钥管理页面，添加新公钥，随便取个名字，内容黏贴进入github中。github的sshkey路径如下图所示：

![](http://odpb4zgu7.bkt.clouddn.com/markdown/image/youdaogit4.png)



**配置jekyll环境**

- [进行ruby下载](http://rubyinstaller.org/downloads/)

![](http://odpb4zgu7.bkt.clouddn.com/markdown/image/youdaorubyInstaller.png)

![](http://odpb4zgu7.bkt.clouddn.com/markdown/image/youdaogit5.png)

- 安装jekyll

直接安装命令：`gem install jekyll`

![](http://odpb4zgu7.bkt.clouddn.com/markdown/image/youdaojekyll.png)

如果是中国大陆用户那么默认的gem源进行安装会有一定困难。这里推荐使用taobao的ruby源。简单的使用以下命令就可以将淘宝repo作为默认repo。
    
    gem sources --remove https://rubygems.org/
    gem sources -a https://ruby.taobao.org/
    gem sources -l

#### 二、建立项目

#### 1 创建本地repo
首先开启gitbash，进入本地项目文件夹，执行git仓库初始化命令，如下图所示初始化一个本地仓库。  

初始化rpo命令：  `$ git init`

![](http://odpb4zgu7.bkt.clouddn.com/markdown/image/youdaogit1.png)



#### 2 克隆项目
使用如下命令，克隆github端的项目：  

    git clone  git@github.com:stopit/stopit.github.io.git


#### 3 修改配置

进入 `cd /e/git_rep/stopit.github.io` 目录，执行：`vim _config.yml` ，修改配置文件。


  markdown: kramdown
    highlighter: rouge
    paginate: 8
    permalink: /:title
    encoding: UTF-8
    gems: [jekyll-paginate]

    title: 你的博客名称
    url: 你的博客地址，就叫 http://github用户名+.github.io
    feed: /atom.xml
    author_info: <a href="http://litaotao.github.io/">你的名字</a>

    myblog:
      gavatar: 你的头像地址
      gpname: 你的名字
      linkedin: 你的 linkedin 地址
      github: 你的 github 地址
      email: mailto:你的 email 地址
      coverimgs: []
      postbgimg: []

    categories: [你的博客目录名称，对应到 your_local_repo/_posts/ 下的文件夹名]



#### 4 本地运行

  进入到 your_local_repo 目录，使用 `jekyll server --watch` 命令启动本地博客。


---


#### 三、参考信息


- [阮一峰：如何搭建github+jekyll的免费博客](http://www.ruanyifeng.com/blog/2012/08/blogging_with_jekyll.html)

- [10分钟搭建一个基于github和jekyll的免费博客](http://cenalulu.github.io/jekyll/how-to-build-a-blog-using-jekyll-markdown/)

- [如何搭建一个独立的博客](http://cnfeat.com/blog/2014/05/10/how-to-build-a-blog/)

- **主要参考**：[github:litaotao](https://github.com/litaotao/github-blog-template)