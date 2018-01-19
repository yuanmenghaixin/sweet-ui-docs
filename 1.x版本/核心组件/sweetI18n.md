# sweetI18n文档

## 使用方法
在js代码头部使用`require`方法将`sweetI18n`引入，并且赋值给自定义变量。

```
var sweetI18n=require("sweetI18n");
```
## 初始化
```
new sweetI18n(options,callback);
```
两个参数，`options`为配置项，`callback`则为初始化完毕的回调函数
```
callback(err,t);
```
该回调函数有两个参数，第一个为错误信息，第二个为i8next组件的t方法。

## 配置项
```
{
  //开启渲染模式 默认为false，若要渲染必须打开，编译模式除外
  enable:true,
  //渲染的目标容器选择器 默认为document           
  renderDom:i18nCtrl.el, 
  //强制使用语言，如果不设置则读取浏览器环境语言全局
  lng:"zh-CN"            
}
```

## 编译
编译则是一种扩展方法，为了方便动态ajax读取数据后，通过编译html片段，从而渲染界面的一种目的。

```
//click 事件
'click #button':function(){
	instance.compile(html,callback);
}
```
### compile方法的参数
#### html
为未编译的html片段，类型为`string`
#### callback(response)
为编译成功后的回调函数，其中参数为response编译的结果。

**动态编译方法是根据全局的语言环境来选择语言，请谨慎使用**





