# URI API

```java
var uri = URI(arg)
```

通过 `URI(arg)` 这个全局 API 构建一个对象实例，可由参数传入一个 uri 字符串，也可以通过所属 API 配置添加每个字段

| 参数名 | 类型   | 必填 | 说明                                                                |
| ------ | ------ | ---- | ------------------------------------------------------------------- |
| arg    | String | 否   | 如 `prc:///system/apps/system_app1#pages/main/main?id=123&name=abc` |

 返回值：Object 类型，包含 uri 个字段操作 API

## uri()

获取 uri 字符串

返回值：String 类型，如 `prc:///system/apps/system_app1#pages/main/main?id=123&name=abc`

示例：

```java
var uri = URI("prc:///system/apps/system_app1#pages/main/main?id=123&name=abc")
var uri_str = uri.uri()
console.log(uri_str)  /* 打印结果：prc:///system/apps/system_app1#pages/main/main?id=123&name=abc */
```

## getScheme()

获取 scheme 字段

返回值：String 类型，如 `app`、`prc`

示例：

```java
var uri = URI("prc:///system/apps/system_app1#pages/main/main?id=123&name=abc")
var uri_scheme = uri.getScheme()
console.log(uri_scheme)  /* 打印结果：prc */
```

## getAuthority()

获取 authority 字段

返回值：String 类型，如 `/system/apps/system_app1`

示例：

```java
var uri = URI("prc:///system/apps/system_app1#pages/main/main?id=123&name=abc")
var uri_authority = uri.getAuthority()
console.log(uri_authority)  /* 打印结果：/system/apps/system_app1 */
```

## getPath()

获取 path 字段

返回值：String 类型，如 `pages/main/main`

示例：

```java
var uri = URI("prc:///system/apps/system_app1#pages/main/main?id=123&name=abc")
var uri_path = uri.getPath()
console.log(uri_path)  /* 打印结果：/system/apps/system_app1 */
```

## getQuery(name)

获取 query 字段或其中的某一个值

| 参数名 | 类型   | 必填 | 说明                                              |
| ------ | ------ | ---- | ------------------------------------------------- |
| name   | String | 否   | 参数名，如 如 `id=123&name=abc` 中的 `id`、`name` |

返回值：String 类型，如 `id=123&name=abc`、`123`、`abc`

示例：

```java
var uri = URI("prc:///system/apps/system_app1#pages/main/main?id=123&name=abc")
var uri_query = uri.getQuery()
console.log(uri_query)  /* 打印结果：id=123&name=abc */
var uri_query_id = uri.getQuery("id")
console.log(uri_query_id)  /* 打印结果：123 */
var uri_query_name = uri.getQuery("name")
console.log(uri_query_name)  /* 打印结果：abc */
```

## setScheme(arg)

设置 scheme 字段

| 参数名 | 类型   | 必填 | 说明                          |
| ------ | ------ | ---- | ----------------------------- |
| arg    | String | 是   | 如 `app`、`prc` 或者 APP 标签 |

示例：

```java
var uri = URI()
uri.setScheme("prc")
var uri_str = uri.uri()
console.log(uri_str)  /* 打印结果：prc: */
```

## setAuthority(arg)

设置 authority 字段，**有转码操作**

| 参数名 | 类型   | 必填 | 说明                          |
| ------ | ------ | ---- | ----------------------------- |
| arg    | String | 是   | 如 `/system/apps/system_app1` |

示例：

```java
var uri = URI()
uri.setScheme("prc")
uri.setAuthority("/system/apps/system_app1")
var uri_str = uri.uri()
console.log(uri_str)  /* 打印结果：prc://%2Fsystem%2Fapps%2Fsystem%5Fapp1 */
```

## setPath(arg)

设置 path 字段，**有转码操作**

| 参数名 | 类型   | 必填 | 说明                 |
| ------ | ------ | ---- | -------------------- |
| arg    | String | 是   | 如 `pages/main/main` |

示例：

```java
var uri = URI()
uri.setScheme("prc")
uri.setAuthority("/system/apps/system_app1")
uri.setPath("pages/main/main")
var uri_str = uri.uri()
console.log(uri_str)  /* 打印结果：prc://%2Fsystem%2Fapps%2Fsystem%5Fapp1#pages%2Fmain%2Fmain */
```

## setQuery(arg)

设置 query 字段

| 参数名 | 类型   | 必填 | 说明                 |
| ------ | ------ | ---- | -------------------- |
| arg    | String | 是   | 如 `id=123&name=abc` |

示例：

```java
var uri = URI()
uri.setScheme("prc")
uri.setAuthority("/system/apps/system_app1")
uri.setPath("pages/main/main")
uri.setQuery("id=123&name=abc")
var uri_str = uri.uri()
console.log(uri_str)  /* 打印结果：prc://%2Fsystem%2Fapps%2Fsystem%5Fapp1#pages%2Fmain%2Fmain?id=123&name=abc */
```

## addQuery(name, value)

设置 path 字段，往其中添加参数

| 参数名 | 类型   | 必填 | 说明                           |
| ------ | ------ | ---- | ------------------------------ |
| name   | String | 是   | 如 `id` `name`                 |
| value  | String | 是   | **有转码操作**，如 `123` `abc` |

示例：

```java
var uri = URI()
uri.setScheme("prc")
uri.setAuthority("/system/apps/system_app1")
uri.setPath("pages/main/main")
uri.addQuery("id", "123")
uri.addQuery("name", "abc")
var uri_str = uri.uri()
console.log(uri_str)  /* 打印结果：prc://%2Fsystem%2Fapps%2Fsystem%5Fapp1#pages%2Fmain%2Fmain?id=123&name=abc */
```
