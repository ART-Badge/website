# EMQ

## 概述

主要介绍消息队列 EMQ API 功能

获取数据池模块: `var emq = require("emq")`

返回值: Object 类型，内含消息队列操作接口

### API 汇总

#### 模块 API

| API | 说明 |
| --- | ---- |
| createEP | 创建消息队列接收端点 |
| send | 发送消息 |

#### 消息队列 API

| API | 说明 |
| --- | ---- |
| onMessage | 监听消息 |
| offMessage | 解除监听消息 |
| close | 关闭接收端点 |

## API 介绍

### EMQ.createEP()

创建一个消息接收端点，返回消息队列操作 API。`var QUEUE = require("emq")`

| 参数 | 类型 | 说明 |
| ---- | ---- | ---- |
| **返回** | **描述** |
| obj | 消息队列操作接口 |

### EMQ.send(String hub.ch, any data)

发送数据至 HUB 的一个通道上。

| 参数 | 类型 | 说明 |
| ---- | ---- | ---- |
| hub.ch | 字符串 | HUB 名.通道名(`system.1`) |
| data | String/Object/Array 等 | JS 原生对象 |
| **返回** | **描述** |
| true | 成功返回 |

### QUEUE.onMessage(String hub.ch, Function callback)

监听一个 HUB 上面的一个通道。

| 参数 | 类型 | 说明 |
| ---- | ---- | ---- |
| hub.ch | 字符串 | HUB 名.通道名(`system.1`) |
| callback | 函数 | 回调函数 |
| **返回** | **描述** |
| true | 成功返回 |

> 目前同一个 HUB 的同一个通道，只能监听一次。

#### ONMESSAGE.callback(any data)

监听回调函数。收到消息会调用此回调函数，数据放在 data 中。

### QUEUE.offMessage(String hub.ch, Function callback)

取消监听

| 参数 | 类型 | 说明 |
| ---- | ---- | ---- |
| hub.ch | 字符串 | HUB 名.通道名(`system.1`) |
| callback | 函数 | 绑定的回调函数 |
| **返回** | **描述** |
| true | 成功返回 |

### QUEUE.close()

关闭接收端点

| 参数 | 类型 | 说明 |
| ---- | ---- | ---- |
| 无   | 无   | 无   |
| **返回** | **描述** |
| true | 成功返回 |
