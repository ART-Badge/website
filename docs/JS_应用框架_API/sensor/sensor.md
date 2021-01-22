## 传感器管理 Sensor API 手册

<br>

`引用模块名`：`sensor`

```
var sensor = require('module/sensor.js');
```

| index | 模块描述     | JS API                     | 备注                   |
| ---- | ------------ | -------------------------- | ---------------------- |
| 1   | acce         | getAccelerometerID         | 获取ID                 |
| 1   | acce         | getAccelerometerData       | 获取数据               |
| 1   | acce         | openAccelerometer          | 打开：加速度传感器     |
| 1   | acce         | closeAccelerometer         | 关闭：加速度传感器     |
| 1   | acce         | onAccelerometerDataChange  | 开启监听：加速度变化   |
| 1   | acce         | offAccelerometerDataChange | 取消监听：加速度变化   |
| 2   | Gyroscope    | getGyroscopeId             | 获取陀螺仪传感器ID     |
| 2   | Gyroscope    | getGyroscope               | 获取陀螺仪数据         |
| 2   | Gyroscope    | openGyroscope              | 开启陀螺仪             |
| 2   | Gyroscope    | closeGyroscope             | 关闭陀螺仪             |
| 2   | Gyroscope    | onGyroscopeChange          | 开启监听：陀螺仪       |
| 2   | Gyroscope    | offGyroscopeChange         | 关闭监听：陀螺仪       |
| 3   | Magnetometer | getMagnetometer            | 获取磁传感器数据       |
| 3   | Magnetometer | getMagnetometerId          | 获取磁传感器ID         |
| 3   | Magnetometer | openMagnetometer           | 开启磁传感器           |
| 3   | Magnetometer | closeMagnetometer          | 关闭磁传感器           |
| 3   | Magnetometer | onMagnetometerChange       | 开启监听：磁           |
| 3   | Magnetometer | offMagnetometerChange      | 关闭监听：磁           |
| 4   | Temperature  | getTemperature             | 获取当前温度值         |
| 4   | Temperature  | getTemperatureId           | 获取温度传感器ID       |
| 4   | Temperature  | openTemperature            | 开启温度检测           |
| 4   | Temperature  | closeTemperature           | 关闭温度检测           |
| 4   | Temperature  | onTemperatureChange        | 开启监听：温度变化     |
| 4   | Temperature  | offTemperatureChange       | 关闭监听：温度变化     |
| 5   | Humidity     | getHumidity                | 获取湿度值             |
| 5   | Humidity     | getHumidityId              | 获取湿度传感器ID       |
| 5   | Humidity     | openHumidity               | 开启湿度检测           |
| 5   | Humidity     | closeHumidity              | 关闭湿度检测           |
| 5   | Humidity     | onHumidityChange           | 开启监听：湿度值变化   |
| 5   | Humidity     | offHumidityChange          | 关闭监听：湿度值变化   |
| 6   | Barometer    | getBarometer               | 获取气压值             |
| 6   | Barometer    | getBarometerId             | 获取气压传感器ID       |
| 6   | Barometer    | openBarometer              | 开启气压传感器         |
| 6   | Barometer    | closeBarometer             | 关闭气压传感器         |
| 6   | Barometer    | onBarometerChange          | 开启监听：气压值变化   |
| 6   | Barometer    | offBarometerChange         | 关闭监听：气压值变化   |
| 7   | Light        | getLight                   | 获取亮度值             |
| 7   | Light        | getLightId                 | 获取Light传感器ID      |
| 7   | Light        | openLightDetect            | 开启亮度检测           |
| 7   | Light        | closeLightDetect           | 关闭亮度检测           |
| 7   | Light        | onLightChange              | 开启监听：亮度值变化   |
| 7   | Light        | offLightChange             | 关闭监听：亮度值变化   |
| 8   | Proximity    | getProximityId             | 获取距离传感器ID       |
| 8   | Proximity    | getProximity               | 获取距离               |
| 8   | Proximity    | openProximity              | 开启距离检测           |
| 8   | Proximity    | closeProximity             | 关闭距离检测           |
| 8   | Proximity    | onProximityChange          | 开启监听：距离         |
| 8   | Proximity    | offProximityChange         | 关闭监听：距离         |
| 9    | HeartRate    | getHeartRate               | 获取心率数据           |
| 9    | HeartRate    | getHeartRateId             | 获取心率传感器ID       |
| 9    | HeartRate    | openHeartRateDetect        | 开启心率检测           |
| 9   | HeartRate    | closeHeartRateDetect       | 关闭心率检测           |
| 9   | HeartRate    | onHeartRateChange          | 开启监听：获取心率数据 |
| 9   | HeartRate    | offHeartRateChange         | 关闭监听：获取心率数据 |
| 10  | TVOC         | getTVOCId                  | 获取TVOC 传感器ID      |
| 10   | TVOC         | getTVOC                    | 获取TVOC 数据          |
| 10  | TVOC         | openTVOC                   | 开启TVOC               |
| 10  | TVOC         | closeTVOC                  | 关闭TVOC               |
| 10  | TVOC         | onTVOCChange               | 开启监听:TVOC          |
| 10  | TVOC         | offTVOCChange              | 关闭监听：TVOC         |
| 11  | Noise        | getNoiseId                 | 获取Noise数据          |
| 11  | Noise        | getNoise                   | 获取Noise传感器ID      |
| 11  | Noise        | openNoise                  | 开启Noise检测          |
| 11  | Noise        | closeNoise                 | 关闭Noise检测          |
| 11  | Noise        | onNoiseChange              | 开启监听：Noise        |
| 11  | Noise        | offNoiseChange             | 关闭监听:Noise         |
| 12   | Step         | getStepCounter             | 获取计步数据           |
| 12   | Step         | getStepCounterId           | 获取计步传感器ID       |
| 12   | Step         | openStepCounter            | 开启计步               |
| 12   | Step         | closeStepCounter           | 关闭计步               |
| 12   | Step         | onStepChange               | 开启监听：计步数据     |
| 12   | Step         | offStepChange              | 关闭监听：计步数据     |
| 13  | Force        | getForceId                 | 获取压力传感器ID       |
| 13  | Force        | getForce                   | 获取压力传感器数据     |
| 13  | Force        | openForce                  | 开启压力传感器         |
| 13  | Force        | closeForce                 | 关闭压力传感器         |
| 13  | Force        | onForceChange              | 开启监听：压力         |
| 13  | Force        | offForceChange             | 关闭监听：压力         |
| 14  | SPO2         | getSPO2                    | 获取血氧               |
| 14  | SPO2         | getSPO2Id                  | 获取血氧传感器ID       |
| 14  | SPO2         | openSPO2                   | 开启血氧               |
| 14  | SPO2         | closeSPO2                  | 关闭血氧               |
| 14  | SPO2         | onSPO2Change               | 开启监听：血氧变化     |
| 14  | SPO2         | offSPO2Change              | 关闭监听：血氧变化     |



