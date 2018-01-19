# 更新日志

</timeline>



## 1.3.34

`2017-01-19`

<content>

- 优化 跳转定位点亮的标签页

</content>

</timeline>



## 1.3.33

`2017-01-10`

<content>

- 优化`sweet.pageMenu`附属菜单模块，解决el唯一性问题导致切换页面不会渲染附属菜单

</content>

</timeline>



## 1.3.32

`2017-01-10`

<content>

- 优化多标签组件，优化open方法，可设置不刷新页面打开已有的页面
- 优化多标签组件，增加隐藏关闭tab标签页按钮

</content>

</timeline>



## 1.3.31

`2017-12-28`

<content>

- 优化close方法，增加回调函数，用于关闭指定页面后的回调，return返回需要打开的页面
- 修复Firefox浏览器的iframe默认打开bug
- 优化代码

</content>

</timeline>



## 1.3.3

`2017-12-27`

<content>

- 优化拓展mutilViews 多标签组件
- 增加close方法
- 增加onClose关闭回调方法
- 优化onClose回调，增加event关闭方式对象
- 增加height配置项
- 优化布局，当组件height为100%时，可以根据外容器的高度自适应
- 增加足迹功能，关闭一个标签页会自动打开上一个浏览过的标签页，默认打开最后一个标签页
- 优化当页面被iframe承载时，pace进度条不显示，并且登录页面跳转对象为父窗口。
- 优化刷新iframe的方法，区分跨域和框架内页面。

</content>

</timeline>



## 1.3.2

`2017-12-20`

<content>

- 重新整合`master`分支，和`demo`分支同步
- 优化`sui-router`
- 优化`SWTOOL.formartFormData`，获取的表单元素值为空时还能输出正确的对象结构

</content>

</timeline>



## 1.3.1

`2017-11-29`

<content>

- 修复获取url参数{ctrl}.page.query的问题

</content>

</timeline>



## 1.3.0

`2017-10-13`

<content>

- 简化`appConfig.js`
- 剥离路由配置项
- 优化全局信息配置
- 删除mkcli gulp任务
- 优化`sweet-cli`相关部分

</content>

</timeline>



## 1.2.41

`2017-10-08`

<content>

- 修改`boostrap-table-fixed-columns`扩展组件
- `bootstrap-table`增加了固定列配置项`fixedColumns`,`fixedNumber`,`fixedDirection`

</content>

</timeline>



## 1.2.4

`2017-09-27`

<content>

- 修改控制器分发机制，采用`promise`异步处理
- 优化`sweet.core.js` 核心代码
- 增加人性化`console.log`提示

</content>

</timeline>


## 1.2.31

`2017-09-27`

<content>

- 增加`更新日志`，方便阅读以及开发
- 增加动态生成`CHANGELOG.MD`

</content>

</timeline>





## 1.2.3

`2017-09-25`

<content>

- 资源动态require 整合完毕
- webpack加入动态引入less全局变量(需要可配置)

</content>

</timeline>



## 1.2.2

`2017-09-21`

<content>

- 增加sweetFlexBox弹性盒子布局方式以及文档更新
- 完善Sweet UI 1.x自定义快速样式以及文档编更新

</content>

</timeline>



## 1.2.2
`2017-09-21`

<content>

- 增加菜单组件demo文档，明确指出对接规范。（解决level层级和菜单收展功能的相互依赖影响）
- sweetMutilViews多标签组件
	* 新增点亮滑动跳转效果
- sweetAsider侧边栏组件
	* 新增`stepBefore`属性的用法，解决异步调用导致重复渲染的bug
	* 取消动作的`setTimeout`和显示动作的`setTimeout`进行了及时清除的处理
	* 解决快速调用`open`方法和`reload`方法，导致`js`卡壳问题。
	
</content>

</timeline>




## 1.2.1

`2017-09-19`

<content>

- sweetI18n国际化组件，新增了组件全局语言环境，包括select2,bootstrapDataTable,boostrapDatePicker。
- sweetI18n国际化组件语言的全局化，`不支持多实例，多实例会导致全局语言环境的变化`
- `compile`方法去除了`targetLang`目标语言，默认为浏览器语言环境。

</content>

</timeline>

