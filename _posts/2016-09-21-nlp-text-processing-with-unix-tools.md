---
layout: post
title: "Unix下文本处理工具"
date: 2016-09-21 20:40:36 +0800
category: nlp
comments: true
---

以下介绍Unix下的常用的文本处理工具以及一些常用的工具的联系

# Unix下常用文本处理命令
<hr style="height:5px;border:none;border-top:5px ridge green;" />

- ## grep

- ## sort

- ## uniq -c

- ## tr

命令说明

```
NAME
       tr - translate or delete characters

SYNOPSIS
       tr [OPTION]... SET1 [SET2]

DESCRIPTION
       Translate, squeeze, and/or delete characters from standard input, writing to standard output.

       -c, -C, --complement
              use the complement of SET1

       -d, --delete
              delete characters in SET1, do not translate

       -s, --squeeze-repeats
              replace each sequence of a repeated character that is listed in the last specified SET, with a single occurrence of that character

       -t, --truncate-set1
              first truncate SET1 to length of SET2

       --help display this help and exit

       --version
              output version information and exit

       SETs are specified as strings of characters.  Most represent themselves.  Interpreted sequences are:

       \NNN   character with octal value NNN (1 to 3 octal digits)

       \\     backslash

       \a     audible BEL

       \b     backspace

       \f     form feed

       \n     new line

       \r     return

       \t     horizontal tab

       \v     vertical tab

       CHAR1-CHAR2
              all characters from CHAR1 to CHAR2 in ascending order

       [CHAR*]
              in SET2, copies of CHAR until length of SET1

       [CHAR*REPEAT]
              REPEAT copies of CHAR, REPEAT octal if starting with 0

       [:alnum:]
              all letters and digits

       [:alpha:]
              all letters

       [:blank:]
              all horizontal whitespace

       [:cntrl:]
              all control characters

       [:digit:]
              all digits

       [:graph:]
              all printable characters, not including space

       [:lower:]
              all lower case letters

       [:print:]
              all printable characters, including space

       [:punct:]
              all punctuation characters

       [:space:]
              all horizontal or vertical whitespace

       [:upper:]
              all upper case letters

       [:xdigit:]
              all hexadecimal digits

       [=CHAR=]
              all characters which are equivalent to CHAR

       Translation  occurs  if -d is not given and both SET1 and SET2 appear.  -t may be used only when translating.  SET2 is extended to length of SET1 by repeating its last character as necessary.  Excess
       characters of SET2 are ignored.  Only [:lower:] and [:upper:] are guaranteed to expand in ascending order; used in SET2 while translating, they may only be used in pairs to specify  case  conversion.
       -s uses the last specified SET, and occurs after translation or deletion.

AUTHOR
       Written by Jim Meyering.

REPORTING BUGS
       GNU coreutils online help: <http://www.gnu.org/software/coreutils/>
       Report tr translation bugs to <http://translationproject.org/team/>

COPYRIGHT
       Copyright © 2016 Free Software Foundation, Inc.  License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>.
       This is free software: you are free to change and redistribute it.  There is NO WARRANTY, to the extent permitted by law.

SEE ALSO
       Full documentation at: <http://www.gnu.org/software/coreutils/tr>
       or available locally via: info '(coreutils) tr invocation'
```

举例说明

例1：将文件file中出现的"abc"替换为"xyz"
```
cat file | tr "abc" "xyz" > new_file
```

[注意]这里，凡是在file中出现的"a"字母，都替换成"x"字母，"b"字母替换为"y"字母，"c"字母替换为"z"字母。而不是将字符串"abc"替换为字符串"xyz"。

例2：使用tr命令“统一”字母大小写

（小写 --> 大写）
```
cat file | tr [a-z] [A-Z] > new_file
```

（大写 --> 小写）
```
cat file | tr [A-Z] [a-z] > new_file
```

例3：把文件中的数字0-9替换为a-j

```
cat file | tr [0-9] [a-j] > new_file
```

例4：删除文件file中出现的"Snail"字符
```
cat file | tr -d "Del" > new_file
```
[注意]这里，凡是在file文件中出现的'D','e','l'字符都会被删除！而不是仅仅删除出现的"Del”字符串。

例5：删除文件file中出现的换行'\n'、制表'\t'字符
```
cat file | tr -d "\n\t" > new_file
```
[注意]不可见字符都得用转义字符来表示的，这个都是统一的

例6：删除“连续着的”重复字母，只保留第一个

```
cat file | tr -s [a-zA-Z] > new_file
```

例7：删除空行
```
cat file | tr -s "\n" > new_file
```

例8：删除Windows文件“造成”的'^M'字符
```
cat file | tr -d "\r" > new_file
或者
cat file | tr -s "\r" "\n" > new_file
```

注意】这里-s后面是两个参数"\r"和"\n"，用后者替换前者

例9：用空格符\040替换制表符\011
```
cat file | tr -s "\011" "\040" > new_file
```

例10：把路径变量中的冒号":"，替换成换行符"\n"
```
echo $PATH | tr -s ":" "\n"
```

- ## wc

- ## sed

- ## cat

- ## echo

- ## cut

- ## paste

- ## head

- ## tail

- ## rev

- ## comm

- ## join

- ## shuf

- ## 文件重定向
```
>
<
|
```

# Unix下文本处理练习
<hr style="height:5px;border:none;border-top:5px ridge green;" />

# 统计文本中单词个数

# 单词列表排序

# 单词中提取有用信息

# 计算n-gram统计
