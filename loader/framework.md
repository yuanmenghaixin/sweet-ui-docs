# 架构总览

## 概述

`sweet-loader`主要由`gulp`和`webpack`两大部分组成，其中`gulp`负责`搬运`和`自主逻辑`，`webpack`则是负责对各类文件进行`编译`和`解析`，最终代码编译后运行，在根目录下还有其他配置文件，比如`eslint`代码校验工具等。

## 移动

该部分功能由`/build/task/move.js`gulp任务处理，包括图片、字体文件、JSON文件等。

## 编译/解析

该部分功能由`/build/webpack/index.js`webpack的loader来处理，包括`.js`、`.vue`、`.(scss|css|less)`以及图片格式和音频格式还有字体格式等。

## 监听

运行`npm start`可以开启本地开发模式，该模式具有自动监听文件变化从而改变浏览器渲染的效果，该部分监听的文件则由`/build/task/watch.js`控制，监听需要监听的文件从而提高开发效率。

## 校验

根目录下配置`.eslintrc.js`、`.eslintignore`等文件。

## 脚本

根目录下配置`package.json`里的`script`。


