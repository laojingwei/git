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
三：删除远程仓库的文件或目录
1、git rm -r --cached a/2.txt //删除a目录下的2.txt文件   删除a目录git rm -r --cached a
2、git commit -m "删除a目录下的2.txt文件" 
git push
3、Note:
用-r参数删除目录, git rm --cached a.txt 删除的是本地仓库中的文件，且本地工作区的文件会保留且不再与远程仓库发生跟踪关系，如果本地仓库中的文件也要删除则用git rm a.txt

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

#git库所在的文件夹中的文件大致有4种状态
一：Untracked:
未跟踪, 此文件在文件夹中, 但并没有加入到git库, 不参与版本控制. 通过git add 状态变为Staged.
 
二：Unmodify:
文件已经入库, 未修改, 即版本库中的文件快照内容与文件夹中完全一致. 这种类型的文件有两种去处, 如果它被修改,
而变为Modified. 如果使用git rm移出版本库, 则成为Untracked文件
 
三：Modified:
文件已修改, 仅仅是修改, 并没有进行其他的操作. 这个文件也有两个去处, 通过git add可进入暂存staged状态,
使用git checkout 则丢弃修改过, 返回到unmodify状态, 这个git checkout即从库中取出文件, 覆盖当前修改
 
四：Staged:
暂存状态. 执行git commit则将修改同步到库中, 这时库中的文件和本地文件又变为一致, 文件为Unmodify状态.
执行git reset HEAD filename取消暂存, 文件状态为Modified
 
五：Git 状态 untracked 和 not staged的区别
1）untrack     表示是新文件，没有被add过，是为跟踪的意思。
2）not staged  表示add过的文件，即跟踪文件，再次修改没有add，就是没有暂存的意思

#分支管理
一：创建dev分支，然后切换到dev分支
$ git checkout -b dev
二：加上-b参数表示创建并切换，相当于以下两条命令
$ git branch dev
$ git checkout deb
三：查看分支
$ git branch
四：合并分支
$ git merge dev
五：删除分支
$ git branch -d dev
六：Git鼓励大量使用分支：
查看分支：git branch
创建分支：git branch <name>
切换分支：git checkout <name>
创建+切换分支：git checkout -b <name>
合并某分支到当前分支：git merge <name>
删除分支：git branch -d <name>
六：查看分支合并情况
$ git log --graph --pretty=oneline --abbrev-commit
$ git log --graph
