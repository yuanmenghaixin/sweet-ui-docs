# 变量配置

## 引用

如果要在某个模块下使用`element-ui`的样式变量或者要使用`sweet-style`的样式变量的话，那么要在该作用域中引入配置文件。

```js
@import '~@sweetui/sweet-style/config.scss';

color: $--color-primary;
```

## 修改/新建变量

如果有要制定符合自己项目业务的特定主题风格并且需要沿用`sweet-style`的，那么一般做法是在自己的`src/modules/theme_style`建立自己的主题风格样式文件夹，分别建立三个`.scss`文件。

### index.scss

```
@import 'config.scss';
@import '~@sweetui/sweet-style/index.scss';

@import 'common.scss';
@import 'fonts.scss';
```
### config.scss

```
// element-ui 所有初始化参数，请查看 var.scss。请基于var.scss内的变量在本文件进行修改
@import '~@sweetui/sweet-style/config.scss';
@import './vars/index.scss';
```

### vars/index.scss

```
// 这里存放自己定义的变量名或者修改原来的变量等。
@import 'common.scss';
@import 'pagination.scss';
@import 'table.scss';
@import 'tootip.scss';
@import 'tree.scss';
@import 'dialog.scss';

/* 我的变量
*/
$uc-text--color: #515152 !default;
$--uc-button-mini--padding: 8px 16px 7px 16px !default;
$--uc-button--padding: 9px 24px 9px 24px !default;

/* Font
*/
$--font-weight-primary: normal;

/* Colors
*/
$--color-text-regular: #4f4f4f;
$--color-primary: #296AB4;

```


