# SWEET核心API

## 全局配置

`appConfig`是一个对象，包含了`sweet框架`的全局配置。可以在`appConfig.js`里去修改以下属性。

### title

* 类型：`string`

* 默认值：`无`

* 说明：设置初始化浏览器页面标题

### baseURL

* 类型：`string`

* 默认值：`无`

* 说明：设置ajax请求接口的前缀`path`

### homeUrl

* 类型：`string`

* 默认值：`无`

* 说明：设置系统默认的首页地址

### loginUrl

* 类型：`string`

* 默认值：`无`

* 说明：设置系统默认的登录页地址

### pageMenu

* 类型：`Object`

* 默认值：`无`

* 说明：附属菜单配置项

* 示例说明：

```
//路由配置了sweet.pageMenu则生效
pageMenu:{
    ajax:{
    	 //请求的url地址
        url:"/json/docsmenu.json",
        //请求方式
        type:"GET",
        //成功回调函数，需要return菜单数组
        response:function(data){
            return data.data
        },
        //请求的参数，需要return一个参数对象
        data:function(params){
            //params为sweet.pageMenu 路由参数
            return {
                activityTypeId:params[1],
                activityId:params[0]
            }
        }
    },
    skin:"Sweet_Menu_Default", //菜单主题,目前只有这一种
    field: {                   //接口返回的权限菜单的字段格式化
        levelField: "level",
        parentIdField: 'parent',
        idField: 'id',
        nameField: 'name',
        treeField: 'path',
        groupField: "group"
    }
},
```



### httpInterceptors

* 类型：`Object`

* 默认值：`无`

* 说明：`SWXHR`请求拦截器

* 示例说明：

```
...
//SWXHR 请求拦截器
httpInterceptors:{
    //统一更改SWXHR模式. "ajaxoption"为新模式 false 为老模式,谨慎使用
    // modelType:"ajaxoption",
    //可选 拦截SWXHR请求之前的ajax参数
    request:function(options,tools){
        if(localStorage.loginInfo)
        {
            var info=JSON.parse(localStorage.loginInfo);
            // console.log(info);
        }
        return options
    },
    //可选 拦截SWXHR成功请求后的
    response:function(data){
        //false 未登录. true 代表登录过
        if(data.code=="user-not-login")
        return false;
        else
        return true;
    }
},
...
```

### routes

* 类型：`Object`

* 默认值：`无`

* 说明：路由规则匹配

* 示例说明：

```
routes: {
    "/main": {
        // 框架
        on: "frame_index",
        // 首页
        "/index": "main_index",
        "/userInfo":{
            on:"userInfo_index",
            "/test":"userInfo_test_index"
        },
        "/resetPwd":"resetPwd_index",
        // 潜客跟进
        "/potentialCusSet":{
            on:"potentialCusSet_index"
        }
    },
     //企业注册
    "/register":"register_index",
    "/findPwd":"findPwd_index",
    "/login": "login_login"
}
```

> 具体的路由匹配规则说明，请移步[路由规则配置说明][3]进行查阅



## 全局API

### app.setTitle(text)

* 说明：

   + 更改页面标题

* 参数：
	
	+ `{string} text`

* 用法：

```
var demo={
	...,
	init:function(){
		app.setTitle("我的标题")
	}
}
```
直接在所需要的地方执行该方法即可。

### app.chkLogin.check()

* 说明：

   + 判断`localStorage`里的登录信息是否存在或者过期

* 参数：
	
	+ `无`

* 用法：

```
var demo={
	...,
	init:function(){
		var bool=app.chkLogin.check();
		if(!bool)
		{
			console.log("登录信息失效，未登录！")
		}
	}
}
```
## sweetHandler 公用组件处理器

`sweetHandler`是一个将公用组件**(查看附件1列表)**进行一个统一封装和处理的工具，开发者可以通过该工具进行一个对公用组件进行渲染。

### sweetHandler.init(container, el, options)

* 说明：

   + 重新渲染指定元素的`默认全局组件`

* 参数：
	
	+ `{Selector} container`
	+ `{Selector} el`
	+ `{Object} options`

* 用法：

```
var demo={
	...,
	init:function(){
		var html='<div data-plugin="switchery"></div>';
		$("#container").html(html);
		sweetHandler.init("#container");
	}
}
```

渲染`#container`里的`switchery`组件，该组件为`默认全局组件`

### sweetHandler.{pluginName}(container, el, options)

* 说明：

   + 重新渲染指定的组件元素

* 参数：
	
	+ `{Selector} container`
	+ `{Selector} el`
	+ `{Object} options`

* 用法：

```
var demo={
	...,
	init:function(){
		var html='<div data-plugin="switchery"></div>';
		$("#container").html(html);
		sweetHandler.switchery("#container");
	}
}
```

渲染`#container`里的`switchery`组件，该组件为`默认全局组件`

## 第三方工具库

### $

**或者jQuery**

> 该全局变量继承了`3.2.1`版本的jquery插件，具体使用方法可以移步[jquery官方文档][4]查阅

### layer

> 该全局变量继承了最新的第三方插件`layer`,可以移步去[layer官方文档][1]查阅。


### template

> 该全局变量继承了最新的第三方插件`arttemplate`，可以移步去[arttemplate官方文档][2]查阅。












[1]:http://www.layui.com/doc/modules/layer.html "layer官方文档"
[2]:https://aui.github.io/art-template/ "arttemplate官方文档"
[3]:http://git.evun.cn/sweet/sweet-ui/blob/demo/src/thirdsources/docs/%E5%BC%80%E5%8F%91%E7%8E%AF%E5%A2%83%E5%AE%89%E8%A3%85.md "路由规则配置说明"
[4]:http://jquery.cuishifeng.cn/on.html "jquery官方文档"

