### 基本命令

- `git init`：将当前目录初始化为git仓库

- `git add file`：将文件file添加到暂存区中(还有追踪列表)  //每更改一次就要添加一次

  

> 撤销您不想跟踪的文件

- `git commit -m "message"`：提交暂存区的内容

> "message"：是这次提交的信息
>
> 当提交时，会分离一个节点(代表这个提交)，然后有个头指针指向最新的节点，通过指针后移回到之前的节点(即`git checkout id1`)//后面介绍，用该节点是存储库的状态来覆盖当前的状态
>
> 新节点指向它之前(最近)的旧节点
>
> 还有个分支指针一直指向该分支最新节点
>
> 这是补充

- `git commit --amend`：已提交但尚未推送到`GitHub`网站上，可以使用 该命令 命令修改提交消息
- `git reset HEAD file`：将添加到暂存区还未提交的文件从暂存区移除，使文件的状态恢复为已修改



### 文件的状态

> modified：修改，staged：暂存

![file-status](./file-status.png)

如图所示，文件分为两大类：

1. 未跟踪的文件：这些文件要么从未被跟踪过，要么已从跟踪中删除。Git 不会维护这些文件的历史记录。
2. 跟踪文件：这些文件已添加到 Git 存储库中，可以处于不同的修改阶段：未修改、已修改或暂存。
   1. 未修改的文件是自上一个版本的文件添加到 Git 存储库以来没有任何新更改的文件。
   2. 修改后的文件与 Git 最近保存的文件不同。
   3. 暂存文件是用户指定为未来提交的一部分的文件（通常通过使用 git add 命令）。

-  `git status`：显示工作树状态(当前目录所在存储库的) 

- `git log`：显示提交日志(当前目录所在存储库的)

  ```text
  //一次提交日志
  commit b550603ae9c7a210581567d6586f564fb35afe4a
  //b550603ae9c7a210581567d6586f564fb35afe4a 是这次提交的id,唯一
  Author: coding小白 <worldkingscoding@gmail.com>
  Date:   Fri Dec 31 15:49:41 2021 +0800
  ```

  > 用q退出

-  `git show id1`：查看id是`id1`的提交内部

- `git checkout id1`：回到运行完了commit为 `id1`的时候

- `git checkout id1 ./lab`：找出运行完了id为 `id1` 的commit后的lab的样子覆盖现在的lab

  >  git checkout 用于切换分支或恢复工作树文件，这个命令很危险，会改写工作区
  >
  >  *checkout 命令不会更改提交历史记录*
  



#### 遥控器

- 添加：`git remote add name URL `：将本地仓库与网站上的仓库关联起来 

> name: 遥控器的名字  ，URL：要关联的网站上的仓库的URL
>
> 用于push,pull

- 查看：`git remote -v`：查看关联的存储库
- 重命名：`git remote rename old-name new-name`
- 删除：`git remote rm name`

> 按照约定，调用主远程的名称是`origin`（对于原始远程存储库）
>
> 当你克隆一个远程时,该远程是 `origin`

- `git pull(push) name main` : 拉(推)到遥控器名字为name的存储库上的man分支

> `pull`: 这相当于一个`fetch + merge`. 不仅会`pull`获取最新的更改，还会将更改合并到您的`HEAD` 分支中。

`git fetch name`

> 这类似于下载最新的提交。它不会将它们合并到本地仓库的当前分支中
>
> 用于获取从远程获取一些当前不在本地存储库中的新提交但不想合并到本地中





#### 分支

> name是分支的名字

1. 创建：`git branch name ` 
2. 切换：`git checkout name`

> 通过更改`HEAD`指针引用的分支从一个分支切换到另一个分支 
>
> 将(name代表的)分支指针赋给head指针

创建并切换：`git checkout -b name`

删除：`git branch -d name`

确定所在分支：` git branch -v`





#### 合并 

