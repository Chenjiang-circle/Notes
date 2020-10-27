# *strcmp()*函数

C语言 strcmp() 函数用于对两个字符串进行比较（区分大小写）。

*头文件：*`string.h`

语法：

```c
int strcmp(const char* str1, const char* str2);
```

strcmp()会根据ASCII编码依次比较str1和str2的每一个字符，直到出现不等的字符，或者到达字符串末尾（遇见`\0`）

*返回值：*

- 如果返回值`<0`，则表示str1小于str2；
- 如果返回值`>0`，则表示str1大于str2；
- 如果返回值`=0`，则表示str1等于str2。

