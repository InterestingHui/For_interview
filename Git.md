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
#### 1
- 先在一个文件夹里右键打开git bash
- 然后初始化：git init
- 然后输入git remote add origin [url]

#### 2
- 先在一个目录下打开git bash
- 直接输入 git clone [url] 克隆项目到本地
- 


### 上传本地代码到远程仓库
- 先git status 查看红色字知道哪些进行了修改
- 然后git add 指定文件或目录上传到暂存区
- 之后git commit把暂存区文件提交到当前分支
- 再git pull 更新到项目最新版本
- 最后在git push origin xx 到远程仓库（也就是上传到xx分支，一般xx就是上面提示的最右边青蓝色括号里的目录），有时可能要加-f参数进行强制上传

### 参考
- [Git教程 - 廖雪峰的官方网站](https://www.liaoxuefeng.com/wiki/896043488029600)
- [RESTful API 最佳实践 - 阮一峰的网络日志](http://www.ruanyifeng.com/blog/2018/10/restful-api-best-practices.html)
- [GitHub - jlevy/the-art-of-command-line: Master the command line, in one page](https://github.com/jlevy/the-art-of-command-line/blob/master/README-zh.md)
