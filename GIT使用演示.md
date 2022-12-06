# Git演示

## Git是什么？版本控制软件

**Git**：版本控制软件，将一人/多人代码的变更以**提交**的形式做一个存储，记录历史、回溯

**Github**：基于Git这个版本控制软件打造的**网站**

一个git库对应一个开源项目，通过git管理git库

### Git的三个概念：

* **提交commit**（代码的变更以==**提交**==的形式做一个==**存储**==）（时光机、**有历史记录**）

* **仓库repository**（项目的**文件夹**）（共享、合作）
* **分支branch**（各写各的互不影响，最后一合并）（分工协作、多人合作）

## Git语言基本命令

```
git init：
```

新建一个Git项目时需要进行**初始化**（initiate empty repository in 你的github文档)，就会建立出一个`.git`的文件夹，这就是可以版本控制，有着丰富历史记录的仓库

### 关于提交的命令

![第一次提交](/Users/itchyandsick/Desktop/Markdown/IMG_5335E5786225-1.jpeg)

已有的代码文件在工作区里面，工作区是直接对应项目文件夹里代码的现在的样子，因为刚开始还没提交commit过一次代码，所以仓库里还是空的。如果想要这些文件**被Git记录到**，需要一口气全都提交到仓库里，以后可以用Git帮助你进行对比或者回滚。

工作区的文件通过**==Git add==**，将其提交到**==暂存区==**，接着暂存区文件通过**==Git commit==**最后提交到**仓库**。

这样的好处：你可以选择把哪些文件提交到暂存区，来控制一次commit涉及到哪些文件，暂时没写好的文件可以不放进去

点击`.git`右键，打开`通过Code打开`，这样打开VS Code编辑器。

右键`Git Bash Here`可以看到终端，不过是分屏形式，点击`查看`,点击`终端`，就可以不用分屏形式。



```
git add-A
```

表示把**==所有（All）==**文件提交进暂存，将指定文件标记为**将要被提交**的文件

`更改`表示文件在工作区

`暂存的更改`表示文件在暂存区

```
git add-file“具体文件名字”
```

```
git commit-m"提交的信息"
```

引号里是**提交信息**会给他**起个名**，描述一下改了什么东西，第一次提交没什么改动，所以一般可以命名为`first commit`，即**`git commit-m"first commit"`**

```
git config--global user.name "xxxx"
git config--global user.email "xxx@.com"
```

**注册账号**，第一次使用时需要注册，告诉Git这个软件你是谁

根据指示，输入名字和邮箱进行注册

之后`commit`的功能就可以实现，文件已经提交到仓库了

当然，如果不想输代码，可以用鼠标点击一下文件那一行的加号。![IMG_83ECA2FD0A7A-1](/Users/itchyandsick/Desktop/Markdown/IMG_83ECA2FD0A7A-1.jpeg)

要是想要暂存**所有**更改，就在**更改**那一栏点击**加号**。

提交时，在**源代码管理器**下面的**搜索栏**输入你要提交的名字first commit，点击**==ctrl加回车键==**。

```
git status
```

查看工作状态，显示当前的工作目录下的提交文件状态

```
git log
```

查看历史**提交记录**

git log**--==stat==**(这是加了一个**参数**，为了展现的信息更丰富一点)

每一个commit会有一个**哈希值**，且是唯一的，来指代commit，会展现提交人的**名字**和**时间**

![IMG_6A51C079F3C0-1](/Users/itchyandsick/Desktop/Markdown/IMG_6A51C079F3C0-1.jpeg)

![IMG_0DAA207015D2-1](/Users/itchyandsick/Desktop/Markdown/IMG_0DAA207015D2-1.jpeg)

![IMG_574F22F05CF0-1](/Users/itchyandsick/Desktop/Markdown/IMG_574F22F05CF0-1.jpeg)

但是在左菜单里有一个**commit**的一栏，点击它，就可以看到每次commit的**更为清晰的信息**。

```
git checkout-文件名
```

对于**==没提交==**的文件**放弃更改**

如果这时文件还没提交，就被老板要求**恢复被更改的文件信息**，使用这个命令来**==恢复==**工作区**被更改的信息**

* 对应简单操作：在被更改的文件名那一栏，点击**`撤回箭头`**,就可以进行放弃更改。

```
git reset--HEAD^
```

对于**==已提交的==**文件，**回滚快照(放弃更改)**。

HEAD指**当前的**提交版本，reset是指要把文件改成HEAD的**==之前==的**具体哪一版本，那么`^`就是后面加**你要撤回到哪一版本**

对应的简单操作：找到你要**回滚**的文件，右键点击**`Undo Commit`**

* 如果老板想让你回到以前已经过了很久了的变更，最好最可控的方法是找到**`FILE HISTORY`**,找到那时候的文件，把那部分信息复制粘贴，重新再利用。

###关于分支的命令

多人合作

不要把没写完的代码放入**主分支master/main**

主分支是一切代码分支的起点和终点

其他分支里的改动不会影响到主分支，也不会影响其他的次分支



