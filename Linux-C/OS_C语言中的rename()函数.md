# *rename()*函数

函数名：`reanme()`

头文件：`<stdio.h>`

*函数语法：*

```c
int rename(char* oldname, char* newname);
```

功能：重命名

参数：

- char* oldname 文件的就名字
- char* newname 文件的旧名字

返回值：

- 成功，返回`0`
- 失败，返回`-1`

*重命名文件：*

- 如果newname指定的文件存在，则会被删除。
- 如果newname与oldname不在一个目录下，则相当于移动文件。

*重命名目录：*

- 如果oldname和oldname都为目录，则重命名目录。
- 如果newname指定的目录存在且为空目录，则先将newname删除。
- 对于newname和oldname两个目录，调用进程必须有写权限。
- 重命名目录时，newname不能包含oldname作为其路径前缀。例如，不能将/usr更名为/usr/foo/testdir，因为老名字(/usr/foo)新名字的路径前缀，因而不能将其删除。