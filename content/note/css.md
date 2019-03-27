
---
title: "css"
date: 2019-03-19T10:47:54+08:00
---
# CSS

## CSS实例
1. 背景设置：图片背景、颜色、位置

    ```css
    body{
        background-image: url();
        background-color: red;
        background-repeat: repeat-x; /* 水平重复 */
        background-position: right top;

        /* 设置渐变背景 */
        background-color: #8EC5FC;
        background-image: linear-gradient(62deg, #8EC5FC 0%, #E0C3FC 100%);
    }
    ```
2. 文本

    1. 文本颜色
        ```css
        body {
            color: red;/* 没有特别设置的该页面所有文本都会是红色 */
        }
        p {
            color: #00f000;
        }
        ```
    2. 对齐、缩进
        ```css
        h1 p{
            text-alian: center; /* left, center, right, justfiy; */
            text-indent: 2em;
        }
    3. 装饰
        ```css
        p.main{
            text-decoration: none; /* overline, line-through, underline; */
            text-transform: uppercase;/* uppercase, lowercase, capitalize; */
            line-height: 100%; /* 行高 */
            letter-spacing: 2px; /* 字符间距 */
        }
        ```
    [文本参考](http://www.runoob.com/css/css-text.html)
3. 字体

    ```css
    font-family:"font1",font2, font3; /* 逐个匹配 */
    font-size: 10px; /* 1.5em; 100%; */
    font-style: normal; /* italic 斜体 */
    font-weight: normal; /* lighter,bold, bolder, 100~900 */
    ```
4. 链接

    一个链接有集中形式，伪类{link, visited, hover}

    ```css
    a:link{
        color: red;
        font-family: "";
        text-decoration: none;
        background-color: red;
    }
    ```
5. 列表

    ```css
    ul {
        list-style: type position image;
        /* type: 类型 
        position: 前标的位置，默认 outside
    }
    ```
6. 盒模型
    所有css元素都可以看作是个盒子，元素定义在盒子内部，从外到内以此为：margin, border, padding, content; width, height指定了content的宽度和高度。
    ![盒模型](http://www.runoob.com/images/box-model.gif)

    ```css
    div {
        width: 22px;
        padding: 3px;
        border: 2px solid gray;
        border-radius: 8px;
        margin: 0px;
        /* outline 为外边框，在border外面 */
        /*margin, padding 可以简写：
        10px 20px; 上下10， 左右20；
        10px 20px 30px; 上10， 左右20， 下30；
        10px 20px 30px 40px；一次对应上下左右;
        */
    }
    ```
7. 选择器
    选择器是css的基础，常见的有元素，类，id，子女等
    1. 元素选择器：`p{}, h1{}`
    2. 类选择器： `.abc{}, p.title{}`
    3. id选择器： `#abc{}`, ID唯一
    4. 子女选择器： `div.abc p{}`
    5. 组选择器： `p, h1, div{}`

    除了这些基本的选择器，sass语法增强了选择器的能力；

8. 定位position
    position可以选值：static(默认), relative, fixed, absolute, sticky
    1. static
        html默认元素，不会受到top, bottom, left, right影响
    2. fixed
        定位于浏览器窗口，不会随页面滚动，会与其他元素重叠;top,left,right顺序有待考究
    3. relative
        相对于元素原位置移动
    4. absolute
        相对于父元素移动， 不占空间，会重叠
    5. stickly
        滚动定位，当页面滚动至指定位置时便不再动
    
    overflow,超出显示部分如何显示：
    1. scroll 滚动
    2. hidden 隐藏
    3. visible 超出显示
    4. auto

9. 居中对齐
    1. 元素居中对齐

        ```css
        .center {
            margin: auto;
            width: 80%; /* 未设置width或者设置为100%，居中不会生效*/
        }
        ```
    2. 文本居中对齐

        ```css
        p {
            text-align: center;
        }
        ```
    3. 图片水平居中

        ```css
        img {
            display: block;
            margin: auto;
            width: 50%;
        }
        ```
    4. 悬挂

        ```css
        .right {
            position: absolute;
            right: 0px;
        }
        ```
    5. 垂直居中
    
        ```css
        .center {
            padding: 100px; /*设置一定量的padding */
        }
        ```
    