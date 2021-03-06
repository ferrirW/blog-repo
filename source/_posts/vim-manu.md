---
title: VIM 指令
date: 2019-01-05 20:29:30
tags:
---

VIM指令是linux入门必学的知识，回想发现和流氓高手里的猥琐秘籍很像哈哈，都讲究一个润物细无声，就是说刚开始的时候可能老是忘记，但是坚持用下去就会感受到大佬们为啥要这样设置。很多键位单纯背是靠不住的，只用在场景中使用过才能真的记住，总结“本”vim秘籍，总结目前掌握的命令，后续有更好的用法也会不断更新。

<!--more-->

### 忘记你我做不到

> - i→ 插入模式，按ESC键返回普通模式
> - x→ 删除光标所在的字符
> - :wq→ 保存退出(:w 保存，:q 退出)
> - dd→ 删除当前行
> - y→ 复制
> - yy→ 复制当前行。
> - p→ 粘贴

### 河东狮吼

1. 插入模式 Plus

> - a→ 在光标后插入
> - A→ 在当前行之后插入新字符
> - o→ 在当前行之后插入新行
> - O→ 在当前行之前插入新行
> - cw→ 替换从光标到单词结束

2. 移动命令

> - 0→ 移动到第一列
> - ^→ 移动到本行第一个非空字符
> - $→ 移动到本行末尾
> - gg→ 1G的简写，移动到文件首行
> - G→ 移动到文件末行
> - NG→ 跳到第N行
> - g_→ 移动到本行最后一个非空字符
> - /{$pattern}→ 搜索pattern字段

3. 撤销/恢复撤销

> - u→ 撤销
> - Ctrl-r→ 恢复

4. 加载/保存/退出/修改 文件(缓存)

> - :e [filepath]→ 打开
> - :w→ 保存
> - :saveas [filepath]→ 保存到
> - :x,ZZ或者:wq→ 保存当前文件并退出
> - :q!→ 退出但不保存，使用:qa!，即使在缓存中还有已经修改的也会退出。
> - :bn(bp)→ 显示下一个(上一个)文件缓存

### 单恋一枝花

> - . →重新执行上一个命令
> - N[命令]→ 会重复执行命令N次.

eg.
> - 2dd → 会删除2行
> - 5p → 会粘贴文本5次
> - 99iabc [ESC] → 会写入"abc" 99次
> - . → 执行上一个命令，即写入99个"abc".
> - 3.→ 会写入3个"abc"(不是99*3个).

### 迷宫

> - w→ 跳到下一个单词的开头
> - e→ 跳到这个单词的末尾
> - 默认单词是由字母和下划线组成。大写字符就是由空格分隔的，使用大写字符的效果，如下图:

![示例](https://static.oschina.net/uploads/img/201308/19135039_AdpL.jpg)

高效率移动
> - % → 找到最近的()
> - *(#) → 找到下一个(上一个)当前光标所在单词的位置

### 过火
大多数命令(y,d,v,gU,gu)使用下面这种通用格式：

<开始位置><命令><结束位置>
> - 0y$意味着：
> - 0→ 跳到本行开头
> - y→ 从这里开始复制
> - $→ 直到本行结束

> ye 意味着：
> - 从当前位置复制到单词的末尾

> y2/foo 意思是：
> - 一直复制到第二个foo出现的地方


### 错位

> - fa→ 跳到这行a字母的下一个出现的地方.
> - tb→ 跳到b字符的前一个字符.
> - 3fa→ 在这行中查找a出现的第三个位置.
> - F、T→ 与f、t相似， 但是方向相反.
> - **dta→ 删除光标与a之前的所有字符 **

![移动示例](https://static.oschina.net/uploads/img/201308/19135039_vFzT.jpg)

### 有一种爱叫做放手

1. 区域选择：<命令>a<对象> 和 <命令>i<对象> 命令可以是d,y,v

对于下图：
![map](https://static.oschina.net/uploads/img/201308/19135040_FZZt.png)
> - vi"→ 将会选择 foo
> - va"→ 将会选择 "foo"
> - vi)→ 将会选择 "foo"
> - va)→ 将会选择 ("foo")
> - v2i)→ 将会选择 map (+) ("foo")
> - v2a)→ 将会选择 (map (+) ("foo"))

2. 矩形选择块

列选择
> - ^ → 将光标定位到这行第一个非空格字符
> - Ctrl-v → 选择开始位置，一般配合I等修改指令实现多行操作
> - Ctrl-d → 向下移动 (也可使用 jjj 或者 %)
> - I## [ESC] → 用 ## 来注释每一行

注：图片来自网络，如有侵权请私信删除。
