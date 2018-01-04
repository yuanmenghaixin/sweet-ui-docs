# 开发规范

## 命名规范

1. 目录和文件

- 目录使用小写+下划线；
- 文件采用驼峰发驼峰法（首字母小写），例如 userList.vue；


2. 函数和类、属性命名

- class类和构造函数的命名采用驼峰法（首字母大写），例如 User、UserType；
- 方法的命名使用驼峰法（首字母小写），例如 getUserName；
- 属性的命名使用驼峰法（首字母小写），例如 tableName、instance；

3. 常量和配置

- 常量和环境变量定义，以大写字母和下划线命名，例如 APP_PATH；

## 代码规范

> 为了保证代码的一致性和避免错误，同时提升团队协作时，代码的可读性和可维护性。框架引入了 ESLint 作为代码风格检查工具。
> 当有报错或者警告时，大家可以通过 http://eslint.cn/ 输入相应的错误代码进行查询

### 编辑器安装ESLint工具

在开发时，为了更方便的获取提醒，甚至自动修正。推荐大家在各自使用的编辑器上安装`ESLint`的相关插件

**1. 全局安装 ESLint**

无论使用何种编辑器，推荐都进行全局安装 ESLint

```
// windows
npm i eslint -g

// mac/linux
sudo npm i eslint -g
```

**2. VSCode**

a. 搜索 `ESLint` 扩展，并安装

b. 左下角齿轮点开，进入`设置`界面

c. 在右侧，添加以下配置

```
"eslint.validate": [
    "javascript",
    "javascriptreact",
    {
        "language": "html",
        "autoFix": true
    },
    {
        "language": "vue",
        "autoFix": true
    }
]
```

**3. Sublime**

安装 `ESLint`，`SublimeLinter` 和 `SublimeLinter-contrib-eslint` 这三个插件即可

**其他编辑器正在整理中……**
