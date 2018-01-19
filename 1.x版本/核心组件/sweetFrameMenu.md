# sweetFrameMenu 菜单组件

### 开始使用

- 首先引入该组件

	```
	var SweetFrameMenu = require("sweetFrameMenu");
	```
	
- 实例化 

	```
	new SweetFrameMenu($selectorId,options)
	```
	
	- $selectorId
		
		渲染目标容器id，带`#`号
		
	- options

		配置项
	
- example

```
new SweetFrameMenu('#frameMenu',{
    skin:(function(){
        if(layoutInfo)
        return layoutInfo.type;
        else
        return "Sweet_Menu_Default:normal"
    })(), 
    data:obj,                  //只接受菜单的数组
    field: {                   //接口返回的权限菜单的字段格式化
        levelField: "level",
        parentIdField: 'parent',
        idField: 'id',
        nameField: 'name',
        treeField: 'path',
        groupField: "group"
    },
    // 0：带top按钮；1：不带top按钮 Sweet_Menu_Default主题有效
    type:(function(){
        if(layoutInfo.type.split(":")[2])
        return 0;
        else
        return 1;
    })(),
    // 数值代表拦截第几层转化为标签(没有展开功能)
    treeLevels:99999,
    //权限部分
    auth:{
        fieldCode:"idField",    //和菜单对应的
        limit:",",          //code码分割符 默认,
        data:data.auth      //code码
    }
});
```

### 基础参数

#### skin

* 类型：`string`

* 默认值：`Sweet_Menu_Default:normal`

* 说明：设置菜单布局皮肤样式

#### data

* 类型：`Arrary`

* 默认值：无

* 说明：接收菜单数组的数据源

#### field

* 类型：`object`

* 默认值：无

* 说明：根据接收的`data`数据源来遍历格式化字段

#### type

* 类型：`boolean`

* 默认值：0

* 说明：设置菜单是否带top导航栏（取菜单数据的第一层数组结构生成导航）

#### treeLevels

* 类型：`number`

* 默认值：无

* 说明：数值代表拦截第几层转化为标签(没有展开功能)

#### auth

* 类型：`object`

- fieldCode

	* 类型:`string`
	
	* 默认值：无
	
	* 说明：和菜单节点对应的字段名（格式化之后）

- limit

	* 类型：`string`

	* 默认值：`,`

	* 说明：code码分割符

- data

	* 类型：`string`

	* 默认值：无

	* 说明：权限code码，字符串形式传入。
	
	
	
### 对接规范

**这里需要注意的是，组件接收的data菜单数据源首先是一个数组，其次其层级规范必须从level为0开始依次递增，level为0的首层可以不设置level属性**
	
	
	






