# GCC命令

**语法**

```bash
gcc (选项) (参数)
```

**选项**

```txt
-o：指定生成的输出文件；
-E：仅执行编译预处理；
-S：将C代码转换为汇编代码；
-wall：显示警告信息；
-c：仅执行编译操作，不进行连接操作。
```

**参数**

```txt
C源文件：指定C语言源代码文件。
```

假设源程序文件名为*test.c*

无选项编译链接

```bash
gcc test.c
```

将test.c预处理、汇编、编译并链接形成可执行文件。这里未指定输出文件，默认输出为a.out。

选项 -o

```bash
gcc test.c -o test
```

将test.c预处理、汇编、编译并链接形成可执行文件test。-o选项用来指定输出文件的文件名。

选项 -S

```bash
gcc -S test.i
```

将预处理输出文件test.i汇编成test.s文件。

选项 -c

```bash
gcc -c test.s
```

将汇编输出文件test.s编译输出test.o文件。

无选项链接

```bash
gcc test.o -o test
```

将编译输出文件test.o链接成最终可执行文件test。

选项 -O

```bash
gcc -O1 test.c -o test
```

使用编译优化级别1编译程序。级别为1~3，级别越大优化效果越好，但编译时间越长。

**多源文件编译**

多个源文件进行编译有两种方法：

> 假设现在有两个源文件：test.c testfun.c

*方法一：*多文件一起编译

```bash
gcc testfun.c test.c -o test
```

这条命令将testfun.c和test.c分别编译后链接成test可执行文件。

*方法二：*分别编译各个源文件，之后对编译后输出的目标文件链接

```bash
gcc -c testfun.c # 将testfun.c编译成testfun.o
gcc -c test.c # 将test.c编译成test.o
gcc testfun.o test.o -o test
```

