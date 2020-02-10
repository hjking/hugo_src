---
title: "org mode 使用和配置"
date: 2018-11-28T15:04:39+08:00
draft: false
---

## Headlines

标题是以 `*` 开头，一个 `*` 表示一级标题，2个 `*` 表示二级标题，以此类推。

### 视图切换

org允许在几种可视模式间切换：折叠，只显示标题，显示全部。

`S-TAB` ： 全局可视模式切换。

`TAB` ：当前标题下切换。

org 默认是设置成折叠模式，只有顶级标题可见。可以通过 `org-startup-folded` 设置全局的。或者在org文件中通过关键字 `#+STARTUP` 设置，只针对当前org文件的。


## Templates
### Structure Template

通过使用 `<s[TAB]` 来插入代码块。

```lisp
(setq org-structure-template-alist
      '(("s" "#+begin_src ?\n\n#+end_src" "<src lang=\"?\">\n\n</src>")
        ("e" "#+begin_example\n?\n#+end_example" "<example>\n?\n</example>")
        ("q" "#+begin_quote\n?\n#+end_quote" "<quote>\n?\n</quote>")
        ("v" "#+BEGIN_VERSE\n?\n#+END_VERSE" "<verse>\n?\n</verse>")
        ("c" "#+BEGIN_COMMENT\n?\n#+END_COMMENT")
        ("p" "#+BEGIN_PRACTICE\n?\n#+END_PRACTICE")
        ("l" "#+begin_src emacs-lisp\n?\n#+end_src" "<src lang=\"emacs-lisp\">\n?\n</src>")
        ("L" "#+latex: " "<literal style=\"latex\">?</literal>")
        ("h" "#+begin_html\n?\n#+end_html" "<literal style=\"html\">\n?\n</literal>")
        ("H" "#+html: " "<literal style=\"html\">?</literal>")
        ("a" "#+begin_ascii\n?\n#+end_ascii")
        ("A" "#+ascii: ")
        ("i" "#+index: ?" "#+index: ?")
        ("I" "#+include %file ?" "<include file=%file markup=\"?\">")))
```

## Agenda


<!-- more -->


## Habit

## Capture
### Capture templates

## Refile

## Publishing

## Archiving


## 参考

