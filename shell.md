- 技巧 :shell 可以使用Tab 补全功能为您补全文件名和目录名。如果您的名称不完整（对于已经存在的名称）

 
 - . 则是表示目前所在的目录
 - ..则表示目前目录的上一级目录

- 更改所在目录

- `cd ..`：返回上一级
- `cd -`:  返回进入此目录之前所在的目录
- `cd ~` ：返回主目录，~代表主目录(c/User/50657目录)
- `cd  ./laboo`  :进入当前目录的子目录lab00
- `cd ~/Desktop/cs61a/lab/lab00 `：进入lab00文件夹


- `ls`：显示在当前目录下的所有文件和文件夹
- `ls ..`: 列出所在目录的父目录下的文件
- `ls filename`:列出所在目录下的filename文件夹的所有子文件



- 移动
- `mv  ~/Downloads/lab   ~/Desktop/cs61a/` :移动文件lab到cs61a文件夹中(cs61a后的/表示移入文件夹中)

- 重命名
- `mv hello he`:将hello重命名为he,因为是同一个目录的

- 删除
- `rm file1`: 从当前目录中删除文件file1。如果file1不存在，它将不起作用
- `rmdir lecture/`:删除当前目录下的文件夹lecture(前提是lesture是空的)


- 复制
- `cp lab1/1    lab2/2`:把lab1目录下的1复制给lab2目录下的2

- 创建目录
- `mkdir lecture`:在当前目录下创建文件夹lecture

```python```:打开python解释器(能写多行代码再运行)
```python lab00.py```:一次性运行lab00.py

```python -i```:打开python解释器(写一行运行一行)

```python -i lab00.py ```:交互式运行lab00.py

```python -m doctest lab00.py```:运行lab00.py的文档字符串

>note:bash vs\ code 被认定为一个参数， vs code 被认定为两个参数


