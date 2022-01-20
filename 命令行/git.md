- `git init`：将当前目录初始化为git仓库

- `git add file`：将文件file添加到下次提交中

- `git commit -m "message"`：提交更改

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

- `git checkout id1`：回到运行完了commit为 `id1`的时候

  >  git checkout 用于切换分支或恢复工作树文件，这个命令很危险，会改写工作区

- `git checkout main`：切换到main分支上
