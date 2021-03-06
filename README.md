## git clone
两种使用：
* 创建一个本地仓库的克隆版本  
假如 仓库地址为：`/e/personal-workspace/learnGit`
执行命令：`git clone /e/personal-workspace/learnGit` 就会将learnGit项目克隆在当前
文件夹下

* 从远程服务器克隆软件

## 工作流
理解三个概念： **工作区(Working Director)**、 **暂存区(Stage或者Index)** 和 **HEAD**
* 工作区(Working Director)  
  就是本地项目目录
* 暂存区(Stage/Index)  
  就是一个缓存区域，临时保存你的文件改动
* HEAD  
  指的是当前"活跃的"分支的游标(或者称为指针)，因为git下可以创建多个分支，那么我们
  当前所处 那个分支就是由 `HEAD` 来指定的，**当使用 `git commit` 命令时，就会将文
  件推送到 `HEAD` 所指向的分支**。

  **查看HEAD指向的分支**：在资源根目录下使用: `cat .git/HEAD` 来查看 HEAD指向的分支

**工作流涉及到的命令**   
- `git add`命令：将 **工作区** 文件的改动提交到 **暂存区**
- `git commit`命令：将 **暂存区** 的内容提交到 **HEAD** 指向的分支上
- `git push origin branch`命令：将 **HEAD** 指向的分支中的内容推送到远程服务器的
   **branch** 分支上，branch 可以替换为任何已经存在的分支，主分支为：**master**

## git push 推送改动
- 执行 `git push origin branch`  
  将已经提交到 HEAD 指向的分支中的内容这个内容是通过git commit提交的)推送到远程
  服务器的 branch 分支上
- 当在本地没有clone仓库时，将本地的内容推送到远程服务器上  
  使用：`git remote add origin <server>` 就可以将本地的文件推送到远程服务器上

## 分支
分支的作用：当有一个新功能需要开发，该功能一时半会还无法开发完成，但是又不能影响到
主分支上其他人的开发，这时就可以创建一个你自己的分支，在该分支下进行开发，开发
完成后再提交，然后合并到 master主分支上，这样你的开发就不会影响到别人

**命令**
- 创建新分支并切换到新分支  
  命令：`git branch -b newBranch` —— 创建newBranch分支并切换到newbranch分支
- 切回主分支  
  命令：`git branch master`  —— master 也可以换成你想切换的其他分支
- 删除分支  
  命令：`git branch -d newBranch`  ——通过添加 `-d` 选项删除`newbranch`分支
- 推送分支  
  除非将分支推送到远程服务器，否则该分支将不被别人看见  
  命令：`git push origin <branch>` ——使用该命令后，在该分支下修改的内容，如果执行
  过`git commit -m ` 命令，则修改的内容也会被推送到远程服务器

## 更新与合并
- 更新  
  命令：`git pull`  ——更新本地仓库到最新版本，并将远程分支自动合并到本地仓库的**当前分支**
- 合并  
  命令：`git merge <branch>`  ——合并`<branch>`分支到当前分支
- 查看差异  
  命令：`git diff <source-branch> <target-branch>`  ——查看这两个分支的差异

## 打标签
打标签就是指针对某次的提交添加一个标签说明
- 列出标签  
  命令：`git tag` ——列出所有的标签  
  命令：`git tag -l 'v1.8.5*'`  ——列出标签为 `v.1.8.5*` 的所有标签
- 显示某个标签的详细信息  
  命令：`git show <标签名>`
- 创建标签  
  标签分为两种类型：**轻量标签(lightweight)** 和 **附注标签**
  - 附注标签  
  命令：`git tag -a v1.0.1 -m "tag message"` ——`-a` 选项后面接`tag标签名`，`-m`选项后面接`tag的信息`
  该命令是针对当前版本进行打标签
  - 轻量标签  
  命令：`git tag v1.0.2` ——对当前版本打上标签，标签名为v1.0.2
- 后期打标签  
  对过去的提交打标签  
  命令：`git log -pretty=online` ——列出提交的版本，并找到需要打标签的版本，然后，使用
  `git tag -a v1.0.3 <校验和>` 即可
- 共享标签  
  默认情况下，`git push`命令并不会传送标签到远程服务器上。在创建标签后必须**显示的
  推送标签到远程服务器上**。这个过程就像推送分支一样，使用如下
  命令：`git push origin v1.0.3`  ——推送v1.0.3标签到远程服务器
  如果想要一次推送多个标签，可以使用如下
  命令：`git push origin --tags`
- 检出标签  
  在Git中并不能真的检出一个标签，如果想要**工作目录与仓库中特定的标签版本完全一样**，
  可以使用`git checkout -b [newBranchName] [targetTagName]`在特定的标签上**创建一个新的分支**
  命令：`git checkout -b version2 v1.0.4`  ——`version2`是新的分支名，`v1.0.4`是需要检出的标签名
  执行该命令后，就会创建一个新的分支`version2`，该分支的内容就是标签`v.10.4`的内容
## log
了解本地仓库的历史记录
- 列出全部提交记录  
  命令：`git log`
- 列出指定作者提交的记录  
  命令：`git log --author=bob`  ——列出bob的提交记录
- 将历史记录压缩成一行显示  
  命令：`git log --pretty=online`  
- 查看`git log`帮助信息  
  命令：`git log --help`

## 替换本地改动  
* 如果操作不当，可以使用如下命令换掉本地改动：  
  命令：`git checkout -- <filename>`  ——执行该命令后，会使用HEAD中的最新内容来替换掉
  工作区指定的文件，**已添加到暂存区的改动以及新文件都不会收到影响**

* 如果想放弃在本地的所有改动与提交，可以从服务器上获取到最新版本历史，并将本地主分支指向它  
  命令：首先拉取最新版本 `git fetch origin`，然后将本地分支指向它，如下
  命令：`git reset --hard origin/master`

## 实用小贴士
* 內建的图形化git：  
  命令：gitk
* 删除实用`git config` 设置的配置项  
  命令：`git config --unset [配置项]`
  



