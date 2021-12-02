# Git常用命令
## 基本命令
    - git config --global user.name "Your Name" 
    - git config --global user.email "Example@email.com" 设置全局的用户名及邮箱，其中的--global可以换成--system或--lacal
    - git config user.name 或 git config user.email 查看当前用户名及邮箱
    - git init 把当前目录变成本地仓库
    - git add 提交文件到暂存库
    - git commit -m "description" 提交当前暂存库文件到版本库并填写说明
    - git status 检视当前库状态
    - git log 检视日志
    - git log --graph --pretty=oneline 检视日志并显示分支合并图，并以一行显示每次操作
    - git diff 检视当前暂存库与版本库的差别
    - git reset --hard HEAD^ 回退到上个版本
    - git reset --hard [commit id] 回退到指定commit版本
    - git reset HEAD [file] 将暂存区修改回退到工作区
    - git reflog 查看之前执行的命令，可以查找之前的commit id
    - git checkout --[file] 丢弃最近一次add或commit之后对工作区的修改
    - git rm [file]  删除版本库中的文件
***
## 远程库相关命令
    - git remote -v 检查当前仓库对应的远程仓库的具体信息
    - git remote rename origin [name] 修改远程仓库名
    - git remote add origin [link](git@github.com:ForDre/learngit.git) 添加远程仓库到本地
    - git remote set-url origin [link](git@github.com:ForDre/learngit.git) 修改本地仓库对应的远程仓库地址
    - 远程关联协议可以是http(s)://或git://或user@server:/path.git支持的SSH协议-速度最快
***
## 比较重要且常用的命令
    - git push origin master 推送本地仓库master分支到远程仓库，后面的master可以改成分支名称
    - git push -u origin master 第一次推送的时候添加'-u'参数，这样会将分支与远程仓库也关联起来
    - git pull origin master 拉取远程仓库到本地仓库
    - git clone [link](git@github.com:ForDre/learngit.git)克隆远程仓库到本地，克隆完成会自动在仓库生成文件README.md
    - git checkout -b dev 创建分支dev并将当前工作切换到分支dev
    - 相当于以下两个命令：
        - git branch dev 创建分支dev
        - git checkout dev 切换到分支dev
    - git branch 查看当前分支情况（只有本地分支情况，在后面添加“-a”参数可以查看本地以及远程分支）
    - git branch -d [branchname] 删除分支
    - git push origin --delete [branchname]  删除远程分支
    - git fetch -p  清理本地分支（远程已删除本地未删除的分支）
    - *重要内容*
        - 由于git checkout [branch]命令与git checkout --[file]即撤销修改是同一个命令，却有两种功能，令人迷惑，所以新版有了新命令来使用分支切换
    - git switch [branch] 切换到新分支
    - 举例：git switch -c [branch] 创建新分支并切换到该分支
    - git merge dev 合并指定分支到当前分支
    - git merge --no-ff -m "description" dev 使用普通模式合并dev分支到当前分支并且不删除分支信息，因为git一般会使用fastforward模式进行合并，这样的合并会丢失分支信息，为了防止分支信息丢失，添加'--no-ff'参数防止分支信息丢失
    - git stash 保存当前工作现场
***
## 打标签（tag）
    - git tag  查看所有标签
    - git tag [name]  默认给最新的commit打标签，若要给某个指定的commit打标签，需要在后面加上commit id，比如：git tag v1.0 [commit id]
    - git tag -a [tagname] -m "blabla..."  指定标签信息
***
## 忽略文件.gitignore
    - 有时一些文件我们不需要添加到版本库的，比如一个编译文件，系统文件等，我们可以创建一个.gitignore文件来忽略这些文件
        - 1.使用 touch .gitignore 直接创建文件
        - 2.先在文件目录下创建gitignore文件，然后使用命令: mv gitignore .gitignore 将gitignore文件设置为隐藏文件（Mac OS系统下不能直接创建.gitignore文件）
        - 3.Mac OS系统下，要显示隐藏的文件最方便的方式是使用快捷键：command + shift + . 或者查看[这里](https://www.jianshu.com/p/1222dace3231)提供的方法。

***
## <font color=#ff8800>常用文件操作命令</font>
    - mkdir [file] 创建文件目录
    - touch [filename] 创建文件
    - rm [filename] 删除文件
    - rmdir 删除目录
    - rm -r 删除目录 rm -rf 强制删除目录
    - find . -type d -name "mydocuments" -exec rm -rf {}+
        - . 表示在当前目录下执行
        - -type d 表示只搜素目录
        - -name "mydocuments" 表示指定目录名称
        - -exec rm -rf 表示执行rm命令删除所有目录内容
        - 若要删除当前目录下所有空目录，可以执行以下命令
        ```find . -type d -empty -delete```
    - cat [filename] 读取文件内容
    - cd [file] 跳转到文件目录
    - pwd 显示当前目录
    - ls -al 显示当前目录下文件明细，同时能显示隐藏文件
***
## 创建SSH-Key步骤
    1. 检查电脑上是否已有SSH-Key，在用户主目录下检查是否有.ssh目录，若有则检查是否有id_rsa,id_rsa.pub两个文件，若有则已具备SSH_Key
    2. 若没有，则需打开终端，输入以下命令
        ```
        ssh-keygen -t rsa -C "Your-email@email.com"
        ```
    3. 若顺利则能在主目录下找到.ssh目录，里面有id_rsa和id_rsa.pub两个文件