<br>

<br>

<br>

# getAccelerometerID()

获取加速度ID值

<br>

## 参数

无

<br>

## 返回

| 属性 | 类型   | 默认值 | 说明               |
| :--- | :----- | :----- | :----------------- |
| ret  | number |        | ID值，如 51（0x33) |



<br><br><br>

# getAccelerometerData()

获取加速度三轴数据

<br>

## 参数

无

<br>

## 返回

| 属性 | 类型     | 默认值 | 说明           |
| :--- | :------- | :----- | :------------- |
| ret  | JSON对象 |        | [100,200,-300] |



<br><br><br>

# openAccelerometer()

打开加速度传感器

<br>

## 参数

无

<br>

## 返回

| 属性 | 类型 | 默认值 | 说明                         |
| :--- | :--- | :----- | :--------------------------- |
| ret  | bool |        | 操作成功：true； 失败：false |



<br><br><br>

# closeAccelerometer()

关闭加速度传感器

<br>

## 参数

无

<br>

## 返回

| 属性 | 类型 | 默认值 | 说明                         |
| :--- | :--- | :----- | :--------------------------- |
| ret  | bool |        | 操作成功：true； 失败：false |



<br><br><br>

# onAccelerometerDataChange(function callback)

开启监听：加速度值变化

<br>

## 参数

| 属性     | 类型     | 返回值 | 说明           |
| :------- | :------- | :----- | :------------- |
| callback | function | 无     | 提示加速度变化 |

<br>

## 返回

| 属性 | 类型 | 默认值 | 说明                                     |
| :--- | :--- | :----- | :--------------------------------------- |
| ret  | bool |        | 注册监听函数操作成功：true； 失败：false |

<br><br><br>



# offAccelerometerDataChange(function callback)

取消监听：加速度值变化

