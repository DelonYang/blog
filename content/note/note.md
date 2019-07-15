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

    设置免密登陆：
    git config --global credential.helper store
    
    建立远程git仓库：
    1. 创建git用户
    2. 创建git仓库：git init --bare demo.git
    3. 修改目录权限
    4. 远程访问：git clone git@192.1.1.1:/data/gitrepo/demo.git
```

[手动搭建git远程项目](https://www.jianshu.com/p/0c939f63af41)

常用git命令与alias：

|alias|command|
|:---|:----|
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
5. 用户管理
   1. 添加用户： `create user name identified by 'passwd';`
   2. 授权： `grant all privileges on db.table to name@'ip' identified by 'passwd';`
   3. `flush privileges;`
      1. all privileges：所有权限
      2. select：读取权限
      3. delete：删除权限
      4. update：更新权限
      5. drop：删除数据库、数据表权限
   4. 删除用户 `drop user zhangsan@'%'`
   5. 修改密码：`update mysql.user set password = password('zhangsannew') where user = 'zhangsan' and host = '%';`


### 工具
#### 1. httpie

[github地址](https://github.com/jakubroztocil/httpie)
相比curl，wget，这简直是神器

用法： `http [flag] method url item`

method 为http方法，默认为 get 或 post，以参数为准

传参：

- get 查询字符串： key==value
- post json/form key=value
- 以原值传，int，bool等类型 key:=value
- 设置header： name: value
- 使用文件内容： key:=@value.json
- 传文件: key@tt.png
- 传json字符串： key:='[1,2,3]'
- 下载文件： http -d/--download http://XXX.tar.gz
