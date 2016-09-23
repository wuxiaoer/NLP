---
layout: post
title: "正则表达式, 文本正则化和编辑距离"
date: 2016-09-23 22:10:36 +0800
category: nlp
comments: true
---

1 总体介绍
=======
**ELIZA** : 早期的自然语言处理对话系统，可以和人类进行简单的对话。类似与当今的聊天机器人(chatbots)

然而现代的对话系统是一个非常复杂的系统，通过对用户的意图进行理解，进行问题回答，订购机票，寻找餐馆等。

首先对描述文本模式的最重要的工具 —— 正则表达式(Regular Expression)进行介绍。

正则表达式可以从文件中提取指定的字符串。


接着开始介绍文本正则化(Text Normalization), 其中正则表达式起到非常重要的作用。

规范化文本—— 即表示把文本转换为更加方便的，标准的形式。

有如下文本正则化任务

- tokenization(分词)

- lemmatization（词形还原）
    - Stemming(词干提取)

- sentence segmentation（句子分段）


最后介绍编辑距离(Edit Distance) —— 用于度量两个字符串的相似度。

编辑距离在自然语言处理中有着广泛的应用，如：
> - 拼写矫正(Spelling Correction)
> - 语音识别(Speech Recognition)
> - 指代消解(Coreference Resolution)

2 正则表达式
======
正则表达式： Regular Expression(RE)

一种指定文本搜索字符串的语言， 应用的非常的广泛，
- 每一种计算机语言中
- 文本处理器
- 文本处理工具（像Unix工具grep或者Emacs）

正则表达式的正式定义：

用来刻画一组字符串的代数标记法。

在文本搜索中尤其有用。

2.1 基本正则表达式模式
------
最简单的正则表达式类型 —— 简单字符序列

例如：
搜索woodchunck, 使用正则表达式/woodchunck/即可

表达式/Buttercup/匹配任何包含子字符串Buttercup的字符串

**表1 一些简单的正则表达式搜索**

|RE|模式匹配例子|
|:---:|:---:|
|/woodchunck/|“interesting links to <u>woodchucks</u> and lemurs”|
|/a/|“M<u>a</u>ry Ann stopped by Mona’s”|
|/!/|“You’ve left the burglar behind again<u>!</u>” said Nori|
