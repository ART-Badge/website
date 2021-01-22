# JS Event

JS的Event是一个用于发送、监听事件的对象类型。用户可以用Event来实现数据传递、触发消息回调等功能。

## Event()

获取 `Event` 对象。

注：可以重复获取，不会新建，为全局性对象。

``` javascript
this.event = Event();  //实例化Event对象
```

### mode(name, mode)

配置 `name` 名称事件的回调模式，当没有对事件进行配置时，默认模式为事件触发时回调所有注册函数。

参数说明：

| 参数 | 类型 | 必填 | 说明 |
|------|----------|------|---------|
| name | string   | 是   | 事件名称 |
| mode | bool     | 是   | 值为 `false` 事件触发时回调所有注册函数， `true` 则在事件触发时只调用最后一个注册的事件回调函数 |

```javascript
var page = {
      /* 此方法在第一次显示窗体前发生 */
  onLoad: function (event) {
      
      	this.event = Event();  //实例化Event对象

      	this.event.mode("test0", true);  //事件触发时只调用最后一个注册函数

      	//该函数是第一个注册的事件回调，将无法监听到事件
      	this.event.on("test0", function (event) { console.log("function 1: " + event); });
      	//该函数是最后一个注册的事件回调，将监听到事件
      	this.event.on("test0", function (event) { console.log("function 2: " + event);});

      	this.event.emit("test0", "emit test0");  //触发回调函数
      
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

### on(name, func) / addListener(name, func)

往 `name` 名称的事件中注册一个回调函数 `func`，当 `name` 事件被触发时，便会触发回调函数`func`。

`on`和`addListener`方法一样，使用上无任何差别。

参数说明：

| 参数 | 类型 | 必填 | 说明 |
|------|----------|------|---------|
| name | string   | 是   | 事件名称 |
| func | function | 是   | 事件回调函数 |


### emit(name, args, ...)

触发 `name` 名称的事件并传参 `args` 。

参数说明：

| 参数 | 类型                    | 必填 | 说明         |
|------|-------------------------|------|--------------|
| name | string                  | 是   | 事件名称     |
| args | string/number/object 等 | 否   | 回调函数入参 |

```javascript
this.event = Event(); //实例化Event对象，默认配置是触发时回调所有注册函数

// test0事件传递一个参数
this.event.on("test0", function (event) { console.log("test0: " + event) });
// test1事件传递两个参数
this.event.on("test1", function (event, value) { console.log("test1: "+ event + value)});

this.event.emit("test0", "emit test0");  //触发test0事件，并传递一个参数
this.event.emit("test1", "emit test2  ", "test2 emit"); //触发test1事件，并传递两个参数

```

### removeListener(name, func)

移除 `name` 名称事件中注册的 `func` 回调函数。

  参数说明：

| 参数 | 类型     | 必填 | 说明         |
|------|----------|------|--------------|
| name | string   | 是   | 事件名称     |
| func | function | 是   | 回调函数入参 |

```javascript
this.event = Event();

this.event.on("test0", this.test0 = function (event) {console.log(event) });

this.event.emit("test0", "emit test0 1");

this.event.removeListener("test0", this.test0); //移除 test0 回调函数 this.test0

this.event.emit("test0", "emit test0 2");  //此时再触发test0, 回调函数 this.test0 将不会触发
```

### removeAllListeners(name)

移除 `name` 名称事件中所有注册回调函数。

参数说明：

| 参数 | 类型   | 必填 | 说明     |
|------|--------|------|----------|
| name | string | 是   | 事件名称 |

```javascript
this.event = Event();

this.event.on("test0", this.func1 = function (event) {console.log("func1: " + event) });
this.event.on("test0", this.func2 = function (event) {console.log("func2: " + event) });

this.event.emit("test0", "emit event1");

this.event.removeAllListeners("test0"); //移除所有触发注册的回调函数

this.event.emit("test0", "emit event2");  //此时再触发test0, 回调函数 都不会触发
```


### removeEvent(name)

移除 `name` 名称事件包括所有注册回调函数。

参数说明：

| 参数 | 类型   | 必填 | 说明     |
|------|--------|------|----------|
| name | string | 是   | 事件名称 |

```javascript
this.event = Event();

this.event.on("test0", this.func1 = function (event) {console.log("func1: " + event) });
this.event.on("test0", this.func2 = function (event) {console.log("func2: " + event) });

this.event.emit("test0", "emit event1");

this.event.removeEvent("test0"); //移除 test0 事件，同时移除所有注册的回调函数

this.event.emit("test0", "emit event2");  //此时再触发test0, 回调函数 都不会触发
```

注： `removeAllListeners` 与 `removeEvent`的区别：

从用户使用角度讲，这两个函数使用方法以及功能都是一样的，效果也是一样的。而从资源释放角度讲，`removeAllListeners`是释放了所有的注册回调函数，而`removeEvent`是连同事件一块释放掉了，资源的释放更彻底。

### eventNames()

获取 `Event` 中所有的事件名称。

返回值说明：

| 类型  | 说明                      |
|-------|---------------------------|
| array | 事件名称数组，string 数组 |

```javascript
this.event = Event();
//注册两个回调函数 test0 和 test1
this.event.on("test0", function (event) { console.log(event) });
this.event.on("test1", function (event) { console.log(event) });

console.dir(this.event.eventNames()); //获取所有注册事件名称
```

### destroy()

销毁 `Event` ，即清除 `Event` 中所有的事件。

```javascript
this.event = Event();

this.event.on("test0", function (event) { console.dir(event) });
this.event.on("test1", function (event) { console.dir(event) });

this.event.destroy(); 
```

## 实例代码

```javascript
var page = {
      /* 此方法在第一次显示窗体前发生 */
  onLoad: function (event) {
      
      	this.event = Event();  //实例化Event对象

      	this.event.on("test0", function (event) { console.log("function 1: " + event); });
      	this.event.on("test0", function (event) { console.log("function 2: " + event); });
      	this.event.emit("test0", "emit test0");  //触发回调函数

        this.event.on("test1", this.test1 = function (event) { console.log("function 3: " + event); });
        this.event.emit("test1", "emit test1 once");  //第一次触发回调函数
        this.event.removeListener("test1", this.test1);
        this.event.emit("test1", "emit test1 again");  //第二次触发回调函数，因为已经移除监听事件，则this.test1将不能触发回调

        console.dir(this.event.eventNames()); //获取所有注册事件名称,此时的event 有 ["test0","test1"]
        this.event.removeEvent("test1"); //移除 test1 事件，同时移除所有注册的回调函数
        console.dir(this.event.eventNames()); //获取所有注册事件名称，此时event只剩下["test0"]

        this.event.destroy();  //销毁Event事件
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
