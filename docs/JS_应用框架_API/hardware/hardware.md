## 硬件管理模块 Hardware JS  API 手册

<br>

`引用模块名`：`hardware`

```
var sensor = require('module/hardware.js');
```

|    | 模块描述   |         JS调用接口          |             备注                                                  |
| :-------: | :----------------------    |  :--------------------------------------------------------------- |  :--------------------------------------------------------------- |
| 1 | realtime | getRealTime | 获取时间戳 |
| 2 | realtime | setRealTime | 设置时间戳 |
| 3 | realtime | onRealTimeChange | 开启监听时间戳 |
| 4 | realtime | offRealTimeChange | 取消监听时间戳 |
| 5 | screen | getScreenMode | 获取屏幕模式 |
| 6 | screen | setScreenMode | 设置屏幕模式 |
|  7  |   screen  | openScreen               | 打开屏幕                             |
|  8  |   screen  | closeScreen              | 关闭屏幕                                           |
|  9  |   screen  | getScreenStatus          | 获取当前屏幕状态                                                |
|  10  |   screen  | onScreenPowerChange      | 开启监听屏幕状态                              |
|  11  |   screen  | offScreenPowerChange     | 取消监听屏幕状态                                        |
| 12 | screen | getScreenBrightness | 获取屏幕亮度 |
| 13 | screen | setScreenBrightness | 设置屏幕亮度 |
|   14   |   touch   | openTouchPanel           | 打开触摸屏                                                     |
|   15   |   touch   | closeTouchPanel          | 关闭触摸屏                                                     |
|   16   |   touch   | getTouchPanelStatus | 获取触摸屏状态                                                     |
|   17   |   touch   | onTouchPanelPowerChange  | 开启监听触摸屏状态              |
|   18   |   touch   | offTouchPanelPowerChange | 取消监听触摸屏状态                                        |
|   19   |   sys   | vibrate                  | 振动                                                        |
|   20   |   sys     | reboot                   | 硬件重启                                                          |
|   21   |   sys     | powerOff         | 硬件关机                                                          |
|   22   |   sys     | getBatteryLevel          | 获取电池电量                                                       |
|   23   |   sys     | onBatteryLevelChange | 开启监听电池电量变化                                                  |
|   24   |   sys     | offBatteryLevelChange    | 取消监听电池电量变化                                                |
|   25   |   sys     | getChargeStatus | 获取充电状态                                                   |
|   26   |   sys     | onChargeChange    | 开启监听充电状态                                   |
|   27   |   sys     | offChargeChange   | 取消监听充电状态                                   |
|   28   |   sys     | getInfo()                  | 获取系统信息                                                  |
|   29   |   key     | onKeyChange | 开启监听按键：press,up,longpress,longup                            |
|   30   |   key     | offKeyChange | 取消监听按键                                                     |


<br><br><br>




# getRealTime()

获取时间戳


<br>


## 参数

无


<br>


## 返回

| 属性      | 类型   | 默认值 | 说明   |
| :-------- | :----- | :----- | :----- |
| timestamp | number |        | 时间戳 |



<br><br><br>




# setRealTime()

设置时间戳


<br>


## 参数

时间戳，如 1601366586


<br>


## 返回

| 属性 | 类型 | 默认值 | 说明                         |
| :--- | :--- | :----- | :--------------------------- |
| ret  | bool |        | 操作成功：true； 失败：false |


<br><br><br>



# onRealTimeChange(function callback)

开启监听：realtime 时间戳变化


<br>


## 参数

| 属性     | 类型     | 返回值 | 说明                                   |
| :------- | :------- | :----- | :------------------------------------- |
| callback | function | 无     | 注册的onChange回调函数，数据变化后执行 |


<br>


## 返回

| 属性 | 类型 | 默认值 | 说明                         |
| :--- | :--- | :----- | :--------------------------- |
| ret  | bool |        | 操作成功：true； 失败：false |



<br><br><br>




# offRealTimeChange(function callback)

取消监听：realtime 时间戳变化


<br>


## 参数

| 属性     | 类型     | 返回值 | 说明                                   |
| :------- | :------- | :----- | :------------------------------------- |
| callback | function | 无     | 注册的onChange回调函数，数据变化后执行 |


<br>


## 返回

| 属性 | 类型 | 默认值 | 说明                         |
| :--- | :--- | :----- | :--------------------------- |
| ret  | bool |        | 操作成功：true； 失败：false |


<br><br><br>


# getScreenMode()

获取屏幕模式


<br>


## 参数

无


<br>


### 返回

| 属性 | 类型   | 默认值 | 说明                              |
| :--- | :----- | :----- | :-------------------------------- |
| ret  | number |        | Normal：0；   AOD: 1；Other：其他 |



<br><br><br>



# setScreenMode()

设置屏幕模式


<br>


## 参数

| 属性 | 类型   | 默认值 | 说明                              |
| :--- | :----- | :----- | :-------------------------------- |
| mode | number |        | Normal：0；   AOD: 1；Other：其他 |


<br>


### 返回