<br>

## 参数

| 属性     | 类型     | 返回值 | 说明                   |
| :------- | :------- | :----- | :--------------------- |
| callback | function | 无     | 注册的onChange回调函数 |

<br>

## 返回

| 属性 | 类型 | 默认值 | 说明                                     |
| :--- | :--- | :----- | :--------------------------------------- |
| ret  | bool |        | 取消监听函数操作成功：true； 失败：false |





<br>

# getGyroscope()

获取 Gyroscope传感器数据

<br>

## 参数

无

<br>

## 返回

| 属性 | 类型 | 默认值 | 说明                 |
| :--- | :--- | :----- | :------------------- |
| ret  | JSON |        | [100,200,-300] |



<br><br><br>

# getGyroscopeId()

获取  Gyroscope 传感器Sensor ID

<br>

## 参数

无

<br>

## 返回

| 属性 | 类型   | 默认值 | 说明                |
| :--- | :----- | :----- | :------------------ |
| ret  | number |        | Gyroscope Sensor ID |



<br><br><br>

# openGyroscope()

打开 Gyroscope传感器

<br>

## 参数

无

<br>

## 返回

| 属性 | 类型 | 默认值 | 说明                         |
| :--- | :--- | :----- | :--------------------------- |
| ret  | bool |        | 操作成功：true； 失败：false |



<br><br><br>

# closeGyroscope()

关闭 Gyroscope传感器

<br>

## 参数

无

<br>

## 返回

| 属性 | 类型 | 默认值 | 说明                         |
| :--- | :--- | :----- | :--------------------------- |
| ret  | bool |        | 操作成功：true； 失败：false |



<br><br><br>



# onGyroscopeChange(function callback)

开启监听：Gyroscope值变化

<br>

## 参数

| 属性     | 类型     | 返回值 | 说明                 |
| :------- | :------- | :----- | :------------------- |
| callback | function | 无     | 提示 Gyroscope  变化 |

<br>

## 返回

| 属性 | 类型 | 默认值 | 说明                                     |
| :--- | :--- | :----- | :--------------------------------------- |
| ret  | bool |        | 注册监听函数操作成功：true； 失败：false |



<br><br><br>

# offGyroscopeChange(function callback)

取消监听：Gyroscope值变化

<br>

## 参数

| 属性     | 类型     | 返回值 | 说明                   |
| :------- | :------- | :----- | :--------------------- |
| callback | function | 无     | 注册的onChange回调函数 |

<br>

## 返回

| 属性 | 类型 | 默认值 | 说明                                     |
| :--- | :--- | :----- | :--------------------------------------- |
| ret  | bool |        | 取消监听函数操作成功：true； 失败：false |



<br><br><br>

# getMagnetometer()

获取 磁传感器数据

<br>

## 参数

无

<br>

## 返回

| 属性 | 类型   | 默认值 | 说明             |
| :--- | :----- | :----- | :----------- |
| ret  | number |        | [100,200,-300] |



<br><br><br>

# getMagnetometerId()

获取 磁传感器 sensor ID

<br>

## 参数

无

<br>

## 返回

| 属性 | 类型   | 默认值 | 说明               |
| :--- | :----- | :----- | :----------------- |
| ret  | number |        | 磁传感器 sensor ID |



<br><br><br>

# openMagnetometer()

开启磁传感器

<br>

## 参数

无

<br>

## 返回

| 属性 | 类型 | 默认值 | 说明                         |
| :--- | :--- | :----- | :--------------------------- |
| ret  | bool |        | 操作成功：true； 失败：false |

<br><br><br>

# closeMagnetometer()

关闭磁传感器

<br>

## 参数

无

<br>

## 返回

| 属性 | 类型 | 默认值 | 说明                         |
| :--- | :--- | :----- | :--------------------------- |
| ret  | bool |        | 操作成功：true； 失败：false |



<br>

# onMagnetometerChange(function callback)

开始监听：磁传感器数据

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



# offMagnetometerChange(function callback)

取消监听：磁传感器数据

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



<br><br>

# getTemperature()

获取当前温度

<br>

## 参数

无

<br>

## 参数

| 属性  | 类型   | 默认值 | 必填 | 说明                        |
| :---- | :----- | :----- | :--- | :-------------------------- |
| value | number |        | 是   | 温度 ：205 为 20.5摄氏度 |

<br><br><br>

# getTemperatureId()

