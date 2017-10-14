## git clone
两种使用：
- 创建一个本地仓库的克隆版本
假如 仓库地址为：`/e/personal-workspace/learnGit`
执行命令：`git clone /e/personal-workspace/learnGit` 就会将learnGit项目克隆在当前
文件夹下

- 从远程服务器克隆软件

## 工作流
理解三个概念： **工作区(Working Director)**、 **暂存区（Stage或者Index）**和 **HEAD**
- 工作区(Working Director)
  就是本地项目目录
- 暂存区(Stage/Index) 
  就是一个缓存区域，临时保存你的文件改动
- HEAD
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

  ***测试添加**8

------- master ： 修改