| 属性 | 类型 | 默认值 | 说明                         |
| :--- | :--- | :----- | :--------------------------- |
| ret  | bool |        | 操作成功：true； 失败：false |



<br><br><br>




# openScreen()

打开（LCD）屏幕



<br>


## 参数

无


<br>


### 返回

| 属性 | 类型 | 默认值 | 说明                         |
| :--- | :--- | :----- | :--------------------------- |
| ret  | bool |        | 操作成功：true； 失败：false |




<br><br><br>


# closeScreen()

关闭（LCD）屏幕


<br>


## 参数

无


<br>


### 返回

| 属性 | 类型 | 默认值 | 说明                         |
| :--- | :--- | :----- | :--------------------------- |
| ret  | bool |        | 操作成功：true； 失败：false |



<br><br><br>



# getScreenStatus()

获取当前（LCD）屏幕状态


<br>


## 参数

无


<br>


## 返回

| 属性  | 类型   | 默认值 | 说明                                  |
| :---- | :----- | :----- | :------------------------------------ |
| value | number |        | 屏幕的状态 0：灭屏， 1：亮屏，2：其他 |



<br><br><br>



# onScreenPowerChange(function callback)

开启监听：屏幕状态改变



<br>


## 参数

| 属性     | 类型     | 返回值 | 说明                                   |
| :------- | :------- | :----- | :------------------------------------- |
| callback | function | 无     | 注册的onChange回调函数，数据变化后执行 |



<br>


## 返回

| 属性  | 类型   | 默认值 | 说明 |
| :---- | :----- | :----- | :--- |
| ret  | bool |        | 操作成功：true； 失败：false |




<br><br><br>



# offScreenPowerChange(function callback)

取消监听：屏幕状态改变


<br>


## 参数

| 属性     | 类型     | 返回值 | 说明                   |
| :------- | :------- | :----- | :--------------------- |
| callback | function | 无     | 注册的onChange回调函数 |


<br>


## 返回

| 属性 | 类型 | 默认值 | 说明                         |
| :--- | :--- | :----- | :--------------------------- |
| ret  | bool |        | 操作成功：true； 失败：false |




<br><br><br>



# getScreenBrightness()

获取屏幕亮度


<br>


## 参数

无


<br>


## 返回

| 属性  | 类型   | 默认值 | 必填 | 说明                                       |
| :---- | :----- | :----- | :--- | :----------------------------------------- |
| value | number |        | 是   | 屏幕亮度值，范围 0 ~ 100。0 最暗，100 最亮 |



<br><br><br>



# setScreenBrightness(number)

设置屏幕亮度



<br>


## 参数

| 属性     | 类型     | 默认值 | 必填 | 说明                                             |
| :------- | :------- | :----- | :--- | :----------------------------------------------- |
| value    | number   |        | 是   | 屏幕亮度值，范围 0 ~ 100。0 最暗，100最亮        |


<br>


## 返回

| 属性 | 类型 | 默认值 | 说明                         |
| :--- | :--- | :----- | :--------------------------- |
| ret  | bool |        | 操作成功：true； 失败：false |



<br><br><br>




# openTouchPanel()

打开触摸屏


<br>


## 参数

无


<br>


## 返回

| 属性 | 类型 | 默认值 | 说明                         |
| :--- | :--- | :----- | :--------------------------- |
| ret  | bool |        | 操作成功：true； 失败：false |



<br><br><br>




# closeTouchPanel()

关闭（TP）触摸屏


<br>


## 参数

无


<br>


## 返回

| 属性 | 类型 | 默认值 | 说明                         |
| :--- | :--- | :----- | :--------------------------- |
| ret  | bool |        | 操作成功：true； 失败：false |



<br><br><br>




# getTouchPanelStatus()

获取当前（TP）触摸屏状态


<br>


## 参数

无


<br>


## 返回

| 属性  | 类型   | 默认值 | 必填 | 说明                   |
| :---- | :----- | :----- | :--- | :--------------------- |
| value | number |        | 是   | TP的状态 0：关， 1：开 |




<br><br><br>



# onTouchPanelPowerChange(function callback)

监听触摸屏（TP）状态改变


<br>


## 参数

| 属性     | 类型     | 返回值 | 说明                                   |
| :------- | :------- | :----- | :------------------------------------- |
| callback | function | 无     | 注册的onChange回调函数，数据变化后执行 |


<br>


## 返回

| 属性  | 类型 | 默认值 | 说明                         |
| :---- | :--- | :----- | :--------------------------- |
| value | bool |        | 操作成功：true； 失败：false |



<br><br><br>



# offTouchPanelPowerChange(function callback)

关闭监听触摸屏（TP）状态改变


<br>


## 参数

| 属性     | 类型     | 返回值 | 说明                   |
| :------- | :------- | :----- | :--------------------- |
| callback | function | 无     | 注册的onChange回调函数 |


<br>


## 返回

| 属性  | 类型 | 默认值 | 说明                         |
| :---- | :--- | :----- | :--------------------------- |
| value | bool |        | 操作成功：true； 失败：false |




<br><br><br>