获取温度Sensor ID

<br>

## 参数

无

<br>

## 参数

| 属性  | 类型   | 默认值 | 必填 | 说明          |
| :---- | :----- | :----- | :--- | :------------ |
| value | number |        | 是   | 温度Sensor ID |

<br><br><br>

# openTemperature()

开启温度检测

<br>

## 参数

无

<br>

## 返回

| 属性 | 类型 | 默认值 | 说明                         |
| :--- | :--- | :----- | :--------------------------- |
| ret  | bool |        | 操作成功：true； 失败：false |



<br><br><br>

# closeTemperature()

关闭温度检测

<br>

## 参数

无

<br>

## 返回

| 属性 | 类型 | 默认值 | 说明                         |
| :--- | :--- | :----- | :--------------------------- |
| ret  | bool |        | 操作成功：true； 失败：false |



<br><br><br>

# onTemperatureChange(function callback)



开启监听：温度的变化

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

<br>

<br>


# offTemperatureChange(function callback)

停止监听：温度的变化

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

# getHumidity()

获取当前湿度

<br>

## 参数

无

<br>

## 参数

| 属性  | 类型   | 默认值 | 必填 | 说明         |
| :---- | :----- | :----- | :--- | :----------- |
| value | number |        | 是   | 湿度 ：0~100 |

<br><br><br>

# getHumidityId()

获取湿度 Sensor ID

<br>

## 参数

无

<br>

## 参数

| 属性  | 类型   | 默认值 | 必填 | 说明           |
| :---- | :----- | :----- | :--- | :------------- |
| value | number |        | 是   | 湿度 Sensor ID |



<br><br><br>

# openHumidity()

开启湿度检测

<br>

## 参数

无

<br>

## 返回

| 属性 | 类型 | 默认值 | 说明                         |
| :--- | :--- | :----- | :--------------------------- |
| ret  | bool |        | 操作成功：true； 失败：false |



<br><br><br>

# closeHumidity()

关闭湿度检测

<br>

## 参数

无

<br>

## 返回

| 属性 | 类型 | 默认值 | 说明                         |
| :--- | :--- | :----- | :--------------------------- |
| ret  | bool |        | 操作成功：true； 失败：false |



<br><br><br>

# onHumidityChange(function callback)

开始监听：湿度的变化

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

# offHumidityChange(function callback)

停止监听：湿度的变化

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



# getBarometer()

获取当前气压

<br>

## 参数

无

<br>

## 返回

| 属性 | 类型   | 默认值 | 说明           |
| :--- | :----- | :----- | :------------- |
| ret  | number |        | Barometer 数据 |

<br><br><br>

# getBarometerId()

获取气压Sensor ID

<br>

## 参数

无


<br>

## 返回

| 属性 | 类型   | 默认值 | 说明                |
| :--- | :----- | :----- | :------------------ |
| ret  | number |        | Barometer Sensor ID |

<br><br><br>

# onBarometerChange(function callback)



开始监听：气压的变化

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



# offBarometerChange(function callback)

取消监听：气压的变化

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

# openBarometer()

开启气压检测

<br>

## 参数

无

<br>

## 返回

| 属性 | 类型 | 默认值 | 说明                         |
| :--- | :--- | :----- | :--------------------------- |
| ret  | bool |        | 操作成功：true； 失败：false |



<br><br><br>

# closeBarometer()

关闭气压检测

<br>

## 参数

无

<br>

## 返回

| 属性 | 类型 | 默认值 | 说明                         |
| :--- | :--- | :----- | :--------------------------- |
| ret  | bool |        | 操作成功：true； 失败：false |



<br>



<br><br>

# getLight()

获取当前亮度（光照ALS）

<br>

## 参数

无

<br>

## 返回

| 属性  | 类型   | 默认值 | 必填 | 说明 |
| :---- | :----- | :----- | :--- | :--- |
| value | number |        | 是   | 亮度 |

<br><br><br>

# getLightId()

获取亮度 Sensor ID

<br>

## 参数

无

<br>

## 返回

| 属性  | 类型   | 默认值 | 必填 | 说明           |
| :---- | :----- | :----- | :--- | :------------- |
| value | number |        | 是   | 亮度 Sensor ID |



<br><br><br>

# onLightChange(function callback)

开始监听：亮度的变化

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

# offLightChange(function callback)



取消监听：亮度的变化

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

# openLightDetect()

开启亮度检测

