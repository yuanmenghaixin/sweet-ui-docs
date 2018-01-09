# 环境配置

## 概述

Sweet Loader 可以配置不同环境的配置文件，通过执行对应的命令进行打包处理，各个环境包含

## 目录结构

```
config
├── dev.server.js   // 本地开发web服务配置，如：端口号，反向代理
└── index.js        // 各个环境配置入口文件
```

## 本地开发 web 服务配置文件

```
{
    // 端口号
    port: 3002,
    // 反向代理设置
    porxys: porxys
}
```

[反向代理配置说明文档](proxy.md)


## 环境配置入口文件 index.js

**通用配置**

```
common: {
    babelInclude: [],  // 
    assetsSubDirectory: 'assets',   
    theme: 'demo_theme'
},
```

### babelInclude

babel压缩混淆包含的文件目录，例如：['node_modules/@sweet', 'test_model']

### assetsSubDirectory

打包输出资源目录，一般为assets，不用更改

### theme

引用的样式主题包目录名称，样式主题包请存放于 `src/modules/` 目录下
