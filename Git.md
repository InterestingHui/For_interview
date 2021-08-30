# Git
- [Git 常用命令](#Git常用命令)
- [放弃本地修改-将本地代码更新到目前远程仓库最新的代码状态](#放弃本地修改-将本地代码更新到目前远程仓库最新的代码状态)
- [简单的放弃本地修改-还原到一开始的状态](#简单的放弃本地修改-还原到一开始的状态)
- [查看本地分支对应的远程分支](#查看本地分支对应的远程分支)
- [git强制push](#git强制push)
- [git连接远程仓库](#git连接远程仓库)
- [上传本地代码到远程仓库](#上传本地代码到远程仓库)
- [git提交本地到一个子分支并合并子分支到另外一个父分支](#git提交本地到一个子分支并合并子分支到另外一个父分支)

#### Git常用命令
- git remote -v ：显示所有远程仓库
- **git pull**
    - 将远程主机 origin 的 master 分支拉取过来，与本地的 brantest 分支合并：git pull origin master:brantest
    - 如果远程分支是与当前分支合并，则冒号后面的部分可以省略：git pull origin master
- git fetch：从远程下载代码库（但并不合并）
- **git push**
    - 如果当前分支只有一个追踪分支，那么主机名都可以省略：git push
- git log -x：查看最近x个版本：
- git reset 版本号：回滚到第几个版本
- git branch XXX：创建分支
- git branch：显示所有分支
- git checkout xxx：切换到指定分支
- git checkout -- .   （**在commit的时候**）： 撤销全部修改


### 放弃本地修改-将本地代码更新到目前远程仓库最新的代码状态
- git fetch origin master
- git reset --hard origin/master

### 简单的放弃本地修改-还原到一开始的状态
- git checkout -f

### 查看本地分支对应的远程分支
- git branch -vv

### git强制push
        git push -f origin br_MXJ_nmm:br_ruu_nmm_mxj

### git连接远程仓库
- 方法1：手动添加远程分支并命名
- 先在一个文件夹里右键打开git bash
- 然后初始化：git init
- 然后输入git remote add origin2 [url]
- “git remote add [name] [url]”表示添加了一个远程仓库，该仓库的网址是url，现在起一个简写加name（如果是clone就是默认是origin）
- 方法2：clone克隆一个仓库
- 先在一个目录下打开git bash
- 直接输入 git clone [url] 克隆项目到本地（不用git init）
- 如果是分支：
- eg：git fetch origin master_2021_ddjsjr
- git checkout origin/master_2021_ddjsjr -b master_2021_ddjsjr_lh

### 上传本地代码到远程仓库
- 先git status 查看红色字知道哪些进行了修改
- 然后git add 指定文件或目录上传到暂存区
- 之后git commit把暂存区文件提交到当前分支
- 再git pull 更新到项目最新版本
- 最后在git push origin xx 到远程仓库（也就是上传到xx分支，一般xx就是上面提示的最右边青蓝色括号里的目录）
- 如果push失败了
- “由于我当前所在分支就是 br_Q2Rest 分支 ,所以本地和远端的参数的默认分支名都是 br_Q2Rest 整的push 参数可以这样写: git push -u lhz br_Q2Rest:br_Q2Rest”
- http://3ms.huawei.com/km/blogs/details/9617226

### git提交本地到一个子分支并合并子分支到另外一个父分支
- git branch
- git checkout [子分支]
- git add ...
- git commit -m ".."  (别忘了 -m)
- git branch （查看所有分支）
- git checkout [父分支名]
- git pull origin [父分支名]  (先更新父分支名的代码）
- git branch
- git checkout [子分支名]
- git rebase [父分支名]
- 注意这里要保证commit的东西已经全部commit的，如果有修改的没有add上去的话，就要git checkout 文件，也就是恢复这个文件，然后在git rebase
- (本地用TorToiseGit，revert是回退到之前的版本，也就是左边的版本；Diff能解决冲突，通过
- 本地使用TortoiseGit
- Revert是回退版本，也就是返回到左边的版本
- 打开的快捷键：右键+T+Enter+v
- 打开后双击能查看版本不同，点OK能回到左边版本
- Diff是解决文件冲突
- 打开的快捷键：右键+T+Enter+Enter
- Resolve 是解决冲突：也就是当将分支合并入主干（在分支：git rebase master）的情况下解决冲突的手段
- 解决冲突文件，解决后“git add 冲突文件”进行提交
- git rebase --continue  继续解决下一个冲突，直到冲突解决完毕
- git push origin [子分支] （注意这里就是在子分支）
（这里如果push失败有可能是还得先pull 子分支的远端分支）
