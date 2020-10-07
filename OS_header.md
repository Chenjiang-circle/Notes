# C头文件的学习

[TOC]

## 1. `<stdio.h>`

> stdio就是“standard input & output”，即标准输入输出。

该头文件定义了三个变量类型，一些宏和各种函数来执行输入和输出。<a href='./OS_宏.md'>什么是宏</a>

具体关于头文件`stdio.h`中定义的变量类型、宏定义、函数，请<a herf="https://www.runoob.com/cprogramming/c-standard-library-stdio-h.html">点击这里</a>

## 2. `<stdlib.h>`

> stdlib就是“standard library”，即标准库。

stdlib.h里面定义了五种类型、一些宏和通用工具函数。

- 类型例如：size_t、wchar_t、div_t、ldiv_t和lldiv_t；

- 宏例如：EXIT_FAILURE、EXIT_SUCCESS、RAND_MAX和MB_CUR_MAX等等；

- 常用的函数如：malloc()、calloc()、realloc()、free()、system()、atoi()、atol()、rand()、srand()、exit()等等。

|      | 宏 & 描述                                                    |
| :--- | :----------------------------------------------------------- |
| 1    | **NULL** 这个宏是一个空指针常量的值。                        |
| 2    | **EXIT_FAILURE** 这是 exit 函数失败时要返回的值。            |
| 3    | **EXIT_SUCCESS** 这是 exit 函数成功时要返回的值。            |
| 4    | **RAND_MAX** 这个宏是 rand 函数返回的最大值。                |
| 5    | **MB_CUR_MAX** 这个宏表示在多字节字符集中的最大字符数，不能大于 MB_LEN_MAX。 |

|      | 函数 & 描述                                                  |
| :--- | :----------------------------------------------------------- |
| 1    | [double atof(const char *str)](https://www.runoob.com/cprogramming/c-function-atof.html) 把参数 *str* 所指向的字符串转换为一个浮点数（类型为 double 型）。 |
| 2    | [int atoi(const char *str)](https://www.runoob.com/cprogramming/c-function-atoi.html) 把参数 *str* 所指向的字符串转换为一个整数（类型为 int 型）。 |
| 3    | [long int atol(const char *str)](https://www.runoob.com/cprogramming/c-function-atol.html) 把参数 *str* 所指向的字符串转换为一个长整数（类型为 long int 型）。 |
| 4    | [double strtod(const char *str, char **endptr)](https://www.runoob.com/cprogramming/c-function-strtod.html) 把参数 *str* 所指向的字符串转换为一个浮点数（类型为 double 型）。 |
| 5    | [long int strtol(const char *str, char **endptr, int base)](https://www.runoob.com/cprogramming/c-function-strtol.html) 把参数 *str* 所指向的字符串转换为一个长整数（类型为 long int 型）。 |
| 6    | [unsigned long int strtoul(const char *str, char **endptr, int base)](https://www.runoob.com/cprogramming/c-function-strtoul.html) 把参数 *str* 所指向的字符串转换为一个无符号长整数（类型为 unsigned long int 型）。 |
| 8    | [void free(void *ptr)](https://www.runoob.com/cprogramming/c-function-free.html) 释放之前调用 *calloc、malloc* 或 *realloc* 所分配的内存空间。 |
| 9    | [void *malloc(size_t size)](https://www.runoob.com/cprogramming/c-function-malloc.html) 分配所需的内存空间，并返回一个指向它的指针。 |
| 10   | [void *realloc(void *ptr, size_t size)](https://www.runoob.com/cprogramming/c-function-realloc.html) 尝试重新调整之前调用 *malloc* 或 *calloc* 所分配的 ptr 所指向的内存块的大小。 |
| 11   | [void abort(void)](https://www.runoob.com/cprogramming/c-function-abort.html) 使一个异常程序终止。 |
| 12   | [int atexit(void (*func)(void))](https://www.runoob.com/cprogramming/c-function-atexit.html) 当程序正常终止时，调用指定的函数 **func**。 |
| 13   | [void exit(int status)](https://www.runoob.com/cprogramming/c-function-exit.html) 使程序正常终止。 |
| 16   | [void *bsearch(const void *key, const void *base, size_t nitems, size_t size, int (*compar)(const void *, const void *))](https://www.runoob.com/cprogramming/c-function-bsearch.html) 执行二分查找。 |
| 17   | [void qsort(void *base, size_t nitems, size_t size, int (*compar)(const void *, const void*))](https://www.runoob.com/cprogramming/c-function-qsort.html) 数组排序。 |
| 18   | [int abs(int x)](https://www.runoob.com/cprogramming/c-function-abs.html) 返回 x 的绝对值。 |
| 19   | [div_t div(int numer, int denom)](https://www.runoob.com/cprogramming/c-function-div.html) 分子除以分母。 |
| 20   | [long int labs(long int x)](https://www.runoob.com/cprogramming/c-function-labs.html) 返回 x 的绝对值。 |
| 21   | [ldiv_t ldiv(long int numer, long int denom)](https://www.runoob.com/cprogramming/c-function-ldiv.html) 分子除以分母。 |
| 22   | [int rand(void)](https://www.runoob.com/cprogramming/c-function-rand.html) 返回一个范围在 0 到 *RAND_MAX* 之间的伪随机数。 |
| 23   | [void srand(unsigned int seed)](https://www.runoob.com/cprogramming/c-function-srand.html) 该函数播种由函数 **rand** 使用的随机数发生器。 |
| 24   | [int mblen(const char *str, size_t n)](https://www.runoob.com/cprogramming/c-function-mblen.html) 返回参数 *str* 所指向的多字节字符的长度。 |

## 3. `<assert.h>`

C 标准库的 **assert.h**头文件提供了一个名为 **assert** 的宏，它可用于验证程序做出的假设，并在假设为假时输出诊断消息。

**assert.h**中定义的唯一的函数：

```c
void assert(int expression)
```

assert只有在 Debug 版本中才有效，如果编译为 Release 版本则被忽略。

##  4. `<unistd.h>`

**unistd.h** 是 C 和 C++程序设计语言中提供对 [POSIX](https://baike.baidu.com/item/POSIX) 操作系统 API 的访问功能的头文件的名称。该头文件由 POSIX.1 标准（可移植系统接口）提出，故所有遵循该标准的操作系统和编译器均应提供该头文件.

对于类 Unix 系统，unistd.h 中所定义的接口通常都是大量针对系统调用的封装（英语：wrapper functions），如 fork、pipe 以及各种I/O 原语（read、write、close、getpid 等等）。

