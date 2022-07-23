##  如何在 GitHub 上找到合适的开源项目

### 在 GitHub 上搜索信息

当我们知道自己要找的技术栈、编程语言或框架等关键要素之后，我们就可以通过搜索引擎或在代码托管平台上进行搜索。以 GitHub 为例，除了直接搜索关键字，GitHub 还提供了许多条件搜索功能，善用这些功能，可以更加快速有效地找到我们想要的、优质的开源项目。比如：

1.  匹配含有 "cats" 字样、星标超过 1000 个的仓库。
    
    ```
    cats stars:>1000
    ```
    
2.  匹配含有 "vue" 字样、有 5 个或更多主题的仓库。
    
    ```
    vue topics:>=5
    ```
    
3.  匹配含有 "node" 字样，有 10,000 或更多关注者的仓库。
    
    ```
    node followers:>=10000
    ```
    
4.  匹配已归类为 "algorithm" 主题的仓库
    
    ```
    topic:algorithm
    ```
    
5.  匹配遵循 Apache License 2.0 授权的仓库
    
    ```
    license:apache-2.0
    ```
    
6.  匹配项目自述文件中提及 "arduino" 的仓库。
    
    ```
    arduino in:readme
    ```
    
7.  搜索地址位于中国，且拥有超过 5000 名关注者的开发者。
    
    ```
    location:china followers:>5000
    ```
    

