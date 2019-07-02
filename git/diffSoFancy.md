# diff-so-fancy配色插件
## 安装
```
npm install -g diff-so-fancy
```
## 使用
```
git config --global core.pager "diff-so-fancy | less --tabs=4 -RFX"
```
## 配色方案
```
//开启配色方案
git config --global color.ui true

git config --global color.diff-highlight.oldNormal "red bold"
git config --global color.diff-highlight.oldHighlight "red bold 52"
git config --global color.diff-highlight.newNormal "green bold"
git config --global color.diff-highlight.newHighlight "green bold 22"

git config --global color.diff.meta "227"
git config --global color.diff.frag "magenta bold"
git config --global color.diff.commit "227 bold"
git config --global color.diff.old "red bold"
git config --global color.diff.new "green bold"
git config --global color.diff.whitespace "red reverse"
```
