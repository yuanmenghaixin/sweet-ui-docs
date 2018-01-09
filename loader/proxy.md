# 反向代理

> Sweet UI 通过配置反向代理的方式解决跨域的问题

## 本地开发服务反向代理设置

在 `config/dev.server.js` 中进行配置

### 示例

1. 后端接口地址：http://10.200.188.30:11300/api/login
2. 反向代理设置

```
const porxys = [{
    paths: ['/api'],
    option: {
        target: 'http://10.200.188.30:11300',
        changeOrigin: true
    }
}]
```
3. 使用

```
this.SWXHR.GET('/api/login')
    .then(res => {
        ……
    });
```

### 多个反向代理服务配置

```
const porxys = [
	{
	    paths: ['/api', '/api2'],
	    option: {
	    	target: 'http://10.200.188.30:11300',
	    	changeOrigin: true
	    }
	},
	{
	    paths: ['/api3', '/api4'],
	    option: {
	    	target: 'http://10.200.188.30:11304',
	    	changeOrigin: true
	    }
	}
];
```


## 部署阶段反向代理设置——Nginx

推荐使用 `Nginx` 作为 web server

Nginx安装方法可自行网上搜索

### Nginx配置

修改 `nginx.conf`

**Nginx配置示例**

```
# 添加server
server {
    # 端口号
    listen    9007;
    server_name  localhost;

    # 根目录路径
    location / {
        root   html/app-cloud/dev;
        index  index.html index.htm;
    }

    # 反向代理设置
    location ~ ^/(anon|doc|service|tenant|system) {
        proxy_pass http://10.86.130.32:19300;
    }
}
```