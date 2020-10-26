# Shell学习

[TOC]

## 1. 文件表达式

- `-e <filename>`如果filename存在，则为真；
- `-d <filename>`如果filename为目录，则为真；
- `-f <filename>`如果filename为常规文件，则为真；
- `-L <filename>`如果filename为符号链接，则为真；
- `-r <filename>`如果filename可读，则为真；
- `-w <filename>`如果filename可写，则为真；
- `-x <filename>`如果filename可执行，则为真；
- `-s <filename>`如果filename长度*不为0*，则为真；
- `-h <filename>`如果filename是软连接，则为真；
- `filename1 -nt filename2`如果filename1比filename2新，则为真；
- `filename1 -ot filename2`如果filename1比filename2旧，则为真。

## 2. 整数变量表达式

| 表达式 | 含义     |
| ------ | -------- |
| `-eq`  | 等于     |
| `-ne`  | 不等于   |
| `-gt`  | 大于     |
| `-ge`  | 大于等于 |
| `-lt`  | 小于     |
| `-le`  | 小于等于 |

## 3. 字符串变量表达式

| 表达式                        | 含义                             |
| ----------------------------- | -------------------------------- |
| `if [ $string1 = $string2 ]`  | 如果string1等于string2，则为真   |
| `if [ $string1 != $string2 ]` | 如果string1不等于string2，则为真 |
| `if [ -n $string ]`           | 如果string非空，则为真           |
| `if [ -z $string ]`           | 如果string为空，则为真           |
| `if [ $string ]`              | 如果string非空，则为真           |

## 4. 逻辑表达式

| 表达式            | 含义   |
| ----------------- | ------ |
| `if [ ! 表达式 ]` | 逻辑非 |
| `if [ 表达式1 -a 表达式2 ]` | 逻辑与 |
| `if [ 表达式1 -o 表达式2 ]` | 逻辑或 |

