# I2C

## pm.openIICPort(Object object)

打开I2C设备接口。

参数 Object object

| 属性 | 类型 | 描述 |
| - | - | - |
| port | String | 要打开的设备名 |

示例代码：

```JavaScript
var iic = pm.openIICPort({port : "i2c2"});
```

## 可配置 flags 值定义

```flags
#define RT_I2C_ADDR_10BIT       (1u << 2)  /* this is a 10bit chip address */
#define RT_I2C_NO_START         (1u << 4)
#define RT_I2C_IGNORE_NACK      (1u << 5)
#define RT_I2C_NO_READ_ACK      (1u << 6)  /* when I2C reading, we do not ACK */
```

## read(Number addr, Buffer buf)

读取数据。

| 参数 | 类型 | 描述 |
| - | - | - |
| addr | Number | 要读取数据的设备地址 |
| buf | Buffer | 存放读取到的数据的 buffer，其中包含又要读取的数据长度，即 buffer 的大小 |

```JavaScript
var iic = pm.openIICPort({port : "i2c2"});
var buf = new Buffer(2);
iic.read(0x5D, buf);
```

## read(Number addr, Buffer buf1, Buffer buf2)

读取数据，先写命名再读数据。

| 参数 | 类型 | 描述 |
| - | - | - |
| addr | Number | 要读取数据的设备地址 |
| buf1 | Buffer | 存放要写入的命名的 buffer |
| buf2 | Buffer | 存放读取到的数据的 buffer，其中包含又要读取的数据长度，即 buffer 的大小 |

```JavaScript
var iic = pm.openIICPort({port : "i2c2"});
var buf1 = new Buffer(2);
var buf2 = new Buffer(4);
buf1.writeUInt16BE(0x8140, 0);
iic.read(0x5D, buf1, buf2);
```

## read(Number addr, Buffer buf1, Buffer buf2, Number flags)

读取数据，先写命名再读数据。

| 参数 | 类型 | 描述 |
| - | - | - |
| addr | Number | 要读取数据的设备地址 |
| buf1 | Buffer | 存放要写入的命名的 buffer |
| buf2 | Buffer | 存放读取到的数据的 buffer，其中包含又要读取的数据长度，即 buffer 的大小 |
| flags | Number | flags 配置 |

```JavaScript
var iic = pm.openIICPort({port : "i2c2"});
var buf1 = new Buffer(2);
var buf2 = new Buffer(4);
buf1.writeUInt16BE(0x8140, 0);
iic.read(0x5D, buf1, buf2, 0x10);   //RT_I2C_NO_START (1u << 4)
```

## write(Number addr, Buffer buf)

写数据。

| 参数 | 类型 | 描述 |
| - | - | - |
| addr | Number | 要写数据的设备地址 |
| buf | Buffer | 存放要写的数据的 buffer，其中包含数据长度，即 buffer 的大小 |

```JavaScript
var iic = pm.openIICPort({port : "i2c2"});
var buf = new Buffer(2);
buf.writeUInt16BE(0x8140, 0);
iic.write(0x5D, buf);
```

## write(Number addr, Buffer buf1, Buffer buf2)

写数据。

| 参数 | 类型 | 描述 |
| - | - | - |
| addr | Number | 要写数据的设备地址 |
| buf1 | Buffer | 存放要写入的命名的 buffer |
| buf2 | Buffer | 存放要写的数据的 buffer，其中包含数据长度，即 buffer 的大小 |

```JavaScript
var iic = pm.openIICPort({port : "i2c2"});
var buf1 = new Buffer(2);
var buf2 = new Buffer(4);
buf1.writeUInt16BE(0x8140, 0);
buf2.writeUInt32BE(0x81408140, 0);
iic.write(0x5D, buf1, buf2);
```

## write(Number addr, Buffer buf1, Buffer buf2, Number flags)

写数据。

| 参数 | 类型 | 描述 |
| - | - | - |
| addr | Number | 要写数据的设备地址 |
| buf1 | Buffer | 存放要写入的命名的 buffer |
| buf2 | Buffer | 存放要写的数据的 buffer，其中包含数据长度，即 buffer 的大小 |
| flags | Number | flags 配置 |

```JavaScript
var iic = pm.openIICPort({port : "i2c2"});
var buf1 = new Buffer(2);
var buf2 = new Buffer(4);
buf1.writeUInt16BE(0x8140, 0);
buf2.writeUInt32BE(0x81408140, 0);
iic.write(0x5D, buf1, buf2, 0x10);    //RT_I2C_NO_START (1u << 4)
```