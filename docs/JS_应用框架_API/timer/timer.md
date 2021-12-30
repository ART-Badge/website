# Timer

可在 JS 脚本中使用的定时器，分为单次超时和重复超时两种类型。

注：`在使用timer时，一般将其定义在page对象内，作为page的属性之一，这样在page退出时可以将无用的timer释放掉，防止内存泄漏`

## setTimeout(timeout, tick, name)

  单次超时定时器配置使能接口。
  
| 参数    | 类型     | 必填 | 说明                                                                |
|---------|----------|------|---------------------------------------------------------------------|
| timeout | function | 是   | 定时器超时回调函数 |
| tick    | number   | 是   | 定时器定时时长，单位毫秒 ms                                         |
| name    | string   | 否   | 定时器名称                                                          |

| 返回值 | 类型   | 说明          |
|--------|--------|---------------|
| timer  | object | JS Timer 对象 |

``` demo
// timer1定义在page内，是page属性之一，调用时要加this
this.timer1 = setTimeout(function () { console.log("Timeout!") }, 1000, "timer1")
// 1000ms后，控制台输出 “Timeout!”
console.dir(this.timer1) 
// 输出 {tick: 1000.000000, timeout: [function], name: "timer1"},说明timer的属性值即为setTimeout入参值
```

## setInterval(timeout, tick, name)

  重复超时定时器配置使能接口。
  
| 参数    | 类型     | 必填 | 说明                                                                |
|---------|----------|------|---------------------------------------------------------------------|
| timeout | function | 是   | 定时器超时回调函数，回调函数中 `this` 对象绑定的是 `timer` 对象本身 |
| tick    | number   | 是   | 定时器定时时长，单位毫秒 ms                                         |
| name    | string   | 否   | 定时器名称                                                          |

| 返回值 | 类型   | 说明          |
|--------|--------|---------------|
| timer  | object | JS Timer 对象 |

``` demo
this.timer2 = setInterval(function () { console.log("Timeout!")) }, 1000, "timer2")
console.dir(this.timer2)
```

## clearTimeout(timer)/clearInterval(timer)

  定时器清空接口。

| 参数  | 类型   | 必填 | 说明       |
|-------|--------|------|------------|
| timer | object | 是   | 定时器对象 |

``` demo
clearTimeout(this.timer1);
clearInterval(this.timer2);
```

## JS timer 使用注意事项

- `setTimeout` / `clearTimeout` 或者 `setInterval` / `clearInterval` 要成对使用，在合适的时刻一定要删除定时器。注意，即使是只会超时一次的 `setTimeout` 也一定要手动删除。`否则，在页面频繁切换或其他情况下，系统会因内存泄漏完而宕机!`
- 在代码中操作定时器变量时，切勿重新赋值。应该确保赋值之前该变量已经不持有定时器（不然就要先删除定时器）
- Page 退出时应该删除当前 Page 中还存在的所有 Timer。在 `onExit` 方法中删除即可。

## 使用示例

```demo

var page = {
  /* 将 timer1、timer2 定义为page对象的两个属性值 */
  timer1: 0,
  timer2: 0,

onLoad: function (event) {

  /* onLoad方法被page对象调用，故此时 this 指代page，而timer又是page的对象
  所以用 this.timer1。*/
  this.timer1 = setTimeout(function(){
  console.log('Run once.')
  },1000,'timer1') // timer1是单次定时器

  this.timer2 = setInterval(function(){
  console.log('Run many times until the timer dead.')
  },2000,'timer2') // timer2是重复循环定时器
},

onExit: function (event) {
  /* 退出界面要手动删除定时器 */
  clearTimeout(this.timer1)
  clearTimeout(this.timer2)
},
}

Page(page);

page = 0;

```
