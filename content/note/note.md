---
title: "好记性不如烂博客！"
date: 2019-01-18T16:38:54+08:00
---

### Git
常用命令:

```
    远程库：
    git init --bare 在远程库中新建项目
    git remote -v 查看远程库
    git remote add url

    stash:
    git stash 将当前工作区、暂存区保存
    git stash save "msg" 保存并起别名
    git stash list
    git stash apply [--index] [<stash>] 恢复，但不会删除保存内容
    git stash pop [--index] [<stash>] 恢复并删除
    git stash clear

    忽略已追踪的文件：
    git rm -r --cached log*
    git add . && git commit -m ""
    修改.gitignore

    git reset "commitID" 版本回退
    git checkout -- file 丢弃更改
    设置换行符：
    git config --global core.safecrlf true 提交时自动转换为LF
    
```

### 数据库

1. 表迁移：
   1. 如果表已经存在
        INSERT INTO newtable (*column) SELECT *column FROM oldtable WHERE ...; 
   2. 表不存在
        SELECT *column INTO newtable from oldtable WHERE ...;