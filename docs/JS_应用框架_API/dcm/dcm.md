# DCM

## 概述

主要介绍数据池 DCM API 功能

获取数据池模块: `var dcm = require("dcm")`

返回值: Object 类型，内含数据池操作接口

### API 汇总

#### 模块 API

| API | 说明 |
| --- | ---- |
| Open | 打开数据池 |
| Create | 创建数据池 |

#### 数据池 API

| API | 说明 |
| --- | ---- |
| setItem | 写入数据 |
| getItem | 获取数据 |
| removeItem | 删除数据 |
| onChange | 绑定数据改变回调 |
| offChange | 解绑数据改变回调 |
| onDelete | 绑定数据删除回调 |
| offDelete | 解绑数据删除回调 |
| close | 关闭数据池 |

## API 介绍

### DCM.Open(String name)

打开数据池，数据池存在时返回数据池操作 API，数据池不存时返回 `UNDEFINED`

| 参数 | 类型 | 说明 |
| ---- | ---- | ---- |
| name | 字符串 | 数据库名字 |
| **返回** | **描述** |
| obj | 数据池操作接口 |

> 打开的数据池，需要在界面关闭或接收对象生命周期结束之前，进行关闭

### DCM.Create(String name)

创建数据池，数据池名字全局唯一。创建成功返回 `true`，创建失败返回 `false`

| 参数 | 类型 | 说明 |
| ---- | ---- | ---- |
| name | 字符串 | 数据库名字 |
| **返回** | **描述** |
| true | 成功返回 |

> 不建议 JS 层直接创建数据池然后使用。

### POOL.setItem(String key, any data)

存放数据到数据池中。只支持原生类型且能够序列化的对象。存放成功返回 `true`，失败返回 `false`

| 参数 | 类型 | 说明 |
| ---- | ---- | ---- |
| key | 字符串 | 关键字 |
| data | String/Object/Array 等 | JS 原生对象 |
| **返回** | **描述** |
| true | 成功返回 |

### POOL.getItem(String key)

从数据池中获取数据。获取成功返回 JS 原生对象，获取失败返回 `UNDEFINED`

| 参数 | 类型 | 说明 |
| ---- | ---- | ---- |
| key | 字符串 | 关键字 |
| **返回** | **描述** |
| any | JS 原生对象 |

### POOL.removeItem(String key)

从数据池中删除数据项。删除成功返回 `true`，失败返回 `false`

| 参数 | 类型 | 说明 |
| ---- | ---- | ---- |
| key | 字符串 | 关键字 |
| **返回** | **描述** |
| true | 成功返回 |

> 数据池中不存在该数据项时，将返回失败

### POOL.onChange(String key, Function callback)

设置数据改变监听回调。监听成功返回 `true`，失败返回 `false`

| 参数 | 类型 | 说明 |
| ---- | ---- | ---- |
| key | 字符串 | 关键字 |
| callback | 函数 | 回调函数 |
| **返回** | **描述** |
| true | 成功返回 |

#### Function.callback(key, value)

onChange 绑定的回调函数至多有两个参数。参数含义如下：

| 参数 | 类型 | 说明 |
| ---- | ---- | ---- |
| key | 字符串 | 数据发生改变的 key |
| value | any | 改变之后的值 |

### POOL.offChange(Function callback)

解绑数据改变回调。解绑成功返回 `true`，失败返回 `false`

| 参数 | 类型 | 说明 |
| ---- | ---- | ---- |
| callback | 函数 | 回调函数 |
| **返回** | **描述** |
| true | 成功返回 |

> 解绑时需要传入一个绑定的 callback，绑定时将 callback 赋值给一个变量，方便后续解绑

### POOL.onDelete(String key, Function callback)

设置数据删除监听回调。监听成功返回 `true`，失败返回 `false`

| 参数 | 类型 | 说明 |
| ---- | ---- | ---- |
| key | 字符串 | 关键字 |
| callback | 函数 | 回调函数 |
| **返回** | **描述** |
| true | 成功返回 |

#### Function.callback(key, value)

onDelete 绑定的回调函数至多有一个参数。参数含义如下：

| 参数 | 类型 | 说明 |
| ---- | ---- | ---- |
| key | 字符串 | 删掉成员的 key |

### POOL.offDelete(Function callback)

解绑数据删除监听回调。解绑成功返回 `true`，失败返回 `false`

| 参数 | 类型 | 说明 |
| ---- | ---- | ---- |
| callback | 函数 | 回调函数 |
| **返回** | **描述** |
| true | 成功返回 |

### POOL.close()

关闭数据池。返回 `UNDEFINED`
