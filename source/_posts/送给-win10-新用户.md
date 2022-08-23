---
title: 送给 win10 新用户
date: 2022-08-23 15:28:22
tags:
- win10
- 家庭版win10系统
- uac
- 用户帐号控制
- 启用administrator帐号
- 电脑操作技巧
---

*禁用 uac 的方法*

1. 开始，运行，输入 uac 回车；设置拖到底（从不通知），确定。
2. 开始，运行，输入 ``` gpedit.msc ``` 回车；在“计算机配置”，展开“windows设置”，“安全设置”，“本地策略”，“安全选项”；
>先找到“``` 用户帐户控制-以管理员模式批准运行所有管理员 ```”，双击打开，设为“``` 已禁用 ```”，点击``` 确定 ```。

3. 重启电脑。

现在你的电脑你作主，可以横着走！

对于家庭版win10，必须切换到``` administrator ``` 帐号操作！
1. 启用``` administrator ```帐号
```bash
net user administrator /active:yes
```
2. 开始，点击当前帐号头像，再选择``` administrator ```切换到administrator登陆系统再执行上述的步骤禁用uac。
