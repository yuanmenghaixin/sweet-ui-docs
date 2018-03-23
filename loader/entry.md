# 入口文件

入口文件是在`/src`的`main.js`以及`index.html`文件。

## main.js

```js
import Vue from 'vue';
import { sweetStore, sweetRouter, SWTOOL } from '@sweetui/sweet';
import App from '@/modules/demo/app';
import ElementUI from 'element-ui';
import Ajax from '@/modules/demo_plugin/ajax';
import '@/modules/demo_theme/index.scss';

Vue.use(ElementUI);
Vue.use(SWTOOL);

// ajax启动
Ajax();

sweetStore.dispatch('initLang').then(i18n => {
    new Vue({
        el: '#app',
        router: sweetRouter,
        store: sweetStore,
        i18n,
        template: '<App/>',
        components: { App }
    });
});

// webpack热加载
if (module.hot) { module.hot.accept(); };
```

在此入口文件中可以配置全局的ajax以及引入全局的模块组件，比如：`vue`、`@sweetui/sweet`、`element-ui`等，并且初始化国际化。

## index.html

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Sweet UI 2.0</title>
  </head>
  <body>
    <div id="app"></div>
    <!-- built files will be auto injected -->
  </body>
</html>

```

`index.html`文件为入口html文件，因为sweet-ui为单应用框架，则该html承载着整个应用的所有dom结构以及样式和javascript。可以更改网页的标题以及引入一些cdn资源等。


