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

常用git命令与alias：
|:---|:----|
|alias|command|
|gst|git status|
|gaa|git add --all|
|gcmsg|git commit -m|
|gcam|git commit -a -m|
|gp|git push|
|gl|git pull|

### 数据库

1. 表迁移：
   1. 如果表已经存在

        ```sql
        INSERT INTO newtable (*column) SELECT *column FROM oldtable WHERE ...; 
        ```
   2. 表不存在
        ```sql
        SELECT *column INTO newtable from oldtable WHERE ...;`
        ```

2. 查询时不区分大小写

    1. 使用方法：`select * from atable where lower(name)=lower("regs")`
    2. 比较时不区分：`select * from atbale where name="regs" COLLATE NOCASE`
    3. 建列时设置不区分：`create table atable (name varchar COLLATE NOCASE)`
3. 改名

    1. 改表名：`alter table old_name rename to new_name`

4. 数据库脚本
   1. sqlite读取sql文件：sqlite3 data.db < tt.sql
