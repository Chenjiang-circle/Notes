[TOC]

## 1. *FILE*类型




可以用该结构体类型来定义文件类型的指针变量

```c
FILE *fp;
```

 FILE是在`stdio.h`中定义的结构体类型，封装了与文件有关的信息，如*文件句柄、位置指针及缓冲区*等，缓冲文件系统为每个被使用的文件在内存中开辟一个缓冲区，用来存放文件的有关信息，这些信息被保存在一个FILE结构类型的变量中，*fp是一个指向FILE结构体类型的指针变量*

## 2. 常用文件操作

### 2.1 *fopen()*函数

函数原型为：

````c
FILE *fopen(const char *filename, const char *mode);
// fopen(文件路径，文件使用方式);
````

fopen函数打开filename指定的文件，返回一个指向FILE类型的指针，无论使用哪种方式，当打开文件时出现了错误，fopen函数都将返回NULL。

常见的文件使用方式：

- 文本文件的使用方式：
	- `"r"`以只读的方式打开文件（该文件必须已经存在，若文件不存在，则会出错）；
	- `"w"`以只写的方式打开文件，**若文件存在则文件长度清为0**，即该文件内容会消失。若文件不存在则建立该文件；
	- `"a"`以只写的方式打开文本文件，位置指针移到文件末尾，**向文件尾部添加数据**，原文件数据保留，若文件不存在则会出错；
	- `"+"`与上面的字符**串**组合，表示以读写的方式打开文本文件，既可向文件中写入数据，也可从文件中读出数据。
- 二进制文件的使用方式：打开二进制文件的模式与打开文本文件的含义是一样的，不同的是模式名称里面多一个字母`b`，以表示以二进制形式打开文件。

### 2.2 *fclose()*函数

功能：关闭文件。

函数原型：

```c
int fclose(FILE *__stream)
```

关闭成功返回值0，否则返回非零值。

> 在执行完文件的操作后，要进行“关闭文件”操作。虽然程序在结束前会自动关闭所有的打开文件，但文件打开过多会导致系统运行缓慢，这时就要自行手动关闭不再使用的文件，来提高系统整体的执行效率。

### 2.3 *getc()*函数

在文件处理中，通过**getc()函数，**我们从输入文件流中获取下一个字符，并递增文件位置指针。 **函数getc()**的原型为：

```c
int getc(FILE *filename);
```

> It returns an integer value which is conversion of an unsigned char. It also returns EOF which itself is also an integer value. Whenever there is a binary file, check for EOF with the function feof().
>
> 它返回一个整数值，该值是无符号char的转换。它还返回EOF，它本身也是一个整数值。只要有二进制文件，请使用feof()函数检查EOF。

*扩展：*

看书的时候，发现了这四个函数，想知道他们的不同。结果上网查发现很多人说fgetc、fputc的f代表的是file，就是这两个函数是和文件有关的！但是一看他们的函数声明，如下图：

　　![img](https://images0.cnblogs.com/blog/693341/201412/121118011502379.png)![img](https://images0.cnblogs.com/blog/693341/201412/121118124312358.png)

　　![img](https://images0.cnblogs.com/blog/693341/201412/121118305405957.png)![img](https://images0.cnblogs.com/blog/693341/201412/121118401652865.png)

发现他们的参数里面都有文件指针啊！后来又去翻了翻APUE，发现那个f代表的其实是function，这是怎么一回事呢，且听我慢慢道来！

fgetc和getc他们的区别并不是在他们的使用上，而是在他们的实现上！具体来说，就是带f的(fgetc、fputc)实现的时候是通过函数来实现的，而不带f(putc、getc)的，实现的时候是通过宏定义来实现的！关于他们的不同点，就拿getc和fgetc来说，APUE(p115)上是这么写的：

1. getc的参数不应当是具有副作用的表达式。
2. 因为fgetc一定是一个函数，所以可以得到其地址。这就允许将fgetc的地址作为一个参数传送给另一个函数。
3. 调用fgetc所需时间很可能长于调用getc，因为调用函数通常所需的时间长于调用宏。

### 2.4 *mkdir()*函数

函数原型： 

```c
#include <sys/stat.h> 

int mkdir(const char *path, mode_t mode); 
```

*参数：*

- path：目录名 

- mode：目录权限 

*返回值：*

- 返回0 表示成功；
- 返回 -1表示错误，并且会设置errno值。 

*mode_t参数：*

```txt
S_IRWXU            00700 文件所有者具有读、写、执行权限
S_IRUSR (S_IREAD)  00400 文件所有者具可读取权限
S_IWUSR (S_IWRITE) 00200 文件所有者具可写入权限 
S_IXUSR (S_IEXEC)  00100 文件所有者具可执行权限
```

```txt
S_IRWXG 00070 用户组具有读、写、执行权限
S_IRGRP 00040 用户组具可读取权限
S_IWGRP 00020 用户组具可写入权限
S_IXGRP 00010 用户组具可执行权限
```

```txt
S_IRWXO 00007 其他用户具有读、写、执行权限
S_IROTH 00004 其他用户具可读取权限
S_IWOTH 00002 其他用户具可写入权限
S_IXOTH 00001 其他用户具可执行权限
```

### 2.5 *rename()*函数

头文件：`<stdio.h>`

*函数语法：*

```c
int rename(char* oldname, char* newname);
```

*功能：*重命名

*参数：*

- char* oldname 文件的就名字
- char* newname 文件的旧名字

*返回值：*

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