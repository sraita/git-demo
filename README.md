# git-demo

# 为什么需要产品管理

# git & github


## git 中的别名设置
`git config alias.shorename <fullcommand>`

eg. 配置格式化的log
```
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
```

### git 显示不同版本之间的差异 git diff
* 显示工作目录与暂存区之间的差异
>`git diff `
*  暂存区与某次提交差异， 默认为HEAD
>`git diff --cached  [<reference>]`
*  工作目录与某次提交的差异
>`git diff <reference>`
* 两次提交之间的差异
> `git diff <commitId1 commitId2> `

### 撤销修改
1. 将文件内容从暂存区复制到工作目录
> `git checkout --<file>`
>   此操作会丢弃你的修改

* 将文件内容从上次提交复制到暂存区
> `git reset HEAD <file>`

![工作目录，暂存区和提交区](http://upload-images.jianshu.io/upload_images/1815393-d7313e55d20249f6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

***

# 分支操作
## 分支的增删查改 git branch
创建分支
git branch <branchName>
删除分支
git branch -d <branchName>
查看所有分支信息
git branch -v

> 所有的分支信息都会存放在下面的文件中
> `cat .git/refs/heads/master`

## git checkout 通过移动HEAD检出版本，可用于分支切换
```
git checkout <branchName> // 切换分支
git checkout -b <branchName> // 新建并切换到一个分支
git checkout -   // 恢复到上一个分支
git checkout <commit> // 切换到某次提交， head处于分离状态，此时避免做write操作

```

### git reset 将当前分支回退到历史某个版本
```
git reset --mixed <commit> (默认) // 会将当前内容复制到暂存区
git reset --soft <commit> // 会暂存区和工作目录的状态，不会有任何变化
git reset --hard <commit> // 会将当前内容复制到暂存区和工作目录
```
> 区别主要在于： 内容是否会恢复到工作目录或者暂存区

### 使用捷径
* A^ : A上的父提交
* A~n: 在A之前的第n次提交

### reset 与 checkout的区别（commit操作&file操作）
dog | bird | cat
:-:|:-:|:-:
foo | foo  | foo
bar | bar  | bar
baz | baz  | baz
