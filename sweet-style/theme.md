# 自定义主题

如若有自定义主题风格的需要，那么要自己建立一个主题文件夹来存放样式文件，以及完成变量配置相关工作，引入配置文件等。并且需要在`config/index.js`里配置好主题包存放的位置。

```js
// 通用配置
common: {
   babelInclude: [],
   assetsSubDirectory: 'assets',
   theme: 'app-uc-style'
},
```

这里的主题包名叫`app-uc-style`，那么要在`src/modules`下有相应的`app-uc-style`的文件夹。

## 目录结构

```js
├── vars                // 存放变量的文件夹
├── common.scss         // 通用样式文件
├── config.scss         // 引入以及配置相关文件 
├── ...                 // 各种控件或模块的样式相关文件
└── index.scss          // 入口文件     
```