`git merge branch` //把分支branch 合并到当前所在分支上(假设为main)

> merge命令创建一个将两个分支连接在一起的新提交，并将main分支上最新的节点指向branch分支上最新的节点

git 将合并这两个版本并添加一个额外的提交，让您知道您已合并。 这很烦人，并导致提交历史非常混乱。 这就是`rebasing `发挥作用的地方。

当您将更改推送到` Github` 并且远程副本已被修改时，系统会要求您拉入更改。 这是您通常会遇到合并冲突的地方。 此时可用使用 `rebase` 标志来拉取：

```
git pull --rebase origin master
```

来自服务器的更改将应用于您的工作副本，并且您的提交将放在顶部。



#### 合并冲突



尝试合并两个可能有冲突的信息的分支。如果两个分支上的提交更改了相同的文件，则可能会发生这种情况。Git 足够复杂，可以解决许多更改，即使它们发生在同一个文件中（尽管位置不同）。但是，有时 Git 无法解决冲突，因为更改会影响相同的方法/代码行。在这些情况下，它会将来自不同分支的两个更改作为*合并冲突*呈现给您

#### 解决合并冲突

当你用git pull 命令拉远程的信息时，如果有冲突的话，Git 会告诉你哪些文件有冲突(这些文件包含了远程和本地的冲突信息)。您需要打开这些文件并手动删除你不想保留的以及无关的行。完成此操作后，然后推上去。远程的信息就是你本地修改后的信息(成功的话)



#### 示例

含冲突信息的文件的内容：

```bash
... 
//下面是冲突的行
<<<<<<< HEAD
it is a bad 
=======
it is a good
>>>>>>> branch
```

基本上，您会看到两个具有相似代码段的段：

1. 上面的代码片段来自main分支。之所以称为 HEAD，是因为 HEAD 指针在合并时引用了这个分支. 继续上面的示例，此代码将来自`main`分支。
2. 底部代码片段来自您要合并到main分支的分支。这就是为什么它显示代码来自`branch`.

我将删除不想要的以及无关的行来得到这个

```bash
...
it is a good
```

这样解决了冲突。对所有含冲突信息的文件的内容执行此操作后，您可以提交。这将完成您的合并



#### 合并提交

您可能会发现自己创建了许多小提交，这些小提交带有微小的相关更改，这些更改实际上可以存储在单个提交中。在这里，您需要使用`rebase`命令压缩您的提交。假设你有四个我想合并的提交。您将输入以下内容：

```
$ git rebase -i HEAD~4
```

从这里，系统会提示您选择一个提交以将其他提交折叠到其中，并选择应该合并哪些提交：

```bash
pick 01d1124 Adding license
pick 6340aaa Moving license into its own file
pick ebfd367 Jekyll has become self-aware.
pick 30e0ccb Changed the tagline in the binary, too.

# Rebase 60709da..30e0ccb onto 60709da
#
# Commands:
#  p, pick = use commit
#  e, edit = use commit, but stop for amending
#  s, squash = use commit, but meld into previous commit
#
# If you remove a line here THAT COMMIT WILL BE LOST.
# However, if you remove everything, the rebase will be aborted.
#
```

最好选择最顶层的提交并将其余提交压缩到其中。您可以通过将文本文件更改为此：

```bash
pick 01d1124 Adding license


squash 6340aaa Moving license into its own file
squash ebfd367 Jekyll has become self-aware.
squash 30e0ccb Changed the tagline in the binary, too.

# Rebase 60709da..30e0ccb onto 60709da
#
# Commands:
#  p, pick = use commit
#  e, edit = use commit, but stop for amending
#  s, squash = use commit, but meld into previous commit
#
# If you remove a line here THAT COMMIT WILL BE LOST.
# However, if you remove everything, the rebase will be aborted.
#
```

瞧！所有这些微小的提交都合并为一个提交，并且您拥有一个更清晰的日志文件。
