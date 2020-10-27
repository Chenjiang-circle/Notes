# *strcpy()*函数

C语言中的`strcpy()`函数用于对字符串进行复制（拷贝）。

来自头文件`string.h`

```c
char* strcpy(char* strDestination, const char* strSource);
```

*参数说明：*

- strDestination：目的字符串。
- strSource：源字符串。

strcpy() 会把 strSource 指向的字符串复制到 strDestination。
必须保证 strDestination 足够大，能够容纳下 strSource，否则会导致溢出错误。
*返回值：*目的字符串，也即 strDestination。