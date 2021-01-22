# Message

JS 的 Message 是JS 与 C 进行消息传递的一个对象，它继承了 `Event`的所有功能。用户在JS层需要和C进行数据传递时（比如C获取到一个字符串数据，需要将该数据显示到屏幕上），此时就需要用户发送消息进行交互。但是这些消息名称是用户自定义的，因此需要用户重新编译固件，才能正常与JS进行Message交互。

# Message()

获取 `Message` 对象。

```javascript
this.message  = Message();  //实例化Message对象。
```

### send(name, value)

`Message` 往底层发送数据。

注：需要底层实现一个接收并处理该消息的函数。

参数说明：

| 参数  | 类型          | 必填 | 说明     |
| :---- | :------------ | :--- | :------- |
| name  | string        | 是   | 名称     |
| value | string/Buffer | 是   | 发送数据 |

```javascript
this.message = Message();  //实例化Message对象

this.message.send("test0", "01234");  //往'test0'发送string类型数据'01234'
this.message.send("test0", Buffer("01234")); //往'test0'发送Buffer数据类型数据'01234'
```

对应C代码接口:

- void js_message_rev_func ( const char  *name , rt_uint8_t  *data ,  rt_uint32_t  *size);

该接口在 工程目录下的`firmware/samples/js_user/js_user_port.c`内已经写出，用户只需将自定义的消息在该函数内部补全即可。

```c
static void js_message_rev_func(const char *name, rt_uint8_t *data, rt_uint32_t size)
{
    LOG_I("js_message name: %s", name);
    ... ...
    // js层的 test0 消息在这里传递过来
	else if (strcmp(name, "test0") == 0)
    {
        //用户将传递来的消息'test0',在此处进行处理即可。
    }
}

```

### on(name, func) / addListener(name, func)

该函数是event继承下来的， 用于监听C往JS发送的Message的消息（即消息回调）。

参数说明：

| 参数 | 类型     | 必填 | 说明         |
| ---- | -------- | ---- | ------------ |
| name | string   | 是   | 事件名称     |
| func | function | 是   | 事件回调函数 |

```javascript
this.message = Message(); //实例化Message对象。

//用户在JS层监听 test0 的消息, 并将该消息打印出来。
this.message.on("test0", function (event) { console.log(event.toString()) });
```

**注：JS监听的消息，是需要C往JS发送消息后才可以监听到。因此需要用户在C上完成消息发送的代码。**

```c
rt_bool_t js_send_message (const char  *name, rt_uint8_t *data, rt_uint32_t *size )
```

```c
static void js_message_rev_func(const char *name, rt_uint8_t *data, rt_uint32_t size)
{
    LOG_I("js_message name: %s", name);
    ... ...
    // js层的 test0 消息在这里传递过来
	else if (strcmp(name, "test0") == 0)
    {
        //用户可在此处将消息发送给JS层。
        js_send_message(name, (rt_uint8_t *)"receive test0", strlen("receive test0"));
    }
}
```

## 示例代码

```javascript
/*
本例子在JS层发送消息'01234'给C代码，然后C代码接收到消息，回应'receive test0', 用户在JS上监听到该消息并打印出来。
*/

var page = {
    /* 此方法在第一次显示窗体前发生 */
    onLoad: function (event) {
        this.message = Message();
        this.message.send("test0", "01234");
        this.message.on("test0", function (event) { console.log(event.toString()) });
    },
    /* 此方法展示窗体前发生 */
    onShow: function (event) {

    },
    /* 此方法展示窗体后发生 */
    onResume: function (event) {

    },
    /* 此方法关闭窗体前发生 */
    onExit: function (event) {

    },
};

Page(page);

page = 0;
```
```c
/*
用户需要将js_message_rev_func函数进行补全完整，然后编译固件重新烧录才能与JS通信。
（该函数在工程目录下的`firmware/samples/js_user/js_user_port.c`内）
*/

static void js_message_rev_func(const char *name, rt_uint8_t *data, rt_uint32_t size)
{
    LOG_I("js_message name: %s", name);
    ... ...
    // js层的 test0 消息在这里传递过来
	else if (strcmp(name, "test0") == 0)
    {
        //用户可在此处将消息发送给JS层。
        js_send_message(name, (rt_uint8_t *)"receive test0", strlen("receive test0"));
    }
}
```



更多相关的JS与C的操作可以参考`PersimM3_JS_GUI_C_TransData`文档。



