# SWXHR 2.x全局AJAX使用和配置

> 基于成熟的xhr组件[Axios][1],二次封装成适配Vue的sweet 2.x版本xhr全局组件。
> 当前版本： v 2.0.1 (2017-12-8)

## 在Vue中注册

```
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

## 执行 `GET` 请求

```
// 为给定 ID 的 user 创建请求
SWXHR.GET('/user?ID=12345')
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  });

// 可选地，上面的请求可以这样做
SWXHR.GET('/user', {
    params: {
      ID: 12345
    }
  })
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  });
```

## 执行 `POST` 请求

```
SWXHR.POST('/user', {
    firstName: 'Fred',
    lastName: 'Flintstone'
  })
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  });
```
## 执行 `DELETE` 请求

```
SWXHR.DELETE('/user', {
    id: 'id'
  })
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  });
```

## 执行 `PUT` 请求

```
SWXHR.PUT('/user', {
    id: 'id'
  })
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  });
```
 
[1]:https://www.kancloud.cn/yunye/axios/234845 "Axios"

