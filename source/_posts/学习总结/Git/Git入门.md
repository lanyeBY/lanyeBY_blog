---
title: Git入门
date: 2020-09-28 16:33
tags: Git
catetory: 学习总结
---

### 1.1 Git基础-获取Git仓库
#### 获取Git仓库
有两种获取Git项目仓库的方式：
1. 将尚未进行版本控制的本地目录转换为 Git 仓库;
2. 从其它服务器 克隆 一个已存在的 Git 仓库。

##### 在已存在的目录中初始化仓库
进入该项目目录之后 执行命令：
```shell
$ git init
```

该命令将创建一个名为`.git`的子目录，包含初始化Git仓库中所有的必须文件。<br>
如果该目录并非一个空文件夹，则需要将这些文件加入追踪:
```shell
$ git add *.c
$ git add LICENSE
$ git commit -m 'initial project version'
```

##### 克隆现有的仓库
克隆仓库的命令是`git clone <url> `。
```shell
$ git clone https://github.com/libgit2/libgit2
```
这会在当前目录下创建一个名为 `libgit2` 的目录，并在这个目录下初始化一个 `.git` 文件夹，从远程仓库拉取下所有数据放入 `.git` 文件夹，然后从中读取最新版本的文件的拷贝。<br>
如果你想在克隆远程仓库的时候，自定义本地仓库的名字，你可以通过额外的参数指定新的目录名：
```shell
$ git clone https://github.com/libgit2/libgit2 mylibgit
```

这会执行与上一条命令相同的操作，但目标目录名变为了`mylibgit`。

### 1.2 Git基础-记录每次更新到仓库
#### 检查当前文件状态
可以用 `git status` 命令查看哪些文件处于什么状态。可以查看到已暂存的和未暂存的文件。 <br>
运行 `git diff` 可以查看暂存前后的变化。

#### 跟踪新文件/暂存已修改的文件
使用命令 `git add` 可以开始跟踪一个文件或暂存已修改的文件。<br>
可以在其后面执行某个文件的文件名，需要注意，该文件名需要包含相对于当前命令行所在的目录的相对路径；也可以使用关键字 `.` 或 `--all` 表示当前目录下的全部更改或未跟踪的文件进行暂存。

#### 忽略文件
若想要将某些文件忽略跟踪，可以创建一个名为 `.gitignore` 的文件，列出要忽略的文件的模式。

```
*.[oa]
*~
```

第一行告诉Git忽略所有以 `.o` 或 `.a` 结尾的文件。第二行告诉Git忽略所有名字以波浪符（~）结尾的文件。<br>

文件 `.gitignore` 的格式规范如下：
- 所有空行或者以 `#` 开头的行都会被 Git 忽略。
- 可以使用标准的 `glob` 模式匹配，它会递归地应用在整个工作区中。
- 匹配模式可以以（`/`）开头防止递归。
- 匹配模式可以以（`/`）结尾指定目录。
- 要忽略指定模式以外的文件或目录，可以在模式前加上叹号（`!`）取反。

所谓的 `glob` 模式是指 `shell` 所使用的简化了的正则表达式。 星号（`*`）匹配零个或多个任意字符；`[abc]` 匹配任何一个列在方括号中的字符 （这个例子要么匹配一个 `a` ，要么匹配一个 `b` ，要么匹配一个 `c`）； 问号（`?`）只匹配一个任意字符；如果在方括号中使用短划线分隔两个字符， 表示所有在这两个字符范围内的都可以匹配（比如 `[0-9]` 表示匹配所有 `0` 到 `9` 的数字）。 使用两个星号（`**`）表示匹配任意中间目录，比如 `a/**/z` 可以匹配 `a/z`、`a/b/z` 或 `a/b/c/z` 等。

#### 提交更新
提交命令 `git commit -m <提交信息>` 。

### 1.3 Git基础-查看提交历史
`git log`
选项：
- `-p` 或 `--patch`：显示每次提交所引入的差异，后面接 `-<number>` 可以限制显示的日志条目数量，例如 `-2` 选项来只显示最近的两次提交。

