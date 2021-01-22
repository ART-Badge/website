# App

## 概述

本文档主要介绍小程序的管理和路由功能 API 接口。

## API

JS API 都归属于全局对象 `app`。

### launch

```java
app.launch(uri)
```

启动 APP

当 APP 在前台时不做任何操作；当 APP 在后台时切换到前台；当 APP 前后台都不在时启动 APP

| 参数名 | 类型   | 必填 | 说明                                                      |
| ------ | ------ | ---- | --------------------------------------------------------- |
| uri    | String | 否   | [URI 介绍文档](app-dev/references/apis/js-fwk/app/uri.md) |

返回值：启动失败返回 `false`，其余返回 `true`

**注意：严禁在 APP 的生命周期回调函数中使用**

### exit

```java
app.exit()
```

关闭退出当前前台 APP 并返回 launcher APP

**注意：严禁在 APP 的生命周期回调函数中使用**

### getInfo

```java
app.getInfo(id)
```

获取 APP 的 `app.json` 数据

| 参数名 | 类型   | 必填 | 说明                                                   |
| ------ | ------ | ---- | ------------------------------------------------------ |
| id     | String | 否   | APP 唯一 ID，不填时获取当前前台 APP 的 `app.json` 数据 |

返回值：object 类型，`app.json` 对象

### listAppInstalled

```java
app.listAppInstalled(argv)
```

获取当前已经安装的应用，包括系统应用和用户应用。系统应用安装路径 `/system/apps`，用户应用安装路径 `/user/apps`

| 参数名 | 类型   | 必填 | 说明                                                                                          |
| ------ | ------ | ---- | --------------------------------------------------------------------------------------------- |
| argv   | String | 否   | 默认不填获取当前已经安装的应用；有效参数 `system` 或 `user`，分别对应获取系统应用或者用户应用 |

返回值：object 类型，如：

```java
{
    com.example.app1: {
        id: "com.example.app1",
        version: "v4.0.0",
        url: "/system/apps/com.example.app1"
    },
    com.example.app2: {
        id: "com.example.app2",
        version: "v4.0.0",
        url: "/system/apps/com.example.app2"
    }
}
```

其中每条属性的对应一个 APP，属性名即为 APP ID 名（如 `com.example.app1`、`com.example.app2`）

每条属性数据类型为 object 存放有 APP 的 app.json 信息和 url 值，如：

```java
{
    id: "com.example.app1",
    version: "v4.0.0",
    url: "/system/apps/com.example.app1"
}
```

### listAppRunning

```java
app.listAppRunning()
```

获取当前已经启动的应用，包含所有前后台应用，不包含 `launcher APP`

返回值：Array 类型，如 `[ "com.example.app1", "com.example.app2" ]`，其中每一项数据类型为 String 对应已安装应用列表 object 对象中的属性名，即 APP ID 名

### getInstance

```java
app.getInstance()
```

获取当前前台 APP 的对象实例

返回值：object 类型，APP 对象实例

### appInstall

```java
app.appInstall(Object object)
```

用户应用安装，安装目录 `/user/apps`，异步安装

**注意：仅在 launcher APP 调用有效，否则接口调用会抛异常**

参数 Object object

| 属性     | 类型     | 描述                                             |
| -------- | -------- | ------------------------------------------------ |
| path     | String   | 安装包全路径名，如 `/pkgs/app.prc`               |
| success  | Function | 接口调用成功的回调函数                           |
| fail     | Function | 接口调用失败的回调函数                           |
| complete | Function | 接口调用结束的回调函数（调用成功、失败都会执行） |

object.success 回调函数

参数 Object res

| 属性 | 类型   | 描述              |
| ---- | ------ | ----------------- |
| id   | String | 安装应用的唯一 ID |

object.fail 回调函数

参数 Object res

| 属性   | 类型   | 描述     |
| ------ | ------ | -------- |
| errMsg | String | 错误信息 |

res.errMsg 的合法值

| 值                          | 说明             |
| --------------------------- | ---------------- |
| fail no such pkgs, ${path}  | 应用安装包不存在 |
| fail invalid pkgs,  ${path} | 无效安装包       |

异常信息值

| 值                     | 说明                 |
| ---------------------- | -------------------- |
| args invalid           | 接口调用失败参数无效 |
| fail permission denied | 接口调用失败无权限   |

### appUninstall

```java
app.appUninstall(id)
```

卸载用户应用，同步卸载

**注意：仅在 launcher APP 调用有效，否则接口调用会抛异常**

| 参数名 | 类型   | 必填 | 说明        |
| ------ | ------ | ---- | ----------- |
| id     | String | 是   | 应用唯一 ID |

返回值：

| 值    | 说明                                      |
| ----- | ----------------------------------------- |
| true  | 卸载成功（卸载不存在的 APP 也会返回成功） |
| fasle | 卸载失败                                  |

异常信息值

| 值                     | 说明                 |
| ---------------------- | -------------------- |
| args invalid           | 接口调用失败参数无效 |
| fail permission denied | 接口调用失败无权限   |

### parse

```java
app.parse(prc)
```

解析应用安装包，解析成功返回一个 `object` 包含应用配置信息和应用图标临时缓存目录

| 参数名 | 类型   | 必填 | 说明             |
| ------ | ------ | ---- | ---------------- |
| prc    | String | 是   | 应用安装包路径名 |

解析失败返回 String：

| 值                | 说明         |
| ----------------- | ------------ |
| fail invalid pkgs | 无效安装包   |
| fail no such pkgs | 安装包不存在 |

异常信息值

| 值           | 说明                 |
| ------------ | -------------------- |
| args invalid | 接口调用失败参数无效 |

解析成功返回值示例：

```log
{
    id: "com.realthread.sport",
    name: "运动",
    author: "realthread",
    vendor: "realthread",
    version: "v1.0.0",
    tag: ["app"],
    apiLevel: {
        min: 1,
        target: 1
    },
    icon: "app.png",
    url: "/tmp/com.realthread.sport"  //图标临时缓存目录，图片路径名 "/tmp/com.realthread.sport/app.png"
}
```

## 生命周期函数

### onLaunch(object)

APP 启动时回调，入参由用户通过 uri `query` 字段传入，可为空对象

入参示例如下：

- query：`id=123&name=abc`
- object：`{ id: "123", name: "abc" }`

### onShow(object)

APP 唤醒时回调，入参由用户通过 uri `query` 字段传入，可为空对象

入参示例如下：

- query：`id=123&name=abc`
- object：`{ id: "123", name: "abc" }`

### onHide

APP 进入后台时回调，无入参，用户切换到其它 APP 时触发

### onExit

APP 关闭退出时触发，无入参，用户关闭 APP 时触发

### onAppChoice(object)

launcher APP 特有函数，通过 APP 标签启动 APP 且该标签下有多个 APP 时触发

入参示例如下：

```java
{
    apps: "system_app1&user_app1",
    path: "pages/main/mian",
    query: "id=123&name=abc"
}
```

| 属性名 | 类型   | 说明                                                                                                              |
| ------ | ------ | ----------------------------------------------------------------------------------------------------------------- |
| apps   | String | 对应已安装应用列表 object 对象中的属性名，多个 APP 属性名用 `&` 字符隔开，如上示例对应了 system_app1 和 user_app1 |
| path   | String | 对应启动 APP 时 uri 的 path 字段，该属性可为空字符串                                                              |
| query  | String | 对应启动 APP 时 uri 的 query 字段，该属性可为空字符串                                                             |

## 参考资料

有关于 URI 的详细介绍，请参阅：[URI 介绍文档](docs/JS_应用框架_API/app/uri.md)
