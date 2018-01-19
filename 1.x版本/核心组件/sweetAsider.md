# SweetAsider API

> 侧边栏SweetAsider是sweet框架团队借鉴layer自主研发的一个针对后台复杂交互的管理系统的jquery组件。通过侧边滑出以及配置自定义选项来快捷进行操作。

> 当前版本： v 1.1.0 (2017-09-21)

### 基础参数

#### width

* 类型：`string`

* 默认值：`40%`

* 说明：设置`asider`容器的宽度，可支持`px`、`%`单位。

#### maxWidth

* 类型：`string`

* 默认值：`400px`

* 说明：设置`asider`容器的最大宽度，可支持`px`单位。

#### zIndex

* 类型：`number`

* 默认值：`1100`

* 说明：设置`asider`容器的层级。

#### title

* 类型：`string`

* 默认值：`我是标题`

* 说明：标题设置

#### content

* 类型：`string`

* 默认值：`欢迎使用SweetAsider组件`

* 说明：页面内容html

#### events

* 类型：`Json`

* 说明：可支持事件集合json，对于`asider`容器内的事件委托。

* 示例：

```
events:{
    'click #btn':function(){
        alert(1);
    },
    ...
}
```


#### btns

* 类型：`Array`

* 默认值：`['按钮1','按钮2','关闭']`

* 说明：设置`asider`滑出层底部按钮组个数以及文本显示

#### btnsClass

* 类型：`Array`

* 默认值：``

* 说明：设置`asider`滑出层底部按钮的按钮样式class

#### btnFn

* 类型：`Array`

* 默认值：

```
[function(){
  SWTOOL.layer.success("我是按钮1");
},function(){
  SWTOOL.layer.success("我是按钮2");
}]
```

* 说明：设置`asider`滑出层底部按钮的点击事件，以数组下标为标识

#### exclude

* 类型：`Array`

* 默认值：

```
[{selector},{selector}]
```

* 说明：设置`exclude`可以置点击到哪些元素不关闭slider。


#### onInit

* 类型：`Function`

* 默认值：

```
onInit: function() {
  return false;
}
```

* 说明：初始化`asider`时执行的回调函数。

#### onOpen

* 类型：`Function`

* 参数：`asider`

* 默认值：

```
onOpen: function(asider) {
  return false;
}
```

* 说明：初始化`asider`完成后执行的回调函数。其中参数`asider`为实例化对象`object`。

#### onClose

* 类型：`Function`

* 参数：`asider`

* 默认值：

```
onClose: function(asider) {
  return false;
}
```

* 说明：关闭`asider`完成后（动画执行完毕）执行的回调函数。其中参数`asider`为实例化对象`object`。


### 内置方法

> `SweetAsider`为组件对象，`asider`为open方法返回的实例化对象

#### SweetAsider.open(options)

* 说明：调用`SweetAsider`的方法，参数为上述的配置项。返回一个对象实例`asider`。

#### asider.reload(options)

* 说明：重载asider侧边栏，根据指定的`options`进行重新渲染。

#### asider.close()

* 说明：关闭asider侧边栏。会触发回调函数`onClose`

#### asider.loadContent(html)

* 说明：改变content内容，参数为`string`格式html片段。

#### asider.getStatus()

* 说明：获取aisder是否打开的状态，{boolean}返回值。

#### asider.stepBefore

* 说明：这个属性是asider容器的一个状态，如果异步调用渲染弹出的，则需要设置下这个属性为`ajax`后方可拦截异步调用。
* 例如：

```
if(asider)asider.stepBefore = "ajax";
SWXHR.GET("/json/auth.json").done(function(data){
 if(data)
 {
     data.auth = data.auth.split(",");
     var html=template("diy1-tpl",data)
     var options={
         title:"选择分组",
         content:html,
         btns:['新增分组','批量删除','确定','取消'],
         btnsClass:['btn-success','btn-primary','btn-primary'],
         btnFn:[null,function(){
             editModel(asider);
         }]
     }

     if(!asider||!asider.getStatus())
     asider=sweetAsider.open(options);
     else if(asider.getStatus())
     asider.reload(options);
 }
})
```