<br>

## 参数

无

<br>

## 返回

| 属性 | 类型 | 默认值 | 说明                         |
| :--- | :--- | :----- | :--------------------------- |
| ret  | bool |        | 操作成功：true； 失败：false |

<br><br><br>

# closeLightDetect()

关闭亮度检测

<br>

## 参数

无

<br>

## 返回

| 属性 | 类型 | 默认值 | 说明                         |
| :--- | :--- | :----- | :--------------------------- |
| ret  | bool |        | 操作成功：true； 失败：false |



<br><br><br>





# getProximity()

获取 Proximity传感器数据

<br>

## 参数

无

<br>

## 返回

| 属性 | 类型 | 默认值 | 说明                |
| :--- | :--- | :----- | :------------------ |
| ret  | JSON |        | Proximity传感器数据 |



<br><br><br>



# getProximityId()

获取  Proximity传感器Sensor ID

<br>

## 参数

无

<br>

## 返回

| 属性 | 类型   | 默认值 | 说明                |
| :--- | :----- | :----- | :------------------ |
| ret  | number |        | Proximity Sensor ID |



<br><br><br>



# openProximity()

打开 Proximity传感器

<br>

## 参数

无

<br>

## 返回

| 属性 | 类型 | 默认值 | 说明                         |
| :--- | :--- | :----- | :--------------------------- |
| ret  | bool |        | 操作成功：true； 失败：false |



<br><br><br>

# closeProximity()

关闭 Proximity 传感器

<br>

## 参数

无

<br>

## 返回

| 属性 | 类型 | 默认值 | 说明                         |
| :--- | :--- | :----- | :--------------------------- |
| ret  | bool |        | 操作成功：true； 失败：false |



<br><br><br>



# onProximityChange(function callback)

开启监听：Proximity 值变化

<br>

## 参数

| 属性     | 类型     | 返回值 | 说明                 |
| :------- | :------- | :----- | :------------------- |
| callback | function | 无     | 提示 Proximity  变化 |

<br>

## 返回

| 属性 | 类型 | 默认值 | 说明                                     |
| :--- | :--- | :----- | :--------------------------------------- |
| ret  | bool |        | 注册监听函数操作成功：true； 失败：false |

<br><br><br>

# offProximityChange(function callback)

取消监听：Proximity 值变化

<br>

## 参数

| 属性     | 类型     | 返回值 | 说明                   |
| :------- | :------- | :----- | :--------------------- |
| callback | function | 无     | 注册的onChange回调函数 |

<br>

## 返回

| 属性 | 类型 | 默认值 | 说明                                     |
| :--- | :--- | :----- | :--------------------------------------- |
| ret  | bool |        | 取消监听函数操作成功：true； 失败：false |

<br>



<br>

# getHeartRate()

获取心率数据

<br>

## 参数

无

<br>

## 返回

| 属性  | 类型   | 默认值 | 必填 | 说明     |
| :---- | :----- | :----- | :--- | :------- |
| value | number |        | 是   | 心率数据 |

<br><br><br>

# getHeartRateId()

获取心率 Sensor ID

<br>

## 参数

无

<br>

## 返回

| 属性  | 类型   | 默认值 | 必填 | 说明          |
| :---- | :----- | :----- | :--- | :------------ |
| value | number |        | 是   | 心率Sensor ID |

<br><br><br>

# onHeartRateChange(function callback)

开始监听：心率数据变化

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

# offHeartRateChange(function callback)

停止监听：心率数据变化

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

# openHeartRate()

开启心率检测

<br>

## 参数

无

<br>

## 返回

| 属性 | 类型 | 默认值 | 说明                         |
| :--- | :--- | :----- | :--------------------------- |
| ret  | bool |        | 操作成功：true； 失败：false |



<br><br><br>

# closeHeartRate()

关闭心率检测

<br>

## 参数

无

<br>


## 返回

| 属性 | 类型 | 默认值 | 说明                         |
| :--- | :--- | :----- | :--------------------------- |
| ret  | bool |        | 操作成功：true； 失败：false |

<br>



<br><br>

# getTVOC()

获取 TVOC传感器数据

<br>

## 参数

无

<br>

## 返回

| 属性 | 类型 | 默认值 | 说明           |
| :--- | :--- | :----- | :------------- |
| ret  | JSON |        | TVOC传感器数据 |



<br><br><br>



# getTVOCId()

