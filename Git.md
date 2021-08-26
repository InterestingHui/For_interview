#### Git 常用命令
- 显示所有远程仓库：git remote -v 
- 从远程获取代码并合并本地的版本：git pull
    - 将远程主机 origin 的 master 分支拉取过来，与本地的 brantest 分支合并：git pull origin master:brantest
    - 如果远程分支是与当前分支合并，则冒号后面的部分可以省略：git pull origin master
- 从远程获取代码库：git fetch
- 上传代码库：git push
    - 强制上传：git push origin br_IntegrationCode -f 
    - 如果当前分支与多个主机存在追踪关系，则可以使用-u选项指定一个默认主机，这样后面就可以不加任何参数使用：git push -u origin master：
    - 如果当前分支只有一个追踪分支，那么主机名都可以省略：git push
- 查看最近x个版本：git log -x 
- 回滚到第几个版本（之后还要git push，可能要加-f参数）：git reset 版本号 ：
- 创建分支：git branch XXX
- 显示当前分支所在目录：git branch
- 切换到指定分支：git checkout xxx

### 其它
- 如果git merge失败了通常是因为有文件冲突了，这时候冲突如果是其他同事上传的，那就只能回滚：git reset --merge

### git连接远程仓库
- 方法1
    - 先在一个文件夹里右键打开git bash
    - 然后初始化：git init
    - 然后输入git remote add origin [url]

- 方法2
    - 先在一个目录下打开git bash
    - 直接输入 git clone [url] 克隆项目到本地（不用git init）
    - 如果是分支：
        - eg：git fetch origin master_2021_ddjsjr
            - git checkout origin/master_2021_ddjsjr -b master_2021_ddjsjr_lh 
-
### Commit
- git checkout -- .    ： 撤销全部修改

### 上传本地代码到远程仓库
- 先git status 查看红色字知道哪些进行了修改
- 然后git add 指定文件或目录上传到暂存区
- 之后git commit把暂存区文件提交到当前分支
- 再git pull 更新到项目最新版本
- 最后在git push origin xx 到远程仓库（也就是上传到xx分支，一般xx就是上面提示的最右边青蓝色括号里的目录），有时可能要加-f参数进行强制上传
- 如果push失败了
    - “由于我当前所在分支就是 br_Q2Rest 分支 ,所以本地和远端的参数的默认分支名都是 br_Q2Rest 整的push 参数可以这样写: git push -u lhz br_Q2Rest:br_Q2Rest” 
    - http://3ms.huawei.com/km/blogs/details/9617226

### git提交本地到一个子分支并合并子分支到另外一个父分支：
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
        - 
    - Resolve 是解决冲突：也就是当将分支合并入主干（在分支：git rebase master）的情况下解决冲突的手段
- git push origin [子分支] （注意这里就是在子分支）
（这里如果push失败有可能是还得先pull 子分支的远端分支）
### 解决冲突的时候要用到git rebase


### 参考
- [Git教程 - 廖雪峰的官方网站](https://www.liaoxuefeng.com/wiki/896043488029600)
- [RESTful API 最佳实践 - 阮一峰的网络日志](http://www.ruanyifeng.com/blog/2018/10/restful-api-best-practices.html)
- [GitHub - jlevy/the-art-of-command-line: Master the command line, in one page](https://github.com/jlevy/the-art-of-command-line/blob/master/README-zh.md)