### 1.4 Git基础-撤销操作
使用 `git reset HEAD <file>...` 来取消某个文件的暂存。<br>
使用 `git checkout -- <file>...` 来撤销某个文件的修改。

### 1.5 Git基础-远程仓库的使用
#### 查看远程仓库
查看已经配置的远程仓库服务器，可以运行 `git remote` 命令。它会列出你指定的每一个远程服务器的简写。<br>
`origin` 是Git给仓库服务器的默认名字：
```shell
$ git remote
  origin
```

指定选项 `-v`，会显示需要读写远程仓库使用的 Git 保存的简写与其对应的URL。
```shell
$ git remote -v
  origin	https://github.com/schacon/ticgit (fetch)
  origin	https://github.com/schacon/ticgit (push)
```

#### 添加远程仓库
 运行 `git remote add <shortname> <url>` 添加一个新的远程Git仓库，同时指定一个方便使用的简写：

 ```shell
  $ git remote
    origin
  $ git remote add pb https://github.com/paulboone/ticgit
  $ git remote -v
    origin	https://github.com/schacon/ticgit (fetch)
    origin	https://github.com/schacon/ticgit (push)
    pb	https://github.com/paulboone/ticgit (fetch)
    pb	https://github.com/paulboone/ticgit (push)
```
 
#### 从远程仓库中抓取与拉取

```shell
$ git fetch <remote>
```

这个命令会访问远程仓库，从中拉取所有你还没有的数据。执行完成后，你将会拥有那个远程仓库中所有分支的引用，可以随时合并或查看。

```shell
$ git pull
```

这个命令会去访问本地分支对应的远程分支相对于本地分支的差异，并更新到本地分支。

#### 推送到远程仓库
`git push <remote> <branch>`

#### 远程仓库的重命名与移除
你可以运行 `git remote rename` 来修改一个远程仓库的简写名。例如，想要将 `pb` 重命名为 `paul`，可以用 `git remote rename`这样做：

```shell
$ git remote rename pb paul
$ git remote
  origin
  paul
```

值得注意的是这同样也会修改你所有远程跟踪的分支名字。 那些过去引用 `pb/master` 的现在会引用 `paul/master` 。<br>
如果因为一些原因想要移除一个远程仓库——你已经从服务器上搬走了或不再想使用某一个特定的镜像了， 又或者某一个贡献者不再贡献了——可以使用 `git remote remove` 或 `git remote rm` ：

```shell
$ git remote remove paul
$ git remote
  origin
```

一旦你使用这种方式删除了一个远程仓库，那么所有和这个远程仓库相关的远程跟踪分支以及配置信息也会一起被删除。

### 2.1 Git分支-分支的新建和合并
#### 分支创建
使用 `git branch <name>` 可以创建一个本地分支。<br>
使用 `git checkout <name>` 可以切换到指定的本地分支。后面可以接选项 `-b`，表示创建一个本地分支并且切换到这个分支上。<br>
如果在后面添加想要关联的远程分支名，可以直接将制定的本地分支名关联到制定的远程分支，从而在 `git push` 的时候不再需要制定远程分支名。

#### 分支合并
将主分支建立并切换出去的工作分支重新合并到主分支中，运行 `git merge` 命令：

```shell
$ git checkout master
  Switched to branch 'master'
$ git merge iss53
  Merge made by the 'recursive' strategy.
  index.html |    1 +
  1 file changed, 1 insertion(+)
```

使用 `git branch -d <name>` 可以删除一个本地分支。

### 2.2 Git分支-分支管理
`git branch` 命令不只是可以创建与删除分支。如果不加任何参数运行它，会得到当前所有分支的一个列表：

```shell
$ git branch
  iss53
* master
  testing
```
注意 `master` 分支前的 `*` 字符：它代表现在检出的那一个分支（也就是说，当前 `HEAD` 指针所指向的分支）。

### 2.3 Git分支-远程分支
将本地分支（当前分支需指向该本地分支）关联到远程分支，使用 `git branch -u <name>` 或 `git branch --set-upstream-to <name>`