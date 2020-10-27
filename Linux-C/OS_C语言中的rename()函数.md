# *rename()*函数

函数名：`reanme()`

头文件：`<stdio.h>`

*函数语法：*

```c
int rename(char* oldname, char* newname);
```

功能：重命名（如果带上文件路径，则为移动文件的操作）

参数：

- char* oldname 文件的就名字
- char* newname 文件的旧名字

返回值：

- 成功，返回`0`
- 失败，返回`-1`

