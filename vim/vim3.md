# vim颜色配置

下载安装
```
git clone https://github.com/tomasr/molokai.git
cd molokai/colors
mv molokai.vim ~/.vim/colors/
vim ~/.vimrc
```

~/.vimrc配置
```
vim ~/.vimrc
set nu
syntax enable
set background=dark
colorscheme molokai
```

# 终端配置

## 安装oh-my-zsh

```
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

## 主题

安装成功后，用vim打开.zshrc，修改主题为‘agnoster’

```
ZSH_THEME="agnoster"
```

## 配置字体

应用这个主题需要特殊的字体支持，否则会出现乱码情况，这时我们来配置字体：

1. 使用 Meslo 字体，点开连接点击 view raw 下载字体。

2. 安装字体到系统字体册。

3. 到对应终端选择meslo字体。

## 自动提示命令

1. 克隆仓库到本地 ~/.oh-my-zsh/custom/plugins 路径下
```
git clone git://github.com/zsh-users/zsh-autosuggestions $ZSH_CUSTOM/plugins/zsh-autosuggestions
```

2. 用 vim 打开 .zshrc 文件，找到插件设置命令，默认是 plugins=(git) ，我们把它修改为

```
plugins=(zsh-autosuggestions git)
```

3. 重新打开终端窗口。

PS：当你重新打开终端的时候可能看不到变化，可能你的字体颜色太淡了，我们把其改亮一些：

移动到 ~/.oh-my-zsh/custom/plugins/zsh-autosuggestions 路径下

```
cd ~/.oh-my-zsh/custom/plugins/zsh-autosuggestions
```

用 vim 打开 zsh-autosuggestions.zsh 文件，修改 ZSH_AUTOSUGGEST_HIGHLIGHT_STYLE='fg=10' （ fg=10 在我电脑上显示良好）。


## 语法高亮

1. 使用homebrew安装 zsh-syntax-highlighting 插件。

```
brew install zsh-syntax-highlighting
```


2. 配置.zshrc文件，插入一行。

```
source /usr/local/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
```

3. 输入命令。

```
source ~/.zshrc
```
