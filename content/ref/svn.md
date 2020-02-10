---
title: "SVN"
date: 2018-11-28T15:04:39+08:00
draft: false
---

# SVN

## SVN Tricks and Tips

### svn ignore

- 当前目录忽略某个文件或某类文件

~~~ shell
svn propset svn:ignore "obj" .
~~~

以上命令不仅仅是添加一条SVN忽略规则，而且会清除掉之前添加的规则。

- 忽略多个文件和目录。

~~~ shell
svn propset svn:ignore "obj log *.class *.apk" .
~~~

- 当前目录和子目录递归忽略

~~~ shell
svn propset svn:ignore -R *.class .
~~~

递归忽略目录和子目录里的class文件。


- 编辑忽略属性

~~~ shell
svn propedit svn:ignore .
~~~

这条命令会打开默认编辑器供输入忽略规则，每行一条。

- 以文件里的列表作为忽略属性

将要忽略的文件和目录写到一个文件里，用以下命令导入来进行忽略：

~~~ shell
svn propset svn:ignore -R -F .svnignore .
~~~

- 如果想查看所有文件的svn信息，包括被忽略的：

~~~ shell
svn status --no-ignore
~~~

**不推荐使用propset**

### SVN Diff

#### 用 Vim 来 diff

首先写一个脚本，比如命名为svndiff：

~~~ shell
#!/bin/sh

# Configure your favorite diff program here.
DIFF="/usr/bin/vimdiff"

# Subversion provides the paths we need as the sixth and seventh
# parameters.
LEFT=${6}
RIGHT=${7}

# Call the diff command (change the following line to make sense for
# your merge program).
$DIFF $LEFT $RIGHT

# Return an errorcode of 0 if no differences were detected, 1 if some were.
# Any other errorcode will be treated as fatal.
~~~

编辑 =~/.subversion/config= , 找到:

~~~ shell
# diff-cmd = diff_program (diff,gdiff, etc.)
~~~

在下方添加一行:

~~~ shell
diff-cmd = /home/hongjin/bin/svndiff
~~~

等号后面是之前新建脚本的路径。
当再次使用 ~svn diff~ 命令时，就会自动调用上述脚本来比较版本差异了。