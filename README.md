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
  件推送到 `HEAD` 所指向的分支 **。

  **查看HEAD指向的分支**：在资源根目录下使用: `cat .git/HEAD` 来查看 HEAD指向的分支

**工作流涉及到的命令** 
- `git add`命令：将 **工作区** 文件的改动提交到 **暂存区**
- `git commit`命令：将 **暂存区** 的内容提交到 **HEAD** 指向的分支上
- `git push origin branch`命令：将 **HEAD** 指向的分支中的内容推送到远程服务器的
   **branch** 分支上，branch 可以替换为任何已经存在的分支，主分支为：**master**


