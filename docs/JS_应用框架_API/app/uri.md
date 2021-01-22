# URI

## URI 结构

```uri
[scheme:][//authority][#path][?query]
```

分为四段：scheme 字段后必须带 `:`；authority 字段前必须带 `//`；path 字段前必须带 `#`；query 字段前必须带 `?`

uri 字符串示例：

```uri
app://com.example.system_map#pages/main/main?id=123&name=abc
```

示例拆解如下：

- `scheme`：app
- `authority`：com.example.system_map
- `path`：pages/main/main
- `query`：id=123&name=abc

该 URI 对应的 app.json 部分属性示例:

```json
{
  "id": "com.example.system_map", // 小程序 唯一 ID
  "name": "地图",                 // 小程序 名称
  "version": "v4.0.0",            // 小程序 版本号
  "tag":[ "map", "system" ]       // 小程序 标签
}
```

## URI 字段介绍

### scheme

该字段必填，可选择的值有如下三种：

1. 小程序标签，对应 `app.json` 中 `tag` 的值 ，用于启动某一类别小程序 ，如：`map://pages/main/main?id=123&name=abc`
2. `app` ：用于启动具体 app_id 的小程序，如：`app://com.example.system_map#pages/main/main?id=123&name=abc`
3. `prc` ：多用于开发调试过程中，可以通过指定的 prc 文件路径来启动小程序，如： `prc:///system/apps/system_map#pages/main/main?id=123&name=abc`

### authority

该字段根据 `scheme` 的值的不同来决定是否选填，主要用于指出要切换到的目标小程序

1. `scheme` 字段为小程序标签时 `authority` 字段不填
2. `scheme` 字段为 `app` 时 `authority` 字段必填，对应小程序唯一 ID，即 `app.json` 中 `id` 的值，如 `system_map`
3. `scheme` 字段为 `prc` 时 `authority` 字段必填，对应为小程序安装路径 `URL`，如 `/system/apps/system_map`

**注意：`scheme` 为小程序标签时，对应标签下只有单个小程序时则直接启动该小程序，如有多个则会回调 launcher 小程序的 onAppChoice 函数**

### path

该字段非必填，可用于指出启动目标小程序后要跳转到的 Page 页面，如 `pages/main/main` 同 Page 导航的 url 参数

### query

该字段非必填，主要用于带值传参，如 `id=123&name=abc`

这里有两个参数：`id` 其值是 "123"；`name` 其值是 "abc"

`query` 参数可以有多个用 `&` 连接，参数名和值用 `=` 分隔

**注意：参数根据小程序的启动逻辑不同，可传递到新小程序的 onLaunch、onShow 以及新 Page 的 onLoad 中一个或多个，入参是解析过的 Object 对象非 query 字段原始字符串，以 `id=123&name=abc` 为例回调入参为 `{ id: "123", name: "abc" }`**

## 参考资料

有关于 URI API 的详细介绍，请参阅：[URI API 介绍文档](app-dev/references/apis/js-fwk/app/uri-api.md)