获取 TVOC 传感器Sensor ID

<br>

## 参数

无

<br>

## 返回

| 属性 | 类型   | 默认值 | 说明           |
| :--- | :----- | :----- | :------------- |
| ret  | number |        | TVOC Sensor ID |



<br><br><br>

# openTVOC()

打开 TVOC 传感器

<br>

## 参数

无

<br>

## 返回

| 属性 | 类型 | 默认值 | 说明                         |
| :--- | :--- | :----- | :--------------------------- |
| ret  | bool |        | 操作成功：true； 失败：false |



<br><br><br>

# closeTVOC()

关闭 TVOC 传感器

<br>

## 参数

无

<br>

## 返回

| 属性 | 类型 | 默认值 | 说明                         |
| :--- | :--- | :----- | :--------------------------- |
| ret  | bool |        | 操作成功：true； 失败：false |



<br><br><br>

# onTVOCChange(function callback)

开启监听：TVOC 值变化

<br>

## 参数

| 属性     | 类型     | 返回值 | 说明            |
| :------- | :------- | :----- | :-------------- |
| callback | function | 无     | 提示 TVOC  变化 |

<br>

## 返回

| 属性 | 类型 | 默认值 | 说明                                     |
| :--- | :--- | :----- | :--------------------------------------- |
| ret  | bool |        | 注册监听函数操作成功：true； 失败：false |

<br><br><br>

# offTVOCChange(function callback)

取消监听：TVOC 值变化

<br>

## 参数

| 属性     | 类型     | 返回值 | 说明                   |
| :------- | :------- | :----- | :--------------------- |
| callback | function | 无     | 注册的onChange回调函数 |

<br>

## 返回

| 属性 | 类型 | 默认值 | 说明                                     |
| :--- | :--- | :----- | :--------------------------------------- |
| ret  | bool |        | 取消监听函数操作成功：true； 失败：false |





<br><br>



# getNoise()

获取 Noise 传感器数据

<br>

## 参数

无

<br>

## 返回

| 属性 | 类型 | 默认值 | 说明            |
| :--- | :--- | :----- | :-------------- |
| ret  | JSON |        | Noise传感器数据 |



<br><br><br>



# getNoiseId()

获取 Noise 传感器Sensor ID

<br>

## 参数

无

<br>

## 返回

| 属性 | 类型   | 默认值 | 说明            |
| :--- | :----- | :----- | :-------------- |
| ret  | number |        | Noise Sensor ID |





<br><br><br>

# openNoise()

打开Noise传感器

<br>

## 参数

无

<br>

## 返回

| 属性 | 类型 | 默认值 | 说明                         |
| :--- | :--- | :----- | :--------------------------- |
| ret  | bool |        | 操作成功：true； 失败：false |



<br><br><br>

# closeNoise()

关闭Noise传感器

<br>

## 参数

无

<br>

## 返回

| 属性 | 类型 | 默认值 | 说明                         |
| :--- | :--- | :----- | :--------------------------- |
| ret  | bool |        | 操作成功：true； 失败：false |



<br><br><br>

# onNoiseChange(function callback)

开启监听：Noise 值变化

<br>

## 参数

| 属性     | 类型     | 返回值 | 说明            |
| :------- | :------- | :----- | :-------------- |
| callback | function | 无     | 提示 Noise 变化 |

<br>

## 返回

| 属性 | 类型 | 默认值 | 说明                                     |
| :--- | :--- | :----- | :--------------------------------------- |
| ret  | bool |        | 注册监听函数操作成功：true； 失败：false |

<br><br><br>

# offNoiseChange(function callback)

取消监听：Noise 值变化

<br>

## 参数

| 属性     | 类型     | 返回值 | 说明                   |
| :------- | :------- | :----- | :--------------------- |
| callback | function | 无     | 注册的onChange回调函数 |

<br>

## 返回

| 属性 | 类型 | 默认值 | 说明                                     |
| :--- | :--- | :----- | :--------------------------------------- |
| ret  | bool |        | 取消监听函数操作成功：true； 失败：false |



<br><br><br>



# getStepCounter()

获取计步数据


<br>

## 参数

无

<br>

## 返回

| 属性  | 类型   | 默认值 | 必填 | 说明     |
| :---- | :----- | :----- | :--- | :------- |
| step  | number |        | 是   | 计步数据 |



<br><br><br>


# getStepCounterId()

获取计步 SensorID

<br>

## 参数

