---
title: linux打补丁相关的两个命令 patch 和 diff
date: 2022-08-23 17:57:31
tags:
---
> 补丁是描述文件修改的文件。准确来说，包括移除或添加的代码清单，以及 (有时) 从参考文档取得的内容，用以取代修改的内文 (可以辨识取代的内容)。
修改文件的工具名称就是 patch。

添加为 diff，用法如下：
```bash
diff -u file.old file.new >file.patch
```
file.patch 文件包括变更 file.old 为 file.new 的指令。可以发送给其他人，用于从两个文件添加 file.new，如：
```bash
patch -p0 file.old <file.patch
```
现在，此文件 file.old 内容等同于 file.new。