更多搜索语法相关内容，请查阅 GitHub Docs 文档 [在 GitHub 上搜索信息 (opens new window)](https://docs.github.com/cn/free-pro-team@latest/github/searching-for-information-on-github)。

### 关注 GitHub 趋势榜

在 [github.com/trending (opens new window)](https://github.com/trending)页面可以了解每天、每周、每月 GitHub 社区里最激动人心的仓库和作者，经常关注 GitHub 趋势榜，更容易找到适合自己学习和使用的优质项目。

### 使用 GitHub 智能推荐

如果你已经在 GitHub 有所积累，那么可以在 [github.com/explore (opens new window)](https://github.com/explore)页面找到 GitHub 根据你的兴趣为你推荐的一些项目。相对来说，技术栈的相关性更强一些。

### GitHub 中文社区

对于新手来说，还有一个不错的选择 —— 通过 [GitHub 中文社区 (opens new window)](https://www.githubs.cn/)进行搜索。该站点整合了 GitHub 热门趋势、精选项目、排行榜、分类搜索等功能，同样可以帮助我们更快地找到想要的优质项目。



### git
想要从本地仓库提交文件到远程仓库，需要在本地仓库的文件夹内鼠标右击，点git bash命令，打开shell命令，先git status，查看状态，再git add，提交文件用git commit -m"提交信息"最后git push。

命令：
- pwd：print work directory 显示工作目录位置
- ls：list file  当前目录下的所有文件
- cd：change directory 切换目录
- git version：版本号
- git config --global：全局配置
- git init：初始化
- git add 文件名：添加文件
- git add .：添加当前目录的全部文件
- git commit：提交
	- git commit 之后会进入vim终端编辑器，按a或者i进入编辑模式，按Esc退出编辑模式，再输入`:wq` 英文状态的冒号和wirte,quit的缩写，代表保存并退出，按回车退出vim终端编辑器。
	- git commit -m "提交说明"  简写方法。如 git commit -m"fix(test): change content"
	- git commit --amend 如果当前是主分支，会在父提交记录上出新建一个分支，并切换到该分支上
- git log 查看日志 唯一ID（哈希值）
- 退会到某个版本 git reset --hard 具体id（哈希值）
- git checkout 切换分支
	- git checkout -b main 创建main分支并切换到该分支
	- git checkout -b main c2 原本是c1，这样可以创建main分支，并且切换到该分支上，且提交一次。
	- git checkout HEAD~1 将HEAD回退到前一个提交记录上
	- git checkout HEAD^ 将HEAD回到第一个父提交记录上
	- git checkout HEAD^2 将HEAD回到第二个父提交记录上
	- git checkout HEAD~\^2~2 将HEAD回退一个提交记录，再回到第二个父提交记录上，再回退两个提交记录。
- git merge  合并分支（一个参数）
- git tag 创建固定版本
- git branch 创建分支
	- git branch -M main 创建一个main分支，并且切换到该分支上。
	- git remote -v  
- git fetch 
	- git fetch upstream 从上游更新代码
	- git log FETCH_HEAD 查看fetch后的日志
- git merge
	- git merge upstream/main 将远程最新的代码合并到自己的main分支中
	- git merge FETCH_HEAD 将fetch后的分支合并到主分支
- git push 提送到远程
- git pull --rebase 是git fetch 和git rebase的简写
- git cherry-pick  哈希值1，哈希值2.....，可以将其他分支上的内容复制到主分支上。
- git rebase -i HEAD~number，number是自己输入的数字，代表向上复制了几步，并且会弹出VIM,可以自己设置复制后的顺序，和git cherry-pick 哈希值1,哈希值2 类似。也可以写在自己上面分支的具体名称。例如 git rebase -i main。但git rebase -i 最多两个参数，且需注意HEAD的位置。
- git rebase main master      main 为主分支时，该命令可以将master分支合并到main分支上，同指向一个哈希值。
- git tag 给某个哈希值打上标签（锚点），可以用标签标记，如git tag v0 c1,
- git describe 分支名 表示描述该分支所处位置，返回值为离最近的锚点的距离，如 v2_1_gC4，表示C4距离最近的锚点v2的距离为一次提交的距离。
- git reset --hard o/main 硬重置



如何参与项目，去他人的github仓库点fork，相当于新建一个分支，点击后就保存在自己的仓库了，点自己仓库的code，复制自己仓库的https链接，在vscode上新建终端，`git clone https地址 .`别忘了英文的句号。这一步是将网盘上自己远程仓库的内容克隆到本地仓库。这个时候再去原项目的仓库得到code里面的https链接地址，用`git remote add upstream https链接`，该命令为添加上游代码库的命令




# 一、Git

### 1.1 介绍

很多人都知道，Linus在1991年创建了开源的Linux，从此，Linux系统不断发展，已经成为最大的服务器系统软件了。

Linus虽然创建了Linux，但Linux的壮大是靠全世界热心的志愿者参与的，这么多人在世界各地为Linux编写代码，那Linux的代码是如何管理的呢？事实是，在

2002年以前，世界各地的志愿者把源代码文件通过diff的方式发给Linus，然后由Linus本人通过手工方式合并代码！

因为很多开发者不断的贡献代码，这样代码越来越多了，就有了管理代码的问题了，所以Linus花了两周时间自己用C写了一个分布式版本控制系统，这就是Git！

一个月之内，Linux系统的源码已经由Git管理了！Git迅速成为最流行的分布式版本控制系统，尤其是2008年，GitHub网站上线了，它为开源项目免费提供Git存

储，无数开源项目开始迁移至GitHub，后来项目越来越多了，其它系统也就开始支持git了

windows， mac等系统都已经支持了Git

我们要使用git就要安装客户端

双击进行下一步安装

安装完成，提供了控制台

Git Bash 为linux家族（unix，mac等）使用的

Git CMD 为window使用的

由于git是为linux提供的，所以建议我们使用linux指令

### 1.2 linux 指令

cd 目录 打开目录

ls 查看当前目录文件的

pwd 查看当前目录所在的系统文件路径

mkdir 文件名名称 创建文件夹

touch 文件名 创建文件的

echo 内容 >> 文件  一个>是覆盖内容，两个>>是追加内容

cat 文件 查看文件内容

clear 清屏

小案例：在D:\class目录下创建一个demo文件夹，并创建一个file.txt文件，并写入 你好明天

### 1.3 git 文件

在git中有三类文件的

第一类文件未纳入缓存的文件

这类文件，一旦删除就再也无法找到

第二类文件是纳入缓存的文件

这类文件，可以通过git找到

第三类文件纳入版本库的文件

这类文件，可以在计算机的各个位置找到

### 1.4 使用 git

通过git init 来初始化一个git仓库

当执行该命令之后，会出现一个隐藏的.git文件

objects目录用于存储纳入缓存的文件

refs目录用于存储纳入版本库的文件

我们可以通过git执令实现三类文件的切换

git add 文件名称

实现将未纳入缓存的文件变为第二类文件（纳入缓存），可以通过*将所有文件纳入缓存

git status 查看文件的状态

一旦纳入缓存，就有机会纳入版本库

git rm 文件名

从版本库中移除文件。

如果添加了--cache，说明是从缓存中移除。

git commit -m “说明”

注意：这个说明一定要有意义

将缓存中的文件，纳入版本库

此时，一旦修改了文件，要通过git status查看一下被修改的是哪个文件

如果想要查看修改的内容，git diff 文件

当查看完毕代码没有问题，继续git add，然后 git commit -m ‘说明’

回退版本：

我们可以通过 git reset --hard HEAD^ 回退到上一个版本，如果想要恢复到上上一个版本 HEAD^^, 如果想要回到前100个， 如果书写100个^^比较容易数不

清楚，HEAD~100

回到未来：

我们可以通过 git reset --hard HEAD commit id实现

一旦将文件纳入版本库，我们可以通过计算机的各个位置去找到文件，但是一旦计算机换掉了，文件就再也找不到了，所以我们要将文件上传到云端（服务

器），这样的话，即使电脑换掉了也可以找到我们想要的文件

### 1.5 建立信任关系

一旦将文件提交到版本库将有机会上传到云端（服务器）

由于你的本地Git仓库和远程仓库之间的传输时通过SSH加密的，所以需要一点设置：

执行指令 ssh-keygen -t rsa -C 邮箱 然后一路回车使用默认值就好

之后进入用户主目录可以找到.ssh目录

打开id_rsa.pub文件，复制里面的内容

将内容粘贴到gitHub或者gitlab上

setting => SSH and GPG keys => add new => 输入标题并粘贴内容

### 1.6 全局配置

创建项目完成之后要进行全局配置：

git config --global user.name ‘注册时候的账户名称’

git config --global user.email ‘注册时候的邮箱’

### 1.7 上传代码

建立连接：

git remote add origin [git@github.com](mailto:git@github.com):YYQH/demo.git

上传代码：

git push -u origin master

预览项目

[http://htmlpreview.github.io/](http://htmlpreview.github.io/)

我们在输入框中输入项目的首页地址，即可预览项目

克隆项目

git clone 项目地址 即可下载别人的项目

### 1.8 多人开发

多人开发的时候，要提交代码要做两件事：拉取代码，合并代码

拉取代码 git fetch origin master

从远程主机的master分支拉取最新内容

合并代码 git merge FETCH_HEAD

将拉取下来的最新内容合并到当前所在的分支中

这两个操作可以通过pull来简化：

git pull <远程主机名> <本地分支名>

### 2.9 分支与主干

分支：不会影响整个项目里面的主线文件：

git分支与主干合并操作

在主干上合并分支：branch （master）git merge branch --squash

在分支上合并主干：（branch）git merge master --squash

创建功能分支：(master) git checkout -b feature

合并最新主干代码

1 (feature) git checkout master

2 (master) git pull

3 (master) git checkout feature

4 (feature) git merge master

5 解冲突 

6 (feature) git commit #

查看分支：git branch

创建分支：git branch \<name>

切换分支：git checkout \<name>

创建+切换分支：git checkout -b \<name>

合并某分支到当前分支：git merge \<name>

删除分支：git branch -d \<name>

Git pull 将远程主机的最新内容拉下来后直接合并 可能会出现冲突