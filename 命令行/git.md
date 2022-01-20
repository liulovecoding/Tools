- `git init`：将当前目录初始化为git仓库
- `git add file`：将文件file添加到暂存区中(还有追踪列表)  //每更改一次就要添加一次

- `git reset HEAD file`：将添加到暂存区还未提交的文件从暂存区移除，使文件的状态恢复为已修改

> 撤销您不想跟踪的文件

- `git commit -m "message"`：提交暂存区的内容

> "message"：是这次提交的信息

- `git commit --amend`：已提交但尚未推送到`GitHub`网站上，可以使用 该命令 命令修改提交消息



> 当提交时，会分离一个节点(代表这个提交)，然后有个头指针指向最新的节点，通过指针后移回到之前的节点(即`git checkout id1`)，用该节点是存储库的状态来覆盖当前的状态
>
> 新节点指向它之前(最近)的旧节点
>
> 还有个分支指针一直指向该分支最新节点





文件的状态

> modified：修改，staged：暂存

![file-status](./file-status.png)

如图所示，文件分为两大类：

1. 未跟踪的文件：这些文件要么从未被跟踪过，要么已从跟踪中删除。Git 不会维护这些文件的历史记录。
2. 跟踪文件：这些文件已添加到 Git 存储库中，可以处于不同的修改阶段：未修改、已修改或暂存。
   1. 未修改的文件是自上一个版本的文件添加到 Git 存储库以来没有任何新更改的文件。
   2. 修改后的文件与 Git 最近保存的文件不同。
   3. 暂存文件是用户指定为未来提交的一部分的文件（通常通过使用 git add 命令）。



-  `git status`：显示工作树状态(当前目录所在存储库的) 

> 查看文件的状态

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
  



- `git remote add name URL `：将本地仓库与网站上的仓库关联起来 

> name: 遥控器的名字  ，URL：要关联的网站上的仓库的URL
>
> 用于push,pull

- `git remote -v`：查看关联的存储库

- `git pull(push) name main` : 拉(推)到遥控器名字为name的存储库上的man分支



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



合并 ：`git merge branch` //把分支branch 合并到当前所在分支上(假设为main)

> merge命令创建一个将两个分支连接在一起的新提交，并将main分支上最新的节点指向branch分支上最新的节点

合并冲突：尝试合并两个可能有冲突的信息的分支。如果两个分支上的提交更改了相同的文件，则可能会发生这种情况。Git 足够复杂，可以解决许多更改，即使它们发生在同一个文件中（尽管位置不同）。但是，有时 Git 无法解决冲突，因为更改会影响相同的方法/代码行。在这些情况下，它会将来自不同分支的两个更改作为*合并冲突*呈现给您

#### 解决合并冲突

Git 会告诉你哪些文件有冲突。您需要打开有冲突的文件并手动删除所有冲突的代码(选择某个分支删除)。完成此操作后，您必须提交以完成两个分支的合并。

#### 示例

有冲突的文件将包含如下所示的段：

```bash
<<<<<<< HEAD
for (int i = 0; i < results.length; i++) {
    println(results[i]);
    println("FIX ME!");
}
=======
int[] final = int[results.length];
for (int i = 0; i < results.length - 1; i++) {
    final[i] = results[i] + 1;
    println(final[i]);
}
>>>>>>> branch
```

基本上，您会看到两个具有相似代码段的段：

1. 上面的代码片段来自main分支。之所以称为 HEAD，是因为 HEAD 指针在合并时引用了这个分支. 继续上面的示例，此代码将来自`main`分支。
2. 底部代码片段来自您要合并到main分支的分支。这就是为什么它显示代码来自`branch`.

我将删除最上面的部分以及无关的行来得到这个

```bash
int[] final = int[results.length];
for (int i = 0; i < results.length - 1; i++) {
    final[i] = results[i] + 1;
    println(final[i]);
}
```

对由冲突解决标记划分的所有段执行此操作可以解决您的冲突。对所有冲突的文件执行此操作后，您可以提交。这将完成您的合并
