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
- git log 查看日志 唯一ID（哈希值）
- 退会到某个版本 git reset --hard 具体id（哈希值）
- git checkout 切换分支
	- git checkout -b main 创建分支并切换到main分支
- git merge 合并分支
- git tag 创建固定版本
- git branch 创建分支
	- git branch -M main 创建一个main分支，并且切换到该分支上。
	- git remote -v  
- git fetch upstream 从上游更新代码
- git merge upstream/main 将远程最新的代码合并到自己的main分支中
- git push 推送到远程仓库




如何参与项目，去他人的github仓库点fork，相当于新建一个分支，点击后就保存在自己的仓库了，点自己仓库的code，复制自己仓库的https链接，在vscode上新建终端，`git clone https地址 .`别忘了英文的句号。这一步是将网盘上自己远程仓库的内容克隆到本地仓库。这个时候再去原项目的仓库得到code里面的https链接地址，用`git remote add upstream https链接`，该命令为添加上游代码库的命令