```
git checkout-b <branchname>创建的分支名
```

以当前分支为基础**新建分支**/从当前节点**新建**分支

你在哪个分支里运行这个命令，那么这个分叉就是从哪个分支产生的

**把b看成build**



```
git branch
```

列举所有的分支



```
git checkout <branchname>
```

**单纯地切换到**某个分支

平常工作就是在哪一个分支里工作改动，就先切换到哪一个分支



```
git merge <branchname>
```

**合并**分支

切换到某一分支A，进行了改动后，==要进行合并的话，先`git checkout master`切换回到主分支，然后再输入`git merge A`==，就进行了合并



如果两个次分支都对同一地方进行了改动，最后合并的时候就会出现冲突，那怎么办呢？

* 如果有一个写的更好，可以选择一个：第一次已经提交改动的叫做**current change**后面提交的叫做**incoming change**，在那一行上面会有显示**accept current change**以及**accept incoming change**，选哪个点击哪个

![IMG_3F91EBF86BB8-1](/Users/itchyandsick/Desktop/Markdown/IMG_3F91EBF86BB8-1.jpeg)

* 如果两个想要进行融合，可以点击上面的**accept both changes**，然后手动把想要的部分复制粘贴，进行部分与部分的融合。

* 如果冲突**过多**，且你又清楚自己想要的是当前分支(current) 还是传入分支(incoming)，可以再左菜单栏里，找到该文件名，右键点击**`全部采用当前内容`/`全部采用传入版本`**

  ![IMG_46E22222482A-1](/Users/itchyandsick/Desktop/Markdown/IMG_46E22222482A-1.jpeg)

* 如果你是在不知道怎么处理这些冲突，建议不要硬合并，而是输入**`git merge--abort`**，直接**放弃合并**，找能处理的同事来处理

```
git branch
```

列举所有的分支



```
git branch-D <branchname>
```

删掉特定的部分

**D看成是delete**



## Git与Github远程仓库

操作流程：新建一个仓库，看到画圈部分加号，点击**`new repository`**

![IMG_443FEC8B916E-1](/Users/itchyandsick/Desktop/Markdown/IMG_F8058DFB96AF-1.jpeg)

![IMG_443FEC8B916E-1](/Users/itchyandsick/Desktop/Markdown/IMG_443FEC8B916E-1.jpeg)

![IMG_734BE084699E-1](/Users/itchyandsick/Desktop/Markdown/IMG_734BE084699E-1.jpeg)

输入仓库名和描述，最后点击绿色按钮`creating repository`

![IMG_6316](/Users/itchyandsick/Desktop/Markdown/IMG_6316.jpg)

把已有仓库提交上去的方法：

```
git remote add origin https://github.com/xxxxxx
```

将新仓库当做一个**远端仓库**添加到**本地的Git**中

```
git branch-M main
```

不要用master 而要用main

对原来的master主分支进行了**改名**

```
git push-u origin main
```

将**本地仓库**添加到**远程**仓库中，输入该行命令发现弹出一个窗口

![IMG_B6E7F708F59D-1](/Users/itchyandsick/Desktop/Markdown/IMG_B6E7F708F59D-1.jpeg)

这一步需要在**本地认证**一下授权

如上这些命令可以不用记，GitHub上有直接可以复制粘贴



```
git push
```

推送当前分支最新的变更提交到**==远程==**

```
git pull
```

拉取远程分支最新的变更提交到**==本地==**

**先pull后push**（先把远程的更改提交到本地，接纳完别人的在把自己本地的提交到远程）就是和远程的更改进行合并



### 将代码拉到本机收藏的方式：

进入官网（作者项目），点击`Code`，复制网址，打开本地文件夹，选择想要保存进入的文件夹，打开，右键`Gitbash here`（这一步会唤醒当前目录下之前看到的gitbash），输入命令`git clone`，把刚复制的网址粘贴进入，点击**回车**，网站里的文件夹就会出现在本地，再点击右键通过Code打开（安装VS Code编辑器就会拥有的一个菜单）

![截屏2022-12-05 下午1.27.36](/Users/itchyandsick/Desktop/Markdown/截屏2022-12-05 下午1.27.36.png)

Gitclone和download zip区别：

**`git clone`**：从远程服务器克隆一个仓库。下载的是**Git仓库**，有丰富历史记录

**Download zip**：下载的是一个普通文件夹，没有`.git`与git软件没有一点关系，要变化成Git仓库，需要对其进行初始化，在文件夹里右键`gitbash here`，在终端输入命令`git init `，点击回车。就可将普通文件夹转为Git仓库。



#### 其他命令：

创建一个新仓库：`git init`

显示提交历史：`git log`



## Github概念和使用

* 目的：借助github**托管项目代码**

* 基本概念：

![截屏2022-12-05 下午1.43.41](/Users/itchyandsick/Desktop/Markdown/截屏2022-12-05 下午1.43.41.png)

* **仓库（Repository）**：用来==**存放项目代码**==，**每个项目对应一个仓库**，多个开源项目则有多个仓库。



