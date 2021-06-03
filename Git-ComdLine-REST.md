# Git

* [Git](#git)
    * [Git 常用命令](#git-常用命令)
* [参考](#参考)

------
#### Git 常用命令
- git remote -v显示所有远程仓库 
- git pull ：从远程获取代码并合并本地的版本
    - 将远程主机 origin 的 master 分支拉取过来，与本地的 brantest 分支合并：git pull origin master:brantest
    - 如果远程分支是与当前分支合并，则冒号后面的部分可以省略：git pull origin master
- git fetch :从远程获取代码库
- git push ：上传代码库
    - git push origin br_IntegrationCode -f 强制上传
- git log -x 查看最近x个版本
- git reset 版本号 ：回滚到第几个版本（之后还要git push，可能要加-f参数）

### 上传本地代码到远程仓库
- 先git status 查看红色字知道哪些进行了修改
- 然后git add 指定文件或目录上传到暂存区
- 之后git commit把暂存区文件提交到当前分支
- 最后在git push origin xx 到远程仓库（一般xx就是上面提示的最右边青蓝色括号里的目录），有时可能要加-f参数进行强制上传

### 参考
- [Git教程 - 廖雪峰的官方网站](https://www.liaoxuefeng.com/wiki/896043488029600)
- [RESTful API 最佳实践 - 阮一峰的网络日志](http://www.ruanyifeng.com/blog/2018/10/restful-api-best-practices.html)
- [GitHub - jlevy/the-art-of-command-line: Master the command line, in one page](https://github.com/jlevy/the-art-of-command-line/blob/master/README-zh.md)
