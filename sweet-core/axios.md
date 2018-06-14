# AXIOS

> Sweet UI 2.0 版本开始 AJAX 全部采用 axios
> `@sweetui/sweet@2.1.16`

## 特色

* 浏览器端发起 XMLHttpRequests 请求
* node 端发起 http 请求
* 支持 Promise API
* 拦截请求和返回
* 转化请求和返回（数据）
* 取消请求
* 自动转化 json 数据
* 客户端支持抵御[XSRF（跨站请求伪造）](https://baike.baidu.com/item/CSRF/2735433?fr=aladdin)

## 了解 Axios

[中文文档](https://segmentfault.com/a/1190000008470355#articleHeader5)
[官方文档](https://github.com/axios/axios)

## Sweet UI 中的使用

### 全局配置

```javascript
var SWXHR_OPTIONS = {
    config: {
        // 配置全局接口前缀
        baseURL: '',
        // 配置全局接口延迟
        timeout: 0,
        // 配置全局接口请求头 ...其他更多配置项可以参考axios文档
        headers: {}
    },
    intercept: {
        // 配置全局SWXHR拦截器 -- > 请求前
        request(p) {
            // console.log('请求前');
            return p;
        },
        // 配置全局SWXHR拦截器 -- > 请求后
        response(res) {
            var result = res.data;

            if (res.status === 200 && result.code !== 'success') {
                Vue.prototype.$message(result.message);
            }

            return result;
        }
    }
};
new SWXHR(SWXHR_OPTIONS);
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


