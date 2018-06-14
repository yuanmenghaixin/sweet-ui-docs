# SWXHR 2.x全局AJAX使用和配置

> 基于成熟的xhr组件[Axios][1],二次封装成适配Vue的sweet 2.x版本xhr全局组件。
> 当前版本： v 2.1.16 (2018-06-14)

## 在Vue中注册

```JavaScript
const SWXHR_OPTIONS = {
    config: {
        // 配置全局接口前缀
        baseURL: '',
        // 配置全局接口延迟
        timeout: 0,
        // 配置全局接口请求头 ...其他更多配置项可以参考axios文档
        headers: {},
        // 配置错误码拦截，小于该数值的错误都会被拦截（不经过response处理）
        maxStatus: 505
    },
    intercept: {
        // 配置全局SWXHR拦截器 -- > 请求前
        request(p) {
            // console.log('请求前');
            return p;
        },
        // 配置全局SWXHR拦截器 -- > 请求后
        response(res) {
			// res 响应结构
			// res = {
				//   // 由服务器提供的响应
				//   data: {},
				//   // 来自服务器响应的 HTTP 状态码
				//   status: 200,
				//   // 来自服务器响应的 HTTP 状态信息
				//   statusText: 'OK',
				//   // 服务器响应的头
				//   headers: {},
				//   // 是为请求提供的配置信息
				//   config: {}
				// }
            var result = res.data;
            if (result.code !== 'success') {
                // Vue.prototype.$message(result.message);
            }
            return result;
        }
    }
};
// 在`Vue.prototype`和`Vuex`中注册全局ajax方法 -- > SWXHR
new SWXHR(SWXHR_OPTIONS, sweetStore);
```

## 在Vue组件实例中调用

```
<style></style>
<template></template>
<script>
export default {
	name: 'useXhrDemo',
	mounted() {
		this.SWXHR.GET('/json/demo').then(res => {
			// do something
			// ....
		});
	}
}
</script>
```

### GET

```javascript
// 在组件内或者vuex 内使用
this.SWXHR.GET(url,{
	// 这里配置选项
	headers: {'X-Requested-With': 'XMLHttpRequest'},
    // 将要请求的参数包在 params 对象中
    params: {
        userName: 'name1',
        id: '1'
    }
})
.then(res => {
    // res是收到的数据
    console.log(res);
})
```

### POST

```javascript
// 在组件内或者vuex 内使用
this.SWXHR.POST(url,{
    // 和GET不一样，这里参数 不需要 包在 params 对象里面
    userName: 'name1',
    id: '1'
}, {
	// 这里配置选项
  	headers: {'X-Requested-With': 'XMLHttpRequest'},
})
.then(res => {
    // res是收到的数据
    console.log(res);
})
```

### PUT

```javascript
// 在组件内或者vuex 内使用
this.SWXHR.PUT(url,{
    userName: 'name1',
    id: '1'
}, {
	// 这里配置选项
  	headers: {'X-Requested-With': 'XMLHttpRequest'},
})
.then(res => {
    // res是收到的数据
    console.log(res);
})
```


### DELETE

```javascript
// 在组件内或者vuex 内使用
this.SWXHR.DELETE(url, {
	// 这里配置选项
  	headers: {'X-Requested-With': 'XMLHttpRequest'},
	params: {
    id: '11'
  }
})
.then(res => {
    // res是收到的数据
    console.log(res);
})
```


## 使用 application/x-www-form-urlencoded 格式化

默认情况下，axios 串联 js 对象为 JSON 格式。为了发送 application/x-wwww-form-urlencoded 格式数据，你可以使用一下的设置。

使用 `qs` 库

```javascript
var qs = require('qs');
this.SWXHR.POST(url, qs.stringify({'bar':123}))
.then(res => {
    // res是收到的数据
    console.log(res);
})
```
 
[1]:https://www.kancloud.cn/yunye/axios/234845 "Axios"

