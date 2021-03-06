---
title: "Sublime Text 3"
summary: "Sublime Text 3 技巧集锦"
date: 2018-11-28T15:04:39+08:00
draft: false
---

# Sublime Text 3

## 常用插件：

- Package Control

    安装和管理插件。

- BracketHighlighter

    高亮显示匹配的括号，引号和标签。

- TrailingSpacer

    高亮显示行尾多余的空格和Tab。

- Alignment

    等号智能对齐和统一缩进。

- SideBarEnhancement

    侧边栏增强。

- MarkDown Editing

    编辑markdown文件时提供语法支持，缩进。

- FileDiffs

    比较文件。

- [Markdown Enhancements](https://github.com/jonschlinkert/sublime-markdown-extended)

    增强编辑markdown文件时的着色和高亮。



## 常用快捷键：

### 移动

> Ctrl + ←/→：进行逐词移动
>
> Ctrl + ↑/↓移动当前显示区域
>
> Ctrl + Shift + L：将当前选中区域打散，实现对所有行进行同时编辑


### 选择

> Ctrl + Shift + J：快速选择同缩进的内容
>
> Ctrl + Shift + Space：快速选择当前作用域（Scope）的内容
>
> Ctrl + Shift + ←/→进行逐词选择
>
> Ctrl + D：选择当前光标所在的词并高亮该词所有出现的位置，再次Ctrl + > D选择该词出现的下一个位置，在多重选词的过程中，使用Ctrl + K进行跳过，使用Ctrl > + U进行回退，使用Esc退出多重编辑
>
> Ctrl + Shift + L：将当前选中区域打散
>
> Ctrl + J：把当前选中区域合并为一行
>
> Ctrl + M：在起始括号和结尾括号间切换
>
> Ctrl + Shift + M：快速选择括号间的内容

### 查找和替换

> Ctrl + D：选择当前光标所在的词并高亮该词所有出现的位置，再次 Ctrl + D选择该词出现的下一个位置，在多重选词的过程中，使用Ctrl + K进行跳过，使用Ctrl + U进行回退，使用Esc退出多重编辑
>
> F3：跳至当前关键字下一个位置
>
> Shift + F3：跳到当前关键字上一个位置
>
> Alt + F3：选中当前关键字出现的所有位置
>
> Ctrl + F 调出搜索框进行搜索
>
> Ctrl + H 进行替换
>
> 在搜索框输入关键字后Enter跳至关键字当前光标的下一个位置，Shift + Enter跳至上一个位置，Alt + Enter选中其出现的所有位置（同样的，接下来可以进行快速替换）
>
> 使用 Ctrl + Shift + F 开启多文件搜索&替换

<!-- more -->

### 跳转

> Ctrl + P会列出当前打开的文件（或者是当前文件夹的文件），输入文件名然后Enter跳转至该文件。
>
> 在Ctrl + P匹配到文件后，可以进行后续输入以跳转到更精确的位置：
> @ 符号跳转：输入@symbol跳转到symbol符号所在的位置
> \# 关键字跳转：输入#keyword跳转到keyword所在的位置
> : 行号跳转：输入:12跳转到文件的第12行。
>
> Ctrl + R会列出当前文件中的符号（例如类名和函数名，但无法深入到变量名），输入符号名称Enter即可以跳转到该处。
>
> Ctrl + G：跳转到指定行号
>
> F12快速跳转到当前光标所在符号的定义处（Jump to Definition）。

### 标签

> 使用Ctrl + N在当前窗口创建一个新标签，Ctrl + W关闭当前标签，Ctrl + Shift + T恢复刚刚关闭的标签。
>
> 分屏: Alt + Shift + 2进行左右分屏，Alt + Shift + 8进行上下分屏，Alt + Shift + 5进行上下左右分屏（即分为四屏）。
>
> 分屏之后，使用Ctrl + 数字键跳转到指定屏，使用Ctrl + Shift + 数字键将当前屏移动到指定屏。
>

### 编辑

> 格式化代码：Ctrl + [向左缩进，Ctrl + ]向右缩进，此外Ctrl + Shift + V可以以当前缩进粘贴代码（非常实用）。
>
> Ctrl + Enter：在当前行下面新增一行然后跳至该行
>
> Ctrl + Shift + Enter：在当前行上面增加一行并跳至该行
>
> Ctrl + Shift + ←/→进行逐词选择
>
> Ctrl + Shift + ↑/↓移动当前行
>
> Ctrl + J：把当前选中区域合并为一行

## 配置

Sublime Text并没有一个专门的配置界面，它使用JSON配置文件。JSON配置文件的引入简化了Sublime Text的界面，但也使得配置变得复杂，可以到[这里](http://sublime-text-unofficial-documentation.readthedocs.org/en/latest/reference/settings.html)查看可用的Sublime Text配置项。

### 主题

### 配色

### 编码


## 参考
1. [Sublime Text 全程指南](http://zh.lucida.me/blog/sublime-text-complete-guide/)
2. [Sublime Text 3 Documentation](http://www.sublimetext.com/docs/3/)
3. [Sublime Text 3 文档-中文](http://feliving.github.io/Sublime-Text-3-Documentation/)
4. [Sublime Text 非官方文档-英文](http://docs.sublimetext.info/en/latest/index.html)