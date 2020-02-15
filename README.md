# Git使用学习
## Git常用命令
+ 基本命令
    - git init 创建本地仓库
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
+ 远程库相关命令
    - git remote -v 检查当前仓库对应的远程仓库的具体信息
    - git remote rename origin [name] 修改远程仓库名
    - git remote add origin [link](git@github.com:ForDre/learngit.git) 添加远程仓库到本地
    - git remote set-url origin [link](git@github.com:ForDre/learngit.git) 修改本地仓库对应的远程仓库地址
    - 远程关联协议可以是http(s)://或git://或user@server:/path.git支持的SSH协议-速度最快
***
+ 比较重要且常用的命令
    - git push origin master 推送本地仓库master分支到远程仓库，后面的master可以改成分支名称
    - git push -u origin master 第一次推送的时候添加'-u'参数，这样会将分支与远程仓库也关联起来
    - git pull origin master 拉取远程仓库到本地仓库
    - git clone [link](git@github.com:ForDre/learngit.git)克隆远程仓库到本地，克隆完成会自动在仓库生成文件README.md
    - git checkout -b dev 创建分支dev并将当前工作切换到分支dev
    - 相当于以下两个命令：
        - git branch dev 创建分支dev
        - git checkout dev 切换到分支dev
    - git branch 查看当前分支情况
    - git branch -d dev 删除分支dev
    - *重要内容*
        - 由于git checkout [branch]命令与git checkout --[file]即撤销修改是同一个命令，却有两种功能，令人迷惑，所以新版有了新命令来使用分支切换
    - git switch [branch] 切换到新分支
    - 举例：git switch -c [branch] 创建新分支并切换到该分支
    - git merge dev 合并指定分支到当前分支
    - git merge --no-ff -m "description" dev 使用普通模式合并dev分支到当前分支并且不删除分支信息，因为git一般会使用fastforward模式进行合并，这样的合并会丢失分支信息，为了防止分支信息丢失，添加'--no-ff'参数防止分支信息丢失
    - git stash 保存当前工作现场
***
## 常用文件操作命令
+ 文件操作
    - mkdir [filename] 创建文件目录
    - rm [filename] 删除文件
    - cat [filename] 读取文件内容
    - cd [file] 跳转到文件目录
    - pwd 显示当前目录
    - ls -al 显示当前目录下文件明细
