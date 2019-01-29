#Flask

## SQLAlchemy
### 1. 使用步骤


### 2. api及关系处理
**1. 一对多关系**


```python
    class User(db.Model):
        id=db.Column(db.Integer, primary_key=True)
        name=db.Column(db.String(60), nullable=False, unique=True)
        addresses=db.relationship('Address', backref='user', lazy=True)

    class Address(db.Model):
        id=db.Column(db.Integer, primary_key=True)
        info=db.Column(db.String(100), nullable=False)
        user_id=db.Column(db.Integer, db.ForeignKey('user.id'), nullable=False)
```
其中`relationship`函数的参数为：
- backref 在一对多或多对一之间建立双向关系
- lazy:默认值是True, 懒加载
- remote_side: 表中的外键引用的是自身时
- secondary: 多对多指定中间表关键字
- cascade: 级联删除
- order_by: 在一对多的关系中，设置排序，比如：

```python
    addresses=db.relationship('Address', backref='user', lazy=True, order_by=lambda: desc(Address.email))
```

**类型对照**

|类型名|Python类型|说明|
|:----:|:--------|:----|
|Integer|int|-|
|SmallInteger|int|-|
|BigInteger|int / long|-|
|Float|float||
|Numeric|decimal.Decimal||
|String|str||
|Text|str||
|Boolean|bool||
|Date|datetime.date||
|Time|datetime.time||
|DateTime|datetime.datetime||
|Interval|datetime.timedelta||
|Enum|str||
|PickleType|AnyObject||
|LargeBinary|str|二进制文件|

**常用的列选项**

- primary_key 主键
- unique
- index 创建索引
- nullable 空值
- default 默认值，函数去掉括号
- onupdate 更新时自动触发

### 3. 增删改查

**1. session中对象的状态**

对数据的更改都是通过操作`session`缓存来的，首先我们需要知道`session`中对象的几种状态：

- Transient：实例还不在session中，还没有保存到数据库中去，没有数据库身份，想刚创建出来的对象
- 用add()一个transient对象后，就变成了一个pending对象，这时候仍然没有flushed到数据库中去，直到flush发生。
- 实例出现在session中而且在数据库中也有记录了，通常是通过flush一个pending实例变成Persistent或者从数据库中querying一个已经存在的实例。
- 一个对象它有记录在数据库中，但是不在任何session中
