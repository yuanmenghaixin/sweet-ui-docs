# 生产部署

## 打包

通过前端打包方式发布生产。开始先在`config/index.js`配置文件配置相关的打包环境参数，再通过`package.json`的打包脚本命令，如：`npm run build`、`npm run build-dev`、`npm run build-pre`、`npm run locale`等，对应`config/index.js`配置文件里的`production`、`production-dev`等进行打包编译。

## 部署

将打包完毕后的`dist`文件夹下的所有代码部署到远端服务器，支持`nginx/apache/iis`等所有的`http`服务，配置好远程`proxy`代理即可完成发布。

