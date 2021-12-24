# systemStorage 接口

系统存储模块，与 localStorage 模块用法相同，不同的是使用 systemStorage  模块存储的信息在任何 APP 中都可访问（无需require, 可直接通过模块名调用其接口）

### systemStorage.setItem(String key, String value);

存储数据

| 参数名       | 类型                             | 必填           | 说明                                             |
| ------------ | -------------------------------- | -------------- | ------------------------------------------------ |
| key          | String                           | 是             | 数据存储相关联的key, 此 key 也是用于访问的关键字 |
| value        | String/Object/Array等JS 原生对象 | 是             | 要存储的数据                                     |
| **返回值**   | **类型**                         | **描述**       |                                                  |
| true / false | Boolean                          | 存储成功或失败 |                                                  |

使用示例：

```js

systemStorage.setItem("sys_test", "hello");
systemStorage.setItem("sys_test", 123);
systemStorage.setItem("sys_test", 12.333);
systemStorage.setItem("sys_test", true);
systemStorage.setItem("sys_test", {key: "test", value: "ttt"});
```



### systemStorage.getItem(String key);

获取存储的数据

| 参数名     | 类型                             | 必填                                           | 说明                     |
| ---------- | -------------------------------- | ---------------------------------------------- | ------------------------ |
| key        | String                           | 是                                             | 要获取存储数据相关的 key |
| **返回值** | **类型**                         | **描述**                                       |                          |
| data       | String/Object/Array等JS 原生对象 | 保存的数据（如果没有相关的存储数据则返回null） |                          |

使用示例：

```js

systemStorage.getItem("sys_test");
```



### stemStorage.removeItem(String key);

删除储存的数据

| 参数名     | 类型     | 必填     | 说明                 |
| ---------- | -------- | -------- | -------------------- |
| key        | String   | 是       | 要删除数据相关的 key |
| **返回值** | **类型** | **描述** |                      |
| true       | Boolean  | 删除成功 |                      |

使用示例：

```js

systemStorage.removeItem("sys_test");
```



### systemStorage.onChange(String key， Function callback);

设置数据改变监听回调。监听成功返回 `true`，失败返回 `false`

| 参数         | 类型     | 必填                           | 说明                                 |
| ------------ | -------- | ------------------------------ | ------------------------------------ |
| key          | String   | 是                             | 要监听数据相关的 key - 关键字        |
| callback     | 函数     | 是                             | 要绑定的回调函数（回调函数介绍如下） |
| **返回**     | **类型** | **描述**                       |                                      |
| true / false | Boolean  | 添加回调返回值，返回成功或失败 |                                      |

#### Function.callback(key, value)

回调函数至多有两个参数。参数含义如下：

| 参数  | 类型                             | 必填 | 说明               |
| ----- | -------------------------------- | ---- | ------------------ |
| key   | string                           | 否   | 数据发生改变的 key |
| value | String/Object/Array等JS 原生对象 | 否   | 改变之后的值       |

使用示例：

```js

this.test_cb = function(key, new_data){
    console.log("new data = " + new_data);
};
systemStorage.onChange("sys_test", this.test_cb);
```



### systemStorage.offChange(String key， Function callback);

取消监听

| 参数         | 类型     | 必填                           | 说明                     |
| ------------ | -------- | ------------------------------ | ------------------------ |
| key          | String   | 是                             | 要取消监听数据相关的 key |
| callback     | 函数     | 是                             | 绑定的回调函数           |
| **返回**     | **类型** | **描述**                       |                          |
| true / false | Boolean  | 取消回调返回值，返回成功或失败 |                          |

使用示例：

```js

systemStorage.offChange("sys_test", this.test_cb);
```