# vibrate(onTime, offTime, repeat)

振动：使电机转动。


<br>


## 参数


| 属性     | 类型     | 默认值 | 必填 | 说明                                             |
| :------- | :------- | :----- | :--- | :----------------------------------------------- |
| onTime   | number|        | 是   | 开启时间 (ms)                                        |
| offTime  | number|        | 是   | 停止时间 (ms)                                         |
| repeat   |  number|        | 是   | 重复次数                                          |


<br>


### 返回

无



<br><br><br>



# reboot()

系统重启（reboot）



<br>


## 参数

无


<br>


## 返回

无




<br><br><br>



# powerOff()

系统关机（shutdown）


<br>


## 参数

无


<br>


## 返回

无





<br><br><br>


# getBatteryLevel()

获取电池电量


<br>


## 参数

无


<br>



## 返回

| 属性  | 类型   | 默认值 | 必填 | 说明              |
| :---- | :----- | :----- | :--- | :---------------- |
| value | number |        | 是   | 电池电量：0 - 100 |




<br><br><br>


# onBatteryLevelChange(function callback)

开启监听：电量变化


<br>


## 参数

| 属性     | 类型     | 返回值 | 说明                                   |
| :------- | :------- | :----- | :------------------------------------- |
| callback | function | 无     | 注册的onChange回调函数，数据变化后执行 |


<br>


## 返回

| 属性 | 类型 | 默认值 | 说明                         |
| :--- | :--- | :----- | :--------------------------- |
| ret  | bool |        | 操作成功：true； 失败：false |



<br><br><br>



# offBatteryLevelChange(function callback)

取消监听：电量变化


<br>


## 参数

| 属性     | 类型     | 返回值 | 说明                                   |
| :------- | :------- | :----- | :------------------------------------- |
| callback | function | 无     | 注册的onChange回调函数，数据变化后执行 |


<br>


## 返回

| 属性 | 类型 | 默认值 | 说明                         |
| :--- | :--- | :----- | :--------------------------- |
| ret  | bool |        | 操作成功：true； 失败：false |




<br><br><br>



# getChargeStatus()

获取充电状态



<br>


## 参数

无



<br>


## 返回

| 属性  | 类型   | 默认值 | 必填 | 说明                         |
| :---- | :----- | :----- | :--- | :--------------------------- |
| value | number |        | 否   | 0：不充电  1：充电   2：充满 |



<br><br><br>



# onBatteryChargeChange(function callback)

开启监听：充电状态变化


<br>


## 参数

| 属性     | 类型     | 返回值 | 说明                                   |
| :------- | :------- | :----- | :------------------------------------- |
| callback | function | 无     | 注册的onChange回调函数，数据变化后执行 |


<br>


## 返回

| 属性 | 类型 | 默认值 | 说明                         |
| :--- | :--- | :----- | :--------------------------- |
| ret  | bool |        | 操作成功：true； 失败：false |





<br><br><br>




# offChargeChange(function callback)

关闭监听：充电状态变化



<br>


## 参数

| 属性     | 类型     | 返回值 | 说明                   |
| :------- | :------- | :----- | :--------------------- |
| callback | function | 无     | 注册的onChange回调函数 |

<br>

## 返回

| 属性 | 类型 | 默认值 | 说明                         |
| :--- | :--- | :----- | :--------------------------- |
| ret  | bool |        | 操作成功：true； 失败：false |





<br><br><br>




# getInfo()

获取当前信息，如版本号等，


<br>


## 参数

无


<br>


## 返回：JSON数组



| 属性             | 类型    | 说明               |
| :--------------- | :------ | :----------------- |
| brand            | string  | 设备品牌           |
| model            | string  | 设备型号           |
| screenWidth      | number  | 屏幕宽度，单位px   |
| screenHeight     | number  | 屏幕高度，单位px   |
| language         | string  | 语言               |
| version          | string  | 版本号         |
| system           | string  | 操作系统及版本     |
| bluetoothEnabled | boolean | 蓝牙的系统开关     |
| locationEnabled  | boolean | 地理位置的系统开关 |



<br><br><br>



# onKeyChange(function callback)

监听按键事件



<br>


## 参数

| 属性     | 类型     | 返回值   | 说明                               |
| :------- | :------- | :------- | :--------------------------------- |
| callback | function | 按键事件 | 注册的onChange回调函数，变化后执行 |


<br>


## 返回

| 属性 | 类型 | 默认值 | 说明                         |
| :--- | :--- | :----- | :--------------------------- |
| ret  | bool |        | 操作成功：true； 失败：false |





<br><br><br>




# offKeyChange(function callback)


关闭监听：按键事件


<br>


## 参数

| 属性     | 类型     | 返回值 | 说明                                   |
| :------- | :------- | :----- | :------------------------------------- |
| callback | function | 无     | 注册的onChange回调函数，数据变化后执行 |


<br>


## 返回

| 属性 | 类型 | 默认值 | 说明                         |
| :--- | :--- | :----- | :--------------------------- |
| ret  | bool |        | 操作成功：true； 失败：false |
