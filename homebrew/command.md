# 安装 Homebrew
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
## 将以上命令粘贴至终端。

# 查看brew的帮助
```
brew –help
```

# 安装软件
```
brew install git
```

# 卸载软件
```
brew uninstall git
```

#搜索软件
```
brew search git
```

# 显示已经安装软件列表
```
brew list
```

# 更新软件，把所有的Formula目录更新，并且会对本机已经安装并有更新的软件用*标明。
```
brew update
```

更新某具体软件

brew upgrade git

查看软件信息

brew [info | home] [FORMULA...]

删除程序，和upgrade一样，单个软件删除和所有程序老版删除。

brew cleanup git 
brew cleanup

查看那些已安装的程序需要更新

brew outdated

 

 

其它Homebrew指令:

brew list   —列出已安装的软件

brew update   —更新Homebrew

brew home  *—用浏览器打开

brew info   *—显示软件内容信息

brew deps * — 显示包依赖

brew server *  —启动web服务器，可以通过浏览器访问http://localhost:4567/ 来同网页来管理包

brew -h brew   —帮助

homebrew本身就是一个git仓库。使用homebrew安装软件包时，会自动先下载软件包，然后解压安装，但有时候下载会卡住，或者很慢，这个时候你可以通过其他工具先将所需的软件包下载 下来，注意版本一定要对应，homebrew放置软件包源码的路径为/Library/Caches/Homebrew/，只要你将所需要的软件包下载正 确的版本，放置在此目录下，那么再使用brew install xxx的时候，brew就能直接安装了，有时候brew install xxx卡在下载界面，这招很管用。

 

Making a formula is easy. Just brew create URL and then brew install $FORMULA (perhaps with --debug --verbose). Basically, a formula is a Ruby file. You can place it anywhere you want (local or remote) and install it by pointing to the file or URL.

formula文件位置：/usr/local/Library/Formula/foo.rb  存放安装工具的rb文件

Packages are installed according to their formulae, which live in $(brew --repository)/Library/Formula. Check some out. You can view any formula at anytime; e.g. brew edit wget.

 

 另 外说明下，brew安装程序的过程中需要用到苹果的xcode中的 编译器，你可以到苹果的官网中免费下载安装（需要注册免费的开发者，然后才能下载），安装后到属性（Xcode -- Perference--Downloads--Components--Command Line Tools）点击下载就可以了

Homebrew工具地址：https://github.com/Homebrew/homebrew
