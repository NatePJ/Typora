#### 新建步骤

- GitHub新建分支
- 本地新建文件夹作为本地仓库
- 需要上传的项目拷贝到新建立的仓库
- cmd进入仓库文件夹下执行以下命令
  - `git init`会在仓库下生成一个名称为`.git`的文件夹
  - 可以使用`git status`查看当前仓库状态，也可以在进行到任何一个步骤时使用该命令查看
  - `git add .`把当前项目添加到仓库
  - `git commit -m "日志内容，通常为修改描述"`把项目提交到仓库
  - `git remote add origin https://github.com/NatePJ/gittest.git`关联GitHub新建分支与本地仓库
  - `git push -u origin master`把本地仓库推送到远程仓库上。由于新建的远程仓库是空的，所以要加上-u这个参数，等远程仓库里面有了内容之后，下次再从本地库上传内容的时候只需下面这样就可以了`git push origin master`



#### 报错处理

> To https://github.com/NatePJ/NatePJ.GitHub.io.git
>  ! [rejected]        master -> master (fetch first)
> error: failed to push some refs to 'https://github.com/NatePJ/NatePJ.GitHub.io.git'
> hint: Updates were rejected because the remote contains work that you do
> hint: not have locally. This is usually caused by another repository pushing
> hint: to the same ref. You may want to first integrate the remote changes
> hint: (e.g., 'git pull ...') before pushing again.
> hint: See the 'Note about fast-forwards' in 'git push --help' for details.

- 原因是其他地方向远程仓库推送了项目，导致远程仓库最新内容本地没有

- 解决方案：
  - `git pull origin master`命令拉去远程仓库内容到本地仓库再`git push origin master`

> To https://github.com/NatePJ/NatePJ.GitHub.io.git
>  ! [rejected]        master -> master (non-fast-forward)
> error: failed to push some refs to 'https://github.com/NatePJ/NatePJ.GitHub.io.git'
> hint: Updates were rejected because the tip of your current branch is behind
> hint: its remote counterpart. Integrate the remote changes (e.g.
> hint: 'git pull ...') before pushing again.
> hint: See the 'Note about fast-forwards' in 'git push --help' for details.

- 解决方案：
  - `git push origin master -f`强制提交，但是不利已协同开发