* **收藏（Star）**：收藏项目，方便下次查看

![截屏2022-12-05 下午1.48.49](/Users/itchyandsick/Desktop/Markdown/截屏2022-12-05 下午1.48.49.png)



* **复制克隆项目（Fork）**：相当于复制别人的项目，点击`Fork`，会在你的页面出现forked from `原作者/test仓库`，这样你就可以在原项目的基础上，进行你的改动。这是**独立于原项目的**，不会影响到原项目的代码和结构。

![截屏2022-12-05 下午1.51.25](/Users/itchyandsick/Desktop/Markdown/截屏2022-12-05 下午1.51.25.png)



* **发起请求（Pull Request）**：在别人基础上做了的改进如果想把自己的改进合并到原有项目里，这个时候就发起pull request，等待原项目作者收到查看，要是觉得不错，就可以接受这个request，并把改进的项目部分进行合并。如图：![截屏2022-12-05 下午2.15.59](/Users/itchyandsick/Desktop/Markdown/截屏2022-12-05 下午2.15.59.png)

* **关注（Watch）**：关注某个项目，有更新会接收到通知提醒

  

* **事务卡片（Issue）**：别人发现项目有bug，会给你提个`issue`，然后你看到了这些问题就可以去逐个修复，修复好了就可以一个个地close掉。

  

![截屏2022-12-05 下午2.05.21](/Users/itchyandsick/Desktop/Markdown/截屏2022-12-05 下午2.05.21.png)

 

* **Github主页**：![截屏2022-12-05 下午2.32.01](/Users/itchyandsick/Desktop/Markdown/截屏2022-12-05 下午2.32.01.png)

* **仓库主页**：![截屏2022-12-05 下午2.32.05](/Users/itchyandsick/Desktop/Markdown/截屏2022-12-05 下午2.32.05.png)

* **个人主页**：![截屏2022-12-05 下午2.32.14](/Users/itchyandsick/Desktop/Markdown/截屏2022-12-05 下午2.32.14.png)



### 创建仓库

过程：

![截屏2022-12-05 下午11.47.59](/Users/itchyandsick/Desktop/Markdown/截屏2022-12-05 下午11.47.59.png)

* 新建文件/上传文件：

![截屏2022-12-05 下午11.57.49](/Users/itchyandsick/Desktop/Markdown/截屏2022-12-06 上午12.00.56.png)

* 编辑页面：

![截屏2022-12-06 上午12.23.28](/Users/itchyandsick/Desktop/Markdown/截屏2022-12-06 上午12.23.28.png)

下面是提交更改内容

![截屏2022-12-06 上午12.23.40](/Users/itchyandsick/Desktop/Markdown/截屏2022-12-06 上午12.23.40.png)



* **新建文件**：

如图：左边是edit new file，填写文件内容

![截屏2022-12-06 下午5.32.53](/Users/itchyandsick/Desktop/Markdown/截屏2022-12-06 下午5.32.53.png)

![截屏2022-12-06 下午5.32.53](/Users/itchyandsick/Desktop/Markdown/截屏2022-12-06 下午5.33.01.png)

下面表单需要填写每次提交的目的，原因：**为了方便其他开发者知道本次添加或修改的原因**

![截屏2022-12-06 下午5.35.03](/Users/itchyandsick/Desktop/Markdown/截屏2022-12-06 下午5.35.03.png)

创建文件后，自动跳转到**仓库主页**

![截屏2022-12-06 下午5.55.27](/Users/itchyandsick/Desktop/Markdown/截屏2022-12-06 下午5.55.27.png)

点击中间的提交文件的标题概述可以看到**文件提交详细信息**，如图：![截屏2022-12-06 下午5.58.40](/Users/itchyandsick/Desktop/Markdown/截屏2022-12-06 下午5.58.40.png)

* **编辑文件**：

**点击文件名**，到文件详情页可以做删除和修改动作

![截屏2022-12-06 下午6.03.07](/Users/itchyandsick/Desktop/Markdown/截屏2022-12-06 下午6.03.07.png)

每编辑一次，都是要提交文件的，所以每次都要写清楚修改的概述

提交后可查看修改记录

![截屏2022-12-06 下午6.16.47](/Users/itchyandsick/Desktop/Markdown/截屏2022-12-06 下午6.16.47.png)

在仓库主页点击提交记录（右上角**小钟表图标+几次 commits**），可以查看每次提交的记录

![截屏2022-12-06 下午6.21.02](/Users/itchyandsick/Desktop/Markdown/截屏2022-12-06 下午6.21.02.png)

* **删除文件**：

点击文件名，进入文件详情页，点击右上角的垃圾桶小图标就可以删除![截屏2022-12-06 下午6.26.03](/Users/itchyandsick/Desktop/Markdown/截屏2022-12-06 下午6.26.03.png)

删除时候也要标记概括！！最后点击commit changes才会进行删除

![截屏2022-12-06 下午6.27.43](/Users/itchyandsick/Desktop/Markdown/截屏2022-12-06 下午6.27.43.png)

* **上传文件**：