无

<br>

## 返回

| 属性 | 类型   | 默认值 | 必填 | 说明          |
| :--- | :----- | :----- | :--- | :------------ |
| step | number |        | 是   | 计步Sensor ID |





<br><br><br>



# OnStepChange(function callback)

开始监听：计步数据变化


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

# offStepChange(function callback)

取消监听：计步数据变化


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

# openStepCounter()

开启计步

<br>

## 参数

无

<br>

## 返回

| 属性 | 类型 | 默认值 | 说明                         |
| :--- | :--- | :----- | :--------------------------- |
| ret  | bool |        | 操作成功：true； 失败：false |



<br><br><br>


# closeStepCounter()

关闭计步


<br>

## 参数

无

<br>

## 返回

| 属性 | 类型 | 默认值 | 说明                         |
| :--- | :--- | :----- | :--------------------------- |
| ret  | bool |        | 操作成功：true； 失败：false |

<br><br><br>



<br><br>

# getForce()

获取 Force 传感器数据

<br>

## 参数

无

<br>

## 返回

| 属性 | 类型 | 默认值 | 说明             |
| :--- | :--- | :----- | :--------------- |
| ret  | JSON |        | Force 传感器数据 |



<br><br><br>

# getForceId()

获取 Force 传感器Sensor ID

<br>

## 参数

无

<br>

## 返回

| 属性 | 类型   | 默认值 | 说明            |
| :--- | :----- | :----- | :-------------- |
| ret  | number |        | Force Sensor ID |



<br><br><br>



# openForce()

打开 Force 传感器

<br>

## 参数

无

<br>

## 返回

| 属性 | 类型 | 默认值 | 说明                         |
| :--- | :--- | :----- | :--------------------------- |
| ret  | bool |        | 操作成功：true； 失败：false |



<br><br><br>

# closeForce()

关闭 Force 传感器

<br>

## 参数

无

<br>

## 返回

| 属性 | 类型 | 默认值 | 说明                         |
| :--- | :--- | :----- | :--------------------------- |
| ret  | bool |        | 操作成功：true； 失败：false |



<br><br><br>

# onForceChange(function callback)

开启监听：Noise 值变化

<br>

## 参数

| 属性     | 类型     | 返回值 | 说明            |
| :------- | :------- | :----- | :-------------- |
| callback | function | 无     | 提示Force  变化 |

<br>

## 返回

| 属性 | 类型 | 默认值 | 说明                                     |
| :--- | :--- | :----- | :--------------------------------------- |
| ret  | bool |        | 注册监听函数操作成功：true； 失败：false |

<br><br><br>

# offForceChange(function callback)

取消监听：Force 值变化

<br>

## 参数

| 属性     | 类型     | 返回值 | 说明                   |
| :------- | :------- | :----- | :--------------------- |
| callback | function | 无     | 注册的onChange回调函数 |



<br>

## 返回

| 属性 | 类型 | 默认值 | 说明                                     |
| :--- | :--- | :----- | :--------------------------------------- |
| ret  | bool |        | 取消监听函数操作成功：true； 失败：false |



<br><br>







# getSPO2()

获取血氧数据


<br>

## 参数

无

<br>

## 返回

| 属性 | 类型   | 默认值 | 说明     |
| :--- | :----- | :----- | :------- |
| ret  | number |        | SPO2数据 |




<br><br><br>


# getSPO2Id()

获取血氧 sensor ID

<br>

## 参数

无

<br>

## 返回

| 属性 | 类型   | 默认值 | 说明           |
| :--- | :----- | :----- | :------------- |
| ret  | number |        | SPO2 sensor ID |

<br>

<br><br><br>



# onSPO2Change(function callback)

开始监听：血氧数据

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



# offSPO2Change(function callback)

停止监听：血氧数据

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

# openSPO2Detect()

开启血氧检测

<br>

## 参数

无

<br>

### 返回

| 属性 | 类型 | 默认值 | 说明                         |
| :--- | :--- | :----- | :--------------------------- |
| ret  | bool |        | 操作成功：true； 失败：false |


<br><br><br>


# closeSPO2Detect()

关闭血氧检测

<br>

## 参数

无

<br>

## 返回

| 属性 | 类型 | 默认值 | 说明                         |
| :--- | :--- | :----- | :--------------------------- |
| ret  | bool |        | 操作成功：true； 失败：false |





<br><br><br>



<br><br>





