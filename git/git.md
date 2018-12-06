#创建版本库
一：创建一个空目录
$ mkdir test
$ cd test
$ pwd
/Users/michael/test
二：把这个目录变成Git可以管理的仓库（会生成一个.git目录）
$ git init
三：创建文件
$ touch test.txt
四：添加到仓库
$ git add test.txt
$ git commit -m "描述内容"
#时光机穿梭
一：仓库当前的状态
$ git status
二：查看不同（修改部分）
$ git diff
#版本回退
一：查看历史记录
$ git log
二：粗略查看历史记录
$ git log --pretty=oneline
三：HEAD的含义：上一个版本就是HEAD^，上上一个版本就是HEAD^^，当然往上100个版本写100个^比较容易数不过来，所以写成HEAD~100
四：回退到上一版本
# git reset --hard HEAD^
五：回退到指定版本（版本号可以写前几位）
$ git reset --hard 1094a
六：查看之前的命令记录
$ git reflog
#工作区和暂存区
一：就是你在电脑里能看到的目录，比如我的learngit文件夹就是一个工作区
二：工作区有一个隐藏目录.git，这个不算工作区，而是Git的版本库（Git的版本库里存了很多东西，其中最重要的就是称为stage（或者叫index）的暂存区，还有Git为我们自动创建的第一个分支master，以及指向master的一个指针叫HEAD。）
#管理修改
一：提交后，用git diff HEAD -- test.txt命令可以查看工作区和版本库里面最新版本的区别
#撤销修改
一：让这个文件回到最近一次git commit或git add时的状态
# git checkout -- test.txt
二：场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令git checkout -- file。

场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令git reset HEAD <file>，就回到了场景1，第二步按场景1操作。

场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交，参考版本回退一节，不过前提是没有推送到远程库。

#删除文件
一：要从版本库中删除该文件，那就用命令git rm删掉，并且git commit
$ git rm test.txt
$ git commit -m "xxxx"
二：删错了
git checkout -- test.txt

#生成密钥
一：可以在用户主目录里找到.ssh目录，里面有id_rsa和id_rsa.pub两个文件，这两个就是SSH Key的秘钥对，id_rsa是私钥，不能泄露出去，id_rsa.pub是公钥，可以放心地告诉任何人
$ ssh-keygen -t rsa -C "youremail@example.com"

#远程仓库
一：本地仓库和远程仓库相关联
$ git remote add origin git@github.com:laojingwei/git.git
二：把本地库的所有内容推送到远程库上(由于远程库是空的，我们第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令)
$ git push -u origin master
三：从现在起，只要本地作了提交，就可以通过命令push
$ git push origin master

#克隆本地库
一：Git支持多种协议，默认的git://使用ssh，但也可以使用https等其他协议。
$ git clone git@github.com:laojingwei/git.git
