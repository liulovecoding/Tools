- 技巧 
您的 shell 可以使用Tab 补全功能为您补全文件名和目录名。如果您的名称不完整（对于已经存在的名称），请尝试按tab自动完成键或可能的名称列表。

如果您想重新键入最近使用的相同指令，请按up键盘上的键，直到看到正确的指令。如果您正在执行重复指令，这将节省打字时间。
 
 . 则是表示目前所在的目录
 
 - `cd  ./laboo`  :进入当前目录的子目录lab00
 
 
..则表示目前目录位置的上一层目录

- `cd ..`：返回上一级
- `ls`：显示在当前目录下的所有文件和文件夹
- `ls ..`: 列出所在目录的父目录下的文件
- `ls filename`:列出所在目录下的子目录的所有子文件 #filename 是其子目录
- `cd -`:  返回进入此目录之前所在的目录
- `cd ~` ：返回主目录，~代表主目录(c/User/50657目录)
- `cd ~/Desktop/cs61a/lab/lab00 `：在主目录下的桌面上的cs61a的lab文件夹找lab00文件

- linux:`mkdir cs61a `:在当前目录下创建文件夹cs61a
- windows:`move <source path> <目的地 path>` //移动文件
- linux:`mv <source path>  <目的地 path>`：将给定源的文件移动到给定的目的地
- `mv  ~/Downloads/lab00   ~/Desktop/cs61a/lab` :移动文件lab00到lab文件夹中
- mv lab1/original lab1/newname:此命令不会移动文件，而是将其从 重命名original 为newname
- rm: 删除文件
- rm file1：此命令将从当前目录中删除 file1。如果file1不存在，它将不起作用。
-  rm -r dir1:此命令将dir1递归删除目录。换句话说，它会删除dir1除dir1自身之外的所有文件和目录。小心这个命令！
- cp: 复制文件
- cp lab1/original lab2/duplicate:此命令将复制目录中的original文件并在lab1目录中创建一个duplicate文件lab2。



```python```:打开python解释器(能写多行代码再运行)
```python lab00.py```:一次性运行lab00.py

```python -i```:打开python解释器(写一行运行一行)

```python -i lab00.py ```:交互式运行lab00.py

```python -m doctest lab00.py```:运行lab00.py的文档字符串

>note:bash vs\ code 被认定为一个参数， vs code 被认定为两个参数


